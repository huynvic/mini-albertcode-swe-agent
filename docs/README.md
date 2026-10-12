# mini-AlbertCode documentation

Everything you need to install, use and run mini-AlbertCode SWE Agent: every command, key and gate, with
examples. mini-AlbertCode is a coding agent you run on your own machine, with two interfaces, a terminal
and a browser workspace, on one local service, and the AlbertCode engine's two human gates.

## Start here

1. [**Getting started**](getting-started.md): install, connect a model, and finish a first task in
   about five minutes.
2. [**How mini-AlbertCode works**](how-it-works.md): the service and its two interfaces, asking and
   changing, the modes, the life of a governed change, sessions and tasks, and what is kept where.
3. [**Using mini-AlbertCode**](usage.md): the short version of everything, with links.

## Using mini-AlbertCode

| Guide | What's in it |
|---|---|
| [The terminal](terminal.md) | `albert-mini`: the prompt, every key, slash command and list, gates, the sidebar, themes |
| [The browser](browser.md) | `albert-mini web`: signing in, the workspace (navigator, gate track, console, inspector), every shortcut, settings |
| [Modes and approvals](modes-and-approvals.md) | Governed, Direct and Ask only; the two human gates and every answer; from scripts |
| [Sessions](sessions.md) | Sessions shared by both interfaces: opening, renaming, pinning, forking, exporting |
| [Models](models.md) | Connecting a provider, choosing and testing a model, local models |

## Extending

| Guide | What's in it |
|---|---|
| [Custom commands and agents](extending.md) | Prompts you call by name, and roles that narrow what a task may do |
| [MCP servers](mcp.md) | Outside tools: adding servers, signing in, the connector catalogue, importing |

## Reference

| Guide | What's in it |
|---|---|
| [Commands](commands.md) | Every `albert-mini` command and option, with examples and exit codes |
| [Installation](installation.md) | Options, updating, uninstalling, requirements, files and folders |
| [Security model](security.md) | The local service, its access token, where keys are kept, what leaves your machine |
| [Troubleshooting](troubleshooting.md) | Fixes for installing, starting, models and tasks |
| [FAQ](faq.md) | Short answers |
| [Glossary](glossary.md) | Every term, in one place |

## Find a command

| I want to… | Terminal | Browser |
|---|---|---|
| Ask a question | Type it | Type it |
| Make a change with approvals | `/plan …`, or the **Governed** mode | `/plan …`, or **Governed** |
| Change files directly | `/do …` | `/do …`, or **Direct** |
| Connect a model | `/connect` | **Settings** › **Connect a provider…** |
| Choose a model | `/model`, or <kbd>Ctrl</kbd> <kbd>X</kbd> <kbd>M</kbd> | The model menu under the box, or <kbd>Alt</kbd> <kbd>M</kbd> |
| Open or clone a project | Start `albert-mini` in its folder | **Project** › **Open a folder…** or **Clone a repository…** |
| Commit, pull, push, branches | Git, in a terminal | The **Git** menu, or the branch under the box |
| Work in a second checkout | `git worktree add` | **Project** › **Worktrees…** |
| Start a new session | `/new` | <kbd>Alt</kbd> <kbd>N</kbd> |
| See every session | `/sessions`, or <kbd>Ctrl</kbd> <kbd>X</kbd> <kbd>L</kbd> | <kbd>Alt</kbd> <kbd>B</kbd> |
| See the change | `/diff`, or <kbd>Ctrl</kbd> <kbd>X</kbd> <kbd>D</kbd> | <kbd>Alt</kbd> <kbd>P</kbd>, **Changes** |
| Give it a file or screenshot | `/attach <path>` | The **+** beside the box |
| Open the session in the other interface | `/web` | `albert-mini -s <id>` in a terminal |
| Add an MCP server | `/mcp` | **MCP servers**, from <kbd>Ctrl</kbd> <kbd>K</kbd> |
| Every command | `/help`, or <kbd>Ctrl</kbd> <kbd>P</kbd> | <kbd>Ctrl</kbd> <kbd>K</kbd> |
| Search this guide | `/docs <words>`, or `albert-mini docs <words>` | **Help** › **Search the guide…**, or `/docs` |
| Show or hide the agent's steps | `/details`, or <kbd>Ctrl</kbd> <kbd>X</kbd> <kbd>O</kbd> | <kbd>Alt</kbd> <kbd>S</kbd> |

## Getting help

- Search this guide where you work: Help in the browser, `/docs <words>` in the terminal, or
  `albert-mini docs <words>` in a shell. It comes with mini-AlbertCode, so it works offline.
- [Troubleshooting](troubleshooting.md) has the fixes for common problems, and `albert-mini doctor`
  checks your installation.
- Report a bug in [Issues](https://github.com/huynvic/mini-albertcode-swe-agent/issues/new/choose), with
  `albert-mini --version` and your operating system. Never include keys, tokens or private code.
