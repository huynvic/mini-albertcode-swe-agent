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

Only Direct needs Git: it writes in your real files and keeps Git as the undo, so a wrong write can be taken
back. Governed builds in a copy and needs none.

**Choosing Direct** in a folder with no Git (the mode buttons in the browser; `tab`, `/mode direct` or
`/mode auto` in the terminal) asks at once, before anything is sent: *Direct needs Git here. Set up Git now?*

| Answer | What happens |
|---|---|
| Yes, set up Git (`y` in the terminal) | Git is started in the folder and what is there now becomes its first commit; files that look like they hold secrets (`.env`, private keys) are left out and stay untracked. Then Direct is chosen. |
| No (`n`, or `esc`) | Nothing is made, and the mode stays as it was. In the terminal, `tab` goes on to Ask only. Governed and Ask only work without Git. |

**Asking for a direct change** in a folder with no Git (`/direct …` or `/do …` in front of a message, *Do it
directly* on a change offered in Ask only, or a session started in Direct) asks the same question in the
conversation:

| Answer | What happens |
|---|---|
| Set up Git and do it directly (`o`) | Git is set up as for *Yes* above, then the change is done directly. |
| Plan it first (`p`) | The change is planned and built in a copy, as Governed; no Git is made. |

Nothing is made until you answer. A folder with more files than a first commit should carry (usually a
dependency folder a `.gitignore` would leave out) is left as it was, and the answer says so.

**Example.** Open a folder of HTML files with no Git and click **Direct**: *Direct needs Git here* pops up.
Choose **Yes, set up Git**: the folder gets Git with one commit, *Baseline before the first direct change*,
and Direct is on. Ask *Add a dark mode toggle*; `git diff` shows exactly what Albert changed, and
`git checkout .` undoes it.

Choose it:

| Where | How |
|---|---|
| Terminal | `tab` cycles the modes; `/mode` lists them; `/mode auto` and the like choose one |
| Browser | Governed, Direct or Ask only, in the box; in Direct, *Ask each write* or *Auto-approve* beside it |
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

Either closes the question at once, and the proposal says it is starting while Albert reads the code; the
steps show as they happen. If the change cannot start (no model connected, say), the proposal is offered
again with a note saying why.

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
