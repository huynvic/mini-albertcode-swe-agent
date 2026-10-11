# Changelog

Every release of mini-AlbertCode SWE Agent, newest first. Each one's installers and checksums are on
its [release page](https://github.com/huynvic/mini-albertcode-swe-agent/releases).

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
- **MCP servers**, local and remote with sign-in, a connector catalogue, and importing your OpenCode
  servers.
- **Installers for Windows, macOS and Linux**, which check the machine, show their plan and ask before
  changing anything, and find the version installed and ask before updating it; `albert-mini update`
  and `albert-mini uninstall`.
- Carries the AlbertCode engine 1.51.1.
