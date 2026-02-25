# deVereAdmin — Pension Transfer Management Platform

> A purpose-built dashboard for managing IVCM, SIPP, Garrison Bridge, and Superannuation transfers — from first contact to completion.

**[View Live Demo →](https://YOUR_USERNAME.github.io/devere-admin-demo)**

---

## Overview

deVereAdmin is an internal administration platform built for the deVere Australia team to manage the full lifecycle of pension transfers. It replaces manual spreadsheet tracking with a real-time, cloud-synced dashboard featuring AI-powered email analysis, automated follow-up drafting, and deep Outlook integration.

## Features

### Transfer Management
- Track IVCM, SIPP, Garrison Bridge, and Superannuation transfers in one place
- Real-time status tracking: Follow-up, Awaiting Client, In Progress, Complete
- Per-transfer document checklists tailored to each transfer type
- Follow-up date alerts with overdue detection
- Timeline/audit log for every transfer
- Document status tracking (SOA Drafted → Sent → Signed → Complete)

### Email Activity
- Outlook integration via Microsoft Graph API
- Auto-matches incoming emails to transfers using client name, scheme, and keyword detection
- AI-powered email analysis — reads content and suggests tracker updates and status changes
- Draft replies directly from the dashboard, saved to Outlook Drafts

### AI Senior Administrator
- OpenAI-powered chat assistant with full access to the transfer database
- Identifies stalled transfers, overdue follow-ups, and missing documents
- Drafts contextual chase emails for clients, schemes, and fund administrators
- Proactive AI Drafts tab — autonomously reviews all transfers and generates a ready-to-send email queue
- Falls back to local processing when no API key is configured

### Tools
- **PDF Filler** — deep-links to a companion Vercel app with client data pre-filled
- **Email Templates** — pre-written templates for common scenarios (chase IVCM, client wet sig, Money Helper, etc.)
- **Doc Checklist** — reference checklists for each transfer type
- **ROA Guide** — quick reference for preparing Records of Advice
- **Import** — bulk import transfers from Excel, CSV, or Word documents
- **Weekly Email Digest** — automated Firebase Cloud Function sends a Monday morning summary

### Infrastructure
- Firebase Firestore for real-time data sync across sessions
- Firebase Authentication (Google + Microsoft)
- Offline persistence — continues working without internet
- Per-user data isolation

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla JS, HTML, CSS |
| Database | Firebase Firestore |
| Auth | Firebase Auth (Google, Microsoft OAuth) |
| Email | Microsoft Graph API |
| AI | OpenAI GPT-4o-mini |
| PDF Tool | React app hosted on Vercel |
| Notifications | Firebase Cloud Functions + Nodemailer |

---

## Project Structure

```
/
├── index.html              # Main app
├── css/
│   └── styles.css          # All styles
├── js/
│   ├── firebase-config.js  # Firebase + auth provider setup
│   ├── auth.js             # Login, logout, session management
│   ├── app.js              # Core dashboard logic
│   ├── microsoft-graph.js  # Outlook email fetching + matching
│   ├── email-activity.js   # Email panel UI + AI features
│   └── ai-email-service.js # AI analysis, reply drafting, proactive drafts
└── functions/
    ├── index.js            # Cloud Function — weekly email digest
    └── package.json
```

---

## Demo

This repository hosts an interactive animated product demo showcasing the key features of the platform.

**Controls:**
- Auto-plays through all scenes
- `→` / `←` arrow keys or on-screen buttons to navigate
- `Space` to advance, `P` to pause

---

## Local Development

Clone the repo and open `index.html` directly in a browser — no build step required.

For the full app with Firebase:
1. Create a Firebase project at [console.firebase.google.com](https://console.firebase.google.com)
2. Enable Firestore, Authentication (Google + Microsoft providers)
3. Replace the config in `js/firebase-config.js`
4. For Microsoft/Outlook: register an app in [Azure Portal](https://portal.azure.com) with `Mail.Read`, `Mail.ReadWrite` scopes

For Cloud Functions (weekly digest):
```bash
cd functions
npm install
firebase deploy --only functions
```

---

## Built By

Jordan · deVere Australia

*Internal tool — not for public distribution.*
