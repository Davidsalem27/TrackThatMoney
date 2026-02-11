💸 Personal Expense Tracker

A cross-platform personal expense tracking application with cloud synchronization, built with FastAPI and designed for Android and Web (PC) clients.

The project focuses on clean backend design, practical authentication, and multi-client data consistency.

🚀 Highlights

🔐 Secure user authentication (JWT)

📱 Android + 💻 Web clients

☁️ Centralized backend with synced data

👤 Multi-user support (starting small, scalable by design)

🧱 Clean, extensible architecture

🧩 Features
✅ Implemented (MVP)

User registration & login

Create / edit / delete expenses

Expense fields:

Amount

Category

Date

Optional note

View expense history

Automatic sync across devices

Strict user data isolation

🛣 Planned

Monthly & category summaries

Budget limits

Charts & analytics

CSV export

Shared wallets

Offline support & conflict resolution

🏗 Architecture
Android App        Web App (PC)
     │                  │
     └────── REST API ──┘
                │
          FastAPI Backend
                │
            SQL Database


REST-based communication

Stateless backend

JWT-based authentication

Designed for easy client expansion

🛠 Tech Stack
Backend

Python

FastAPI

SQLAlchemy

PostgreSQL (SQLite for local development)

JWT Authentication

Alembic (migrations)

Clients

Android: Kotlin + Retrofit

Web: HTML/CSS/JS (React planned)

🗄 Database Schema
users
Field	Type
id	PK
email	unique
password_hash	string
expenses
Field	Type
id	PK
user_id	FK → users.id
amount	number
category	string
note	string
date	date
created_at	timestamp
🔐 Authentication

Email + password login

JWT access tokens

Token sent via HTTP header:

Authorization: Bearer <token>


Backend validates token per request

🔄 Synchronization Strategy

Clients fetch latest data on startup

All changes are immediately persisted to the backend

No real-time sync or offline conflict handling in MVP

Architecture allows future extension

▶️ Running the Backend Locally
python -m venv venv
source venv/bin/activate

pip install -r requirements.txt

uvicorn app.main:app --reload


API available at:

http://localhost:8000


Swagger docs:

http://localhost:8000/docs

🧪 Development Notes

SQLite used for local development

PostgreSQL recommended for production

Backend-first development approach

Emphasis on readability, maintainability, and scalability

🎯 Project Goals

Build a real-world, multi-platform application

Practice backend API & auth design

Demonstrate clean architecture and tradeoff awareness

Serve as a strong portfolio project for software engineering roles
