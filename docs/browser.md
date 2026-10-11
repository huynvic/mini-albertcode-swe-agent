# The browser

```bash
albert-mini web              # open the workspace, signed in, in your browser
albert-mini web --no-open    # print the address instead
```

The browser workspace and the terminal are two views of one service on your machine: a session
started in one shows in the other at the same moment, and an answer given at a gate in one is seen at
once in the other.

## Signing in

`albert-mini web` opens an address that carries this installation's access token once. The service
swaps it at once for a cookie that the page cannot read and that other sites cannot send, and takes
it out of the address. See [Security](security.md).

## The workspace

```text
┌ menu bar: Session · Project · Git · View · Settings · Help ──────────────────────────────┐
│ SESSIONS        │ Fix the discount at checkout                      │ INSPECTOR          │
│ + New session   │ ✓ Plan ─ ◆ Your approval ─ ○ Build ─ ○ Checks ─ ◇ │ Changes Context    │
│ ⌕ Find          │                                                    │ Task               │
│ ▾ shop          │   ❯ what you said                                  │                    │
│   ● Fix the…    │   Albert · deepseek-flash                          │                    │
│ ▾ api           │   the answer, the task's steps…                    │                    │
│   ○ How the…    │  ┌ ❯ the console ─────────────────────────────┐    │                    │
│                 │  │ + [Governed|Direct|Ask only] provider model│    │                    │
│ Every session   │  └────────────────────────────────────────────┘    │                    │
├ status bar: ● Live · shop · ⎇ main ↑1 ● 2 · Governed · provider / model · MCP · Inspector ┤
```

- **The navigator**, down the left: every project with its sessions under it, newest first, each with a
  lamp (working, waiting for you, stopped with an error); a new session, here or in a given project; a
  search; and every session in full. Fold it to a rail of icons with the arrow at its top; it stays as
  you left it. Beside the open inspector on a screen narrower than 1360 pixels it folds by itself, so the
  conversation keeps its room.
- **The session**, in the middle. Its head has the title (click to rename), where it works and its mode,
  and, when its latest task is governed, the **gate track**: the work as circles, the two human gates as
  diamonds: *Plan → Your approval → Build in a copy → Checks and reviews → Your acceptance → In your
  files*. The step the task is on is lit: blue while it works, orange while it waits for you, red where
  it stopped. Click it for the task in full. Direct and Ask only have no gates, so no track.
- **The conversation**: what you said as prompt lines (❯), Albert's answers under a line naming the model.
- **The console**, at the session's foot: type at the ❯, and under it + (attach), the mode (Governed,
  Direct or Ask only, one click each; with Direct, whether each write is asked about or approved), the
  provider and the model, the agent, and send. Under the console, what it works on: the project, its
  checkout (the repository itself or one of its worktrees) and its branch, each a menu.
- **The inspector** (`Alt+P`), on the right: the change, a file at a time, of the task's isolated copy
  or of your working tree; the session's context and usage; and the task in full.
- **The status bar**, along the foot: whether the service is live, the project and its branch (↑ ahead,
  ↓ behind, ● changed files), the mode, the provider and model, what the session's tasks used, MCP
  servers, and the inspector. Each is a button to where it is changed or seen in full.
- **Every session** (`Alt+B`): newest first, by day, pinned on top, searchable, each with its actions.

A new session opens on the **launchpad**: a greeting that names the project, the console, and tiles: the
sessions to pick up again, how the two gates work (in the Governed mode), and the ways to start (open or
clone a project, connect a provider).

## The menu bar

| Menu | Holds |
|---|---|
| Session | New session, every session, rename, pin, fork, export, import, archive, stop, delete |
| Project | Open a folder, clone a repository, the projects you worked on recently, worktrees |
| Git | Changes, commit, pull, push, switch branch, new branch, new worktree, set up Git in a folder without it |
| View | The inspector's tabs, the theme, the time of each message |
| Settings | Settings, providers, connect a provider, models, MCP servers, agents |
| Help | Every command, keys and commands, this guide, the service's status |

Click a menu to open it, move along with the arrow keys or the mouse, and press `Esc` to close it.

## Projects

*Open a folder…* (the Project menu, or the project under the box) walks this machine's folders: your
home, the folder the service started in, and every drive with its free space on the left; the folder's
folders on the right, a repository marked with its branch. Type a path and press `Enter` to go
straight there, filter the folders by name, and make a new folder where you are. *Use this folder*
makes it the project new sessions work on.

*Clone a repository…* takes the repository's address (GitHub, GitLab or any Git host), where to put it
(beside the project you are on, or your home; *Browse…* to choose) and, if you like, a folder name and
a branch. Private repositories use the sign-in Git already has on your machine. Only `https`, `http`,
`ssh` and `git` addresses are taken, and a password in an address is never shown.

## Git

The branch under the box shows how far it is ahead (↑) and behind (↓) its upstream. Its menu, and the
Git menu, do what you would do at a terminal:

- **Commit…**: a message, and the changed files the Changes tab shows. A file that looks like it holds
  secrets (`.env`, keys) is never committed. *Commit and push* does both.
- **Pull** and **Push**: from and to the branch's upstream. The first push of a new branch sets its
  upstream on `origin`.
- **Switch branch…**: your branches and the remote's; a remote branch becomes a local one that follows
  it. Uncommitted changes go with you, unless they clash.
- **New branch…**: a name, and the branch it starts from.
- **Set up Git here**: for a folder without a repository, on branch `main`. Governed and Direct work
  need Git: it is the undo.

```text
shop  /  main checkout  /  main ↑1
```

## Worktrees

A worktree is another checkout of the same repository, on a branch of its own, in a folder beside it
(`shop-worktrees/pricing` for a repository in `shop`). Work there does not touch your main checkout, so
one session can fix a bug while another builds a feature. *Worktrees…* lists them; *New worktree…* takes
a branch name and the branch to start from, makes it, and opens a session there. *Work here* moves new
sessions to one; removing one takes its folder and keeps its branch and commits (with changes not yet
committed, you are asked twice). It works the same for a repository you opened and for one you cloned.

## Keys

| Key | Does |
|---|---|
| `Enter` | Send |
| `Shift+Enter` | A new line |
| `Esc` | Stop a run · close · go back |
| `Ctrl+K` | Every command |
| `Alt+N` | A new session |
| `Alt+B` | Every session |
| `Alt+P` | Show or hide the inspector |
| `Alt+M` | Choose the model |
| `/` | Commands, in the box |
| `@` | Mention a file, in the box |
| `↑` `↓` | Earlier messages you sent, in an empty box |

## Gates

A gate is a card over the box with its answers in a row:

| Gate | Answers |
|---|---|
| Plan ready for your approval | Approve and build (`a`) · Ask for changes (`e`) · Read the whole plan (`d`) · Reject (`r`) |
| Permission required (a write, in Direct · ask each write) | Allow once (`a`) · Allow the rest of this task (`⇧A`) · Decline (`n`) |
| The change is ready | Accept into your files (`a`) · View the diff (`v`) · Ask for changes (`e`) · Discard (`x`) · Reject (`r`) |
| Start this change? (Ask only) | Plan it first (`p`) · Do it directly (`o`) |

## Settings

The Settings menu, or every command (`Ctrl+K`, *Settings*). A section at a time:

| Section | Holds |
|---|---|
| General | The theme (shared with the terminal), the time of each message, the folder new sessions work in, the mode they start in |
| Providers | Each provider, connected or what it needs, with *Connect* or *Change* |
| Models | The model new sessions use |
| MCP servers | How many, and how many connected; manage them |
| Agents | Choose an agent to work as |
| Keys | Every key |
| About | This installation and its engine, the service's status |

Six themes, the same as the terminal's: Nebula and Aurora (the defaults, dark and light, by your
system's setting: glass panels over a lit backdrop), Ember, Ember light, Slate and High contrast.

## On a phone or a tablet

Below 900 pixels wide the navigator is a drawer (the ☰ at the left of the status bar opens it, and it shuts
once you choose), the inspector takes the screen, and the launchpad's tiles are one column; every button
is at least 44 pixels on a touch screen.
