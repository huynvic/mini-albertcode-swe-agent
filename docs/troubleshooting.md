# Troubleshooting

Start with:

```bash
albert-mini doctor
```

It checks the installation, the service and what it is connected to, and says what to do about each
problem.

## Installing

| Problem | Fix |
|---|---|
| `pypi.org could not be reached` | Behind a proxy, set `HTTPS_PROXY` (and `HTTP_PROXY`) and run the command again. |
| `this installer is for … processors` | Use the one-line command: it picks the installer for your machine. |
| `Git is not installed, and this installer cannot install it here` | Install Git with your package manager, then run the command again. |
| `this was run with sudo` | Run it as yourself. It asks for your password only for what needs it. |
| `this Linux uses musl` | Alpine and other musl systems aren't supported; use a glibc distribution. |
| macOS says it can't verify the installer | Use the one-line command, or *System Settings → Privacy & Security → Open Anyway*. |
| Windows SmartScreen stops the installer | *More info → Run anyway*, or use the one-line command. |
| Windows: the old files are in use | Close every terminal that uses mini-AlbertCode, or restart Windows, then run the installer again. |
| Anything else | The installer's log: `~/.local/share/mini-albertcode-installer/install.log` (Windows: `%LOCALAPPDATA%\mini-albertcode-installer\install.log`). |

## Starting

| Problem | Fix |
|---|---|
| `albert-mini: command not found` | Open a new terminal: the installer added it to the PATH of new ones. |
| `Waiting for the service at http://127.0.0.1:8778 …` | It is starting. If it keeps waiting, run `albert-mini doctor`, then `albert-mini stop` and try again. |
| `The service … refused this terminal` | Its access token no longer matches: `albert-mini stop`, then start again. |
| The port is taken | `albert-mini --port 8790` (the service uses 8778 by default). |

## Models

| Problem | Fix |
|---|---|
| `No model connected yet.` | Pick a provider in the list that opens, or `/connect` later. |
| `No model chosen yet.` | Pick a model in the list that opens, or `/model` later. |
| A provider shows `key not accepted` | The provider refused the key. Connect it again with a new key. |
| A local server shows `not answering` | Start your model server, then check its address with `/connect`. |
| The model answers but never changes anything | It may not support tool calling. `albert-mini models test` checks. |

## Tasks

| Problem | Fix |
|---|---|
| A change is waiting and nothing happens | It is at a gate: answer it in either interface (`albert-mini -c` reopens the session). |
| `esc` does nothing | `esc` stops a running task; at a gate it moves between the box and the gate. `/stop` stops it too. |
| The diff is not shown while a task works | It is shown when the step ends; the inspector lists the files changed so far. |

## Reporting a bug

[Open an issue](https://github.com/huynvic/mini-albertcode-swe-agent/issues/new/choose) with
`albert-mini --version`, your system, and what `albert-mini doctor` says. Leave out keys and private
code.
