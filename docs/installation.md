# Installation

## Quick install

| System | Command |
|---|---|
| macOS, Linux | `curl -fsSL https://raw.githubusercontent.com/huynvic/mini-albertcode-swe-agent/main/installer/install.sh \| sh` |
| Windows | `irm https://raw.githubusercontent.com/huynvic/mini-albertcode-swe-agent/main/installer/install.ps1 \| iex` |

The command downloads a small bootstrap script from this repository. The bootstrap finds the latest
release, downloads the installer for your system and processor, and checks it against the release's
published SHA-256 checksums. Then it runs the installer. If the checksum doesn't match, it stops
before running anything.

Prefer to read before running? Download [`installer/install.sh`](../installer/install.sh) or
[`installer/install.ps1`](../installer/install.ps1), read it, then run it.

## What the installer does

1. **Checks, changing nothing.** It looks for an existing mini-AlbertCode and its version, a running
   mini-AlbertCode service, a suitable Python, uv, Git, a browser for the browser tools, free disk
   space, and whether it can reach the package index.
2. **Shows its plan and asks `Proceed? [Y/N]`.** If you answer N, nothing changes.
3. **Installs, for your user only.**
   - It downloads what is missing first, so a failed download leaves an existing installation
     untouched.
   - It stops the service and replaces an older mini-AlbertCode, keeping your sessions.
   - It installs mini-AlbertCode in an environment of its own, so your other Python projects are
     unaffected.
   - It adds the `albert-mini` command to your PATH.
4. **Verifies.** It checks the version and the command. Then it starts the service once on a spare
   port, with a scratch folder of its own, and waits for it to answer with its version.

An example, on Linux:

```text
mini-AlbertCode SWE Agent 0.1.9 installer
Checking this machine. Nothing is changed until you say so.

Found
  Linux            Ubuntu 24.04 LTS, x86_64
  mini-AlbertCode  not installed
  Python           3.12 at /usr/bin/python3.12
  uv               not installed
  Git              2.43.0 at /usr/bin/git
  Browser          /usr/bin/chromium
  Disk             26.9 GB free
  Network          pypi.org reachable

Will do
  1. Download uv 0.9.5 (about 20 MB, checked against its published SHA-256) ...
  2. Use your Python 3.12 (/usr/bin/python3.12); nothing is installed into it.
  3. Install mini-AlbertCode 0.1.9 with its browser tools, in its own environment ...
  4. Use /usr/bin/chromium for the browser tools (no browser download).
  5. Add ~/.local/bin to your PATH in your shell's startup file, so 'albert-mini' works in any new terminal.
  6. Check that it installed: its version, its commands, and its service starting and answering.

Proceed? [Y/N] Y

Installing
  ...
Checking the installation
  Version 0.1.9
  albert-mini starts
  Browser tools load
  Git works
  New terminals find albert-mini
  The service starts and answers (0.1.9)

mini-AlbertCode 0.1.9 is ready.
  Open a new terminal and run:   albert-mini
  Or open it in your browser:    albert-mini web
  Then connect a model: it asks on the first start, or /connect at any time.
```

Administrator rights are needed only if Git is missing: the installer uses winget on Windows, Apple's
Command Line Tools on macOS, and your package manager (with `sudo`) on Linux.

## Requirements

| | |
|---|---|
| **Windows** | Windows 10 or 11, x64 (the x64 build also runs on ARM PCs). PowerShell 5.1 or 7 |
| **macOS** | macOS 11 or later, on Apple silicon or Intel |
| **Linux** | x86-64 with glibc: Ubuntu 20.04+, Debian 10+, Fedora, RHEL 8+, openSUSE, Arch. Not Alpine or other musl systems |
| **Disk** | About 1 GB free |
| **Network** | pypi.org and github.com while installing; your model provider while working |

You don't need Python: the installer uses your Python 3.12 if you have one, and otherwise downloads one
for mini-AlbertCode alone.

## Options

Pass options to the bootstrap after `-s --` on macOS and Linux:

```bash
curl -fsSL https://raw.githubusercontent.com/huynvic/mini-albertcode-swe-agent/main/installer/install.sh | sh -s -- --check
```

On Windows, set them in `MINI_ALBERTCODE_INSTALL_ARGS` before running the command:

```powershell
$env:MINI_ALBERTCODE_INSTALL_ARGS = '--check'; irm https://raw.githubusercontent.com/huynvic/mini-albertcode-swe-agent/main/installer/install.ps1 | iex
```

| Option | Meaning |
|---|---|
| *(none)* | Check, show the plan, ask, install |
| `--check` | Only check and show the plan |
| `--yes` | Install without asking (scripts, CI) |
| `--reinstall` | Install again even when this version is already installed |
| `--version X.Y.Z` | Install that release instead of the latest |
| `--uninstall` | Remove mini-AlbertCode (see below) |

## Updating

```bash
albert-mini update            # find the latest release, and run its installer
albert-mini update --check    # only say whether there is a newer one
```

`albert-mini update` reads the latest release, says whether it is newer than the version you have, and
runs its installer, checked against the release's SHA-256 first. Running the install command again does
the same. The installer finds the version installed and shows its plan before replacing anything:

```text
Found
  mini-AlbertCode  0.1.0 (uv, ~/.local/share/uv/tools/mini-albertcode/bin/python3)
  ...
Will do
  1. Update mini-AlbertCode 0.1.0 to 0.2.0 (installed with uv); your sessions are kept.
  ...
  5. Saved keys, model choices and settings are kept: it carries the same AlbertCode engine.
  6. Check that it installed: its version, its commands, and its service starting and answering.

Proceed? [Y/N]
```

Your sessions are always kept. When a new version carries a new AlbertCode engine, the plan says so,
and saved keys and model choices are cleared the first time it starts: connect your model again with
`/connect`. On Windows the installer opens in a window of its own, so it can replace the running
program's files.

If a running mini-AlbertCode service is found, the installer stops it first (`albert-mini stop` does
the same by hand); it starts again by itself the next time an interface needs it.

## Uninstalling

```bash
albert-mini uninstall           # the program and the installer's files
albert-mini uninstall --all     # and your settings, saved keys, sessions and history
albert-mini uninstall --check   # only show what it would do
```

It shows its plan and asks `Proceed? [Y/N]` first. It needs nothing from the internet. The install
script can do it too, keeping your settings:

```bash
curl -fsSL https://raw.githubusercontent.com/huynvic/mini-albertcode-swe-agent/main/installer/install.sh | sh -s -- --uninstall
```

```powershell
$env:MINI_ALBERTCODE_INSTALL_ARGS = '--uninstall'; irm https://raw.githubusercontent.com/huynvic/mini-albertcode-swe-agent/main/installer/install.ps1 | iex
```

Your repositories are never touched. Your settings, sessions and saved keys stay unless you use
`--all`; [Privacy](../PRIVACY.md) lists the folders.

## Downloading an installer by hand

From the [latest release](https://github.com/huynvic/mini-albertcode-swe-agent/releases/latest), take
the file for your system:

| File | For |
|---|---|
| `Install-mini-AlbertCode-<version>-windows-x64.cmd` | Windows 10 and 11 (x64; also runs on ARM): double-click it |
| `Install-mini-AlbertCode-<version>-macos-arm64.zip` | Mac with Apple silicon: open the zip, then double-click the installer inside |
| `Install-mini-AlbertCode-<version>-macos-x86_64.zip` | Mac with Intel: open the zip, then double-click the installer inside |
| `Install-mini-AlbertCode-<version>-linux-x86_64.sh` | Linux, x86-64: `bash Install-mini-AlbertCode-<version>-linux-x86_64.sh` |

Check it against the release's `SHA256SUMS` before running it:

```bash
sha256sum -c SHA256SUMS --ignore-missing          # Linux
shasum -a 256 -c SHA256SUMS --ignore-missing      # macOS
```

```powershell
(Get-FileHash .\Install-mini-AlbertCode-<version>-windows-x64.cmd -Algorithm SHA256).Hash   # Windows: compare with SHA256SUMS
```

The installers aren't code-signed yet. On macOS, the first time, choose *Done*, open **System
Settings → Privacy & Security**, click **Open Anyway**, then open the installer again. On Windows,
SmartScreen may say it protected your PC: choose *More info* → *Run anyway*. The one-line commands
avoid both.

## Behind a proxy

Set `HTTPS_PROXY` (and `HTTP_PROXY`) before running the command. The installer and mini-AlbertCode use
it for every download. A network that inspects secure connections with its own certificate is
handled too: the installer retries with your computer's own certificates.

## Files and folders

| What | Where |
|---|---|
| The program | `~/.local/share/uv/tools/mini-albertcode` (Windows: `%APPDATA%\uv\tools\mini-albertcode`) |
| The command | `~/.local/bin/albert-mini` (Windows: `%USERPROFILE%\.local\bin\albert-mini.exe`) |
| The installer's files and log | `~/.local/share/mini-albertcode-installer` (Windows: `%LOCALAPPDATA%\mini-albertcode-installer`) |
| Settings, sessions and history | See [Privacy](../PRIVACY.md) |
