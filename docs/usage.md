# Using mini-AlbertCode

The short version of everything. Each section links to its full guide.

## Two interfaces, one service

| Interface | Start it | Good for | Guide |
|---|---|---|---|
| Terminal | `albert-mini` | Working where you already are; scripts and CI | [The terminal](terminal.md) |
| Browser | `albert-mini web` | Plans and diffs side by side; several sessions in tabs | [The browser](browser.md) |

Both talk to the same local service, so a session started in one is live in the other. See
[How mini-AlbertCode works](how-it-works.md).

## Modes

| Mode | What happens | Use it when |
|---|---|---|
| **Governed** (default) | You approve a plan, it works in an isolated copy, runs your tests and reviews the result, then you approve the diff | Changes you care about |
| **Direct · ask each write** | It works in your files and asks before each write | Quick changes you're watching |
| **Direct · auto-approve** | It works in your files without asking | Small, safe changes, with Git as the undo |
| **Ask only** | It answers, and offers a change for your go | Understanding a codebase |

`tab` cycles them in the terminal; the mode chip beside the box chooses one in the browser. `/plan …`,
`/do …` and `/direct auto …` choose one for a single message. See
[Modes and approvals](modes-and-approvals.md).

## Approvals

| Gate | Answers |
|---|---|
| The plan | `a` approve and build · `e` ask for changes · `d` read the whole plan · `r` reject |
| The result | `a` accept into your files · `v` view the diff · `e` ask for changes · `x` discard · `r` reject |
| A write (Direct · ask each write) | `a` allow once · `A` allow the rest of the task · `n` decline |
| A change offered (Ask only) | `p` plan it first · `o` do it directly |

The same keys work in both interfaces, and an answer given in one is seen at once in the other.

## Everyday commands

| Command | What it does |
|---|---|
| `/connect` | Connect a model provider |
| `/model` | Choose a model |
| `/plan <request>` | Start a governed change |
| `/do <request>` | Change your files directly, asking before each write |
| `/mode` | Choose the mode |
| `/sessions` | Open, rename, pin or delete sessions |
| `/diff` | This session's change, or your working tree's |
| `/attach <paths>` | Attach files to your next message |
| `/web` | Open this session in the browser |
| `/help` | Every command, to search and run |

In the browser, `Ctrl+K` lists every command. See [The terminal](terminal.md#commands) and
[The browser](browser.md#keys).

## Sessions

A session is one conversation with its tasks, the same in both interfaces. `albert-mini -c` continues
the latest one in a folder, and `albert-mini -s <id>` opens one. Rename, pin, fork, export or import them
from either interface. See [Sessions](sessions.md).

## Scripting

```bash
albert-mini run "add a health check endpoint" --approve plan,result
```

`run` sends one request and prints what happens. It answers only the gates `--approve` names; a change
that stops at another gate exits with code 3, to be answered in either interface. See
[Commands](commands.md#run).

## Attachments

Give it files or screenshots to read: `/attach <paths>` in the terminal, or the `+` beside the box in the
browser. They go with your next message.

## Checking your setup

```bash
albert-mini --version        # the version, and the AlbertCode engine it carries
albert-mini doctor           # the installation, the service and what it is connected to
albert-mini models test      # one tool-calling request to the chosen model
```

See [Troubleshooting](troubleshooting.md) when something is wrong.
