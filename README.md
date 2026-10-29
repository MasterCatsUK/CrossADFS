<img src="docs/images/acorn-floppy.png" width="64" height="64" alt="CrossADFS green Acorn floppy icon" align="right">

# CrossADFS for Amiga

Read and write Acorn ADFS floppy disks from Workbench, and format or verify them with **AcornFormat**. Developed as CrossAcorn; the filesystem is **CrossADFSFileSystem** and mounts the internal drive as **ADFS0:**.

CrossADFS is my personal project, which I decided to share with the community. I'm Andrew (MasterCatsUK); I direct the project and carry out the physical testing on my Amiga and Acorn A3010.

**AI-assisted development:** I've had substantial help from OpenAI's ChatGPT/Codex with research, code generation, debugging, automated testing and documentation. See [development credits and sources](CREDITS.md).

**[Download the installer](https://github.com/MasterCatsUK/CrossADFS/releases/tag/v0.9.25)** · [Installation](docs/INSTALL.md) · [AcornFormat guide](docs/AcornFormat.txt) · [Metadata copying](docs/METADATA.txt) · [Filetypes](docs/FILETYPES.txt) · [Compatibility and testing](docs/COMPATIBILITY.md) · [Credits and sources](CREDITS.md)

The latest public **test release** is CrossADFSFileSystem **0.9.25**, with AcornFormat **0.9.1**. Download **CrossAcorn-Setup-0.9.25.zip** from Releases, extract the complete drawer, and double-click **Install**. GitHub's green Code download contains this project page and documentation, rather than the installer.

## New in 0.9.25

- Acorn metadata can survive ordinary Workbench copies and return trips through an Amiga file comment. This carries the original load/execute fields, filetype, full Acorn timestamp and catalogue attributes for files and drawers. No separate `.inf` file or copy application is required.
- Expanded new-file associations cover pictures, documents, music and archives, including IFF/ILBM, ProTracker modules, MP3, RTF, SVG, TAR/GZip/BZip2 and Office/OpenDocument formats.
- Streaming checks distinguish IFF pictures from other IFF containers, identify common ProTracker headers, and distinguish CRLF-only plain text without changing its bytes. They add no floppy reads; emulated copy-flow read/write/erase counts match 0.9.24.

Metadata preservation requires a destination and copy tool that retain Amiga file comments. Keep the comment and file intact: changed-length files cannot restore the old record, and ADFS L cannot represent every F/D/E attribute bit. Host shared folders, PC/FAT disks and archives may discard comments. This is catalogue preservation, not a guarantee for every application's extended metadata. See the [metadata guide and round-trip test](docs/METADATA.txt).

Filetype associations do not convert file contents or supply an Acorn viewer/player. Unknown IFF subtypes remain Data; `.img` disk images are not blindly assigned a picture type. Existing metadata carried back in the comment takes precedence over new-file defaults. See the [full mapping and limits](docs/FILETYPES.txt).

## What it does

- Opens recognised ADFS disks in Workbench for files and folders, including subfolders.
- Supports ADFS L, D, E and F, with LongFiles support and RAM-based sprite icons retained.
- Installs AcornFormat and its green Acorn floppy icon in **SYS:Tools**.
- Adds Workbench **Format Disk** integration for the selected Acorn volume. Other volumes are passed to the original Amiga formatter.
- Offers **Format**, **Quick Format**, **Verify** and **Cancel**, with progress inside the main window: red while writing and dark green while verifying.
- Checks the inserted disk when entering **Current format** in the standalone format menu. Installed, running CrossMAC/CrossDOS handlers can supply Mac/PC identification for information only, including Mac 1.44MB.

## Formats

| Format | Capacity | Media and drive |
| --- | --- | --- |
| ADFS L | 640K | DD floppy, supported Amiga 3.5-inch drive |
| ADFS D | 800K | DD floppy, supported Amiga 3.5-inch drive |
| ADFS E | 800K | DD floppy, supported Amiga 3.5-inch drive |
| ADFS F | 1.6M | HD floppy and an Amiga HD drive |

F+ is not supported. Mac and PC formatting are not included.

## Requirements and test status

Classic Amiga, **68020 or later**, internal **DF0:**, and **Kickstart/Workbench 3.1 or later**. Uses integer code; no FPU is required. No ReAction, chooser.gadget, MUI or Coffin OS dependency.

Physical disk testing has been reported on **Workbench 3.2.1** with copied files and disk verification checked on an **Acorn A3010**. The owner also reported the **0.9.24 metadata round trip working** on that setup. For 0.9.25, **62 automated m68k runs with 65,140 assertions** passed across 68020/68040 and L/D/E/F; source/API checks prohibit post-V40 calls. The expanded filetype checks still need physical hardware feedback. **A full stock Workbench 3.1 boot has not been tested.** Later Workbench releases have not each been independently boot-tested. See the [testing details](docs/COMPATIBILITY.md).

Workbench 3.1 uses the included standard four-colour icon fallback. Newer icon libraries can use the colour image; screen palette and theme affect its appearance.

## Install and open

1. Extract the complete installer ZIP on the Amiga and open its drawer.
2. Double-click **Install** and follow the Workbench Installer pages. Close Acorn files and Format windows first.
3. Restart once. The ADFS0 mount starts automatically; no StartCrossAcorn command is needed.
4. Open your system disk → **Tools → AcornFormat** to choose a format. To retain the inserted Acorn disk's format, select its volume and choose Workbench **Format Disk**.

The installed Amiga **Installer** utility must be available. If its name is not on the Workbench command path, select its installed location in the Install icon's Information window.

Formatting erases directory contents. Full Format writes all tracks before the separate verification pass. Quick Format requires a readable ADFS disk already in the chosen format; it only rewrites and verifies metadata tracks. [Read the guide](docs/AcornFormat.txt) before formatting.

## Coffin OS screenshots

![AcornFormat ready window](docs/images/coffin-ready-background-removed.png)

![Format list and Current format submenu](docs/images/coffin-menu-background-removed.png)

These are presentation edits of supplied Coffin OS captures, with the blue desktop background removed. The [original ready capture](docs/images/coffin-ready.png) and [original menu capture](docs/images/coffin-menu.png) are retained. “No disk / unavailable” reflects the menu capture's disk state. These images are not evidence of a Workbench 3.1 boot.

## Reports and support

If formatting fails, keep **RAM:AcornFormatReport.txt** before restarting. [Open an issue](https://github.com/MasterCatsUK/CrossADFS/issues) with the Workbench/Kickstart versions, CPU, drive/media type, selected ADFS format, steps to reproduce and report text. Do not include personal files or whole disks unless you intend to share their contents.

The runtime installer excludes development tests, logs, generated software previews and disk captures. This repository provides the public downloads, documentation and images; source code is not included in this release.

## Acknowledgements

CrossADFS draws on Acorn documentation and earlier community work, including
Russell King's Linux ADFS algorithms, Jason Tribbeck's LongFiles, and the
Amiga interface/icon references. See [credits, references and provenance](CREDITS.md)
for the recorded sources and the outstanding provenance/licence review.
