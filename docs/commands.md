# Commands

Every `albert-mini` command. `albert-mini --help` lists them too.

## Starting

```bash
albert-mini                      # the terminal interface, on the current folder
albert-mini --mini               # inline in the lower part of the terminal, instead of full screen
albert-mini web                  # the browser workspace, signed in
albert-mini web --no-open        # print its address instead of opening it
albert-mini attach <url>         # the terminal interface on a service elsewhere
albert-mini --version
```

| Option | Meaning |
|---|---|
| `-w`, `--workspace PATH` | The repository to work on (default: this folder) |
| `-s`, `--session ID` | Open this session |
| `-c`, `--continue` | Continue the latest session in this folder |
| `-m`, `--model MODEL` | The model for new sessions (`provider` or `provider:model`) |
| `--mode MODE` | How a change is handled in new sessions: `governed`, `direct`, `direct_auto` or `ask` |
| `--port N` | The local service's port (default 8778) |
| `--url URL`, `--api-key KEY` | Talk to a service elsewhere, with its key |

## The service

```bash
albert-mini status               # whether the service is running, and which version
albert-mini stop                 # stop it; it starts again when an interface needs it
albert-mini serve                # run it in the foreground (Ctrl+C stops it)
albert-mini serve --port 8790
albert-mini doctor               # check this installation, the service and what it is connected to
albert-mini doctor --json
```

The service starts by itself the first time an interface needs it, listens on `127.0.0.1:8778`, and keeps
running in the background. `serve --host` makes it listen elsewhere; anything but this machine needs
authentication.

## run

One request, start to finish, without the interface, printing what happens:

```bash
albert-mini run "what does this project do?"
albert-mini run "add a health check endpoint" --approve plan,result
albert-mini run "rename the helper" --lane direct_auto
albert-mini run "add a test for cart totals" --approve all --json
```

| Option | Meaning |
|---|---|
| `--lane MODE` | `governed`, `direct`, `direct_auto` or `ask`, for this request only |
| `--approve GATES` | Answer these gates on your behalf: `plan`, `result`, `writes`, or `all` (comma separated) |
| `--json` | Print every event as one JSON line |
| `--timeout SECONDS` | Give up after this long (default 3600) |

| Exit code | Meaning |
|---|---|
| 0 | Done: answered, or the change was applied |
| 1 | Failed, or the change was rejected |
| 2 | Refused: a wrong option, or nothing that could run it |
| 3 | Stopped at a gate `--approve` did not cover: answer it in either interface |
| 124 | Timed out |

## sessions

```bash
albert-mini sessions                         # newest first
albert-mini sessions --search discount       # titles and message text
albert-mini sessions show <id>
albert-mini sessions rename <id> "New title"
albert-mini sessions export <id> [file]
albert-mini sessions import <file>
albert-mini sessions delete <id>
```

Each takes `--json`. See [Sessions](sessions.md).

## models

```bash
albert-mini models                           # providers (connected, or what each needs) and ready models
albert-mini models use openrouter:some/model # the default for new sessions
albert-mini models test                      # one tool-calling request to the chosen model
```

See [Models](models.md).

## mcp

```bash
albert-mini mcp                                  # list, with state and tools
albert-mini mcp add NAME --command "…"           # a local server; --env KEY=VALUE for its environment
albert-mini mcp add NAME --url URL               # a remote one; --header KEY=VALUE, --no-oauth
albert-mini mcp enable|disable|connect|remove NAME
albert-mini mcp auth NAME                        # sign in, in your browser
albert-mini mcp logout NAME
albert-mini mcp tools|prompts|resources NAME     # what it offers
albert-mini mcp debug NAME                       # what it reports, for finding a problem
albert-mini mcp connectors                       # the catalogue
albert-mini mcp install ID key=value …           # add one from the catalogue
albert-mini mcp import FILE [--apply]            # servers from a block of JSON (mcpServers)
```

See [MCP servers](mcp.md).

## stats

```bash
albert-mini stats            # sessions, messages, tasks, files changed, model calls, tokens and cost
albert-mini stats --json
```

## update and uninstall

```bash
albert-mini update             # find the latest release; its installer shows its plan and asks
albert-mini update --check     # only say whether there is a newer one
albert-mini update --yes       # install it without asking
albert-mini uninstall          # the program and the installer's files; asks first
albert-mini uninstall --all    # and your settings, saved keys, sessions and history
albert-mini uninstall --check  # only show what it would do
```

See [Installation](installation.md#updating).

## classic

```bash
albert-mini classic
```

The AlbertCode engine's own terminal interface, on mini-AlbertCode's service.
