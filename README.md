# 🔁 LabLoop

**Rent. Share. Buy. Sell. Exchange.**
A campus marketplace that keeps electronics and microcontroller gear in circulation, with an AI chatbot that finds the part you need from a single sentence.

---

## 📌 Description

LabLoop is a web platform where verified students list the electronics hardware they own (sensors, microcontrollers, boards, modules) and other students can **rent, buy, or swap** it within campus. An **AI inventory chatbot** turns plain-language requests such as *"I need an ESP32 under 300 taka"* into structured search filters and returns real listings as cards directly in the chat.

> **Short GitHub description (repo "About" field):**
> Campus marketplace to rent, share, buy, sell & exchange electronics, with an AI chatbot that finds hardware from a single sentence. React + FastAPI + MySQL.

**Suggested topics:** `react` `vite` `fastapi` `mysql` `marketplace` `llm` `chatbot` `tool-calling` `jwt` `campus` `electronics` `university-project`

---

## 🎯 The Problem

| | |
|---|---|
| **Cost** | Boards and sensors add up, but projects need them for weeks, not years. |
| **Waste** | Working hardware sits idle in drawers after the course ends. |
| **Discovery** | Facebook groups offer no search, no availability status, and no trust. |

**Target users:** undergraduates, graduate researchers, and project teams (EEE, CSE, and related departments).

## 💡 The Solution

LabLoop creates a **campus gear loop**: *Search or ask AI → Request → Meet → Return.*

| | Searchable | Verified | Rent / swap | Part-aware | AI search |
|---|:-:|:-:|:-:|:-:|:-:|
| Facebook groups | ✗ | ✗ | ✗ | ✗ | ✗ |
| Generic marketplace | ✓ | ✗ | ✗ | ✗ | ✗ |
| Lab stock | ✗ | ✓ | ✗ | ✗ | ✗ |
| **LabLoop** | ✓ | ✓ | ✓ | ✓ | ✓ |

---

## ✨ Core Features (MVP)

- **Verified sign-up**: student ID or university email
- **Smart listings**: rent, sell, or swap, with photos, price, and deposit
- **Search and filters**: by part, category, and availability
- **Request and chat**: approve requests, message in-app, arrange a meetup
- **Ratings and returns**: deposits and condition logs
- **AI inventory chatbot**: ask in plain words, get listing cards

## 🚀 What Makes LabLoop Different (USP)

1. **AI inventory chatbot**: plain-language search over live listings; only shows what actually exists.
2. **Part-aware catalog**: structured by component, specs, condition, and availability (it knows a Raspberry Pi 4 from a Pi Zero).
3. **Campus-verified trust**: real students, deposits, and ratings.

**Example**

```
You:       Need an ESP32 under Tk 300
LabLoop:   Found 3 nearby. Showing listings:
           • ESP32 DevKit  – Tk 40/day, Available
           • ESP32-CAM     – Tk 60/day, Available
```

---

## 🏗️ System Architecture

```
Browser (React + Vite + chat widget)
        │  HTTPS
        ▼
Cloudflare Tunnel
        │
        ▼
FastAPI (JWT auth, REST, chat tools) ───► MySQL (XAMPP)
        │
        ▼
LLM API (tool calling)
```

**Chatbot flow**

1. The prompt reaches FastAPI.
2. The LLM extracts structured search filters via tool calling.
3. FastAPI runs a **read-only, parameterized SQL query** on MySQL.
4. Matching listing cards are returned to the chat.

## 🧰 Tech Stack

| Layer | Technology | Why |
|---|---|---|
| Frontend | React + Vite | Reusable components, instant reloads |
| Backend | FastAPI (Python) | Async, auto-generated Swagger docs |
| Database | MySQL (XAMPP) | Relational data, identical setup for everyone |
| AI | LLM API with tool calling | Grounded answers from real inventory |
| DevOps | Cloudflare Tunnel | Free HTTPS from a local host |

## 🗄️ Data Model & Security

- **Entities:** Users, Items, Requests, Reviews
- Hashed passwords and **JWT** authentication
- Chatbot limited to a **read-only, parameterized** search tool, so it cannot modify or leak data
- Deposit and condition logging on every rental
- Reporting and admin moderation (account suspension)

---

## 🗺️ Modules & Milestones

| Phase | Module | Scope |
|:-:|---|---|
| 1 | Foundation | DB schema, authentication, verification |
| 2 | Core | Listings, catalog, search |
| 3 | Transactions | Requests, chat, returns |
| 4 | AI & Polish | Chatbot, ratings, testing, demo |

Each phase ends with a working, demo-able increment.

## ⚠️ Risks & Mitigation

| Risk | Mitigation |
|---|---|
| Late or missing returns | Deposits and ratings |
| Local hosting uptime | Move to a cloud VPS later |
| Chatbot errors | Answers only from database results |

## 🔭 Roadmap

- [ ] Mobile app
- [ ] Push notifications
- [ ] Lab-stock integration
- [ ] Photo-based part recognition

---

## ⚙️ Getting Started

> Update the paths and commands below to match your repository structure.

**Prerequisites:** Node.js 18+, Python 3.10+, XAMPP (MySQL), an LLM API key.

```bash
# 1. Clone
git clone https://github.com/<your-username>/labloop.git
cd labloop

# 2. Database: start MySQL in XAMPP, then create the schema
#    (import database/schema.sql via phpMyAdmin or the mysql CLI)

# 3. Backend
cd backend
python -m venv venv && source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env        # set DB credentials, JWT_SECRET, LLM_API_KEY
uvicorn main:app --reload   # API docs at http://localhost:8000/docs

# 4. Frontend
cd ../frontend
npm install
npm run dev                 # http://localhost:5173
```

**Optional: public HTTPS via Cloudflare Tunnel**

```bash
cloudflared tunnel --url http://localhost:5173
```

---

## 👥 Team

| Name | Student ID |
|---|---|
| Md. Mahabub Hossain | 0112230137 |
| Mahadin Islam | 0112230380 |
| Abu Bakkar | 0112230090 |
| Suriya Islam | 011221553 |

*Course project: SE Lab, Section E.*

---

## 📄 License

Released under the [MIT License](LICENSE). *(Change if your course requires otherwise.)*

**Less waste. Lower cost. Faster projects.**
