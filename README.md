# Aoma Private AI

A free AI chat that runs **100% on the visitor's own device** — part of the **Aoma AI Agency Free Tools Desk**.

**What it does:** after a one-time model download (~800 MB, cached in the browser), a compact AI model (Llama 3.2, 1B) answers questions using the device's own graphics chip (WebGPU). No account, no server inference, no chat logs — there is no backend at all. Closing the tab erases the conversation.

**Why it exists:** it's Aoma's live proof of the privacy pitch — "AI that never leaves your laptop" — and a genuinely useful drafting assistant for small-business tasks (review replies, follow-ups, post ideas).

## Aoma's layer (our original work)

- The assistant's coaching prompt: a small-business marketing/ops persona with honesty rules (no invented prices or facts) — see `SYSTEM` in `index.html`.
- The interface, starter-question chips, privacy explanation, and branding.
- The integration choice: library self-hosted from this repo; model weights stream once from the public model library and cache on-device (see UPSTREAM.md for why weights aren't in the repo).

## Honest limits (also stated on the page)

- A 1B model is a drafting assistant, not a research engine. The page says so.
- Requires WebGPU: recent Chrome/Edge (desktop/Android) or Safari on iOS 26+. Unsupported browsers get an explanation, not a broken page.
- First load is heavy (~800 MB). Returning visits are instant from cache.

## Run locally

```bash
cd aoma-private-ai
python3 -m http.server 8000
# open http://localhost:8000 in a WebGPU-capable browser
```

## Verification (2026-10-25)

Headless Chromium (SwiftShader WebGPU) at iPhone size (390×844): engine load + streamed answer to a live question verified end-to-end; see git history / program notes for the run log. Real-device check on an iPhone (Safari 26 WebGPU) is the one pass that can't be done from the build machine — flagged, not hidden.

## Deploy

Static hosting (Vercel project connected to this repo). Planned live home: Aoma Free Tools Desk (aomaai.com) — final URL recorded here once live.
