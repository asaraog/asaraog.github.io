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

The entire product, spanning backend, retrieval, and frontend, is a single Go binary built on the standard library alone: no web framework, no vector store, no external services, one Docker layer. (One exception earned its place later: a pure-Go SQLite driver for the match-history archive below.) Go was a deliberate choice over Python for speed. It compiles to native code with no interpreter overhead, so deterministic answers like scores, definitions, and win math return in microseconds, and searching all ~9,500 corpus documents by brute-force cosine similarity takes under a millisecond, which is precisely why no vector database is needed. Goroutines make concurrency nearly free, so market prices for all of a match's outcomes are fetched and enriched in parallel. The compiled binary cold-starts instantly and serves everything from memory inside a 512MB free-tier container, where a Python equivalent with its dependency stack would struggle to fit, let alone respond as fast.

- **Answer tiers, deterministic first.** Exact questions (score, who's winning, who's batting, term definitions) never reach an LLM: they're computed from parsed match state or served from a curated glossary, instantly and token-free. The LLM writes only narrative, sandwiched between a deterministic header and footer, and is forbidden from inventing numbers. Narrative and speech are served by Groq, chosen for inference latency fast enough to keep pace with live play. Market prices, DLS pars, and stats are quoted only when present in context.
- **Retrieval inside the binary.** A ~9,500-document corpus (authored rules and betting mechanics, a jargon glossary, and per-format career aggregates for 9,417 players derived from ball-by-ball archives of 22,000+ professional matches) is embedded via `go:embed` and searched three ways: exact name matching with prominence tie-breaks, semantic search over compressed word embeddings shipped in the binary, and BM25 with a relevance floor, falling back gracefully so retrieval never has a hard external dependency.
- **Fan-side data plane.** Live scoreboard and ball-by-ball data are fetched by each user's browser directly from public feeds and handed to the server to parse, so data freshness scales with the audience rather than against it and the backend stays stateless.
- **Live market integration.** Prediction-market prices stream in beside the model's estimate, and a market-pulse detector surfaces sharp price moves. Traders react seconds after the action, well before scoreboard feeds update.
- **Batter-vs-bowler cards.** 67,678 career head-to-heads aggregated from ball-by-ball archives ride in the binary (2.6MB). When a new pairing appears in live mode, a card pops like a batter-vs-pitcher graphic: "Kohli vs Bumrah: 164 off 110, out 5x". Name resolution folds three naming conventions (full names in live feeds, bare surnames in commentary, initials in archives) onto one key, and fails silent rather than ever showing the wrong player's numbers.
- **Archived-match answers.** "Who bowled the 4th over of the final?" is answered from a 141MB SQLite archive of 8,825 matches, every delivery since 2004. The server resolves the match from team names, a year, or tournament language, pulls the exact scorecard and over, and the LLM only narrates it. The archive ships in the container image rather than the binary, and point lookups cost a few milliseconds and a few MB of memory, which is why SQLite beat an analytics engine for the job.
- **Neural narration.** Read-aloud streams a neural voice from an LLM-based text-to-speech model on Groq, with the browser's built-in voice as an automatic mid-sentence fallback. LLM-based TTS will improvise words when fed text truncated mid-thought, so speech is chunked into whole sentences only.
- **Durable telemetry on disks that vanish.** Free-tier disks reset on every deploy and idle spin-down, so chat and feedback logs are mirrored at write time to a private Git repository as human-readable daily pages plus raw JSONL, batched and retried with a bounded buffer, and new feedback triggers an email through a CI job.
- **CI/CD.** Automated tests and deployment to production and staging environments on every push, with the Chrome extension generated from the web UI and drift-checked in CI.

## Go vs Python, measured

The Go rewrite is about 4× faster than the Python original. The first version of this product was Python (FastAPI + uvicorn). Both versions still run, so the comparison is empirical, not theoretical: same laptop, same JSON endpoint, warmed, 50 sequential requests.

| | Python 3.11 (FastAPI + uvicorn) | Go 1.20 (standard library) |
|---|---|---|
| Request latency | 1.61 ms | **0.41 ms** |
| Boot to serving | 1.90 s | **1.14 s** |

The per-request gap is framework and interpreter overhead, paid on every call forever; it is also a throughput ceiling (roughly 600 vs 2,400 requests per second per process, before Go's native multi-core scaling). The boot number understates the difference: the Go figure includes building a BM25 index over ~9,500 documents, loading 20,000 word embeddings, and parsing 9,417 player careers at startup, none of which the Python version did.

## A win model calibrated on 2.6 million balls

The win probability shown beside the market price started as hand-tuned constants. Backtesting them on 2.65 million ball-by-ball states from 8,184 completed matches (T20 internationals, IPL, MLC, BBL, PSL, CPL, and ODIs) showed they were badly miscalibrated: first-innings estimates scored worse than always predicting a coin flip, and chase estimates ran about 20 points too optimistic. States the model called "90% to win" won 48% of the time.

The replacement is a set of interpretable logistic models per format and innings, over five match-state features plus a pre-match team Elo rating computed chronologically from 8,614 matches, so no game ever sees a rating that includes its own result. Held-out log-loss, by match split:

| Segment | Hand-tuned | Fitted |
|---|---|---|
| T20 first innings | 0.759 | **0.603** |
| T20 chase | 0.516 | **0.402** |
| ODI first innings | 1.074 | **0.546** |
| ODI chase | 0.967 | **0.365** |

Three results made the simple model the final one. A tuned gradient-boosted model on the same states could not beat the logistic. Adding lineup strength, toss, and momentum features moved accuracy by 0.4 points. And the estimated ceiling for any predictor across all ball-states is roughly 74-76%, because the first half of a cricket match genuinely is close to a coin flip; the fitted model reaches 75% overall and 92% when it takes a confident position. Claims of flat "90% accuracy" in sports prediction are a choice about when to measure, not a property of a model.

An adversarial review pass on the pipeline caught two real defects before shipping: model selection had leaked onto the held-out split, and tied matches were being silently dropped, biasing exactly the knife-edge endgames a win model exists for. Both were fixed and the fit re-run.

The live validation: during a real T20 chase, the deployed model tracked the betting market within one to two percentage points, independently, from match state and team ratings alone.
