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
│ SESSIONS        │ Fix the discount at checkout                ▷ ⌨  │ INSPECTOR          │
│ + New session   │ ✓ Plan ─ ◆ Your approval ─ ○ Build ─ ○ Checks ─ ◇ │ Changes Preview    │
│ ⌕ Find          │                                                    │ Terminal Context   │
│ ▾ shop          │   ❯ what you said                                  │ Task               │
│   ● Fix the…    │   Albert · deepseek-flash                          │                    │
│ ▾ api           │   the answer, the task's steps…                    │                    │
│   ○ How the…    │  ┌ ❯ the console ─────────────────────────────┐    │                    │
│                 │  │ + [Governed|Direct|Ask only] provider model│    │                    │
│ Every session   │  └────────────────────────────────────────────┘    │                    │
├ status bar: ● Live · shop · ⎇ main ↑1 ● 2 · Governed · provider / model · MCP · Inspector ┤
```

- **The navigator**, down the left: every project with its sessions under it, newest first, each with a
  lamp (working, waiting for you, stopped with an error); a new session, here or in a given project; a
  search; and every session in full. Each session's `⋯` holds Rename, Pin, Stop, Archive and Delete, and
  a session at work has a stop button of its own. A project's `⋯` starts a session there, takes the
  project off the list (its sessions are archived, still under Every session; its folder is untouched),
  or deletes its sessions. Fold the navigator to a rail of icons with the arrow at its top; it stays as
  you left it. Beside the open inspector on a screen narrower than 1360 pixels it folds by itself, so the
  conversation keeps its room.
- **The session**, in the middle. Its head has the title (click to rename), where it works and its mode,
  Stop while it works, Preview (▷) and the terminal (⌨), its actions (`⋯`), and, when its latest task is governed, the **gate track**: the work as circles, the two human gates as
  diamonds: *Plan → Your approval → Build in a copy → Checks and reviews → Your acceptance → In your
  files*. The step the task is on is lit: blue while it works, orange while it waits for you, red where
  it stopped. Click it for the task in full. Direct and Ask only have no gates, so no track.
- **The conversation**: what you said as prompt lines (❯), Albert's answers under a line naming the model.
  You see the work as it happens. Before Albert answers, each thing it reads or searches shows as a step
  (*Read cart.py*, *Searched for "discount"*), with the one under way spinning beside it. Then the answer
  flows in word by word, and the steps fold to one line (*3 steps before answering*) that opens again on
  a click. A task shows as a card from its first moment, while it is still planning, not only once the
  plan is ready. The card lists each step as it lands, with the step under way at its foot (*Running
  python -m pytest -q…*, or *Thinking…* while the model works out what to do next) and the time it has
  been at it. While the model thinks, the last of what it is thinking shows under *Thinking…*, for a
  model that shares it.
- **The agent's steps**: `Alt+S`, or *Show the agent's steps* in the View menu, shows or hides the
  steps of answers and tasks. Hidden, an answer or a task still shows the one step under way, so you see
  it working; a task's card has its own *Steps* switch too. The choice is kept in this browser.
- **The console**, at the session's foot: type at the ❯, and under it + ([attach](usage.md#attachments)), the mode (Governed,
  Direct or Ask only, one click each; with Direct, whether each write is asked about or approved), the
  provider and the model, the agent, and send. Under the console, what it works on: the project, its
  checkout (the repository itself or one of its worktrees) and its branch, each a menu.
- **The inspector** (`Alt+P`), on the right: the change, a file at a time, of the task's isolated copy
  or of your working tree (every changed file listed at once, a file's diff read when you open it); the
  project running in [Preview](#preview); a [terminal](#terminal) in the project's folder; the
  session's context and usage; and the task in full, or, before there is one, how a task goes and the
  recent work in the project. Drag its edge to give it or the conversation more room (or focus the edge
  and use the arrow keys); the width is kept, and a double click puts it back.
- **The status bar**, along the foot: whether the service is live, the project and its branch (↑ ahead,
  ↓ behind, ● changed files), the mode, the provider and model, what the session's tasks used, MCP
  servers, and the inspector. Each is a button to where it is changed or seen in full.
- **Every session** (`Alt+B`): newest first, by day, pinned on top, searchable, each with its actions.

A new session opens on the **launchpad**: a greeting that names the project, the console, and tiles: the
sessions to pick up again, how the two gates work (in the Governed mode), and the ways to start (open or
clone a project, run it in [Preview](#preview), open a [terminal](#terminal) in it, connect a provider).

## The menu bar

| Menu | Holds |
|---|---|
| Session | New session, every session, rename, pin, fork, export, import, archive, stop, delete |
| Project | Open a folder, clone a repository, the projects you worked on recently, worktrees |
| Git | Changes, commit, pull, push, switch branch, new branch, new worktree, set up Git in a folder without it |
| View | The inspector's tabs (Changes, Preview, Terminal, Context, Task), the theme, the time of each message |
| Settings | Settings, providers, connect a provider, models, MCP servers, agents |
| Help | Search the guide, every command, keys and commands, the guide online, the service's status |

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
- **Set up Git here**: for a folder without a repository, on branch `main`. Direct work needs Git: it
  is the undo. Choose Direct in a folder without it and you are asked at once whether to set it up (see
  [Modes and approvals](modes-and-approvals.md#the-modes)). Governed builds in a copy and needs none.

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

## Preview

**Preview** (▷ in the session's head, *Run this project* on a new session's launchpad, or the Preview tab
of the inspector) runs the project beside the conversation, so you see what Albert changed as you would
use it:

- **An app** (a `dev`, `start`, `serve` or `preview` script in `package.json`, run with the package
  manager its lockfile names, or Django's `manage.py`) is started with its own command, and the panel
  says which and why: *Runs `npm run dev` (the dev script in package.json)*. *Run the app* starts it.
  For anything else, type the command that starts it (`python app.py`, `flask run`) in the box under
  it; a command that brought the app up is remembered for next time.
- **Web pages** with nothing to start (an `index.html`, a browser game) are served as they are: *Serve
  the pages*. Only this computer can reach them, only to read; a file or folder whose name begins with a
  dot (`.env`, Git's folder), a file that looks like it holds secrets, or a link out of the folder is
  never served. Each load is fresh, so an edit shows on the next one.

Running, the bar says where it answers and how fast (*Running · localhost:5173 · 200 · 12 ms*), and holds
*Desktop*, *Tablet* and *Phone* widths, Restart, Open in a new tab, and Stop. If the port it asks for is
busy, it runs on another and says which. If the app does not start, or stops by itself, or answers with
an error, the panel shows what it wrote: *Ask Albert to fix* puts it in the box, ready to send, and
*Logs* shows the rest.

It keeps running while you work, and in the project's other sessions, until you stop it or the service
ends; the terminal's `/preview` shows the same run. Restart starts an app again; for pages it loads them
again.

**Example.** In a folder holding `index.html`, `style.css` and `game.js`, open Preview and press *Serve
the pages*: the game plays in the panel, at `http://localhost:8000/`. Ask *make the board bigger*, apply
the change, and press Restart to see it.

## Terminal

**Terminal** (⌨ in the session's head, *Open a terminal here* on the launchpad, the Terminal tab, or
`` Ctrl+` ``) is a real shell in the project's folder, in the page: zsh or bash on macOS and Linux, PowerShell on Windows.

It is off until you turn it on. The first time, the tab explains what it allows: what you type runs on
this computer as you, outside the limits mini-AlbertCode puts on Albert. Only your own mini-AlbertCode
page can connect to it, and no model key is in its environment. Turning it on or off is recorded; what
you type is not.

- **Tabs.** **+** opens another shell (up to 8); **×** or a middle-click closes one.
- **It keeps running.** Hide it, switch to another tab, or reload the page: each shell carries on and
  comes back with what it wrote. A shell that has ended says so; press `Enter` for a new one.
- **Open in your terminal app** opens your own terminal in the project's folder instead, on or off.
- **Turn off** closes every shell it opened.

**Example.** Turn the terminal on, then run `git status` to see what Albert changed, or
`npm test` to run the tests yourself while Albert waits for your answer at a gate.

## Keys

Keyboard shortcuts, also under Help (`/help`):

| Key | Does |
|---|---|
| `Enter` | Send |
| `Shift+Enter` | A new line |
| `Esc` | Stop a run · close · go back |
| `Ctrl+K` | Every command |
| `Alt+N` | A new session |
| `Alt+B` | Every session |
| `Alt+P` | Show or hide the inspector |
| `` Ctrl+` `` | Show or hide the terminal |
| `Alt+M` | Choose the model |
| `Alt+S` | Show or hide the agent's steps |
| `/` | Commands, in the box |
| `@` | Mention a file, in the box |
| `↑` `↓` | Earlier messages you sent, in an empty box |

## Help and the guide

Help (the Help menu, `/help` or `/docs` in the box) searches this guide as you type: write a few words
(*update*, *model*, *stop*, *keys*) and the sections that answer them are listed, best
first, each with the line that matched. Click one, or press `Enter`, to read it in place; *Online*
opens it on GitHub. The guide comes with mini-AlbertCode, so the search needs no network and always
matches the version you have. With nothing typed, Help lists the guide's pages, every key, the answers
at a gate and the modes.

```text
/docs update          the sections on updating, the command first
/docs model           how to choose a model, in each interface
```

## Gates

A gate is a card over the box with its answers in a row:

| Gate | Answers |
|---|---|
| Plan ready for your approval | Approve and build (`a`) · Ask for changes (`e`) · Read the whole plan (`d`) · Reject (`r`) |
| Permission required (a write, in Direct · ask each write) | Allow once (`a`) · Allow the rest of this task (`⇧A`) · Decline (`n`) |
| The change is ready | Accept into your files (`a`) · View the diff (`v`) · Ask for changes (`e`) · Discard (`x`) · Reject (`r`) |
| Start this change? (Ask only) | Plan it first (`p`) · Do it directly (`o`) |

A pressed answer says so on its own button at once (*Approving…*, *Accepting…*, *Starting the plan…*) while
the other answers wait, so it cannot be given twice. Once the service has it, the gate says what happened
(*Approved. The build starts in an isolated copy now.*) until the work moves on, within a moment. Stop says
*Stopping…* the same way.

No answer waits for the model. Plan it first and Do it directly close the question at once: the proposal says
*Starting the plan…* and the steps show as Albert reads and plans; the plan comes back as its own question.
Stop answers at once too, even while the model is in the middle of a long step: the session is free again
straight away, and that step ends quietly in the background.

**Example.** In Ask only, Albert offers "Add `greet()` to `app.py`". Press `p`: the card closes, the
proposal says *Starting the plan…*, and *Reading app.py…* shows below it. About half a minute later, with
DeepSeek, *Plan ready for your approval* opens. Press `Esc` while it plans instead, and the session is free
in under a second.

## Settings

The Settings menu, or every command (`Ctrl+K`, *Settings*). A section at a time:

| Section | Holds |
|---|---|
| General | The theme (shared with the terminal), the time of each message, the folder new sessions work in, the mode they start in, and the speed |
| Providers | Each provider, connected or what it needs, with *Connect* or *Change* |
| Models | The model new sessions use |
| MCP servers | Your servers and where each stands, or the connectors ready to add; manage them |
| Agents | Albert and this project's custom agents, what each may do, and how to add one |
| Keys | Every key |
| About | This installation and its engine, how to update it, the guide, what's new, the licences |

**Speed** sets how much the model thinks at each step of a task, shared with the terminal (`/speed`):

| Speed | What it does |
|---|---|
| Fast (the default) | Quick answers in the conversation, and a lighter review; planning and writing as deep as ever |
| Balanced | The engine's own depth at each step |
| Thorough | The most thinking at every step: slower, for changes that need it |

A model that thinks just as hard whatever it is asked (such as DeepSeek) has its thinking switched off
where a step asks for a light think: at Fast, answers in the conversation and the review.

**Example.** "Build a simple HTML chess game" with DeepSeek, Governed, at Fast: the review took 43 s
where it took 128 s, and the whole task about 10 minutes instead of 11 (605 s against 677 s). Planning
and writing keep their depth: with DeepSeek's thinking off for writing too, the same game was built in 3
minutes once, but more often it took longer, the model clicking through its page hundreds of times.

Every check and every review runs at every speed. At every speed, a task that goes round in circles (the same steps answered the same way, or a failing step asked again in other words and failing the same way) is stopped, and what it wrote is checked and reviewed as it stands; it is never started over just to go round again.

Six themes, the same as the terminal's: Nebula and Aurora (the defaults, dark and light, by your
system's setting: glass panels over a lit backdrop), Ember, Ember light, Slate and High contrast.

## On a phone or a tablet

Below 900 pixels wide the navigator is a drawer (the ☰ at the left of the status bar opens it, and it shuts
once you choose), the inspector takes the screen, and the launchpad's tiles are one column; every button
is at least 44 pixels on a touch screen.
