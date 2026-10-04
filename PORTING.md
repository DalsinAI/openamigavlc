# Porting VLC to AmigaOS

From AmigaChrome's design for OpenMedia and VLC (4 October 2026). VLC drives
OpenMedia as the browser drives OpenRTG: what the player needs decides what
OpenMedia offers first.

## What it needs

- **Toolchain:** pthreads and C11/C++, from the GCC 16 stove and its
  compatibility library.
- **The machine:** OpenRTG for the picture, OpenGPU for conversion, scaling
  and compositing, OpenMedia for decoding, AHI for sound, and OpenSocket for
  network streams.

## Its Amiga modules

Each one is a VLC module of our own, written fresh against VLC's module
interface and MIT-licensed (see the README).

- **Interface:** GadTools (below).
- **Video output:** OpenRTG and OpenGPU (below).
- **Audio output:** AHI, timed against the video clock.
- **Decoder:** OpenMedia, hardware first (H.264, then HEVC), with FFmpeg as
  the CPU fallback.
- **Input:** files, and network streams through OpenSocket.

## The interface: GadTools controls, OpenRTG drawing

Dale, 4 October 2026: "it should have a GadTools interface but leverage
OpenRTG as much as possible". GadTools draws the controls. OpenRTG and
OpenGPU draw everything else, and the CPU never touches a pixel of the
picture.

**Why GadTools.** Dale, the same day: "GadTools is universal and we can
always alter its look and feel with a patch or tweak to the relevant library,
not chase our tail across a dozen UI things". GadTools runs on every OS 3.x
and on AROS. Its gadgets are drawn by intuition's frameiclass and sysiclass,
and OpenRTG's window look chains exactly those classes. So the player's look
changes when the library changes, for every GadTools program at once, and the
player keeps no look of its own.

**The window.** The video is at the top, with a GadTools row beneath it:
open, play/pause, stop, previous and next, a seek slider with the time, a
volume slider and full screen. The menus are GadTools menus, and the
playlist is a GadTools list view in a window of its own. On an OpenRTG
system with the new window look, the window and its gadgets get that look as
every other GadTools program does, with nothing in the player for it.

**Where OpenRTG does the work:**

| Job | How | Not |
| --- | --- | --- |
| Frames | OpenMedia decodes into a surface in the monitor's video RAM (`AllocBitMapTags`) | Decoded on the CPU and copied |
| YUV to RGB, and scaling to the window | One OpenGPU COMPOSITE per frame (`CompositeTags`, filtered), straight into the window's area | A CPU conversion loop and `WritePixelArray` |
| Window resizing | The composite's scale changes; nothing is reallocated | Re-sizing buffers |
| Showing frames on time | The board shows a frame at the head's vertical blank | Tearing, or the CPU waiting on the beam |
| Subtitles, the on-screen seek bar, volume | Alpha surfaces composited over the frame | Drawn into each frame by the CPU |
| Full screen | An OpenRTG screen on the monitor the window is on, or the one chosen. Its mode comes from `GetMonitorDataTags`, and the prefs' Standard modes are offered first. Workbench stays on the other monitors | Fixed to one monitor |
| Controls in full screen | With OpenRTG's compositing, the GadTools window floats translucent over the video and fades | A second, hand-drawn control set |
| Screen dragging | The board composes the screens, so the video keeps playing while a screen in front is dragged | Freezing during a drag |
| Thumbnails (playlist, seek preview) | Scaled blits of decoded frames by the board | CPU scaling |

**Without OpenRTG.** The same modules also run on Picasso96 or CyberGraphX
systems through the CyberGraphX calls (`WritePixelArray`, with the CPU doing
YUV and scaling). That path is slower and only a fallback; OpenRTG is the
target.

## Phases

| Phase | Delivers | Done when |
| --- | --- | --- |
| 1 | OpenMedia decodes H.264 in AmigaChrome (its own repository); a test player that composites through OpenRTG | A 1080p H.264 file plays smoothly on an OpenRTG monitor, with no CPU copies |
| 2 | VLC built for OS 3.2 with the Amiga modules above, and the GadTools interface | VLC plays a local file and a network stream in its window and full screen |
| 3 | Subtitles and the on-screen display as composited surfaces; HEVC, VP9 and AV1 through OpenMedia | |
| 4 | A PiStorm (VideoCore through OpenMedia), and the CPU fallback path | VLC plays on a PiStorm |
| 5 | An Installer; Aminet (gfx/show), after VideoLAN's trademark policy is checked | |
