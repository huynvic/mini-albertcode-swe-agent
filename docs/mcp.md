# MCP servers

MCP servers give tasks outside tools: a database, a browser, an issue tracker, your own scripts.
mini-AlbertCode runs local servers (started as a command on your machine) and remote ones (Streamable
HTTP, with sign-in where the server asks for it).

## Managing them

| Where | How |
|---|---|
| Terminal | `/mcp`, or `ctrl+x c`: `enter` switches one on or off, `ctrl+r` reconnects, `ctrl+a` signs in, `ctrl+d` removes |
| Browser | *Settings → MCP servers…* in the menu bar, or *MCP* in the status bar |
| Command line | `albert-mini mcp …`, below |

The welcome screen and the sidebar say how many are connected, and how many need your attention
(`2 connected, 1 needs attention`).

## Adding one

**Ready to add.** *MCP servers…* (the Settings menu, or *MCP* in the status bar) lists every connector
under *Ready to add*. Each one has been installed on a clean machine, connected, and had its tools listed
and called. Most are a single click; a few ask one question first, such as a folder, in a field that
hides anything secret. In the terminal it is *+ Add a connector…* in `/mcp`, and on the command line
`albert-mini mcp connectors`, then `albert-mini mcp install <id>`.

| Connector | What it gives Albert | Needs on your machine | Asks for |
|---|---|---|---|
| Git | Status, diffs, log and branches of a repository | `uv` | The repository's folder |
| Filesystem | Read, write and search files, only inside the folders you name | Node.js | The folders |
| Fetch | A web page, as Markdown | `uv` | Nothing |
| AWS Documentation | Search and read AWS's documentation | `uv` | Nothing |
| Hugging Face | Search models, datasets, Spaces and papers; sign in for your own | Nothing (remote) | Nothing (sign in is optional) |
| Playwright | A real browser to open pages, click, type and read | Node.js and Google Chrome | Nothing |
| Chrome DevTools | A live Chrome: console, network, performance, the page | Node.js and Google Chrome | Nothing |
| PostgreSQL | Read-only SQL, schemas and query plans | `uv` | The connection URI |
| Memory | A knowledge graph Albert keeps notes in across sessions | Node.js | Nothing |
| Sequential Thinking | Notes for working through a hard problem step by step | Node.js | Nothing |
| Time | The current time and time-zone conversion | `uv` | Nothing |
| Everything | The protocol's reference server, for trying MCP out | Node.js | Nothing |

The first start of each downloads its server (a few seconds; up to two minutes on a slow connection).

**From a server's instructions.** Most MCP servers say how to add them with a block of JSON. Paste it
into *Import JSON…* in the MCP dialog (or open the file it is in), or give the file to the command line.
Servers under `mcpServers` or `servers` are read, comments are fine, and nothing connects until you add
it. Values of `env` and `headers` are only ever shown masked:

```json
{
  "mcpServers": {
    "memory": { "command": "npx", "args": ["-y", "@modelcontextprotocol/server-memory"] },
    "docs": { "url": "https://mcp.example.com/mcp", "headers": { "Authorization": "Bearer {env:DOCS_TOKEN}" } }
  }
}
```

```bash
albert-mini mcp import servers.json           # show what would be added
albert-mini mcp import servers.json --apply   # add them
```

**By hand:**

```bash
albert-mini mcp add files --command "npx -y @modelcontextprotocol/server-filesystem ."
albert-mini mcp add docs --url https://mcp.example.com/mcp
albert-mini mcp add api --url https://mcp.example.com/mcp --header "Authorization=Bearer <token>"
```

## Signing in

A remote server that needs a sign-in says so in the MCP list. Sign in with `ctrl+a` in the terminal's
list, *Sign in* in the browser, or `albert-mini mcp auth <name>`: your browser opens the server's sign-in
page, and the service receives the result itself (OAuth with PKCE). `albert-mini mcp logout <name>`
forgets it. A sign-in made in one interface works in the other.

## Prompts

A server's prompts become commands: `/server:prompt key=value …` asks the server to fill the prompt in,
and the result lands in the box for you to read, change and send.

## Command line

```bash
albert-mini mcp                         # list them, with their state and tools
albert-mini mcp enable <name>           # switch one on; disable switches it off
albert-mini mcp connect <name>          # connect again
albert-mini mcp tools <name>            # what it offers
albert-mini mcp connectors              # the catalogue
albert-mini mcp install <id> key=value  # add one from the catalogue
albert-mini mcp import FILE [--apply]   # servers from a block of JSON
albert-mini mcp remove <name>
```
