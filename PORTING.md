# Porting VLC to AmigaOS

From AmigaChrome's design for OpenMedia and VLC (4 October 2026). VLC drives
OpenMedia as the browser drives OpenRTG: what the player needs decides what
OpenMedia offers first.

## What it needs

- **Toolchain:** pthreads and C11/C++, from the GCC 16 stove and its
  compatibility library.
- **The machine:** OpenSocket for network streams, AHI for sound, OpenRTG for
  the window, OpenGPU for scaling and colour conversion, and OpenMedia for
  decoding.

## Its Amiga modules

- **Video output:** OpenRTG and OpenGPU, in a window or full screen on any
  monitor. Decoded frames are composited from video RAM with no CPU copy.
- **Audio output:** AHI, timed against the video clock.
- **Decoder:** OpenMedia, hardware first (H.264, then HEVC), with FFmpeg as the
  CPU fallback.
- **Input:** files, and network streams through OpenSocket.
- **Interface:** a GadTools window with the controls VLC's simple interfaces
  have (open, play, pause, seek, volume, playlist).

## Phases

| Phase | Delivers | Done when |
| --- | --- | --- |
| 1 | OpenMedia decodes H.264 in AmigaChrome (its own repository); a test player | A 1080p H.264 file plays smoothly on an OpenRTG monitor |
| 2 | VLC built for OS 3.2 with the Amiga modules above | VLC plays a local file and a network stream |
| 3 | HEVC, VP9 and AV1 through OpenMedia | |
| 4 | A PiStorm (VideoCore through OpenMedia), and the CPU path | VLC plays on a PiStorm |
| 5 | An Installer; Aminet (gfx/show), after VideoLAN's trademark policy is checked | |
