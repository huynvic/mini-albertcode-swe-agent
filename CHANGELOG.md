# Changelog

Every release of mini-AlbertCode SWE Agent, newest first. Each one's installers and checksums are on
its [release page](https://github.com/huynvic/mini-albertcode-swe-agent/releases).

## 0.1.11

- **Attachments show as themselves, and the work gets them.** A picture or a PDF you attach now shows as a
  small picture of itself in the box the moment you add it, and in your message once sent; a Word, Excel,
  PowerPoint or any other file shows its kind and size; a click opens it. Albert reads pictures (for a model
  that accepts them), PDFs (a scanned one's pages as pictures), Word, Excel, PowerPoint, text and code
  files. A change started from the conversation used to get none of the session's files, so the work could
  not see the screenshot just read; now it gets them all. Sending while a file is still uploading waits for
  it, rather than leaving it behind.
- **Switching mode mid-conversation works.** In Governed, a change's plan waits for your approval; switching
  to Direct and saying *do it* used to be taken as feedback on that plan, which was planned again, still in
  Governed, however often you said you had switched. Now the plan is set aside and the change done directly.
  Albert is also told the mode on every message, so *I've switched to Direct, go ahead* is understood; and
  when it tells you to switch mode for a change, it starts nothing and offers the change instead.
- **105 connectors ready to add, 58 of them services you sign in to.** With network access, about 120 hosted
  MCP servers were tried in mini-AlbertCode as you would add one. Sixteen that need no sign-in connected and
  answered a real tool call: DeepWiki, Context7, Microsoft Learn, Cloudflare Docs, GitMCP, Astro Docs,
  Svelte, Exa Search, LiveKit Docs, javadocs.dev, OpenAI Docs, LangChain Docs, Convex, CoinGecko,
  OpenZeppelin Contracts and Socket. Fifty-eight services reached with your own account were checked as far
  as anyone can go without that account: *Add* registered mini-AlbertCode with the service and opened its
  own sign-in or consent page. Among them are GitLab, Linear, Notion, Jira and Confluence, Asana, Sentry,
  Stripe, Supabase, Neon, Vercel, Netlify, five Cloudflare servers, PostHog, Miro, monday.com, ClickUp,
  Airtable, PayPal, Square, Zapier and Webflow, grouped by kind. GitHub, Figma, Slack and a few others do
  not let an app register itself; the guide shows how to add them with a token.
- **A sign-in asks for what the server names.** Upstash refused mini-AlbertCode's sign-in ("invalid_scope")
  because it was asked for every scope its sign-in server lists; it is now asked for the scopes the server
  itself names, as the MCP specification says. A server whose declared resource differs from its address
  (Vercel, Airtable, Asana and others) is now asked for the resource it declares, only ever on its own site.
  Consent pages name *mini-AlbertCode SWE Agent* rather than AlbertCode.
- **Nineteen more, mostly run on your machine**, each added from the directory exactly as you would, connected,
  and answering a real tool call: ESLint, Code Index, Tree-sitter, Repomix, shadcn/ui, Next.js DevTools,
  Angular CLI, Shopify Dev, AWS Knowledge, PyPI, npm Search, SQLite, DuckDB, Chroma, Qdrant, Excel,
  MarkItDown, Word documents and Calculator.
- **A connector that signs in is one step.** *Add* opens its sign-in page at once, in a new tab (in the
  terminal and with `albert-mini mcp install <id>`, in your browser): sign in, allow access, and it connects
  by itself, with no key typed anywhere. The page you end on now says to go back to mini-AlbertCode rather
  than AlbertCode.

## 0.1.10

- **Choosing Direct in a folder without Git asks at once.** Direct keeps Git as its undo, so in a folder
  without it a direct change used to stop at a question only once you had asked for it. Now the question comes
  the moment you choose Direct (the mode buttons in the browser; `tab` or `/mode direct` in the terminal):
  *Direct needs Git here. Set up Git now?* **Yes** starts Git with what is in the folder as its first commit
  (files that look like they hold secrets are left out) and turns Direct on; **No** makes nothing and keeps
  the mode as it was. In a folder that has Git, Direct is chosen as fast as before, with no question.

## 0.1.9

- **Preview: run the project beside the conversation.** ▷ in a session's head (or `/preview` in the terminal)
  runs the project's app with its own script (`npm run dev`, Django's `runserver`, or the command you type),
  or, for plain web pages such as a browser game, serves them as they are, at an address of their own. The
  panel shows it at desktop, tablet or phone width, says whether it answers, and, when it fails, shows the
  error with *Ask Albert to fix*. Pages are served only to this computer, and never a `.env`, a key or Git's
  folder.
- **A terminal in the page.** ⌨ in a session's head (or `` Ctrl+` ``) opens a real shell in the project's
  folder, with tabs; each shell keeps running when the panel is hidden or the page reloads. It is off until
  you turn it on, only your own page can connect to it, and no model key is in its environment. *Open in your
  terminal app* (`/terminal` in the terminal) opens your own terminal there instead.
- **Direct in a folder with no Git asks instead of failing.** It used to end in *That did not work: … Shall it
  set one up?*, with nothing to answer it with. Now the question has its answers: *Set up Git and do it
  directly* starts Git in the folder with what is there as the first commit (files that look like they hold
  secrets are left out), then does the change; *Plan it first* builds it in a copy, which needs no Git. Nothing
  is made until you answer, in the browser or the terminal.

## 0.1.8

- **No answer waits for the model.** *Plan it first* and *Do it directly* on a proposed change used to keep
  the question open, its button spinning, until the model had planned the change (a direct change: until it
  was done), half a minute or more; in the terminal, every key pressed after it waited in line. The question
  now closes at once, the proposal says it is starting, and the steps show as Albert reads and plans. If the
  change cannot start, the proposal is offered again with a note saying why.
- **Stop answers at once**, even while the model is in the middle of a long step. Stop used to wait for that
  step to end (with DeepSeek, a minute or more of *Stopping…*); the session is now free again in under a
  second, and the step ends quietly in the background.
- Measured with a long build running: approving a plan closes its question in 0.3 s, accepting a change in
  0.15 s, starting a proposed change in 0.3 s, and typing keeps up (under 75 ms a key).

## 0.1.7

- **A build no longer goes round in circles.** A task that looked at its page in the browser lost its place:
  each screenshot was counted as if it were 400,000 characters of text, over the whole memory budget, so the
  task folded its memory after every look, forgot it had already written the change, and started finding out
  again. A simple browser chess game never finished: still going after 25 minutes, 234 model calls and 4.9
  million input tokens. This release carries AlbertCode's own fix, before AlbertCode releases it: a picture
  counts what it costs, only the latest two screenshots stay in the conversation (pictures you attach are
  never dropped), and a fold names the files already changed.
- **Any task going round in circles is stopped.** When every step repeats an earlier one and gets the same
  answer, the task is told so after three rounds, refused its tools after five and stopped after seven; what
  it wrote is checked and reviewed as it stands, and it is never started over just to go round again. A
  failing step asked again in other words counts too: a task that ran one failing test command 91 times,
  one flag longer each time, is now stopped after seven.
- **DeepSeek thinks lightly where a step asks it to.** DeepSeek thinks just as hard whatever level it is
  sent, so a light think now switches its thinking off: at Speed: Fast, answers in the conversation and the
  review. "Build a simple HTML chess game" with DeepSeek, Governed: the review in 43 s instead of 128 s, the
  task in about 10 minutes instead of 11; a short question's first word in 1.9 s instead of 2.4 s. Planning
  and writing keep their depth: switched off there too, DeepSeek built the same game in 3 minutes once, but
  more often took longer, clicking through its page hundreds of times.
- **A model that turns pictures down is not sent them again**, and is told it cannot look at them, instead of
  being told "the image is attached; look at it".

## 0.1.6

- **Answers start sooner.** With the same model, a conversation now asks it for a light think (Speed:
  Fast), where it used to ask for the provider's deepest, and a change you ask for is said and started at
  once instead of being read through twice. With DeepSeek: a question's first word came in 4.3 s (from
  6.0), a direct change started in 2.5 s (from 7.1), a governed change showed its card in 3.6 s (from
  8.1), and its plan was ready in 11 s (from 16).
- **The browser keeps up.** A long answer used to be drawn again in full for every few words; now only
  the paragraph being written is, a frame at a time, and following the conversation no longer makes the
  page measure itself on every word. On a slow laptop the page stayed responsive while an answer streamed
  (its longest pause 0.24 s, from 1.7 s).
- **What the model is thinking** shows under *Thinking…* while it thinks, for a model that shares it
  (DeepSeek, among others), so a long think is never a blank wait. It is shown live and never kept.
- **Show or hide the agent's steps** with `Alt+S`, the View menu, or a task card's own *Steps* switch.
  Hidden, you still see the one step under way. The choice is kept in your browser.
- **More room for the conversation.** The box is one line until you type more, the session's head and a
  gate are tighter, the project bar shows only on a new session, and a notice is a short strip at the top
  instead of covering the conversation: on a 1366 × 768 screen with a plan waiting, the conversation has
  370 pixels, from 230.
- **Search the guide where you work.** Help in the browser (`/docs`), `/docs` in the terminal and
  `albert-mini docs` in a shell search this guide as you type and show the section that answers you, with
  its link online. The guide comes with mini-AlbertCode, so it works offline and matches your version.
- **The terminal shows a planned change while it is planned**: its task appears in the conversation
  from its first moment, as in the browser, not once the plan is ready.
- A command that opens a dialog from the box (`/model`, `/docs`) leaves the keys with the dialog.

## 0.1.5

- **A pressed answer shows at once.** Approve, Accept, Allow, Reject, Discard, *Plan it first* and *Do it
  directly* say on their own button what they are doing (*Approving…*, *Accepting…*, *Starting the
  plan…*) the moment you press them, and the other answers wait, so nothing is answered twice. Once the
  service has the answer, the gate says what happened until the work moves on. Stop says *Stopping…*, and
  the send button shows that your message is on its way.
- **Replies show what they read.** Before Albert answers, each file it reads and each search shows as a
  step (*Read cart.py*, *Searched for "discount"*), with the step under way beside it, in the browser and
  the terminal. Words said before reading stay as a step instead of vanishing. Then the answer flows in
  word by word, and the steps fold to one line that opens again.
- **A task is followed from its first moment.** A planned change shows its card while it is being planned,
  not once the plan is ready (with DeepSeek, about five seconds sooner), and a change started from *Plan
  it first* shows at once instead of after its planning. The card lists each step as it lands, with the
  step under way at its foot and the time it has been at it, counting.
- **The terminal says what Albert is doing**: the line over the prompt names the step (*Reading cart.py…*,
  *Running python -m pytest -q…*) rather than only *Working*.

## 0.1.4

- **Faster everywhere.** Typing in the browser now takes about a frame (11 ms a key, from 64 ms), an
  answer streams at 60 frames a second (from 10), and moving to another session while one works takes a
  tenth of a second: the panels were a live blur painted again on every keystroke. The working tree lists
  every changed file at once and reads a file's diff when you open it, where it read all of them first
  (and left out every file after the 60th).
- **Speed: Fast, Balanced or Thorough** sets how much the model thinks at each step (Settings, General, or
  `/speed`). Fast, the default, lightens the review and keeps planning and writing as deep as ever: a
  governed fix with DeepSeek took about a quarter less time, every check and review still run.
- **Stop, archive, delete and remove.** Each session in the navigator has its actions (rename, pin, stop,
  archive, delete) and a stop button while it works; a project can be taken off the list (its sessions
  archived, its folder untouched) or have its sessions deleted. Sessions run on their own: while one
  works, open, use and stop the others.
- **A resizable inspector**: drag the edge between the conversation and the inspector, or move it with the
  arrow keys; the width is kept.
- **MCP servers ready to add.** The MCP dialog lists every connector (Git, Filesystem, Fetch, AWS
  Documentation, Hugging Face, Playwright, Chrome DevTools, PostgreSQL, Memory, Sequential Thinking, Time,
  Everything), each a click or one answer away. Import the JSON block a server's instructions give
  (`mcpServers`), in the browser, in the terminal's `/mcp` or with `albert-mini mcp import FILE`.
- **Nothing empty.** The inspector before a session or a task, Settings (MCP servers, agents, about) and
  Every session with none yet now say what is there and what to do next.
- **The terminal's prompt follows the welcome**, instead of waiting at the foot of an empty screen.

## 0.1.3

- **A browser workspace of its own.** A navigator down the left lists every project with its sessions,
  each with a lamp for what it is doing. A governed task's session head has the **gate track**: the work
  as circles, the two human gates as diamonds, lit where the task stands (working, waiting for you,
  stopped). You type at the console's ❯, with the mode one click away (Governed, Direct or Ask only) and
  the provider and the model beside it. The inspector shows the change, the context and the task; a status
  bar shows the service, the branch, the model and what the session used. A new session opens on a
  launchpad. Nebula and Aurora, the new default themes, are glass over a lit backdrop.
- **A menu bar, projects, Git and worktrees in the browser.** Open a folder from your drives and folders
  (or make a new one), clone a repository, commit what the Changes tab shows (never a file that looks
  like it holds secrets), pull, push, switch or make branches, and make, use and remove worktrees.
- **Connecting a provider lists its models.** The address comes with `https://` (or `http://` on your
  machine) already there, the key is checked as you type it, and the models it can use are listed to
  choose one; a model per tier is folded under *Advanced*. DeepSeek, Groq, Mistral, Together AI and xAI
  are offered by name. In the terminal, `/connect` ends with the models to choose from.
- **The model list shows each connected provider's own models**, in the browser and the terminal,
  recently used first; providers not connected are folded away, and a model's ID can be typed. It used
  to list three empty tiers per provider, so a provider just connected offered nothing to choose.
- **Settings by section**: General, Providers, Models, MCP servers, Agents, Keys, About.
- **Windows: the terminal takes your typing on a slow start.** The list that offers a model at the first
  start opened over the prompt there, and what you typed went into its search.
- **The Changes tab's working tree no longer fails with "Internal Server Error"** on Windows: Git's
  output is read as UTF-8 whatever the system's code page, and any unexpected failure now says what it was.
- Escape closes a dialog even when focus has left it.

## 0.1.2

- **`albert-mini serve` keeps what is done through it.** Started by hand, the service kept its sessions
  and tasks in memory and its settings in a folder of its own: everything done through it was gone once it
  stopped, and the service `albert-mini` starts did not see its settings. It now uses the same folders as
  the service `albert-mini` and `albert-mini web` start.
- **Updating says what is kept.** The installers said every update would clear saved keys and model
  choices. They are cleared only when the AlbertCode engine changes, and 0.1.2 carries the same engine as
  0.1.1 (1.51.1): keys, model choices, settings and sessions are kept.
- The line a reply ends with for the engine (`@@CHANGE@@ …`) is no longer shown while the reply is being
  written, in the terminal, the browser or `albert-mini run`.
- `albert-mini run` shows the plan it stops at or approves: its objective, steps, files and risk.

## 0.1.1

- **`albert-mini` and `albert-mini web` start the service again.** In 0.1.0 neither could start
  mini-AlbertCode's background service, on any system: both stopped with "The mini-AlbertCode SWE Agent
  service could not be started", and only `albert-mini serve` worked. Update with `albert-mini update`,
  or run the install command again; your settings, keys and sessions are kept.
- `albert-mini doctor` shows the Python it runs on, not the one the release was built with.
- Each release is now installed with the README's own commands on clean Windows, macOS and Linux
  machines, and its service started as `albert-mini` starts it, before it is called done.

## 0.1.0

The first release.

- **Two interfaces, one service.** A full-screen terminal interface (`albert-mini`, or `--mini`
  inline) and a browser workspace (`albert-mini web`) on one local service: a session started in one
  shows in the other at the same moment, and closing either never stops a task.
- **Four modes.** Governed (a plan for your approval, built in an isolated copy, your files changed
  only when you apply it), Direct with each write approved, Direct with writes carried out, and Ask
  only. Questions are always just answered.
- **Two human gates**, answered with the same keys in both interfaces.
- **AlbertCode's terminal look**, with no box, rule or line: its welcome, its prompt with the folder,
  the model and the mode, and its lists.
- **Models.** OpenRouter, OpenAI, Anthropic, Kimi, Hugging Face, any OpenAI-compatible service, or a
  model server on your machine. Connect a provider opens by itself on the first start, and a key is
  checked before it is saved.
- **MCP servers**, local and remote with sign-in, and a connector catalogue.
- **Installers for Windows, macOS and Linux**, which check the machine, show their plan and ask before
  changing anything, and find the version installed and ask before updating it; `albert-mini update`
  and `albert-mini uninstall`.
- Carries the AlbertCode engine 1.51.1.
