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
