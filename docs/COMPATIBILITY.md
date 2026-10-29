# Compatibility and testing

Release: CrossADFSFileSystem 0.9.25 with AcornFormat 0.9.1, 29 October 2026.

## Intended platform

Classic 68k Amiga, 68020 or later, internal DF0, Kickstart and Workbench 3.1 or later. Integer/soft-float build; no FPU required. No ReAction, chooser.gadget, MUI or Coffin OS dependency. This does not add 68000, PPC-native AmigaOS or F+ support.

| Area | Validation |
| --- | --- |
| Workbench 3.2.1 and physical floppy | Testing reported by the user; copied files and disk verification checked on an Acorn A3010 |
| File-comment metadata round trip | The owner reported the preceding 0.9.24 round trip working on their Amiga/A3010 setup |
| Expanded 0.9.25 filetypes and streaming detection | Automated tests passed; physical hardware feedback still needed |
| Workbench 3.1 APIs | NDK-based source audit and V40-limited automated m68k tests passed |
| Full stock Workbench 3.1 boot | **Not tested**; no matching installation available |
| Other Workbench versions | Intended to use the same compatible interfaces; individual boot tests not performed |
| Native installer script | Interpreter tests for the exact public script; native 3.1 Installer GUI not boot-tested |
| 68020 and 68040 | Automated m68k execution passed |

## Automated checks

- 27 production C translation units compile with 51 post-V40 entry-point/wrapper names prohibited. A deliberately newer call is rejected. This includes the metadata codec and the unchanged AcornFormat sources.
- 62 automated m68k runs passed for 0.9.25 on 68020/68040: eight filetype runs, eight metadata runs and 46 regression runs, with 65,140 assertions in total. The runs use controlled Amiga API/device endpoints, not a complete Workbench boot.
- The earlier 0.9.23 V40-runtime compatibility baseline passed 40 automated m68k runs with 9,800,010 assertions. These are earlier results, not additional runs of the new handler. NDK function tables, a runtime guard and positive/negative probes checked that baseline's OS boundary.
- The new filetype tests cover the associations, IFF/PDF/MOD signatures, CRLF text, exact copied bytes and metadata overriding inferred defaults. Seven host streaming-classifier tests and 16 existing host write tests also passed. The classifier uses bytes already supplied by the client; small, nested and 256KiB copy-flow models have identical raw read/write/erase counts to 0.9.24.
- Metadata tests cover typed and untyped load/execute fields, exact timestamps and attributes, files and nested drawers, zero and 65,537-byte files, all six orders of comment/date/protection copying, and refusal of malformed, incompatible, protected or busy restores. Native Amiga OFS/FFS image-storage tests from 0.9.24 demonstrate comment persistence, not a live Workbench copy.
- GUI endpoint tests cover native controls and titlebar tags, all format choices, inline progress, disk binding, cancellation, failures and cleanup. They are not a native Workbench renderer.
- Full-format models cover all writes preceding the verification pass, persistent disk contents, CRC and data corruption, cancellation and media changes for L/D/E/F.
- Quick-format models check exact metadata overlays, preservation of unrelated bytes, one metadata track for L/D/E or three for F, and failure handling without silently switching to Full Format.
- Drive and detection models cover density, protection, busy refusal, handover, cache invalidation, swaps and current-format observations from installed handlers.
- Workbench launcher tests cover CLI/WB forwarding and startup-message/resource lifetime.
- RAM disk-icon packet tests use copied L/D/E/F fixtures and leave whole image bytes unchanged. Delivered icons contain a standard DiskObject and complete 48×48 two-bitplane fallback before the optional colour extension.
- Installer interpreter tests cover fresh installation, updating, creation of a missing Tools drawer, pretend mode, missing files/native Format and helper failure. Production m68k installer-helper tests cover install/update/restore with byte checks in isolated SYS volumes.
- Public archive contents and checksums are verified.

The emulated tests use controlled GUI/device endpoints. They do not establish physical drive timing, full OS scheduling, native Workbench rendering or a complete ROM boot. The handler has been updated for metadata and filetypes; the AcornFormat app and icons remain byte-for-byte unchanged from the earlier tested release.

## Media

L/D/E need DD media and a supported Amiga 3.5-inch floppy drive. F needs HD media and an Amiga HD drive. CrossMAC/CrossDOS observations are informational and require matching handlers already running. They do not enable Mac GCR hardware support or Mac/PC formatting.

## Icons and screenshots

Stock Workbench 3.1 uses the standard four-colour icon fallback with its available palette. Newer icon libraries can use the colour extension. Coffin OS captures show that setup's appearance; background-removed presentation edits are labelled and originals are retained. No generated software preview is presented as a native boot-test screenshot.

The [AmigaOS version table](https://wiki.amigaos.net/wiki/AmigaOS_Versions) identifies V40 as 3.1; [DOS autodocs](https://developer.amigaos3.net/autodocs/dos.library/) explain the library-version annotations.
