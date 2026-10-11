# Glossary

**AlbertCode engine.** What does the work: planning, the isolated copy, the checks and reviews, the
gates. mini-AlbertCode carries it; `albert-mini --version` names its version.

**Agent.** A role a task works as, which can only narrow what it may do. See
[Custom commands and agents](extending.md).

**Direct.** Modes that work in your real files: *ask each write* waits for your OK at each write;
*auto-approve* doesn't.

**Gate.** A point where a task waits for you: the plan, the result, or a write. See
[Modes and approvals](modes-and-approvals.md).

**Governed.** The mode in which a change is planned for your approval, built in an isolated copy,
checked and reviewed, and applied only when you say so.

**Isolated copy.** A temporary copy of your repository that a governed change is built in, so your
files are untouched until you apply it.

**MCP server.** A program that gives tasks outside tools. See [MCP servers](mcp.md).

**Provider.** Where a model runs: a hosted service, an OpenAI-compatible service, or a server on your
machine. See [Models](models.md).

**Service.** The local program both interfaces talk to, on `127.0.0.1:8778`.

**Session.** One conversation with its tasks, shared by both interfaces. See [Sessions](sessions.md).

**Task.** The work one request for a change starts: its plan, its steps, its checks and its result.
