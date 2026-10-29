# Install CrossADFS and AcornFormat

Download **CrossAcorn-Setup-0.9.25.zip** from [Releases](https://github.com/MasterCatsUK/CrossADFS/releases/tag/v0.9.25) and extract the whole drawer, retaining the `.info` files. Close Acorn files and Format windows, then double-click **Install**. The native Amiga Installer handles the copy steps. Restart once afterward to load the updated handler. Installation itself does not format a disk.

The update adds file-comment metadata round trips and expanded filetype associations. Read [METADATA.txt](METADATA.txt) before testing copies, and [FILETYPES.txt](FILETYPES.txt) for the complete mapping. Use a native Amiga disk or RAM: for the metadata test; a Mac/emulator shared folder may discard comments.

The Installer utility supplied with your Amiga setup must be installed. The Install icon's Default Tool is `Installer`; if it is not on the command path, use Icon Information to select the actual installed utility. No third-party Installer binary is bundled.

## App location

Open your system disk → **Tools → AcornFormat**. The files are `SYS:Tools/AcornFormat` and `SYS:Tools/AcornFormat.info`. A matching command copy is installed in `C:` for Shell use and Workbench Format Disk integration.

## Installed files

| Location | Purpose |
| --- | --- |
| `L:CrossADFSFileSystem` | ADFS filesystem |
| `DEVS:DOSDrivers/ADFS0` | Automatic boot mount for internal DF0 |
| `C:CrossAcornControl` | Filesystem controls |
| `C:CrossAcornStatus` | Filesystem status |
| `C:CrossAcornDriveStatus` | Read-only drive diagnostics |
| `C:AcornFormat` and `.info` | Formatter command and icon |
| `SYS:Tools/AcornFormat` and `.info` | Visible formatter app |
| `SYS:System/Format` | Workbench Format dispatcher |
| `SYS:System/Format.Native` | Retained original Amiga Format command |

The installer does not edit Startup-Sequence or User-Startup. Keep `Format.Native`: it is how non-ADFS targets continue to open the original formatter. Re-running Install supports updates and retains the original formatter.

## Workbench Format Disk

Select a recognised Acorn volume and choose Format Disk. This opens AcornFormat bound to that inserted disk's ADFS format, shown in its title. It has no format dropdown; progress stays in the main window. Reopen it after changing disks.

Open AcornFormat from Tools to select another ADFS format or prepare blank media. [Formatting guide](AcornFormat.txt).

## Pause and reports

Close Acorn files/windows before issuing `CrossAcornControl STOP` to pause monitoring; `CrossAcornControl START` resumes it. Save `RAM:AcornFormatReport.txt` after a formatting failure. Installer logging, when enabled, uses `RAM:CrossAcornInstall.log`.

## Restore the original Format command

The installer drawer contains `CrossADFSFormatInstall`. To restore the retained native Format command, open a Shell in that drawer and run:

```text
CrossADFSFormatInstall REMOVE
```

This restores only the Format dispatcher. It does not remove the filesystem, ADFS0 mount or formatter app. Restart after making mount changes.
