# Changelog

Every release of mini-AlbertCode SWE Agent, newest first. Each one's installers and checksums are on
its [release page](https://github.com/huynvic/mini-albertcode-swe-agent/releases).

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
