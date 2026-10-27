# Compatibility and testing

Release: CrossADFSFileSystem 0.9.23 with AcornFormat 0.9.1, 27 October 2026.

## Intended platform

Classic 68k Amiga, 68020 or later, internal DF0, Kickstart and Workbench 3.1 or later. Integer/soft-float build; no FPU required. No ReAction, chooser.gadget, MUI or Coffin OS dependency. This does not add 68000, PPC-native AmigaOS or F+ support.

| Area | Validation |
| --- | --- |
| Workbench 3.2.1 and physical floppy | Testing reported by the user; copied files and disk verification checked on an Acorn A3010 |
| Workbench 3.1 APIs | NDK-based source audit and V40-limited automated m68k tests passed |
| Full stock Workbench 3.1 boot | **Not tested**; no matching installation available |
| Other Workbench versions | Intended to use the same compatible interfaces; individual boot tests not performed |
| Native installer script | Interpreter tests for the exact public script; native 3.1 Installer GUI not boot-tested |
| 68020 and 68040 | Automated m68k execution passed |

## Automated checks

- 26 production C translation units compile with 51 post-V40 entry-point/wrapper names prohibited. A deliberately newer call is rejected.
- 40 automated m68k regression runs passed, with 9,800,010 assertions in total. Exec/DOS are configured as V40; NDK function tables and a runtime guard reject post-V40 calls. Separate positive and negative probes verify that boundary.
- GUI endpoint tests cover native controls and titlebar tags, all format choices, inline progress, disk binding, cancellation, failures and cleanup. They are not a native Workbench renderer.
- Full-format models cover all writes preceding the verification pass, persistent disk contents, CRC and data corruption, cancellation and media changes for L/D/E/F.
- Quick-format models check exact metadata overlays, preservation of unrelated bytes, one metadata track for L/D/E or three for F, and failure handling without silently switching to Full Format.
- Drive and detection models cover density, protection, busy refusal, handover, cache invalidation, swaps and current-format observations from installed handlers.
- Workbench launcher tests cover CLI/WB forwarding and startup-message/resource lifetime.
- RAM disk-icon packet tests use copied L/D/E/F fixtures and leave whole image bytes unchanged. Delivered icons contain a standard DiskObject and complete 48×48 two-bitplane fallback before the optional colour extension.
- Installer interpreter tests cover fresh installation, updating, creation of a missing Tools drawer, pretend mode, missing files/native Format and helper failure. Production m68k installer-helper tests cover install/update/restore with byte checks in isolated SYS volumes.
- Public archive contents and checksums are verified.

The emulated tests use controlled GUI/device endpoints. They do not establish physical drive timing, full OS scheduling, native Workbench rendering or a complete ROM boot. Existing runtime binaries required no change for the API-level 3.1 audit.

## Media

L/D/E need DD media and a supported Amiga 3.5-inch floppy drive. F needs HD media and an Amiga HD drive. CrossMAC/CrossDOS observations are informational and require matching handlers already running. They do not enable Mac GCR hardware support or Mac/PC formatting.

## Icons and screenshots

Stock Workbench 3.1 uses the standard four-colour icon fallback with its available palette. Newer icon libraries can use the colour extension. Coffin OS captures show that setup's appearance; background-removed presentation edits are labelled and originals are retained. No generated software preview is presented as a native boot-test screenshot.

The [AmigaOS version table](https://wiki.amigaos.net/wiki/AmigaOS_Versions) identifies V40 as 3.1; [DOS autodocs](https://developer.amigaos3.net/autodocs/dos.library/) explain the library-version annotations.
