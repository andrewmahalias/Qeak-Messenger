# Qeak Messenger

**Real-time messaging backend with AI-powered message translation.**

Qeak Messenger is an asynchronous messaging backend built with **Python and FastAPI**. It provides REST API endpoints for user authentication, contact management, and chat operations, alongside WebSocket-based real-time messaging.

The project explores asynchronous Python development, persistent data storage, real-time communication, and integration of AI-powered translation into the messaging workflow.

## Features

- **Real-time messaging** — bidirectional communication using WebSockets.
- **AI-powered translation** — translates messages during the messaging workflow.
- **JWT authentication** — secure user authentication and protected endpoints.
- **Chat management** — create chats, manage contacts, and retrieve messages.
- **Persistent storage** — stores users, chats, and messages in PostgreSQL.
- **Automated tests** — tests for authentication and messaging functionality.

## Architecture

The application is built around a FastAPI backend that exposes REST endpoints and WebSocket connections.

```mermaid
flowchart TD
    A[Client Application] -->|REST API| B[FastAPI Backend]
    A -->|WebSocket| B
    B --> C[Authentication]
    B --> D[Chat Services]
    D --> E[(PostgreSQL)]
    D --> F[Translation Service]
    F --> G[OpenAI API]
    D --> H[Real-time Message Delivery]
    H --> A
```

The client is external to this repository. This repository contains the backend implementation and API.

## Tech Stack

| Category | Technologies |
|---|---|
| Language | Python |
| Backend | FastAPI |
| Database | PostgreSQL |
| ORM | SQLAlchemy |
| Communication | REST API, WebSockets |
| Authentication | JWT |
| AI integration | OpenAI API, LangChain |
| Background processing | Celery, Redis |
| Testing | Pytest |
| Documentation | OpenAPI / Swagger |

## API Overview

| Endpoint | Method | Description |
|---|---|---|
| `/auth/register` | POST | Register a user |
| `/auth/login` | POST | Authenticate a user |
| `/auth/users/me` | GET | Retrieve the current user |
| `/contacts` | GET | Retrieve contacts |
| `/chat` | POST | Create a chat |
| `/chat/{chat_id}/message` | POST | Send a message |
| `/chat/{chat_id}/message` | GET | Retrieve chat messages |

WebSocket connections are used for real-time message exchange.

Interactive API documentation is available at `/docs` when the application is running.

## Getting Started

### Requirements

- Python 3.10+
- PostgreSQL
- Redis (if background workers are enabled)

### Installation

Clone the repository:

```bash
git clone https://github.com/andrewmahalias/Qeak-Messenger.git
cd Qeak-Messenger
```

Create and activate a virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

### Environment Variables

Create a `.env` file in the project root:

```env
APP_VERSION=1.0.0
SECRET_KEY=your-secret-key
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
DATABASE_URL=postgresql+asyncpg://user:password@localhost:5432/messenger
```

Configure additional environment variables if required by your local setup.

### Run the Application

```bash
uvicorn app.main:app --reload
```

API documentation:

- Swagger UI: `http://127.0.0.1:8000/docs`
- ReDoc: `http://127.0.0.1:8000/redoc`

### Run Tests

```bash
pytest
```

## Project Structure

```text
.
├── app/
│   └── ...
├── core/
├── database/
├── tests/
├── .github/
├── requirements.txt
└── README.md
```

## Project Goals

This project focuses on practical backend engineering concepts:

- Building asynchronous APIs with FastAPI.
- Implementing real-time communication with WebSockets.
- Managing relational data with SQLAlchemy and PostgreSQL.
- Implementing authentication and access control.
- Integrating AI services into backend workflows.
- Testing API functionality and application logic.

---

**Author:** Andrii Mahalias
