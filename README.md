# TrackThatMoney
A cross-platform personal expense tracking application with user accounts and cloud synchronization. The app is designed to be used on Android and PC (via a web interface), with a shared backend ensuring data consistency across devices.

✨ Features
User registration and authentication (email + password)
Add, edit, and delete personal expenses
Expense fields:
  -amount
  -category
  -date
  -optional note
View expense history
Data synchronized across all devices
Secure user-specific data isolation

Planned / Future Features
Monthly and category summaries
Budget limits per category
Charts and analytics
CSV export
Shared wallets (multiple users sharing expenses)
Offline support and conflict handling

🏗 Architecture Overview

The system follows a client–server architecture:

Android App        Web App (PC)
     │                  │
     └─────── REST API ─┘
                │
           FastAPI Backend
                │
            SQL Database


Both clients communicate with the backend via a REST API.

Authentication is handled using JWT tokens.

All expense data is stored centrally to enable synchronization.

🧠 Tech Stack
Backend

Python

FastAPI

SQLAlchemy

PostgreSQL (SQLite for local development)

JWT authentication

Alembic (database migrations)

Frontend

Android: Kotlin + Retrofit

Web (PC): HTML/CSS/JavaScript (React planned)

🗄 Database Schema (Simplified)
Users

id (primary key)

email (unique)

password_hash

Expenses

id (primary key)

user_id (foreign key → users.id)

amount

category

note

date

created_at

Each expense belongs to exactly one user.

🔐 Authentication Flow

User registers or logs in with email and password

Backend returns a JWT access token

Clients store the token securely

Token is sent with every request via:

Authorization: Bearer <token>


Backend validates the token and identifies the user

🔄 Synchronization Model

Clients fetch the latest data from the server on startup

Any create/update/delete operation is immediately sent to the backend

No real-time or offline conflict resolution in the MVP

Designed to be extended later if needed

🚀 Getting Started (Backend)
# create virtual environment
python -m venv venv
source venv/bin/activate

# install dependencies
pip install -r requirements.txt

# run the server
uvicorn app.main:app --reload


The API will be available at:

http://localhost:8000


Interactive API docs:

http://localhost:8000/docs

🧪 Development Notes

SQLite is used for local development for simplicity

PostgreSQL is recommended for production

The project is intentionally scoped to stay simple while remaining extensible

Emphasis is placed on clarity, maintainability, and clean separation of concerns

🎯 Project Goals

Build a real, usable personal finance tool
