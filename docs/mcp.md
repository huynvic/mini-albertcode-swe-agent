# MCP servers

MCP servers give tasks outside tools: a database, a browser, an issue tracker, your own scripts.
mini-AlbertCode runs local servers (started as a command on your machine) and remote ones (Streamable
HTTP, with sign-in where the server asks for it).

## Managing them

| Where | How |
|---|---|
| Terminal | `/mcp`, or `ctrl+x c`: `enter` switches one on or off, `ctrl+r` reconnects, `ctrl+a` signs in, `ctrl+d` removes |
| Browser | *MCP servers* in the top bar |
| Command line | `albert-mini mcp …`, below |

The welcome screen and the sidebar say how many are connected, and how many need your attention
(`2 connected, 1 needs attention`).

## Adding one

**From the connector catalogue** (GitHub, Playwright, PostgreSQL, web fetch and more): *Add a
connector…* in the MCP list. It asks only what that connector needs, such as a token, typed into a
field that doesn't show it.

**By hand:**

```bash
albert-mini mcp add files --command "npx -y @modelcontextprotocol/server-filesystem ."
albert-mini mcp add docs --url https://mcp.example.com/mcp
albert-mini mcp add api --url https://mcp.example.com/mcp --header "Authorization=Bearer <token>"
```

**From OpenCode.** If you already set up MCP servers for OpenCode, bring them across. It reads your
OpenCode files the way OpenCode does (global, project and `.opencode`), keeps `{env:…}` references as
references, and masks secrets in everything it shows:

```bash
albert-mini mcp import-opencode           # show what would be added
albert-mini mcp import-opencode --apply   # add them
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
albert-mini mcp remove <name>
```
