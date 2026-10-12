# Models

mini-AlbertCode works with the model you connect: a hosted provider, any OpenAI-compatible service, or a
model server on your own machine.

## Connecting a provider

| Where | How |
|---|---|
| Terminal | `/connect`, or `ctrl+x k`; it also opens by itself on the first start |
| Browser | *Connect a provider…* in the Settings menu, the model list (`Alt+M`) or the provider menu under the box |

The list is grouped:

| Group | Providers |
|---|---|
| Popular | OpenAI, Anthropic, OpenRouter (recommended: one key for most of the market, open models included) |
| Other | Kimi, Hugging Face, any other OpenAI-compatible service (its address and key); in the browser also DeepSeek, Groq, Mistral, Together AI and xAI by name, their addresses filled in |
| On this machine | A local server: Ollama, LM Studio, llama.cpp |

One OpenAI-compatible service is connected at a time: connecting DeepSeek replaces Groq, and the other
way round.

Each provider is tagged as the service last found it: `connected`, `key not accepted` or
`not answering`. A provider is called connected only once it has accepted your key, or once its server
has answered with a model; a saved key alone is not enough.

Then, as the provider needs:

- **Its address**, for a local server or another service. The scheme is there already, so you type
  only the rest: `https://` for a service on the internet, `http://` for one on your machine or your
  network (in the browser it changes by itself as you type such an address, until you choose one).
  Ollama is `127.0.0.1:11434/v1`, LM Studio `127.0.0.1:1234/v1`. A whole address pasted, scheme and
  all, keeps its own scheme.
- **Its API key**, typed into a field that doesn't show it. An empty key changes nothing.

The key is checked with the provider as soon as it is typed, before anything is saved: a wrong key is
said at once and never stored. Then **the models it can use are listed, to choose one**; it is used at
once and becomes the provider's model. In the browser, *Advanced: a different model for each tier*
(folded) gives each of the provider's three tiers (Advanced, Balanced, Economy) a model of its own,
each one you can switch to from the model list; unless set, all three use the model chosen.

```text
Connect DeepSeek
  Address   [https://] api.deepseek.com
  API key   ••••••••••••••••          ✓ Accepted
  Model · 2 models this key can use
            (•) deepseek-flash   ( ) deepseek-v4-pro
  > Advanced: a different model for each tier
                                     [Test] [Save and use]
```

Saved keys are kept by your system's own protection (the macOS Keychain, Windows data protection, or
your Linux desktop keyring) and never shown again. See [Security](security.md).

## Choosing a model

Change the model at any time; the next message uses it.

| Where | How |
|---|---|
| Terminal | `/model`, or `ctrl+x m` |
| Browser | The provider and model menus under the box, or the model list (`Alt+M`) |
| A new session | `albert-mini --model provider:model` |
| From scripts | `albert-mini models use provider:model` |

The model list has the models you used recently first, then each connected provider's models as the
provider lists them, and *Connect a provider…* at its foot; in the browser the providers not connected
yet are folded under *Not connected*. The one in use is ticked. A model's ID that is not listed can be
typed: the list offers *Use* it with each connected provider (`compatible:my-model`). Choosing one sets
it for this session; `ctrl+s` in the terminal's list, or *Also the default for new sessions* in the
browser's, also makes it the default for new sessions. The choice is shared: a model chosen in the
browser is the terminal's, and the other way round.

Under the browser's box, the **provider menu** lists the connected providers (choosing one moves to the
model you last used with it, or its first) and the **model menu** lists that provider's models.

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
