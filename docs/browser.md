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

- **The top bar**: the tabs of your open sessions, a new session, and every session.
- **The conversation**, in a centred column, with the box at its foot: the mode chip and the model chip
  beside it, attachments, and send.
- **The side panel** (`Alt+P`): the change, a file at a time, of the task's isolated copy or of your
  working tree; the session's context and usage; and the task in full.
- **Every session** (`Alt+B`): newest first, by day, pinned on top, searchable.

## Keys

| Key | Does |
|---|---|
| `Enter` | Send |
| `Shift+Enter` | A new line |
| `Esc` | Stop a run · close · go back |
| `Ctrl+K` | Every command |
| `Alt+N` | A new session |
| `Alt+B` | Every session |
| `Alt+P` | Show or hide the side panel |
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

Open them from every command (`Ctrl+K`, *Settings*): the theme (shared with the terminal), timestamps,
the keys, and about this installation. The same six themes as the terminal: Graphite and Paper (the
defaults, by your system's light or dark setting), Ember, Ember light, Slate and High contrast.

## On a phone or a tablet

Below 900 pixels wide the side panel takes the screen and the session list is one column; every button
is at least 44 pixels on a touch screen.
