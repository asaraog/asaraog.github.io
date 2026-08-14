---
title: Cricket for Noobs
date: 2026-07-27T20:30:00-05:00
draft: false
projects: dataengineering
featuredImage: /images/cricket-noobs.svg
---
## A live AI cricket helper for American sports fans

**[cricketfornoobs.com](https://cricketfornoobs.com)**, live now

Cricket for Noobs is a production web app that explains live cricket to Americans in baseball terms. It is built for the fan that Major League Cricket and prediction markets are creating: someone staring at "311 & 126/7 (43 ov)" with real curiosity, sometimes real money, and no translator. Users pick a live match and ask anything; a live mode narrates the game ball-by-ball in plain English, with spoken commentary, per-over score summaries, player career stats, and side-by-side win probabilities from the betting market and an in-house model.

- **Live market integration.** Prediction-market prices stream in beside the model's estimate, and a market-pulse detector surfaces sharp price moves. Traders react seconds after the action, well before scoreboard feeds update.
- **Two model providers, one voice.** Gemini writes the narrative, with automatic failover to Groq's Llama on an error or a refusal. Groq also hosts the neural voice behind read-aloud.
- **CI/CD.** Automated tests and deployment to production and staging environments on every push.
- **Also an MCP server.** The same model and archive are published separately as [mcp-cricket](https://github.com/asaraog/mcp-cricket), an open-source [Model Context Protocol](https://modelcontextprotocol.io) server, so any AI assistant can query them directly. It ships eleven read-only tools as a single static binary, with no API key.

## Go vs Python, measured

The entire product, spanning backend, retrieval, and frontend, is a single Go binary built on the standard library alone: no framework, no vector store, one Docker layer. Retrieval is RAG: a ~9,500-document corpus rides inside the binary, searched by compressed word embeddings and BM25, and the top three hits are injected into the prompt before the LLM generates. Brute-force cosine similarity over all of it takes under a millisecond, which is precisely why no vector database is needed.

The Go rewrite is about 4× faster than the Python original. The first version of this product was Python (FastAPI + uvicorn), and both versions run on the same setup.

| | Python 3.11 (FastAPI + uvicorn) | Go 1.20 (standard library) |
|---|---|---|
| Request latency | 1.61 ms | **0.41 ms** |
| Boot to serving | 1.90 s | **1.14 s** |

The per-request gap is framework and interpreter overhead, paid on every call forever. The boot number understates the difference: the Go figure includes building a BM25 index over ~9,500 documents, loading 20,000 word embeddings, and parsing 9,417 player careers at startup, none of which the Python version did.
