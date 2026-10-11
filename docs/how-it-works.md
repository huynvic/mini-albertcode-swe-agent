# How mini-AlbertCode works

The ideas behind every page: the service and its two interfaces, asking and changing, the modes, the
life of a governed change, sessions and tasks, and what mini-AlbertCode keeps where.

## One service, two ways in

mini-AlbertCode is one service on your machine, with two interfaces on it:

| Interface | Start it | Guide |
|---|---|---|
| Terminal | `albert-mini` in your project folder (`--mini` to stay inline) | [The terminal](terminal.md) |
| Browser | `albert-mini web` | [The browser](browser.md) |

The service listens on `127.0.0.1:8778`. It starts by itself the first time an interface needs it and
keeps running in the background, so closing a window never stops a task. Both interfaces show the same
sessions at the same moment: a message sent in one appears in the other, and an answer given at a gate in
one is seen at once in the other.

```bash
albert-mini status    # whether the service is running, and which version
albert-mini stop      # stop it; it starts again when an interface needs it
```

To use a service running elsewhere, `albert-mini attach <url>` opens the terminal on it, with
`--api-key` when it needs one.

## Asking and changing

Every message is first read as a conversation. A question is answered from your repository's own files,
which it reads but never changes. A request for a change is restated back in a sentence, and what happens
next depends on the mode.

## Modes

The mode decides what happens to a change. Questions are always just answered.

| Mode | A change… |
|---|---|
| **Governed** (default) | starts with a plan for your approval, is built in an isolated copy, checked and reviewed, and reaches your files when you accept it |
| **Direct · ask each write** | is made in your files, and every write and command waits for your OK |
| **Direct · auto-approve** | is made in your files without asking |
| **Ask only** | is offered: it starts when you say go, planned first (`p`) or done directly (`o`) |

The mode belongs to the session, so both interfaces show the same one. See
[Modes and approvals](modes-and-approvals.md).

## The life of a governed change

1. **Plan.** The repository is read, and a plan comes back: the goal, the files it will change and how,
   the steps, the tests, the security considerations, how to undo it, and the risk. Nothing is written.
2. **The first gate.** You approve the plan, ask for changes (a revised plan comes back), read it in
   full, or reject it.
3. **Build.** The change is made in an isolated copy of your repository. Your working tree is untouched.
4. **Verify.** Your project's own tests and checks run in the copy, and the change is reviewed for
   security and for quality, independently of the work that made it.
5. **The second gate.** You read the diff, the checks and the reviews, then accept the change into your
   files, ask for changes (the work continues in the same copy), discard it, or reject it.

When the reviews block a change, applying it anyway asks for a reason, which is recorded. Accepted
changes are ordinary edits: commit them, or undo them, with Git.

## Sessions and tasks

A **session** is one conversation, with its tasks. Sessions belong to the service, not to a window, so
either interface can continue what the other started. See [Sessions](sessions.md).

A **task** is one change, from its plan to its result. It keeps its plan, its steps, its checks, its
reviews and its diff together: in the browser, the side panel's Task and Changes tabs; in the terminal,
the conversation and the sidebar (`ctrl+x b`). A session shows whether it is working, waiting for you, or
idle.

## What mini-AlbertCode keeps, and where

| What | Where |
|---|---|
| The program | `~/.local/share/uv/tools/mini-albertcode` (Windows: `%APPDATA%\uv\tools\mini-albertcode`) |
| The installer's files and log | `~/.local/share/mini-albertcode-installer` (Windows: `%LOCALAPPDATA%\mini-albertcode-installer`) |
| Settings, sessions, task history and task workspaces | Linux: `~/.config/mini-AlbertCode SWE Agent` and `~/.local/share/mini-AlbertCode SWE Agent`. macOS: `~/Library/Application Support/mini-AlbertCode SWE Agent`. Windows: `%APPDATA%\mini-AlbertCode SWE Agent` and `%LOCALAPPDATA%\mini-AlbertCode SWE Agent` |
| Provider keys and MCP sign-ins | Your system's own protection: the macOS Keychain, Windows data protection, or your Linux desktop keyring |

`albert-mini uninstall` keeps your settings and history; `--all` removes them too. See
[Installation](installation.md#uninstalling).

## What the model sees

Your requests, the parts of your repository a task reads, and the files you attach, sent to the model
provider you connected. With a local model, nothing leaves your machine. There is no telemetry. See
[Privacy](../PRIVACY.md) and [Security](security.md).
