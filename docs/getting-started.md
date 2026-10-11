# Getting started

A first task, in about five minutes. You need mini-AlbertCode installed ([Installation](installation.md))
and a Git repository to work in.

## 1. Open it in your repository

```bash
cd your-project
albert-mini
```

The terminal opens on a new conversation: the name in solid letters, the version, the folder and the
model, and the commands to start with. The prompt at the bottom says where you are, which model answers
and which mode you are in:

```text
your-project · gpt-4o · governed ❯ Ask anything, or say what to change; a change is planned first
```

Prefer the browser? `albert-mini web` opens the same thing there. Both show the same sessions.

## 2. Connect a model

The first time, nothing is connected, so **Connect a provider** opens by itself:

```text
No model connected yet. Pick a provider to connect one now, or press Esc to skip and use /connect later.

   Connect a provider
   Search: ▏                          type to filter · ↑↓ · Enter · Esc
   POPULAR
 › OpenAI                             OpenAI's GPT models
   Anthropic                          Anthropic's models
   OpenRouter (recommended)           One key for most of the market, open models included
   OTHER
   ...
   ON THIS MACHINE
   Local server                       A model server on this machine: Ollama, LM Studio, llama.cpp
```

Type to filter, choose with the arrows and `enter`, and paste your API key when it asks (or give a local
server's address). The key is checked with the provider before anything is saved, and it is never shown
again. Then pick a model from the list that opens. See [Models](models.md).

## 3. Ask a question

Questions are always just answered, in every mode:

```text
your-project · gpt-4o · governed ❯ What does this project do, and how are its tests run?
```

## 4. Ask for a change

In the Governed mode (the default), a change starts on a plan:

```text
your-project · gpt-4o · governed ❯ The discount in cart.py is applied twice. Fix it and add a test.
```

mini-AlbertCode reads the repository and proposes a plan, and waits:

```text
Approve this plan?
Nothing has been changed yet · 2 files · risk low

❯ 1. approve   a   Approve the plan and begin isolated implementation.
  2. revise    e   Say what should change; a revised plan comes back.
  3. details   d   Read the whole plan before deciding.
  4. reject    r   Discard this plan and delete its temporary workspace.
```

Press `a` (or `enter`). It builds the change in an isolated copy of your repository, runs your tests,
reviews the result, and stops again:

```text
Apply reviewed changes?
Built and checked in an isolated copy; your files are untouched until you apply it
```

Press `v` to read the diff, then `a` to apply it. Only now do your files change. See
[Modes and approvals](modes-and-approvals.md).

## 5. Next

- `tab` switches between the modes; Direct works in your files directly, each write asking first.
- `/help` lists every command; `/keys` every key.
- `ctrl+x b` shows the sidebar with the session's mode, model, task and changed files.
- Close the terminal at any time: the task keeps going, and `albert-mini -c` continues the session.

Then:

- [How mini-AlbertCode works](how-it-works.md): the ideas behind every page.
- [Modes and approvals](modes-and-approvals.md): the modes, the two gates and every answer.
- [The terminal](terminal.md) and [the browser](browser.md): every key and command.
- [Custom commands and agents](extending.md) and [MCP servers](mcp.md): your own commands, roles and tools.
- [All the documentation](README.md).
