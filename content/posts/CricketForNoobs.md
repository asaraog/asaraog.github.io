---
title: Cricket for Noobs
date: 2026-07-27T20:30:00-05:00
draft: false
projects: dataengineering
featuredImage: /images/cricket-noobs.svg
---
## A live AI cricket helper for American sports fans

**[cricketfornoobs.com](https://cricketfornoobs.com)**, live now

**Abstract**

Cricket for Noobs is a production web app that explains live cricket to Americans in baseball terms. It is built for the fan that Major League Cricket and prediction markets are creating: someone staring at "311 & 126/7 (43 ov)" with real curiosity, sometimes real money, and no translator. Users pick a live match and ask anything; a live mode narrates the game ball-by-ball in plain English, with spoken commentary, per-over score summaries, player career stats, and side-by-side win probabilities from the betting market and an in-house model.

**Systems design**

The entire product, spanning backend, retrieval, and frontend, is a single Go binary built on the standard library alone: no frameworks, no database, no vector store, one Docker layer. Go was a deliberate choice over Python for speed. It compiles to native code with no interpreter overhead, so deterministic answers like scores, definitions, and win math return in microseconds, and searching all ~9,500 corpus documents by brute-force cosine similarity takes under a millisecond, which is precisely why no vector database is needed. Goroutines make concurrency nearly free, so market prices for all of a match's outcomes are fetched and enriched in parallel. The compiled binary cold-starts instantly and serves everything from memory inside a 512MB free-tier container, where a Python equivalent with its dependency stack would struggle to fit, let alone respond as fast.

- **Answer tiers, deterministic first.** Exact questions (score, who's winning, who's batting, term definitions) never reach an LLM: they're computed from parsed match state or served from a curated glossary, instantly and token-free. The LLM writes only narrative, sandwiched between a deterministic header and footer, and is forbidden from inventing numbers. Market prices, DLS pars, and stats are quoted only when present in context.
- **Retrieval inside the binary.** A ~9,500-document corpus (authored rules and betting mechanics, a jargon glossary, and per-format career aggregates for 9,417 players derived from ball-by-ball archives of 22,000+ professional matches) is embedded via `go:embed` and searched three ways: exact name matching with prominence tie-breaks, semantic search over compressed word embeddings shipped in the binary, and BM25 with a relevance floor, falling back gracefully so retrieval never has a hard external dependency.
- **Fan-side data plane.** Live scoreboard and ball-by-ball data are fetched by each user's browser directly from public feeds and handed to the server to parse, so data freshness scales with the audience rather than against it and the backend stays stateless.
- **Live market integration.** Prediction-market prices stream in beside the model's estimate, and a market-pulse detector surfaces sharp price moves. Traders react seconds after the action, well before scoreboard feeds update.
- **CI/CD.** Automated tests and deployment to production and staging environments on every push.
