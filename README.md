# VLC for AmigaOS (port in progress)

A port of the VLC media player to AmigaOS 3.x. It has a GadTools interface
and leaves the drawing to OpenRTG and OpenGPU wherever it can: frames stay in
video RAM, and they are converted, scaled and composited by the graphics
board. Decoding goes through OpenMedia (the graphics chip's video engines, or
the PC's on AmigaChrome), sound through AHI, and network streams through
OpenSocket. This is an unofficial port, not made or endorsed by VideoLAN.

We, 4 October 2026: "can we port VLC to the Amiga based on our OpenRTG,
OpenGPU, and the not specified openmediahardware project", and "it should
have a GadTools interface but leverage OpenRTG as much as possible".
`PORTING.md` is the plan.

Status, 4 October 2026: planned.

## Licences

Our files are MIT; VLC's files keep VLC's licences, and everything we ship
complies with them. We, 4 October 2026: "we want to stay legal, so we
comply with the licences; our parts are MIT".

- **Our files** are MIT, Copyright (c) 2026 Dalsin Limited (`LICENSE`). This
  covers the Amiga modules (the GadTools interface, OpenRTG video output, AHI
  audio output, the OpenMedia decoder), the build scripts and the documents.
  Each source file says so on an SPDX line (`SPDX-License-Identifier: MIT`).
- **VLC's code** belongs to VideoLAN and its authors and keeps its licences.
  libVLC, libvlccore and most modules are LGPL 2.1 or later (`COPYING.LIB`).
  The player and some modules are GPL 2 or later (`COPYING`). A change we make
  to one of VLC's files stays under that file's licence. FFmpeg, when built
  in, keeps its own licence.
- **Written fresh.** Our modules are written against VLC's module interface,
  not copied from VLC's modules, so they can be MIT. A file that does start
  from one of VLC's files keeps VLC's licence and says so on its SPDX line.
- **What we ship complies.** The built player is a GPL 2-or-later program as
  a whole. MIT code may be part of it, and our files stay MIT on their own.
  Every release names the VLC version and includes `COPYING`, `COPYING.LIB`
  and `LICENSE`. It also includes the complete source (our files, VLC's, and
  our changes to VLC's), or a written offer of it.
- OpenMedia, OpenRTG, OpenGPU and OpenSocket are MIT, in their own
  repositories. This port only uses them.

VLC's source comes from VideoLAN (https://code.videolan.org/videolan/vlc), at
a pinned release. This repository holds what the Amiga needs on top of it.

"VLC" and the cone are VideoLAN's trademarks. Their trademark policy is
checked before anything is released under that name.

If you use or build on our part of this work, we ask (we do not require)
that you credit Dalsin Limited and AmigaChrome. The Amiga port was started by
Dalsin Limited, for AmigaChrome.

## Contributors

VLC for AmigaOS is created and maintained by [SacredTrees](https://github.com/SacredTrees) with the AmigaChrome agent team, copyright Dalsin Limited. Everyone whose work it includes is credited in [`CONTRIBUTORS.md`](CONTRIBUTORS.md).
