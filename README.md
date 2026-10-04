# VLC for AmigaOS (port in progress)

A port of the VLC media player to AmigaOS 3.x, on the Open family: video
through OpenRTG and OpenGPU, decoding through OpenMedia (the graphics chip's
video engines, or the PC's on AmigaChrome), sound through AHI, network streams
through OpenSocket, and a GadTools window. This is an unofficial port; it is
not made or endorsed by VideoLAN.

Dale, 4 October 2026: "can we port VLC to the Amiga based on our OpenRTG,
OpenGPU, and the not specified openmediahardware project, that work will drive
that media hardware idea". `PORTING.md` is the plan.

Status, 4 October 2026: planned.

## Licences

Unlike the rest of the Open family, this repository is not MIT, because it is
VLC's code and ours joined to it:

- libVLC and libvlccore, and most of VLC's modules, are under the GNU Lesser
  General Public License 2.1 or later (`COPYING.LIB`). Our Amiga modules
  (video output, audio output, the OpenMedia decoder, the window) are under
  the same licence, Copyright (c) 2026 Dalsin Limited.
- The VLC player and some modules are under the GNU General Public License 2
  or later (`COPYING`).
- FFmpeg, when built in, keeps its own licence (LGPL 2.1 or later, or GPL with
  some options).
- OpenMedia, OpenRTG, OpenGPU and OpenSocket themselves are MIT, in their own
  repositories; this port only uses them.

VLC's source is VideoLAN's (https://code.videolan.org/videolan/vlc); this
repository holds what the Amiga needs on top of a pinned VLC version.

"VLC" and the cone are VideoLAN's trademarks. Their trademark policy is
checked before anything is released under that name.

Our Amiga port was started by Dale Kirkwood at Dalsin Limited, for AmigaChrome.
