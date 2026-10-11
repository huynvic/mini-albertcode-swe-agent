# Models

mini-AlbertCode works with the model you connect: a hosted provider, any OpenAI-compatible service, or a
model server on your own machine.

## Connecting a provider

| Where | How |
|---|---|
| Terminal | `/connect`, or `ctrl+x k`; it also opens by itself on the first start |
| Browser | *Connect a provider…* in the model list (`Alt+M`) |

The list is grouped:

| Group | Providers |
|---|---|
| Popular | OpenAI, Anthropic, OpenRouter (recommended: one key for most of the market, open models included) |
| Other | Kimi, Hugging Face, any other OpenAI-compatible service (its address and key) |
| On this machine | A local server: Ollama, LM Studio, llama.cpp |

Each provider is tagged as the service last found it: `connected`, `key not accepted` or
`not answering`. A provider is called connected only once it has accepted your key, or once its server
has answered with a model; a saved key alone is not enough.

Then, as the provider needs:

- **Its address**, for a local server or another service. Ollama is `127.0.0.1:11434/v1`, LM Studio
  `127.0.0.1:1234/v1`. An address typed without `http://` or `https://` gets `http://` when it is on
  your machine or your network, and `https://` elsewhere.
- **Its API key**, typed into a field that doesn't show it. An empty key changes nothing.

The key is checked with the provider before anything is saved: a wrong key is said at once and never
stored. Saved keys are kept by your system's own protection (the macOS Keychain, Windows data
protection, or your Linux desktop keyring) and never shown again. See [Security](security.md).

## Choosing a model

| Where | How |
|---|---|
| Terminal | `/model`, or `ctrl+x m` |
| Browser | The model chip beside the box, or `Alt+M` |
| A new session | `albert-mini --model provider:model` |
| From scripts | `albert-mini models use provider:model` |

The terminal's list has the models you used recently first, then each connected provider's, and
*Connect a provider…* at its foot. The one in use is ticked. Choosing one sets it for this session;
`ctrl+s` in the list also makes it the default for new sessions. The choice is shared: a model chosen
in the browser is the terminal's, and the other way round.

When no model is ready, both interfaces say so and open the list instead of sending your message;
what you typed waits in the box.

## Checking

```bash
albert-mini models              # the providers, each connected or what it needs, and the models ready
albert-mini models test         # one tool-calling request to the chosen model: can it do the work?
albert-mini models test openrouter:some/model
```

## Local models

Start your model server (Ollama, LM Studio, llama.cpp's server), then connect **Local server** and give
its address. Nothing leaves your machine. A local model must support tool calling to make changes; the
`models test` command shows whether it does.
