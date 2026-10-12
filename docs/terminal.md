# The terminal

```bash
albert-mini              # full screen, on the current folder
albert-mini --mini       # the same, inline in the lower part of the terminal
albert-mini -c           # continue the latest session here
albert-mini -s <id>      # open a session
```

It is drawn as AlbertCode's terminal is, with no box, rule or line: a new conversation opens on its
name in solid letters, the version beside "Two human gates", the folder, the model and any MCP servers,
and the commands to start with.

## The prompt

```text
your-project · gpt-4o · governed ❯
```

Before `❯`: the folder, the model, and the mode. Type a question or a change, then `enter`. Under the
prompt are the keys worth knowing now and a dot for the connection to the service (green when live).

While Albert works, the line over the prompt says what it is doing right now, with the seconds it has
been at it:

```text
⠹ Reading cart.py…  (3s · esc to stop)
⠼ Running python -m pytest -q…  (21s · esc to stop)
```

A reply lists what it reads before it answers (*Read cart.py*), then folds the list to one line once
the answer begins (*3 steps before answering*). A change's task shows in the conversation from its first
moment, with each step as it lands, while it is still being planned.

| Key | Does |
|---|---|
| `enter` | Send. A command typed in full runs at once |
| `ctrl+j` or `alt+enter` | A new line |
| `↑` / `↓` | Earlier messages you sent |
| `tab` | The next mode |
| `/` | Commands, filtered as you type |
| `@` | Mention a file of the repository |
| `esc` | Stop a run · go between the box and a gate · close a list |
| `ctrl+p` | Every command, mode and session in one list |
| `ctrl+c` | Clear the box; twice to leave |
| `pageup` / `pagedown` | Scroll the conversation |

## Commands

`/help` lists them all to search and run. A command that needs words after it waits in the box for
them.

| Command | Does |
|---|---|
| `/plan <request>` | A governed change: a plan for your approval first |
| `/do <request>` | Direct, ask each write: in your files, every write waits for your OK |
| `/direct auto <request>` | Direct, auto-approve: in your files, carried out without asking |
| `/new` | A new session |
| `/sessions` | Open, rename, pin or delete sessions |
| `/model` | The model for this session |
| `/mode [governed\|direct\|auto\|ask]` | How a change is handled; with no word, the list |
| `/agent` | Work as one of this repository's custom agents |
| `/connect` | Connect a model provider |
| `/mcp` | MCP servers: on or off, sign in, add a connector, import from JSON |
| `/diff` | This session's change, or your working tree's |
| `/stop` | Stop what the session is doing |
| `/rename [title]` | Rename this session |
| `/fork` | A new session holding this one's messages |
| `/export [file]` | Save this session as a JSON file |
| `/import <file>` | Open a session saved as JSON |
| `/attach <paths>` | Attach files to your next message |
| `/theme` | Choose a colour theme |
| `/speed [fast\|balanced\|thorough]` | How much the model thinks at each step of a task (shared with the browser) |
| `/details` | Show every step of the tasks here |
| `/web` | Open this session in the browser |
| `/status` | The service, the engine and what is connected |
| `/help` | Every command, to search and run |
| `/docs [words]` | Search this guide; Enter reads a match (`/docs update`) |
| `/keys` | Every key, and the answers at a gate |
| `/exit` | Leave (the service and any task keep going) |

Your [custom commands](extending.md) run as `/name`, and an MCP server's prompts as `/server:prompt`.

## Leader keys

Keyboard shortcuts: `ctrl+x`, then one letter:

| Key | Opens | Key | Opens |
|---|---|---|---|
| `n` | A new session | `l` | Sessions |
| `m` | Models | `a` | Agents |
| `c` | MCP servers | `d` | The diff |
| `k` | Connect a provider | `t` | Themes |
| `s` | Status | `h` | Help |
| `b` | The sidebar | `o` | Every step |
| `y` | Timestamps | `r` | Rename |
| `f` | Fork | `e` | Export |
| `w` | Open in the browser | | |

## Lists

Every list works the same way: its title, then `Search:` and what you have typed, then the rows, under
headings where they have groups. Type to filter, `↑` `↓` to choose (the chosen row is marked `›`),
`enter` to take it, `esc` to close. The one in use is ticked `✓`. Some lists have keys of their own,
named under them: in **Sessions**, `ctrl+r` renames, `ctrl+t` pins and `ctrl+d` deletes; in **Choose a
model**, `ctrl+s` also makes it the default for new sessions.

## Gates

A gate is a question over the prompt, with numbered answers: the arrows choose, `enter` gives the
chosen one, or its number or its letter does. `esc` goes back to the box, and `esc` from the box comes
back to the gate. See [Modes and approvals](modes-and-approvals.md) for every gate and answer.

## The guide

`/docs` searches this guide as you type, offline: it comes with mini-AlbertCode, so it always matches
the version you have. `Enter` reads the section chosen, with its link to the guide online, and `esc`
goes back to the matches. With nothing typed, it lists the guide's pages.

```text
/docs update            the sections on updating
/docs model             how to choose a model
```

## The sidebar

`ctrl+x b` shows the sidebar on the right: the session's mode, model and status, its task and its
steps, usage, the changed files, MCP servers, and at its foot the folder, the branch, the service and the
version. A narrow terminal hides it until you ask.

## Themes

`/theme` or `ctrl+x t`: **AlbertCode** (the default: your terminal's own colours, with AlbertCode's
coral), Graphite, Paper, Ember, Ember light, Slate and High contrast. The browser has the same themes,
and the choice is shared.

## Leaving

`/exit`, or `ctrl+c` twice. The service and any running task keep going. On leaving, the terminal
prints the session and the exact command that opens it again.
