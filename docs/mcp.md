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

**Ready to add.** *MCP servers…* (the Settings menu, or *MCP* in the status bar) lists 105 connectors
under *Ready to add*, by kind, with a search. Each one in the first table below was added there, connected,
and had a tool called; each service you sign in to (the second table) was added there and its own sign-in
page opened from *Add*, which is as far as anyone can go without your account. Most are a single click; a
few ask one question first, such as a folder, in a field that hides anything secret. In the terminal it is
*+ Add a connector…* in `/mcp`, and on the command line `albert-mini mcp connectors`, then
`albert-mini mcp install <id>`.

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
| ESLint | Lint JavaScript and TypeScript with the project's own ESLint setup | Node.js | Nothing |
| Code Index | Index a project and search its code, files and symbols quickly | `uv` | Nothing |
| Tree-sitter | Parse code in thirty-odd languages: syntax trees, symbols, structural queries | `uv` | Nothing |
| Repomix | Pack a repository into one file Albert can read whole | Node.js | Nothing |
| shadcn/ui | Browse, search and add shadcn/ui components from a project's registries | Node.js | Nothing |
| Next.js DevTools | Next.js documentation, and a running dev server's errors and routes | Node.js | Nothing |
| Angular CLI | Angular's best practices, documentation search, examples and migrations | Node.js | Nothing |
| Shopify Dev | Shopify's API documentation and schemas, and checks of code written against them | Node.js | Nothing |
| AWS Knowledge | AWS documentation, regional availability and guidance, hosted by AWS | Nothing (remote) | Nothing |
| PyPI | Python packages: versions, dependencies, compatibility, downloads | `uv` | Nothing |
| npm Search | Search the npm registry | Node.js | Nothing |
| SQLite | Query and change a SQLite database file | `uv` | The database file |
| DuckDB | Analytical SQL in memory over CSV, Parquet and JSON files | `uv` | Nothing |
| Chroma | A vector database in a folder: store documents, search them by meaning | `uv` | The folder |
| Qdrant | Store notes and find them again by meaning, kept in a folder | `uv` | The folder |
| Excel | Read, write and format Excel workbooks | Node.js | Nothing |
| MarkItDown | PDF, Word, Excel, PowerPoint, HTML and more turned into Markdown | `uv` | Nothing |
| Word documents | Create, read and edit Word (.docx) documents | `uv` | Nothing |
| Calculator | Exact arithmetic: expressions worked out, not guessed | `uv` | Nothing |
| DeepWiki | Ask about any public GitHub repository and read the wiki written for it | Nothing (hosted) | Nothing |
| Context7 | Up-to-date documentation and code examples for thousands of libraries, by version | Nothing (hosted) | Nothing |
| Microsoft Learn | Search and read Microsoft's documentation: Azure, .NET, Microsoft 365 and more | Nothing (hosted) | Nothing |
| Cloudflare Docs | Search Cloudflare's documentation: Workers, Pages, R2, D1 and the rest | Nothing (hosted) | Nothing |
| GitMCP | The documentation and code of any GitHub project, read from its repository | Nothing (hosted) | Nothing |
| Astro Docs | Search the Astro web framework's documentation | Nothing (hosted) | Nothing |
| Svelte | Svelte and SvelteKit documentation, and a checker for Svelte code | Nothing (hosted) | Nothing |
| Exa Search | Search the web and read pages, for information newer than the model | Nothing (hosted) | Nothing |
| LiveKit Docs | LiveKit's documentation, SDKs and examples for real-time audio, video and voice agents | Nothing (hosted) | Nothing |
| javadocs.dev | Javadoc, source and latest versions of any Java library on Maven Central | Nothing (hosted) | Nothing |
| OpenAI Docs | Search and read OpenAI's developer documentation and API reference | Nothing (hosted) | Nothing |
| LangChain Docs | Search the LangChain, LangGraph and LangSmith documentation | Nothing (hosted) | Nothing |
| Convex | Convex's guides for starting, building and scaling an app on its backend | Nothing (hosted) | Nothing |
| CoinGecko | Cryptocurrency prices, market data and history | Nothing (hosted) | Nothing |
| OpenZeppelin Contracts | Solidity contracts (tokens, NFTs, governance) written from OpenZeppelin's audited library | Nothing (hosted) | Nothing |
| Socket | Security, quality and licence scores for npm, PyPI and other packages before you add them | Nothing (hosted) | Nothing |

The first start of one that runs on your machine downloads its server (a few seconds; up to two minutes on
a slow connection). A hosted one has nothing to download.

**Services you sign in to.** These reach your own account at a service. *Add* opens the service's sign-in
page; sign in, allow access, and it connects ([Signing in](#signing-in)). Nothing is installed and no key
is typed anywhere.

| Kind | Connectors |
|---|---|
| Code and repositories | GitLab, Postman |
| Browser and testing | Cloudflare Browser Rendering, Apify |
| Data | Supabase, Neon, Prisma Postgres, Upstash, Airtable, Algolia, Hex, Cloudflare Radar |
| Cloud and deploy | Vercel, Netlify, Cloudflare Workers, Cloudflare Workers Builds, Railway, Expo, Buildkite, Clerk |
| Monitoring and analytics | Sentry, PostHog, Amplitude, Honeycomb, Grafana Cloud, Cloudflare Observability |
| Work and planning | Linear, Notion, Jira and Confluence, Asana, monday.com, ClickUp, Todoist, Shortcut, Coda, Miro, Granola, Fireflies.ai, Jam, Zapier, Make |
| Sites and content | Webflow, Wix, WordPress.com, Sanity, Contentful, Cloudinary, Mux |
| Business and payments | Stripe, PayPal, Square, Plaid, Mercury, Intercom, Close, Attio, Klaviyo, Resend |

Each says what it gives Albert where it is listed, for example *Linear: find, create and update issues,
projects and comments*.

GitHub, Figma, Slack, Dropbox, HubSpot and a few others do not let an app register itself for a sign-in, so
they are not in the list. Add one by hand with a token you make on its site (for GitHub, a personal access
token from *Settings → Developer settings*). It is kept readable only by you and only ever shown masked:

```bash
albert-mini mcp add github --url https://api.githubcopilot.com/mcp/ --header "Authorization=Bearer <your token>"
```

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

Adding a connector that signs in takes you straight to its sign-in page: *Add* in the browser opens it in a
new tab, and the terminal and `albert-mini mcp install <id>` open it in your browser. Sign in, allow access,
and it connects by itself; no key is typed anywhere. The page you end on says *Signed in*, and you can close
it. mini-AlbertCode registers itself with the service on the spot and checks the answer (OAuth with PKCE),
and the sign-in is kept in your system's key store.

A remote server added another way says so in the MCP list when it needs a sign-in. Sign in with `ctrl+a`
in the terminal's list, *Sign in* in the browser, or `albert-mini mcp auth <name>`. `albert-mini mcp logout
<name>` forgets it. A sign-in made in one interface works in the other.

**Example.** In *Ready to add*, search *linear* and press *Add* beside Linear. A tab opens on Linear's page
asking whether *mini-AlbertCode SWE Agent* may use your workspace; press *Approve*. The tab says *Signed in
to linear*, and within a few seconds Linear shows *connected* in the MCP list with its tools. Ask Albert
*What are my open Linear issues this week?*

A server you added by its address, `https://mcp.example.com/mcp`, shows *needs sign-in* in the same way.
Press *Sign in*, allow access on its page, and it connects.

Some services ask a question of their own first: Grafana Cloud asks for your stack's address, PostHog
whether your project is in the US or the EU, and a few show a "verify you are human" check before their
sign-in page.

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
