# Sessions

A session is one conversation, with its tasks. Sessions belong to the service, not to a window: the
terminal and the browser show the same sessions, live, and either can continue what the other started.
Closing a window never stops a task.

## Opening

| Where | How |
|---|---|
| Terminal | `/sessions` or `ctrl+x l`; `ctrl+p` also lists them |
| Browser | The navigator down the left, every project with its sessions; `Alt+B` for every session |
| Starting the terminal | `albert-mini -c` continues the latest session in this folder; `albert-mini -s <id>` opens one |

A new session is named after its first message.

## Managing

| Action | Terminal | Browser | Command line |
|---|---|---|---|
| Rename | `/rename`, or `ctrl+r` in the list | The title | `albert-mini sessions rename <id> "title"` |
| Pin | `ctrl+t` in the list | The session's `⋯` in the navigator, or Every session (`Alt+B`) | |
| Stop | `/stop`, or `Esc` | Stop in the session's head, or the stop button beside it in the navigator | |
| Archive (kept, off the list) | | The session's `⋯` in the navigator | |
| Fork (a new session with the same messages) | `/fork` | `Ctrl+K`, *Fork this session* | |
| Export as JSON | `/export [file]` | `Ctrl+K`, *Export this session as JSON* | `albert-mini sessions export <id> [file]` |
| Import | `/import <file>` | `Ctrl+K`, *Import a session from JSON* | `albert-mini sessions import <file>` |
| Delete | `ctrl+d` in the list | The session's `⋯` in the navigator, or Every session (`Alt+B`) | `albert-mini sessions delete <id>` |
| Take a project off the list | | The project's `⋯` in the navigator, *Remove from the list…* | |

Deleting a session removes its messages; its tasks and their evidence stay. Taking a project off the list
archives its sessions (Every session still has them) and never touches its folder. Sessions run on their
own: while one works you can open, use and stop the others.

```bash
albert-mini sessions                    # newest first
albert-mini sessions --search discount  # titles and message text
albert-mini sessions show <id>
```

## Leaving and coming back

When you leave the terminal, it prints the session and the exact command that opens it again:

```text
Fix the discount in cart totals (4f1c2e7a90b3)
It is waiting for you to decide, in either interface.
Continue it: albert-mini --session 4f1c2e7a90b3
```
