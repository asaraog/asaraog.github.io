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

Major League Cricket and prediction markets are creating a new fan: an American staring at "311 & 126/7 (43 ov)" with real curiosity — and sometimes real money — and no translator. Cricket for Noobs explains live matches in baseball terms: pick a match, ask anything, and get grounded answers, ball-by-ball narration with spoken commentary, player career stats, and side-by-side win probabilities from the betting market and an in-house model.

**Under the hood**

The entire product — backend, retrieval, and frontend — is a single Go binary built on the standard library alone: no frameworks, no database, no vector store. Go over Python was a deliberate speed choice: compiled answers return in microseconds, searching the ~9,500-document knowledge base takes under a millisecond in memory, and the whole thing cold-starts instantly in a 512MB free-tier container. The AI is kept on a short leash — anything exact (scores, stats, win math) is computed deterministically, and the model only narrates around verified facts. Total infrastructure cost: $0/month.

The interesting parts — how live data stays fresh as the audience grows, how the market signal works, and what powers retrieval — are deliberately not written up here. The code is private and the product may be commercialized, but I'm happy to walk through the full architecture in conversation.

Within six hours of launch it had organic visitors from four countries and its first search-engine referral.
