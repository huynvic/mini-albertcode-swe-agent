# Custom commands and agents

## Custom commands

A command is a prompt you write once and call by name. It is a Markdown file:

```markdown
---
description: Review a file for correctness bugs
agent: reader          # optional: run as this custom agent
mode: ask              # optional: ask, governed or direct
argument-hint: <file>
---
Review $ARGUMENTS for correctness bugs, not style. Start with $1.
```

Saved as `.albertcode/commands/review.md` in a repository, it is `/review`:

```text
your-project · gpt-4o · governed ❯ /review src/cart.py
```

| Where | Applies to |
|---|---|
| `.albertcode/commands/<name>.md` in a repository | That repository; shared when you commit it |
| `commands/<name>.md` in your settings folder | Every repository, for you only |

- `$ARGUMENTS` is everything typed after the command; `$1` to `$9` are its words, quoted as a shell
  would. With neither in the text, what you typed is added at the end.
- When two places define the same name, the repository wins. A command can never take a built-in's
  name: `/plan` is always `/plan`.
- **A command is text.** Running one runs no program and reads no file: what it expands to is sent as
  your own message, and the mode and the approvals apply as if you had typed it.

Custom commands appear in the `/` list and in `/help`.

## Custom agents

An agent is a role a task works as. It can only narrow what mini-AlbertCode may do, never widen it.
Keep agents in `.albertcode/agents/` in a repository, or in `agents/` in your settings folder. Choose
one with `/agent` (or `ctrl+x a`) in the terminal, or the agent chip in the browser; *Albert* goes back
to the default. A custom command's `agent:` line uses one for that message only.

- With no `tools` line, an agent changes only the instructions.
- An agent that cannot edit answers questions only: a change asked of it is refused before anything
  starts, with the reason.
- The agent is fixed when a task starts.
