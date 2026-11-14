# LabLoop 🔌🔄
**Rent. Share. Buy. Sell. Exchange.**  
*A verified peer-to-peer campus lab hardware exchange powered by an AI inventory assistant.*

## Overview
**LabLoop** is a university-gated electronics and microcontroller marketplace designed to keep lab components in circulation across semesters. Instead of letting Arduinos, ESP boards, sensors, and lab kits sit unused after finals, verified students can rent, share, buy, sell, or exchange hardware with peers on campus—and search live inventory using natural language via an AI assistant.

## Key Features
- **Five Transaction Modes:** Rent, share, buy, sell, and exchange campus electronics gear in one unified platform.
- **AI Inventory Assistant (Gemini Function Calling):** Parses natural-language queries (e.g., *"show ESP boards within 500 taka"*) into structured parameters executed safely via parameterized SQL queries on MySQL, returning interactive product cards directly inside the chat.
- **Campus-Verified Trust & Accountability:** JWT authentication, bcrypt password hashing, deposit tracking, pickup/return condition logging, user reviews, and admin moderation.

## Tech Stack
- **Frontend:** React (SPA), Vite, Tailwind CSS
- **Backend:** Python, FastAPI, JWT Auth
- **Database:** MySQL 8.0
- **AI Integration:** Gemini API (Tool / Function Calling)
- **Networking / Demo Tunnel:** Cloudflare Edge Tunnel (HTTPS)

## Team (UIU Software Engineering Lab)
- **Md. Mahabub Hossain** (`0112230137`)
- **Mahadin Islam** (`0112230380`)
- **Abu Bakkar** (`0112230090`)
- **Suriya Islam** (`0112221553`)
