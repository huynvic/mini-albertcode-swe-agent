# Security

## The local service

The terminal and the browser talk to one service on your machine.

- It listens on `127.0.0.1` only, unless you start it otherwise (`albert-mini serve --host`), and then it
  requires authentication.
- It answers only requests that carry this installation's access token. The token is kept in a file
  only your user can read.
- The browser receives the token once, in the address `albert-mini web` opens. The service swaps it at
  once for a cookie that the page cannot read and that other sites cannot send, and takes it out of the
  address.
- Its pages carry a strict content security policy, and what a conversation contains (a model's answer,
  a file's text) is shown as text, never run.

## Your keys

- Provider keys and MCP sign-ins are kept by your system's own protection: the macOS Keychain, Windows
  data protection, or your Linux desktop keyring. Without a keyring, they go in a file only your user can
  read.
- A key is checked with its provider before it is saved, and is never shown again, in either interface
  or in any log.
- A key is sent only to the provider it belongs to.
- Tasks run with a cleaned environment: the keys you saved are not handed to the commands a task runs.

## Your files

- **Governed**: a change is built in an isolated copy of your repository, and reaches your files only
  when you apply it at the second gate. The copy is deleted when you discard or reject it.
- **Direct · ask each write**: each write and each command waits for your OK, showing what it changes.
- **Direct · auto-approve**: writes are carried out without asking. Use it with Git, which is the undo.
- Commands a task runs are limited to what the engine allows, and file access stays inside the
  repository.
- Your repositories are never touched by installing, updating or uninstalling.

## What leaves your machine

Only what a feature you use needs: your requests and the parts of your repository a task reads go to
the model provider you connected (nothing, with a local model), and what an MCP server's tools are given
goes to that server. There is no telemetry. See [Privacy](../PRIVACY.md).

## Reporting a problem

Privately, through the repository's Security tab: see [SECURITY.md](../SECURITY.md).
