# Nexus AI

A single-file, browser-based AI chat and image generation app powered by [Groq](https://groq.com)'s free-tier API. No backend, no build step, no cost — just an HTML file and a free API key.

## Features

- **Chat mode** — conversational assistant with markdown rendering (code blocks, headers, bold, lists)
- **Image mode** — describe an image in plain language; the app refines your prompt into a detailed generation prompt, then renders it
- **Session history** — multiple conversations saved locally, with titles, timestamps, and message counts
- **Zero backend** — runs entirely client-side; your API key and chat history never leave your browser

## Setup

1. Open `nexus-ai.html` in any modern browser
2. Visit [console.groq.com](https://console.groq.com) and create a free account (no credit card required)
3. Go to **API Keys** → **Create API Key**, then copy it
4. Paste the key into the setup modal on first launch

Your key is stored only in `localStorage` on your device.

## Models

| Purpose | Model | Notes |
|---|---|---|
| Chat responses | `qwen/qwen3-32b` | Static model, knowledge cutoff ~March 2025. No real-time web access. |
| Image prompt refinement | `openai/gpt-oss-120b` | Turns a short description into a detailed, optimized image-generation prompt |
| Image rendering | [Pollinations.ai](https://pollinations.ai) | Free, no-key image generation from the refined prompt |

Both text models are served on Groq's free tier — no cost, but subject to Groq's published rate limits (requests/tokens per minute).

## Known limitations

- **No real-time information.** The chat model cannot answer questions about current events, scores, or anything after its training cutoff. This is a deliberate trade-off in favor of answer quality and reliability over Groq's web-search-enabled `compound` models, which were found to occasionally state incorrect facts with confidence.
- **Free-tier rate limits apply.** Heavy or rapid use may return a 429 (rate limit) error; wait a moment and retry.
- **Large conversations can hit request-size limits (413).** Groq caps how large a single request body can be. Very long sessions may eventually need to be trimmed or restarted.

## Project structure

Everything — HTML, CSS, and JavaScript — lives in a single file (`nexus-ai.html`) for easy portability. There is no build process; just open it in a browser.

## License

For personal
