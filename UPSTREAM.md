# Upstream provenance — read this before reusing this repo

| Component | Version | License | Source |
|---|---|---|---|
| @mlc-ai/web-llm (engine library, vendored at `vendor/webllm/index.js`) | 0.2.80 | Apache-2.0 (LICENSE vendored alongside) | https://github.com/mlc-ai/web-llm |
| Llama 3.2 1B Instruct, MLC build (`Llama-3.2-1B-Instruct-q4f16_1-MLC`) | — | Llama 3.2 Community License (Meta) | https://huggingface.co/mlc-ai/Llama-3.2-1B-Instruct-q4f16_1-MLC |

## Notes

- The engine library is **unmodified** upstream code, vendored so the page has no third-party script dependency.
- Model **weights are not in this repo** (too large for git). At first use, the engine downloads them from the public Hugging Face model library and caches them in the visitor's browser (Cache Storage). After that, inference is fully on-device and offline-capable; **no chat content is ever transmitted anywhere** — the download is weights-in, nothing out.
- "Built with Llama" attribution appears in the app footer, as the Llama Community License requires.
- Aoma's own code is `index.html` (interface + assistant prompt). It contains no WebLLM or Meta code.

Downloaded from the npm registry on 2026-10-25: `@mlc-ai/web-llm/-/web-llm-0.2.80.tgz`.

## The house rule this repo follows

Credit loudly, own the layer. Every Aoma tool built on open source carries a file like this one: exact upstream versions, exact licenses, and a bright line between the upstream engine and the original Aoma work on top of it.
