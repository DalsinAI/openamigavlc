# Restart: VLC for AmigaOS

_Written 6 October 2026 at about 23:55 UTC, while all work is paused on @SacredTrees's word (23:28 UTC). Read this first when work resumes; the newest capsule and the live PR list win if they disagree._

## What this repo is

A port of VLC to AmigaOS 3.x with a GadTools interface, drawing through OpenRTG and OpenGPU and decoding through OpenMedia. Unofficial; VLC's LGPL/GPL kept.

## Where it stands

Designed, not started. It waits on OpenGPU, the ACRTG v3 ring and OpenMedia.

## Merged lately

- #1 (38c0e52, 2026-10-06): Credit who made VLC for AmigaOS: CONTRIBUTORS.md

## Open pull requests

- None.

## Next step

1. Start after OpenMedia has a host-decode driver.

## Waiting on @SacredTrees

- Nothing.

## Who owns it

No active thread.

## Capsules

Restart capsules for this repo's workstreams, in amigachrome's `capjumps/` shelf:

- [`20261006_AmigaChrome_OpenGPU_Mesa_GPU_Restart_Capsule.zip`](https://github.com/DalsinAI/amigachrome/tree/main/capjumps)

Team rules that still hold: commits as SacredTrees with no co-author lines; third-party code only on "yes with review" (licence checked, commit and sha256 pinned, fetched at build, never committed); deploys with deploy_dev.py only, on a typed line.
