# ⚖️ Kill · Fix · Ship — a Jev decision jury

A one-call startup-idea jury built on the Pollinations **Jev** decision endpoint (`POST /alpha/decisions`, model `typesafe/jev-1.13`), submitted for **quest #15722**.

**Try it:** https://svirepyibambr.github.io/jev-jury/  → https://svirepyibambr.github.io/pollinations-jev-jury/

## How it works
- You paste an idea → the app sends **one** `POST /alpha/decisions` request with 6 typed questions:
  - `verdict` — a **choice** (KILL / FIX / SHIP) with confidence
  - `novelty`, `demand`, `feasibility`, `monetization` — **score**s on an ordered scale with legends
  - `build_now` — a **noul** yes/no probability
- **Your code — not an LLM — assembles the page** from the typed answers: verdict banner, score bars, urgency gauge, per-question probability spreads, token usage and latency. No free-text parsing anywhere.
- Bring your own Pollen: the player's key stays in localStorage; no secrets embedded.

## Live check (real API run, 2026-09-29)
Request: mystery canned-fish subscription. Response: `model: typesafe/jev-1.13`, `verdict: FIX` (confidence 0.48), `demand: 1.34` (legend none/low/medium/high), `build_now: 0.14`, usage 410+72 tok. The endpoint validated our first request against the published OpenAPI schema (`score` requires `criteria` rungs) — fixed and re-verified.

## API
- `POST https://gen.pollinations.ai/alpha/decisions` — the only AI call, paid with the user's own Pollen.
