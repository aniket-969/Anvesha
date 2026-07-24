# Anvesha

AI-powered Chrome extension that helps users understand any website's privacy policy in one click with concise summaries, risk scores, and key privacy insights.

## Demo

| Analysis | Detailed Report |
|----------|-----------------|
| ![Home](screenshots/home.png) | ![Report](screenshots/report.png) |

---

## Features

- 🔍 Automatically locates a website's privacy policy
- 🤖 AI-powered privacy analysis
- ⚠️ Privacy risk assessment
- 📊 Easy-to-read summaries
- 🔒 Highlights data collection, sharing, tracking, retention, and user rights
- ⚡ Caches repeated analyses for faster responses

---

## How It Works

1. User clicks **Analyze**.
2. The extension locates the website's privacy policy.
3. The policy is extracted and cleaned.
4. The content is sent to an AI pipeline.
5. The user receives a structured privacy report.

---

## Privacy Policy Extraction

Anvesha uses multiple strategies to reliably locate privacy policies across different websites.

### Strategy 1 — Current Page

If the user is already on the privacy policy page, the extension extracts the article immediately.

### Strategy 2 — Homepage Discovery

If no privacy policy is found on the current page, the extension:

- navigates to the website's homepage
- searches for links such as *Privacy*, *Privacy Policy*, *Legal*, etc.
- opens the discovered page
- extracts the article

### Strategy 3 — SPA Support

For Single Page Applications (React, Next.js, Vue, etc.), the extension waits for client-side rendering before extracting the content.

Article extraction is powered by **Mozilla Readability**, which removes navigation menus, headers, footers, advertisements, and other non-essential elements.

---

## AI Pipeline

The backend uses a two-stage AI pipeline powered by **DeepSeek V3 Flash**.

### 1. Information Extraction

The model extracts factual privacy information into a structured JSON format, including:

- Data collected
- Data sharing
- Tracking technologies
- Third-party services
- User rights
- Data retention
- International transfers

### 2. Risk Assessment

A second AI pass evaluates the extracted information and generates:

- Overall privacy risk
- Executive summary
- Key highlights
- User-friendly explanations

This two-stage approach improves consistency by separating factual extraction from evaluation.

---

## Tech Stack

### Frontend

- React
- Vite
- Mozilla Readability

### Backend

- Node.js
- Express.js
- better-sqlite3 (analysis cache)

### AI

- DeepSeek V3 Flash


---

---

## Future Improvements

- Faster processing of large privacy policies