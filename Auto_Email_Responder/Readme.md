# 📬 Auto Email Responder (n8n + AI)

An intelligent, fully automated email response system for businesses dealing with handcrafted furniture, bamboo, and eco-friendly décor products.

---

## 💡 Features

- ⏰ Checks Gmail every hour for new emails
- ✨ Cleans raw email content (removes HTML/scripts)
- 🧠 AI-based email categorization into:
  - `Ready to Send Data`
  - `More Info Needed`
  - `Not Interested`
  - `Pending`
- 🔍 Searches a Supabase vector store for relevant past Q&A
- ✍️ Crafts HTML email replies (with personalized tone)
- 🏷 Adds Gmail labels based on classification
- 📤 Sends or drafts replies automatically

---

## 🧰 Tech Stack

| Tool/Service         | Use Case                              |
|----------------------|----------------------------------------|
| **n8n**              | Workflow automation                    |
| **LangChain**        | AI orchestration and output parsing    |
| **OpenAI GPT-4o-mini** | AI text generation and formatting      |
| **Groq LLaMA**       | Fast AI inference                      |
| **Supabase**         | Vector similarity search               |
| **Google Gemini**    | Embeddings for email content           |
| **Gmail API**        | Email operations (trigger, reply, tag) |

---

## 🔁 Email Categorization Logic

| Category            | Example Triggers                                      |
|---------------------|--------------------------------------------------------|
| Ready to Send Data  | Pricing, stock, orders, partnerships, shipping         |
| More Info Needed    | Vague inquiries, customization questions               |
| Not Interested      | Spam, unrelated pitches (e.g. SEO services)            |
| Pending             | Incomplete, unclear, or generic messages               |

---

## 🚀 How It Works

1. **Trigger**: Email received via Gmail.
2. **Preprocessing**: HTML stripped from body using JS code.
3. **Categorization**: AI assigns one of 4 categories.
4. **Match Check**: Looks for existing answers in Supabase vector store.
5. **Response**:
   - If found → Uses answer
   - If not → Generates new AI response
6. **Formatting**: Crafts email in polished HTML.
7. **Send**: Replies or drafts email + applies Gmail labels.

---

## 📦 Deployment

1. Import the workflow into [n8n](https://n8n.io/)
2. Set up credentials:
   - Gmail OAuth2
   - Supabase API
   - OpenAI & Groq API keys
   - Google Gemini (PaLM) for embeddings
3. Activate the workflow
4. Watch your inbox respond like magic 🪄

---

## 📬 Example Use Case

> Customer emails: _"Do you ship bamboo furniture to Germany?"_  
> → Auto-responder:
- Categorizes as `Ready to Send Data`
- Finds matching Q&A in Supabase
- Sends formatted reply in HTML with greeting, answer, and closing

---

## 📩 Labels Used

| Label Name                | Usage                                  |
|--------------------------|----------------------------------------|
| `Ready to Send Data`     | Confirmed business intent              |
| `More Info Needed`       | Needs clarification                    |
| `Not Interested`         | Irrelevant/spam                        |
| `Pending`                | Vague or unclear inquiry               |

---

## 🔒 Notes

- Emails must be in English (currently)
- Easily extensible for other product domains
- Supports HTML responses and structured email handling

---

## 🤖 Built By

This system is designed for **Eco Woodies**, a company focused on handcrafted, sustainable home décor.

For contributions or support, contact the project team or raise a GitHub issue.

---
