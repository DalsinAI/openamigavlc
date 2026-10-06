# Contributors

## Creator and maintainer

- **SacredTrees** ([@SacredTrees](https://github.com/SacredTrees)): created and maintains this AmigaOS port of VLC. VLC itself is made by VideoLAN and its authors; this is an unofficial port, not made or endorsed by VideoLAN.

## The AmigaChrome team

We are the AI agents who build VLC for AmigaOS alongside SacredTrees:

- **Agnus**, our coordinator, who keeps every thread moving.
- **Thufir**, **Kynes** and **Galen**, the earlier agents who started the work on SacredTrees's PC.
- **The Claude Code threads**, each one taking a piece of the work from design to release.

## Copyright holder

Our files (the Amiga modules, build scripts and documents) are
Copyright (c) 2026 Dalsin Limited, released under the MIT licence (`LICENSE`).

## Third-party work in this repository

| Component | Where | Authors | Licence |
| --- | --- | --- | --- |
| GNU General Public License, version 2: the licence of the VLC player and some modules | `COPYING` | Free Software Foundation, Inc. | Verbatim copies permitted |
| GNU Lesser General Public License, version 2.1: the licence of libVLC, libvlccore and most modules | `COPYING.LIB` | Free Software Foundation, Inc. | Verbatim copies permitted |

## Fetched at build time, not committed

- **VLC media player** (VideoLAN and its authors): from https://code.videolan.org/videolan/vlc at a pinned release. libVLC, libvlccore and most modules are LGPL 2.1 or later, the player and some modules GPL 2 or later. A change we make to one of VLC's files stays under that file's licence.
- **FFmpeg**, when built in, keeps its own licence.

### From our other repositories

OpenMedia, OpenRTG, OpenGPU and OpenSocket (MIT, Dalsin Limited) are used by
the port and live in their own repositories.

"VLC" and the cone are trademarks of VideoLAN. Amiga, AmigaOS and other
product names are trademarks of their respective owners.
