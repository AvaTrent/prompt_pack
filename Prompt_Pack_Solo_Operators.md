---
title: Prompt Pack for Solo Operators
author: Ava Trent
version: 1.0
date: June 2025
license: CC-BY-SA 4.0
---

# Prompt Pack for Solo Operators

_A tactical playbook for turning AI into personal leverage._

> The same systems that scale companies can scale **you**.

---

## Table of Contents

1. Tooling Stack  
2. Safety Guards  
3. Prompt Library  
4. Automation Blueprints  
5. Bonus Prompt Scaffolds  
6. Testing & Continuous Improvement  
7. Resources & License  

---

## 1. Tooling Stack

- **ChatGPT / Claude / Perplexity** → ad-hoc prompt runs  
- **Replit** → one-click scripts & scheduled jobs  
- **Zapier / Make** → no-code automations  
- **Google Sheets** → cheap data lake for logs & trend charts  

---

## 2. Safety Guards

Each prompt includes fallback logic such as:

> “If input is empty → return a default response.”

Use these guards to prevent silent failures, blank outputs, or misclassifications in edge-cases.

---

## 3. Prompt Library

### 1. Inbox Zero Classifier

```
You are Inbox Bot, a senior executive assistant. Label each email as one of:

["Action", "Read Later", "Delegate", "Delete"]

Return a JSON object like:
{"label": ..., "reason": ...}

If the email body is empty, return:
{"label":"Delete", "reason":"Blank body"}

Email Content → {{email_text}}
```

**Example Input:**

> Subject: Meeting tomorrow  
> Body: "Hi Ava, just confirming we're still good for 3pm."

**Example Output:**

```
{"label": "Action", "reason": "Meeting confirmation requires response or calendar check"}
```

---

### 2. Investment Screener

```
You are a CFA charter-holder. From the CSV of stock tickers and P/E ratios, select the five lowest P/E stocks.

Skip any rows with missing P/E. Output as a Markdown list, followed by:
- A 70-word explanation titled “Why these picks”

CSV → {{csv_block}}
```

---

### 3. Meeting Minutes Summarizer

```
You are a Chief of Staff. Summarize this transcript into:

- Decisions  
- Action Items  
- Owners  
- Deadlines  

Each section ≤ 50 words.

Transcript → {{transcript}}
```

---

### 4. Daily Cash-flow Snapshot

```
Role: Startup Controller.

From today's Stripe charges JSON:
1. Calculate revenue, refunds, and trend vs. 7-day average.
2. Output a JSON summary:
{"revenue": ..., "refunds": ..., "trend": "up|flat|down"}
3. Follow with a short summary ≤ 120 words.

Stripe Data → {{stripe_data}}
```

---

### 5. Growth Idea Prioritizer

```
You are a Product Analyst. Score each idea:

- Impact: 1–10  
- Confidence: 1–10  
- Effort: 1–10  

Calculate ICE = (Impact × Confidence) / Effort.  
Return a Markdown table sorted by ICE. Explain each score in ≤ 15 words.

Ideas → {{idea_list}}
```

---

### 6. Content Repurposer

```
From the following blog post, generate:

1. A Twitter thread (7 tweets)  
2. A LinkedIn post  
3. A 60-second video script (bullets only)

Cap each block at 300 tokens.

Blog Post → {{article}}
```

---

## 4. Automation Blueprints

### Gmail → GPT → Todoist

**Tools**: Zapier, OpenAI, Gmail, Todoist, Google Sheets

1. Trigger: New Gmail email  
2. Action: OpenAI → Inbox Zero Classifier  
3. Filter: label = "Action"  
4. Create task in Todoist  
5. Update Gmail label  
6. Append row in Google Sheet  

---

### Stripe → GPT Digest

**Tools**: Zapier, OpenAI, Google Sheets

1. Trigger: Stripe charge  
2. Append to Google Sheet  
3. Daily at 7am: Pull last 24h  
4. OpenAI → Daily Snapshot  
5. Retry on error x3  
6. Email digest → founders  
7. Update rolling trend log  

---

## 5. Bonus Prompt Scaffolds

### Summarize Anything

```
Summarize the text into:

- 3 action steps  
- 1 risk  
- 1 next best action  

Keep the full output ≤ 120 words.
```

---

### Problem → Solution Email

```
Write an email in three parts:

1. State the problem  
2. Present the solution  
3. End with a single clear CTA

Tone: friendly expert.
```

---

### Market Research Extractor

```
Turn feedback snippets into a Markdown table with:

| Feature | Frequency | Sentiment | Priority |
|---------|-----------|-----------|----------|

Output ≤ 10 rows.
```

---

## 6. Testing & Continuous Improvement

- **Regression Set**: 20–30 real inputs per prompt (refresh monthly)  
- **Scorecard**: Rate outputs for Accuracy, Structure, Helpfulness  
- **Acceptance Rule**: Keep changes only if avg. score ↑ ≥ 0.3  
- **Self-Critique Loop**: Prompt GPT to audit its own answers  
- **Nightly Optimizer**: Use MARS or beam search to test prompt variants  

---

## 7. Resources & License

- Subscribe: [avasinbox.substack.com](https://avasinbox.substack.com)  
- Contact: DM [@avatren_ai](https://twitter.com/avatren_ai)  
- License: [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)

---

© 2025 Ava Trent  
