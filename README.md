# Keln provider for Agent Zero

Use [Keln](https://keln.ai) models in [Agent Zero](https://github.com/agent0ai/agent-zero) as a chat
model provider.

Keln is an inference platform for open models with an OpenAI-compatible API. Keln maintains this
plugin. It is not affiliated with Agent Zero.

## Why a plugin?

Agent Zero can reach Keln through its "Other OpenAI compatible" option. This plugin adds **Keln** to
the provider dropdown, sets the base URL, and maps your key to `KELN_API_KEY`.

## Install

Install **Keln Provider** from the Plugin Hub in Agent Zero.

## Configure

1. Sign up at [app.keln.ai](https://app.keln.ai/signup). Open **Keys** → **Create key** and copy the
   key.
2. In Agent Zero, open **Settings** → **Models** → **Edit Presets**.
3. Under **Main Model**, set **Provider** to **Keln**, choose a model such as `zai-org/glm-5.3`, and
   paste your key into **API key**. Turn on **Supports Vision** only for a model that accepts
   images.
4. To run Agent Zero's background tasks on Keln as well, set **Utility Model** the same way, for
   example `zai-org/glm-5.3-flash`. The key carries over.
5. Click **Save**.

## Models

Agent Zero reads the list from `https://api.keln.ai/v1/models`. These models support tool calling,
which agent work needs:

| Model | Input |
|---|---|
| `zai-org/glm-5.3` | text |
| `zai-org/glm-5.3-flash` | text, images |
| `moonshotai/kimi-k3` | text, images |
| `qwen/qwen3.8-2.4t-a95b` | text |
| `deepseek-ai/deepseek-v4.1-flash` | text, images |

The list also includes `cloudflare/clef` and `typesafe/jev-1.14`. These are decision models. They
answer typed questions through `/v1/decisions` and do not write text, so they do not work as the
agent's chat model.

Prices are on [Models & pricing](https://docs.keln.ai/models-pricing/).

## Security and footprint

- **Network:** Agent Zero sends your requests, including prompts and any files or images in them, to
  `https://api.keln.ai` using your Keln key. See
  [Privacy & zero data retention](https://docs.keln.ai/capabilities/privacy/).
- **Code:** the plugin holds only configuration: 1 provider entry. It runs no code, adds no tools, and
  has no dependencies.
- **Credentials:** Agent Zero holds the key. The plugin stores no secrets.
- **Telemetry:** the plugin sends no telemetry.

## Remove

Remove the plugin from Agent Zero's plugin settings. Your other providers stay as they are.

## License

MIT
