# Using mini-AlbertCode

The short version of everything. Each section links to its full guide.

## Two interfaces, one service

| Interface | Start it | Good for | Guide |
|---|---|---|---|
| Terminal | `albert-mini` | Working where you already are; scripts and CI | [The terminal](terminal.md) |
| Browser | `albert-mini web` | Plans and diffs side by side; every project's sessions in one list | [The browser](browser.md) |

Both talk to the same local service, so a session started in one is live in the other. See
[How mini-AlbertCode works](how-it-works.md).

## Modes

| Mode | What happens | Use it when |
|---|---|---|
| **Governed** (default) | You approve a plan, it works in an isolated copy, runs your tests and reviews the result, then you approve the diff | Changes you care about |
| **Direct · ask each write** | It works in your files and asks before each write | Quick changes you're watching |
| **Direct · auto-approve** | It works in your files without asking | Small, safe changes, with Git as the undo |
| **Ask only** | It answers, and offers a change for your go | Understanding a codebase |

`tab` cycles them in the terminal; in the browser, Governed, Direct and Ask only are in the box, a click
each. `/plan …`, `/do …` and `/direct auto …` choose one for a single message. See
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
| `/docs <words>` | Search this guide (`albert-mini docs <words>` in a shell) |

In the browser, `Ctrl+K` lists every command, and Help searches this guide. See [The terminal](terminal.md#commands) and
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

Give it screenshots, documents and other files to read with your message.

| Interface | How |
|---|---|
| Browser | The **+** under the box, paste a screenshot, or drop files onto the page |
| Terminal | `/attach <paths>`: one or more paths, globs work (`/attach logs/*.txt error.png`). `/attach` alone lists what is waiting; `/attach clear` drops it |

In the browser each file shows as a tile in the box the moment you add it: a picture or a PDF as a small
picture of itself, any other file with its kind and size. **×** on a tile removes it. Once sent, the same
tiles show in the message, and a click opens the file.

| What you attach | What the model gets |
|---|---|
| Pictures: PNG, JPEG, GIF, WebP | The picture itself, when the model accepts pictures; otherwise you are told it could not see it |
| PDF | Its text; a scanned page, with no text in it, as a picture of the page |
| Word (`.docx`), Excel (`.xlsx`), PowerPoint (`.pptx`) | Their text, and a spreadsheet's cells |
| Text and code: `.txt`, `.md`, `.csv`, `.json`, `.log`, `.py`, `.ts` and the like | The text |
| Video: MP4, MOV, WebM | Stills from it in order, each with its time, when the model accepts pictures |
| Older Office files (`.doc`, `.xls`, `.ppt`) and anything else | Its name and size only: save it as `.docx`, `.xlsx`, `.pptx` or PDF for it to be read |

Up to 20 files, each up to 500 MB. They go with your next message, and a change started in the session,
then or later, gets the session's files too, so the work sees the screenshot the conversation just read.
A file is kept apart from your repository, never written into it.

For example: drop `error.png` and `invoice.pdf` onto the page, type *Why does checkout show this error,
and does the total match the invoice?* and send. Albert reads the error in the picture and the total in
the PDF; with Direct chosen, *fix it* then starts the change with both files to hand.

## Checking your setup

```bash
albert-mini --version        # the version, and the AlbertCode engine it carries
albert-mini doctor           # the installation, the service and what it is connected to
albert-mini models test      # one tool-calling request to the chosen model
```

See [Troubleshooting](troubleshooting.md) when something is wrong.
