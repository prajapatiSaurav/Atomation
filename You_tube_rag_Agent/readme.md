# 📺 YouTube RAG Agent – Intelligent YouTube Comment Analyzer

This project is a **Retrieval-Augmented Generation (RAG)** workflow built in **n8n** to help content creators deeply understand their audience and craft better YouTube content using real comment insights. It automates video and comment fetching, stores data in a vector database, and enables natural language queries using AI.

---

## 🚀 What It Does

- Fetches **top YouTube videos** for given channels (from Airtable)
- Extracts and stores **comments** with metadata
- Embeds comments using **Google Gemini**
- Stores them in **Supabase Vector Store**
- Enables an **AI Agent** (via webhook) to:
  - Analyze viewer interests & trends
  - Suggest new video ideas
  - Provide content structure and hooks
  - Reference real viewer feedback

---

## 🧠 How It Helps

| 🎯 Use Case                  | 📈 Benefit                                                      |
|-----------------------------|------------------------------------------------------------------|
| Trend Detection             | Spot emerging viewer topics and engagement triggers              |
| Content Ideation            | Auto-generate content based on real audience demand              |
| Sentiment Analysis          | Understand positive/negative feedback trends                     |
| Gap Identification          | Find overlooked questions or unmet content needs                 |
| SEO/Hook Optimization       | Use viewer language to write better titles and hooks             |

---

## 🧩 Architecture Overview

```mermaid
graph TD
  A[Airtable (Channel List)] --> B[Get Channel ID via YouTube API]
  B --> C[Fetch Recent Videos]
  C --> D[Fetch Comments]
  D --> E[Clean + Structure]
  E --> F[Embed (Google Gemini)]
  F --> G[Store in Supabase Vector DB]
  H[Webhook (chat trigger)] --> I[AI Agent (Langchain + Groq)]
  G --> I
```

---

## 🛠️ Tools & Technologies

| Tool                 | Purpose                                                |
|----------------------|--------------------------------------------------------|
| **n8n**              | Workflow orchestration                                 |
| **YouTube API**      | Fetch videos and comments                              |
| **Airtable**         | Channel queue and status management                    |
| **Google Gemini**    | Generate vector embeddings for comments                |
| **Supabase**         | Vector store database for semantic search              |
| **Groq LLM**         | Responds with insights, ideas, and structured content  |
| **Langchain (n8n)**  | AI orchestration and memory                            |

---

## ⚙️ Workflow Overview

### 1. 📥 Input from Airtable
- Fetches channels where `Status != done`

### 2. 🔍 Channel ID Resolution
- Extracts username from `@handle` and uses YouTube API to get channel ID

### 3. 🎥 Video & Comment Collection
- Fetches top 50 recent videos from last 30 days
- Extracts top-level comments using YouTube API

### 4. 🧼 Data Processing
- Cleans comment data
- Adds metadata (videoId, channelId, video URL, etc.)

### 5. 🧠 Embedding & Storage
- Text split into chunks
- Embedded using **Google Gemini**
- Stored in **Supabase** with metadata for querying

### 6. 🤖 AI Agent (Webhook)
- Langchain AI Agent connects to:
  - Groq LLM
  - Supabase Vector Store (via Langchain Tool)
  - Memory buffer (context handling)
- Accepts queries like:
  - _“What trends can you find?”_
  - _“Give me a video idea based on our audience”_

---

## 🧠 AI Agent Capabilities

### Prompt System Includes:

```
SYSTEM CONTEXT:
You are a YouTube content strategist...
...

RESPONSE FORMATS:

1. TREND REPORT
Key Patterns:
Emerging Topics:
Audience Sentiment:
Content Gaps:

2. CONTENT PROPOSAL
Title:
Target Audience:
Key Hook:
Script Structure:
Introduction, Main Content, Engagement, Conclusion
Supporting Evidence:
```

---

## 🧪 How To Use

1. **Setup Credentials** in n8n:
   - YouTube OAuth2
   - Airtable API
   - Supabase API
   - Google Gemini (PaLM)
   - Groq API

2. **Add Channels to Airtable**:
   - Column: `Channel` (format: `@handle`)

3. **Trigger Workflow**:
   - Use "Test Workflow" or schedule it on a Cron

4. **Chat with AI Agent**:
   - Via webhook (public)
   - Ask about trends, video ideas, sentiment

---

## 🗃️ Folder Customization

- 💬 Slack/Discord trigger instead of webhook
- 📤 Weekly email reports with trends
- 🧹 Filters for sentiment/keywords
- 📊 Analytics dashboards using Supabase + charts

---

## 📎 Useful Links

- [n8n Docs](https://docs.n8n.io/)
- [Supabase Vectors](https://supabase.com/docs/guides/ai/vector)
- [LangChain (JS)](https://js.langchain.com/)
- [Google Gemini](https://makersuite.google.com/)
- [Groq Console](https://console.groq.com/)

---

## ✅ Summary

**YouTube RAG Agent** empowers content creators with actionable insights from real comments, transforming YouTube strategy from guesswork to data-driven decisions.

> _“Let your audience guide your next video — and let AI turn it into a hit.”_

---

