# 🤖 MyTaskMate-n8n-RuleBased

> A Rule-Based AI Chat Task Assistant built with n8n automation, Groq LLM, and Google Sheets.

![Type](https://img.shields.io/badge/AI_Type-Rule--Based-red) ![n8n](https://img.shields.io/badge/n8n-Automation-orange) ![Groq](https://img.shields.io/badge/Groq-LLaMA_3.3_70B-blue) ![Google Sheets](https://img.shields.io/badge/Google-Sheets-green) ![Chat](https://img.shields.io/badge/Interface-Chat_UI-purple)

---

## 🎯 What is MyTaskMate?

MyTaskMate is a **Rule-Based AI Chat Task Assistant** that lets you manage your daily tasks using natural language text input. It uses **Groq LLaMA 3.3** only for intent detection and routes that intent through fixed automation rules built in n8n.

> **Note:** This is a **Rule-Based AI system**, not an Agentic AI. The LLM only classifies intent — all actions follow predefined rules. This project was built to understand the basics of n8n, Groq API, and Google Sheets automation before moving to a full AI Voice Agent.

---

## 🧠 How It Works

```
User Input → LLM detects intent → Fixed rule executes → Response returned
```

The LLM classifies input into one of 5 intents:
`add_task` | `list_tasks` | `complete_task` | `delete_task` | `casual_chat`

---

## ✨ Features

- 💬 Chat Input — Type commands naturally
- 📋 Task Management — Add, list, complete and delete tasks
- 🧠 AI Intent Detection — Groq LLaMA 3.3
- 📊 Google Sheets — All tasks stored as a database
- ⚡ n8n Automation — Handles all backend logic
- 🌐 Browser Based — Just open the HTML file, no installation needed

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| n8n Cloud | Workflow automation and webhook handling |
| Groq API (LLaMA 3.3 70B) | Intent detection and casual chat |
| Google Sheets | Task database (CRUD operations) |
| HTML / CSS / JS | Frontend chat UI |

---

## 🏗️ Architecture

```
User Text Input
        ↓
HTML Frontend
        ↓
n8n Webhook (POST)
        ↓
Groq API → Intent Detection
        ↓
IF Node Chain → Route by Intent
        ↓
┌──────────────────────────────────────────┐
│ add_task     → Google Sheets Append Row  │
│ list_tasks   → Google Sheets Get Rows    │
│ complete_task→ Google Sheets Update Row  │
│ delete_task  → Google Sheets Update Row  │
│ casual_chat  → Groq API Chat Response    │
└──────────────────────────────────────────┘
        ↓
Respond to Webhook → Display in chat
```

---

## ⚙️ Requirements

- ✅ Any modern browser
- ✅ Internet connection
- ✅ n8n Cloud account — [n8n.io](https://n8n.io)
- ✅ Groq API Key — [console.groq.com](https://console.groq.com)
- ✅ Google account

---

## 🚀 Setup Guide

### Step 1 — Google Sheets Setup
1. Open Google Sheets and create or use any existing sheet
2. Add these 5 column headers in Row 1 (required):

| ID | Task | Status | Created At | Completed At |
|---|---|---|---|---|

---

### Step 2 — n8n Workflow Setup

**Import workflow (Recommended):**
1. Login to n8n Cloud → Click **"New Workflow"**
2. Click **"..." menu** → **"Import from file"**
3. Upload `workflow.json` from this repo
4. Connect your Groq and Google Sheets credentials
5. Click **"Publish"** to activate

**Build manually:**

| Node | Type |
|---|---|
| Webhook | Trigger — POST, Response Mode: Response Node |
| HTTP Request | Groq API call for intent detection |
| Code | Parse JSON response |
| IF (x4) | Route by intent |
| Google Sheets (x4) | Append / Get / Update operations |
| Merge | Combine all responses |
| Respond to Webhook | Send reply back |

---

### Step 3 — Groq API Credential in n8n
- Auth Type: `Header Auth`
- Name: `Authorization`
- Value: `Bearer YOUR_GROQ_API_KEY`

---

### Step 4 — Run the Frontend
1. Download `mytaskmate.html` and open it in any browser
2. Paste your **n8n Production Webhook URL** in the config bar and click **Save**
3. Start chatting!

---

## 💬 Example Commands

| Intent | Example |
|---|---|
| Add task | *"add task finish the project"* |
| Show tasks | *"show my tasks"* |
| Complete task | *"complete task finish the project"* |
| Delete task | *"delete task buy groceries"* |
| Casual chat | *"hello how are you"* |

---

## 📁 Project Structure

```
MyTaskMate-n8n-RuleBased/
├── mytaskmate.html    ← Frontend chat UI
├── workflow.json      ← n8n workflow export
└── README.md          ← This file
```

---

## 🔄 Rule-Based vs Agentic AI

| Feature | This Project | Agentic AI (Next Project) |
|---|---|---|
| LLM Usage | Intent detection only | Full autonomous reasoning |
| Responses | Fixed templates | AI generated |
| Decision Making | Fixed rules | Autonomous |

> This project was a stepping stone — built to learn n8n automation basics. The next project will be a full **AI Voice Agent** with autonomous reasoning. 🚀

---

## 🙏 Credits

- [n8n](https://n8n.io) — Workflow automation
- [Groq](https://groq.com) — LLM inference
- [Google Sheets](https://sheets.google.com) — Database

---

## 📄 License

MIT License — free to use and modify!

---

⭐ **If this helped you, please give it a star!**
