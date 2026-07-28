---
title: Cricket for Noobs
date: 2026-07-27T20:30:00-05:00
draft: false
projects: artificialintelligence
featuredImage: /images/cricket-noobs.svg
---
## A live AI cricket helper for American sports fans

**[cricketfornoobs.com](https://cricketfornoobs.com)** — live now

**Abstract**

Cricket for Noobs is a production web app that explains live cricket to Americans in baseball terms — built for the fan Major League Cricket and prediction markets are creating: someone staring at "311 & 126/7 (43 ov)" with real curiosity (and sometimes real money) and no translator. Users pick a live match and ask anything; a live mode narrates the game ball-by-ball in plain English, with spoken commentary, per-over score summaries, player career stats, and side-by-side win probabilities from the betting market and an in-house model.

**Systems design**

The entire product — backend, retrieval, and frontend — is a single Go binary built on the standard library alone: no frameworks, no database, no vector store, one Docker layer.

- **Answer tiers, deterministic first.** Exact questions (score, who's winning, who's batting, term definitions) never reach an LLM: they're computed from parsed match state or served from a curated glossary, instantly and token-free. The LLM writes only narrative, sandwiched between a deterministic header and footer, and is forbidden from inventing numbers — market prices, DLS pars, and stats are quoted only when present in context.
- **Retrieval inside the binary.** A ~9,500-document corpus (authored rules and betting mechanics, a jargon glossary, and per-format career aggregates for 9,417 players derived from ball-by-ball archives of 22,000+ professional matches) is embedded via `go:embed` and searched three ways: exact name matching with prominence tie-breaks, semantic search over compressed word embeddings shipped in the binary, and BM25 with a relevance floor — falling back gracefully so retrieval never has a hard external dependency.
- **Fan-side data plane.** Live scoreboard and ball-by-ball data are fetched by each user's browser directly from public feeds and handed to the server to parse — so data freshness scales with the audience rather than against it, and the backend stays stateless.
- **Live market integration.** Prediction-market prices stream in beside the model's estimate, and a market-pulse detector surfaces sharp price moves — traders react seconds after the action, well before scoreboard feeds update.
- **Zero-cost operations.** CI/CD to prod and staging environments on push, a self-ping keep-alive defeating free-tier sleep, key-protected log endpoints with a scheduled local collector for durable analytics, and per-chat geo/telemetry — total infrastructure cost: $0/month.

Within six hours of the domain going live, the site had organic visitors from four countries — including its first search-engine referral — and real users asking the exact questions it was designed for.

The code is private (the product may be commercialized), but I'm happy to walk through the architecture in depth — there's a write-up of the product philosophy at [cricketfornoobs.com/blog](https://cricketfornoobs.com/blog/building-cricket-for-noobs).
