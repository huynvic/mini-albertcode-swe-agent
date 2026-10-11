# Modes and approvals

## The modes

The mode decides what happens when you ask for a **change**. Questions are always just answered, in
every mode.

| Mode | What happens |
|---|---|
| **Governed** | A plan comes back for your approval. The change is built in an isolated copy of your repository, your tests run, and the result is reviewed. Your files change only when you apply it. |
| **Direct · ask each write** | Works in your real files. Every write and every command waits for your OK. No plan to approve. Git is the undo. |
| **Direct · auto-approve** | Works in your real files and carries the whole change out without asking. Git is the undo. |
| **Ask only** | Answers, and offers a change; nothing starts until you say go. |

Choose it:

| Where | How |
|---|---|
| Terminal | `tab` cycles the modes; `/mode` lists them; `/mode auto` and the like choose one |
| Browser | The mode chip beside the box; in Direct, the approval switch beside it |
| One message | `/plan …`, `/do …` or `/direct auto …` in front of it |
| A new session | `albert-mini --mode governed\|direct\|direct_auto\|ask` |

The mode belongs to the session, so both interfaces show the same one.

## The two human gates

In the Governed mode a change stops twice for you.

**1 · The plan.** Before anything is written: the goal, the files it will change and how, its tests and
its risk.

| Key | Answer |
|---|---|
| `a` | Approve the plan and begin the isolated implementation |
| `e` | Say what should change; a revised plan comes back |
| `d` | Read the whole plan before deciding |
| `r` | Reject: discard the plan and delete its temporary workspace |

**2 · The result.** After it was built and checked in the isolated copy, before anything reaches your
files.

| Key | Answer |
|---|---|
| `a` | Apply the reviewed change to your repository |
| `v` | Read the change, file by file |
| `e` | Ask for changes; work continues in the same isolated copy |
| `x` | Discard the isolated copy without changing your repository |
| `r` | Reject the change; your repository stays as it is |

When the reviews block a change, applying it anyway asks for a reason, which is recorded.

## Writes, in Direct · ask each write

Each write and each command waits for you, with what it changes:

| Key | Answer |
|---|---|
| `a` | Allow this one write |
| `A` | Allow every write for the rest of this task |
| `n` | Decline this write; the task is told why |

## A change offered, in Ask only

| Key | Answer |
|---|---|
| `p` | Plan it first: a plan comes back for your approval |
| `o` | Do it directly in your files |

## Answering

In the terminal, a gate is a question over the prompt with numbered answers: the arrows choose and
`enter` gives the chosen one, or its number or letter does. In the browser it is a card with its
answers in a row, and the same letters work. An answer given in one interface is seen at once in the
other, and a task is never answered twice.

## From scripts

`albert-mini run` sends one request and prints what happens. Gates are answered only as `--approve`
says:

```bash
albert-mini run "add a health check endpoint" --approve plan,result
```

Without `--approve`, a governed change stops at its plan and exits with code 3. See
[Commands](commands.md#run).
