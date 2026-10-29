# Credits, references and provenance

CrossADFS builds on the work of the Acorn/RISC OS and Amiga communities.
The first public project page omitted these acknowledgements. That omission
has been corrected. Thank you to the authors and maintainers below.

This list distinguishes format documentation, implementation references,
compatibility research, linked runtime components and development tools.
Acknowledgement does not imply an author's endorsement.

## Project direction and AI assistance

CrossADFS is Andrew's personal project, which he decided to share with the
community.

**Andrew / MasterCatsUK** directs the project, chooses its features, supplies
test material and feedback, and carries out physical testing on the Amiga
and Acorn A3010.

**OpenAI's ChatGPT/Codex** has provided substantial AI assistance with
research, implementation and code generation, debugging, automated tests,
documentation and release preparation. This is an AI-assisted development
project. The original authors of referenced or reused work remain credited
below; AI assistance does not replace those acknowledgements or resolve the
outstanding provenance/licence review.

## ADFS and FileCore

- **Acorn Computers and the authors of the RISC OS Programmer's Reference
  Manuals** — FileCore disc records, allocation maps, directory entries,
  checksums, file attributes, sprites and screen modes. References:
  [FileCore](https://www.riscos.com/support/developers/prm/filecore.html),
  [ADFS](https://www.riscos.com/support/developers/prm/adfs.html),
  [FileSwitch](https://www.riscos.com/support/developers/prm/fileswitch.html),
  [sprites](https://www.riscos.com/support/developers/prm/sprites.html) and
  [video](https://www.riscos.com/support/developers/prm/video.html).
- **Russell King and Linux ADFS contributors** — prior ADFS implementation
  work. An earlier CrossAcorn source note explicitly identifies the Linux
  `fs/adfs` algorithms alongside the Acorn PRM as the basis for adaptations
  in the original read-only validator, including ZoneCheck/map layout and
  directory check-byte handling. Relevant source:
  [map.c](https://github.com/torvalds/linux/blob/master/fs/adfs/map.c) and
  [dir_f.c](https://github.com/torvalds/linux/blob/master/fs/adfs/dir_f.c).
  Those Linux files identify Russell King and carry GPL-2.0-only notices.
- **Acorn, Castle Technology and the FileCore contributors** — FileCore
  source and internal documentation were consulted to check allocation,
  directory and formatting behaviour. The inspected reference tree was
  [RISC_OS_AWH3Dev](https://github.com/experimentech/RISC_OS_AWH3Dev), whose
  FileCore files carry Castle/licensor notices. Their existing licence
  terms are not replaced by this acknowledgement.

### Provenance status

The earlier Linux-algorithm adaptation note means it would be inappropriate
to describe the entire inherited implementation as independently authored
without further review. A complete code-provenance and licence review has
not yet been completed. This acknowledgements page is not a substitute for
any source-distribution, notice or permission obligations where code has
been incorporated or adapted. The current repository contains public
runtime releases and documentation, rather than the complete development
source. That distribution choice does not by itself settle those obligations.

Specific missing references or code similarities can be reported through a
project issue for review. Sources are credited when their involvement is
established, rather than attributing code to someone merely because they
raised a question about the project.

## Long filenames

- **Jason Tribbeck — LongFiles** — the author and original application
  used for LongFiles format compatibility research and index tests.
  [Author's LongFiles page](https://www.tribbeck.com/index.php/software/longfiles).
  The author's private source was not obtained. The LongFiles application
  is not bundled with the CrossADFS installer.
- **Arcarc and APDL archive maintainers** — preservation and availability of
  historical LongFiles materials used during compatibility research.
  [Arcarc](https://arcarc.nl/) and [APDL library](https://www.riscos.com/apdl/pd_library/main.htm).

## Filetype associations and format recognition

- **Acorn PRM authors, RISC OS Products Directory maintainers and RISC OS Internet/MimeMap maintainers** — published filetype numbers, foreign extension associations and modern document/archive mappings. References: [PRM filetypes](https://www.riscos.com/support/developers/prm/filetypes.html), [historical directory](https://www.riscos.com/the_archive/rol/productsdb/sw/types.htm) and [MimeMap reference](https://github.com/experimentech/RISC_OS_AWH3Dev/blob/master/RISC_OS_Dev/mixed/RiscOS/Sources/SystemRes/Internet/Resources/files/MimeMap).
- **DigitalCD/TimPlayer author and maintainers** — tracker player/filetype associations. [TimPlayer documentation](https://www.riscos-digitalcd.net/digitalcd/modules/timplayer.htm).
- **Jerry Morrison / Electronic Arts and Commodore-Amiga contributors** — the IFF ILBM format specification. [ILBM specification](https://wiki.amigaos.net/wiki/ILBM_IFF_Interleaved_Bitmap).
- **Lars Hamre, Norman Lin, Kurt Kennett, Mark Cox, Peter Hanning, Steinar Midtskogen, Marc Espie and Thomas Meyer**, credited by the module format document — documented SoundTracker/NoiseTracker/ProTracker fields and signatures. [Module format reference](https://www.aes.id.au/modformat.html).

These references informed the new filetype associations and bounded checks of incoming file bytes. The complete supported list and application-dependent distinctions are in [FILETYPES.txt](docs/FILETYPES.txt). They do not close the wider provenance/licence review above.

## Amiga interfaces and icon formats

- **Commodore/Amiga documentation authors and the AmigaOS developer
  documentation maintainers** — DOS packets, filesystem startup, Workbench,
  Intuition controls and device interfaces. References:
  [ROM Kernel Reference Manual: DOS](https://developer.amigaos3.net/sites/default/files/downloads/2024-10/Amiga_ROM_Kernel_Reference_Manual_DOS.pdf),
  [Workbench Library](https://wiki.amigaos.net/wiki/Workbench_Library) and
  [CrossDOS manual](https://wiki.amigaos.net/wiki/AmigaOS_Manual%3A_Workbench_CrossDOS).
- **Michiel Pelt and the PFS3 contributors** — PFS3 source was consulted to
  understand native filesystem startup and Workbench Format behaviour.
  [PFS3 source distribution](https://aminet.net/package/disk/misc/PFS3src).
  PFS3 is not bundled with the installer.
- **The AROS Development Team** — icon-library readers and structure
  definitions were consulted to check classic DiskObject and colour-icon
  serialization. References:
  [diskobjio.c](https://github.com/aros-development-team/AROS/blob/master/workbench/libs/icon/diskobjio.c),
  [diskobj35io.c](https://github.com/aros-development-team/AROS/blob/master/workbench/libs/icon/diskobj35io.c)
  and [icon_intern.h](https://github.com/aros-development-team/AROS/blob/master/workbench/libs/icon/icon_intern.h).
- **Andreas Falkenhahn / Airsoft Softwair — Iconic documentation** — an
  additional icon-format reference. [Iconic manual](https://www.hollywood-mal.com/docs/pdf/iconic.pdf).
- **CrossMAC developers and historical documentation authors** — the supplied
  CrossMAC binary and published material were inspected for drive/handler
  identification and default-icon behaviour. CrossMAC is not bundled.

## Runtime and development tools

- **GNU GCC/libgcc developers and Amiga toolchain maintainers** — the m68k
  compiler and linked integer-support routines.
- **libnix authors and AmigaPorts maintainers** — the C runtime linked into
  the command-line/GUI programs. [libnix project and manual](https://github.com/AmigaPorts/libnix).
- **Christian Vogelgsang and amitools/vamos contributors**, with the
  machine68k/Musashi contributors — m68k execution, Amiga filesystem/image
  tooling and automated test infrastructure.
  [amitools](https://github.com/cnvogelg/amitools).
- **InstallerLG authors and contributors** — interpreter used for isolated
  installer-script tests. [InstallerLG](https://github.com/sodero/InstallerLG).
  InstallerLG is not bundled: installation uses the user's Amiga Installer.
- **Amiga NDK authors and maintainers** — headers, function descriptors and
  API-version information used during compilation and compatibility checks.
  The SDK is not included in the runtime download.

## Artwork, screenshots and testing

- **Coffin OS and the creators of the supplied floppy artwork** — the
  user-supplied Coffin floppy icon was the visual basis for the combined
  Acorn floppy artwork. The individual original icon artist has not yet
  been established; this is not a claim of original authorship of that art.
- **Acorn's original logo designers** — the supplied green Acorn emblem.
  The combined badge/icon was produced with AI-assisted image editing and
  converted to Amiga icon formats.
- **Andrew / MasterCatsUK** — project direction, supplied icons and captures,
  repeated physical Amiga/A3010 disk tests, verification and feedback.
  Background-removed screenshot presentation edits are labelled; original
  Coffin OS captures remain available.

This list reflects the retained evidence and will be corrected when additional
sources are established. Public availability of a document or source does not
make it public domain or remove the need to respect its terms.
