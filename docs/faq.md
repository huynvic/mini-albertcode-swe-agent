# FAQ

**What is it?** A coding agent on your machine, with a terminal interface and a browser workspace on one
local service, carrying the AlbertCode engine. It is proprietary software, distributed through this
repository's releases; see [LICENSING.md](../LICENSING.md). Model use is billed by your model provider,
or costs nothing with a local model.

**Does it send my code anywhere?** Only to the model provider you connect, and to MCP servers you add.
No telemetry, no account. See [Privacy](../PRIVACY.md).

**Can it change my files without asking?** Only in Direct · auto-approve, which you choose. In Governed,
your files change only when you apply a reviewed change; in Direct · ask each write, each write waits
for you.

**Do the terminal and the browser have to stay open?** No. Tasks run in the local service; close either
and they keep going. Open either again to see them.

**Can I use it beside AlbertCode SWE Agent?** Yes. mini-AlbertCode has its own command, its own port
(8778), and its own folders, keys and sessions; nothing is shared between them.

**Which model should I use?** One that supports tool calling. OpenRouter is a good start: one key for
most of the market. `albert-mini models test` checks a model.

**How do I update?** `albert-mini update`, or run the install command again. Your sessions are kept.

**How do I remove it completely?** `albert-mini uninstall --all`.

**Where is the source code?** It is not published. This repository has the installers' bootstrap, the
documentation and the releases.
