# Nimbus-Help
An AI FAQ chatbot that answers user questions using TF-IDF and cosine-similarity matching — built with vanilla JavaScript
# CodeAlpha_FAQChatbot

**Nimbus Help** — an FAQ chatbot built for the CodeAlpha AI Internship (Task 2).

A single-file web app. Open `index.html` in any browser — no install, no build, no backend.

## Features
- A knowledge base of 15 FAQs for a sample online store (shipping, returns, payments, warranty, accounts…).
- Matches a user's question to the most relevant FAQ using **TF-IDF + cosine similarity**.
- Shows the matched question and a **confidence score** under each answer.
- Falls back gracefully ("I'm not sure…") when no FAQ is similar enough.
- Chat UI with message bubbles, a typing indicator, and tappable suggested questions.

## How the matching works (the NLP)
All of this runs client-side in plain JavaScript:

1. **Preprocessing** — every question is lowercased, stripped of punctuation, tokenized,
   cleared of stop-words ("the", "is", "how"…), and lightly stemmed ("shipping" → "ship").
2. **TF-IDF vectors** — each FAQ becomes a vector. *Term Frequency* weights words that
   appear often in a FAQ; *Inverse Document Frequency* down-weights words common to all FAQs.
   The question text is weighted ×2 so it dominates matching.
3. **Cosine similarity** — the user's message is vectorized the same way, then compared to
   every FAQ vector by the cosine of the angle between them. The highest score wins.
4. **Threshold** — if the best score is below 0.12, the bot returns a fallback message
   instead of a wrong answer.

## Customize it
Edit the `FAQS` array near the top of the `<script>` block — add your own
`{q: "...", a: "..."}` pairs and the index rebuilds automatically.

## Run it
- Locally: double-click `index.html`.
- Deploy: drag the folder onto [Netlify Drop](https://app.netlify.com/drop) or push to GitHub Pages.

Built by **[your name]** · CodeAlpha Internship.
