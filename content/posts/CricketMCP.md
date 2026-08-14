---
title: Cricket MCP Server
date: 2026-08-14T12:30:00-05:00
draft: false
projects: artificialintelligence
featuredImage: /images/cricket-mcp.svg
---
## A fitted cricket model, exposed to any AI assistant over the Model Context Protocol

**[github.com/asaraog/mcp-cricket](https://github.com/asaraog/mcp-cricket)**, open source, BSD 3-Clause

**Abstract**

Cricket MCP Server gives AI assistants real cricket knowledge instead of recalled training data. It is a [Model Context Protocol](https://modelcontextprotocol.io) server that publishes eleven read-only tools: a calibrated win-probability model, a ball-by-ball archive of 22,479 matches and 11.4M deliveries, career and batter-vs-bowler records, phase and venue splits, live scores, and live prediction-market prices. It runs in Claude Desktop, Claude Code, Cursor or any other MCP client, as a single static binary with no API key and no account. The analytics behind it are the same ones running in production at [cricketfornoobs.com](https://cricketfornoobs.com).

**Why a server rather than a prompt**

No language model can compute a win probability. Asked who is favoured at 149 for 7 chasing 178, it will produce a confident number that is not derived from anything. The model in this server is a logistic regression fitted offline on 17,907 matches and 5.6M ball states, segmented by format and innings, with pre-match Elo ratings. Held-out log loss is 0.42 on T20 chases and 0.40 on ODI chases. The division of labour is the point: the assistant decides which tool to call and with what arguments, and the arithmetic stays in Go, where it is tested and versioned.

The tool descriptions are the interface to the model, not developer documentation. `balls_per_over` carries the note that The Hundred bowls five-ball sets, because a client that silently passes six reports every required rate a fifth too low. A vague description is a defect that surfaces as wrong arguments.

**Systems design**

- **One static binary, standard library only.** No web framework, no vector store, no runtime, no interpreter. It speaks JSON-RPC over stdio, so the client forks it as a child process and there is no port, no network listener and no attack surface.
- **Par is per ground.** A first-innings score means nothing except relative to what the ground usually yields, and two of the seven innings-one features are measured against par. Par is a table of 371 grounds and 7 leagues rather than one global constant, falling back ground → league → global so an unrecognised spelling degrades softly. Real pars run from 153.7 to 172.5 by league alone. Passing a venue moves the same 80 for 2 at ten overs from 47% at Chinnaswamy to 60% at Newlands, and is worth 0.006 of held-out log loss.
- **Fitted, then measured, then shipped.** Every coefficient change is reported as held-out loss on a chronological split by match, so a match's own future cannot leak into its training. Calibration is checked per slice afterwards, because a better aggregate loss can hide a skew in the slice that matters.
- **Ambiguity is refused, not guessed.** Name resolution folds three conventions onto one key: full names in live feeds, bare surnames in commentary, initials in archives. Where a lookup is genuinely ambiguous it returns nothing rather than the wrong player, and archive tools report a missing database rather than inventing an answer.
- **Markets beside the model.** `cricket_market_odds` reads public prices from Kalshi, a CFTC-regulated exchange where a price in cents is the implied probability. Placed next to the model's number, the gap is the edge a trader would be claiming. The tool's own output says the market can see injuries, weather and team news that a state-based model cannot, so the number arrives with its caveat attached rather than in a separate paragraph nobody reads.
- **Archive on demand.** On first use the server downloads a prebuilt SQLite archive once into the OS cache directory and reuses it. Live-score tools work with no archive at all.

**What it is not**

It cannot see injuries, weather, pitch reports or team news, which is often exactly why it disagrees with the market. Market data is read-only: no account, no orders, no advice.
