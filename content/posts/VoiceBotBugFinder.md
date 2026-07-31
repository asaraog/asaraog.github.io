---
title: Voice Bot Bug Finder
date: 2026-07-01T18:30:00-05:00
draft: false
projects: artificialintelligence
featuredImage: /images/voicebot-bugfinder.svg
---
## Automated QA for healthcare voice agents with telephony and realtime AI

**Abstract**

Voice Bot Bug Finder is an end-to-end testing and evaluation workflow for healthcare phone agents. It places outbound calls through Twilio, streams live audio into Azure OpenAI Realtime, transcribes calls, and then analyzes outcomes to detect safety, handling, and policy failures.

The framework runs scenario-based test calls such as medication refill requests, language-access interactions, wrong-department routing, and weekend scheduling edge cases. After each call, transcripts and call artifacts are scored with structured bug categories so failures can be prioritized quickly.

This project is designed to make conversational QA repeatable, measurable, and deployment-ready for voice workflows where reliability matters.

## Architecture

Twilio places the outbound call and opens a Media Stream WebSocket. The bridge proxies audio bidirectionally into a single realtime session at roughly 300 ms round trip, so the agent can be interrupted mid-sentence the way a person can.

| Layer | Technology |
| --- | --- |
| Telephony | Twilio, outbound PSTN with dual-channel recording |
| Live audio bridge | FastAPI and WebSockets |
| Speech to speech | Azure OpenAI `gpt-realtime-mini` |
| Transcription | Azure AI Speech, en-US and hi-IN |
| Bug analysis | Azure OpenAI GPT-5-mini |

## Test scenarios

Ten scenarios, written to provoke failure rather than confirm success. The interesting bugs in a voice agent are not crashes. They are the moments where it sounds fluent and confident while leaving something out.

| ID | Scenario | What it probes |
| --- | --- | --- |
| 01 | New patient scheduling | Collects name, date of birth, reason for visit |
| 02 | Reschedule appointment | Reschedule plus policy clarification |
| 03 | Medication refill | Lisinopril and atorvastatin |
| 04 | Insurance inquiry | BCBS PPO, Medicare, UHC |
| 05 | Sunday booking | Agent should refuse a weekend slot |
| 06 | Multiple requests | Multi-intent handling in a single call |
| 07 | Urgent same-day | Chest tightness triage and escalation |
| 08 | Barge-in | Recovery from mid-sentence interruption |
| 09 | Wrong department | Caller believes they reached the pharmacy |
| 10 | Hindi only | Language access under Title VI |

## What it found

16 issues across the run, of which 4 were critical, 8 high and 4 medium. Every finding carries a severity, a category, the transcript file and timestamp, what the agent actually said, what it should have said, and the business impact.

The most instructive one was not a malfunction. The agent booked a new patient without collecting insurance details or stating whether the clinic was in network, and it sounded complete and helpful while doing so. That patient arrives to a surprise bill.

## Running it

To run locally, clone the project and start from the notebook workflow:

```bash
git clone https://github.com/asaraog/voicebotbugfinder.git
pip install fastapi uvicorn websockets twilio openai requests python-dotenv
cp .env.example .env
# Start tunnel first, then set SERVER_DOMAIN in .env using the public URL
npx localtunnel --port 8080   # Terminal 1
jupyter nbconvert --to notebook --execute --inplace voicebotbugfinder.ipynb
```

See the full implementation on [GitHub](https://github.com/asaraog/voicebotbugfinder).
