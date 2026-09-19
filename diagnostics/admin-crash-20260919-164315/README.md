# WESTSIDE ADMIN crash diagnostics

**DIAGNOSTICS ONLY - NOT A CRASH FIX.**

This package enables the launcher's existing full-memory crash dump option.
It does not change updater heads, manifests, the bootstrap, or runtime DLLs.
The latest runtime release remains `5a322ef5ea5a32533feff3466601a8650d5c2e32`.

[Download the diagnostic ZIP](WESTSIDE_ADMIN_DIAGNOSTICS_20260919_164315.zip)

## Use on the PC that crashes

1. Extract the ZIP and close WESTSIDE ADMIN and its crash dialog.
2. Run `01_ENABLE_FULL_DUMP.cmd`. The helper backs up `CitizenFX.ini`, enables
   full dumps, and temporarily disables automatic crash uploads.
3. Restart ADMIN and reproduce the crash once. Allow several GB of free space
   and wait for the dump to finish writing.
4. Retain the new `*-full.dmp` in `crashes` and the matching session log in
   `logs`, next to the runtime's `CitizenFX.ini`.
5. Close WESTSIDE and run `02_RESTORE_SETTINGS.cmd` to restore the previous
   diagnostic/upload settings without overwriting other INI edits.

See `README_VI.txt` inside the ZIP for Vietnamese instructions and custom paths.
The helper does not delete caches, stop processes, disable anti-cheat, or upload
files. It has passed six fixture test groups; this is not gameplay validation.

## Investigation status

The supplied crash is `washington-twenty-july`, build 3258, at RVA `0x2FB6E8`:
the game reads `[RAX+0x290]` with `RAX=0`. The previous guard was installed.
The small dump does not include the relevant object or getter code, so the
source of the missing state is not yet established. No new runtime fix is
claimed or deployed by this diagnostic publication.

**Keep full dumps private.** They can contain credentials, chat, and other
personal data. Do not post dumps, logs, INI files, or configuration backups to
GitHub. This directory contains only the helper package and its checksum.
