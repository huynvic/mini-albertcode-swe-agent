# Privacy

mini-AlbertCode SWE Agent runs on your machine. **It collects no telemetry, no analytics and no usage
data, and it has no account to sign in to.** Nothing about you or your code is sent to its makers.

## Where your data goes

Data leaves your machine only where a feature you use needs it:

| What | Sent to | When |
|---|---|---|
| The parts of your repository a task needs, your requests, and attached files | The model provider you connected | Whenever the model works on a task or answers a question. With a local model, this stays on your machine. |
| Search queries | DuckDuckGo, or a search service you configured with your own key | When a task searches the web |
| Requests for documentation pages | The documentation site | When a task reads documentation |
| Whatever an MCP server's tools are given | That MCP server | When a task uses one of its tools |

Each provider and service handles what it receives under its own terms. Read your model provider's
data-use policy before sending it private code. If you want no code to leave your machine, use a
local model.

## What is kept on your machine

- **Settings**: the providers and MCP servers you connected, your model choice and preferences. The
  provider keys and MCP sign-ins you saved are kept by your system's own protection: the macOS
  Keychain, Windows data protection, or your Linux desktop keyring. Without a keyring, they go in a
  file only your user can read. Keys are sent only to the provider they belong to.
- **Sessions and task history**: your conversations, plans, diffs, test results and reviews, so you
  can come back to past work in either interface.
- **Task workspaces**: the isolated copies of your repository that governed tasks work in.

| System | Folders |
|---|---|
| Windows | `%APPDATA%\mini-AlbertCode SWE Agent` and `%LOCALAPPDATA%\mini-AlbertCode SWE Agent` |
| macOS | `~/Library/Application Support/mini-AlbertCode SWE Agent` |
| Linux | `~/.config/mini-AlbertCode SWE Agent` and `~/.local/share/mini-AlbertCode SWE Agent` |

Uninstalling leaves them in place; `albert-mini uninstall --all` removes them, with your saved keys
and sign-ins.

## The local service

The terminal and the browser talk to one service on your machine. It listens on `127.0.0.1` only, and
answers only requests carrying this installation's access token, which is kept in a file only your
user can read. The browser receives it once, in the address `albert-mini web` opens, and swaps it at
once for a cookie that the page cannot read and that other sites cannot send.

## The installer

The installer downloads from:

- this repository's releases;
- the official uv release on GitHub, pinned and checked against its SHA-256;
- Python's package index, pypi.org, for mini-AlbertCode's dependencies;
- if needed, a Python build, Git (through winget, Apple's tools or your Linux package manager), and a
  browser for the browser tools.

It sends nothing about your machine anywhere.

## Changes

Any change to what mini-AlbertCode sends, or where it sends it, will be listed in this file and in the
[changelog](CHANGELOG.md) before it ships.
