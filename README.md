# 💸 Personal Expense Tracker

A cross-platform personal expense tracking application with **cloud synchronization**, built with **FastAPI** and designed for **Android and Web (PC)** clients.



## 🧩 Features

### ✅ Implemented (MVP)
- User registration & login
- Create / edit / delete expenses
- Expense fields:
  - Amount
  - Category
  - Date
  - Optional note
- View expense history
- Automatic sync across devices
- Strict user data isolation

### 🛣 Planned
- Scan receipts
- Monthly & category summaries
- Budget limits
- Charts & analytics
- CSV export
- Shared wallets
- Offline support & conflict resolution

---

## 🏗 Architecture

Android App Web App (PC)
│ │
└────── REST API ──┘
│
FastAPI Backend
│
SQL Database


## 🛠 Tech Stack

### Backend
- Python
- FastAPI
- SQLAlchemy
- PostgreSQL (SQLite for local development)
- JWT Authentication
- Alembic (migrations)

### Clients
- Android: Kotlin + Retrofit
- Web: HTML/CSS/JavaScript (React planned)

---

## 🗄 Database Schema

### users
| Field | Description |
|------|-------------|
| id | Primary key |
| email | Unique |
| password_hash | Hashed password |

### expenses
| Field | Description |
|------|-------------|
| id | Primary key |
| user_id | Foreign key → users.id |
| amount | Expense amount |
| category | Expense category |
| note | Optional note |
| date | Expense date |
| created_at | Timestamp |

---

## 🔐 Authentication

- Email + password login
- JWT access tokens
- Token sent via HTTP header:
