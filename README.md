# 💼 AutoRecruit AI — Autonomous HR Resume Screening & Candidate Processing Engine

> **An automated end-to-end recruitment pipeline built with n8n, Local LLMs (Ollama), Google Sheets, and Gmail.**

---

## 📌 Overview

**AutoRecruit AI** is an intelligent HR automation workflow designed to streamline the hiring process. It automatically captures job applications, extracts text from CVs/Resumes (PDF format), evaluates candidate qualifications using a local **Ollama LLM Agent**, logs candidate statuses into **Google Sheets**, and dispatches tailored notification emails via **Gmail**.

---

## ✨ Key Features

* **📥 Form Submission Trigger:** Automatically captures incoming applicant data and resume attachments.
* **📄 PDF Text Extraction:** Parses uploaded CV documents to extract candidate skills, experience, and background.
* **🧠 AI Candidate Screening (Ollama):** Evaluates applicant profiles against predefined hiring criteria using local LLMs.
* **⚡ Logic & Decision Routing:**
  * Custom **JavaScript Processing Node** to format AI evaluation scores.
  * Conditional branching (**If Node**) to dynamically route Accepted vs. Rejected applications.
* **📊 Automated Tracking:** Updates designated **Google Sheets** (Accepted/Rejected tabs) in real-time.
* **✉️ Automated Email Dispatch:** Sends personalized response emails to candidates based on their status via **Gmail API**.

---

## 🛠️ Tech Stack

* **Workflow Orchestration:** [n8n](https://n8n.io/)
* **AI Model Engine:** [Ollama](https://ollama.com/) (Local Chat Models)
* **Document Parsing:** n8n Extract from File (PDF)
* **Data Storage:** Google Sheets API
* **Communication:** Gmail API

---

## 🏗️ Architecture Workflow

```text
[ Form Submission ] ──► [ Extract PDF ] ──► [ AI Agent (Ollama) ] ──► [ JS Formatter ]
        │                                                                   │
        ├──► [ Sheet (Accepted Raw) ]                                       ▼
                                                                     [ If Node ]
                                                                   /             \
                                                           (True) /               \ (False)
                                                                 ▼                 ▼
                                                         [ Send Email ]    [ Send Email ]
                                                                 │                 │
                                                                 ▼                 ▼
                                                         [ Sheet Accept ]  [ Sheet Reject ]
