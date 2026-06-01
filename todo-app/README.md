# KitabKosh - Reading Companion & Book Tracker

A full-stack web application for managing your reading journey, built with Next.js, FastAPI, and AI-powered conversational interface.

## 🚀 Project Overview

KitabKosh is a modern reading companion that helps you organize your book collection, track reading progress, and manage your library through both traditional GUI and natural language conversations with an AI assistant.

## 📋 Project Phases

- Command-line todo application with in-memory storage
- Basic CRUD operations (Add, Delete, Update, View, Mark Complete)
- Python 3.13+ with UV package manager
- RESTful API with FastAPI backend
- Next.js 16+ frontend with responsive UI
- User authentication with Better Auth + JWT
- Persistent storage with Neon Serverless PostgreSQL
- User data isolation and security
- AI chatbot for natural language book management
- OpenAI Agents SDK integration
- MCP (Model Context Protocol) server with standardized tools
- Stateless chat architecture with database-backed conversations
- OpenAI ChatKit frontend integration

## 🛠 Technology Stack

### Frontend
- **Framework**: Next.js 16+ (App Router)
- **Language**: TypeScript 5.0+
- **Styling**: Tailwind CSS 3.4+
- **Authentication**: Better Auth with JWT plugin
- **Chat UI**: OpenAI ChatKit 
- **Icons**: Lucide React

### Backend
- **Framework**: FastAPI (latest stable)
- **Language**: Python 3.13+
- **ORM**: SQLModel (with Pydantic v2)
- **Database**: Neon Serverless PostgreSQL
- **Migrations**: Alembic
- **AI Framework**: OpenAI Agents SDK 
- **MCP Server**: Official MCP SDK 
- **Authentication**: JWT verification with python-jose

## 📁 Project Structure

```
todo-app/
├── frontend/              # Next.js application
│   ├── src/
│   │   ├── app/          # App Router pages
│   │   ├── components/   # React components
│   │   │   ├── tasks/    # Book management UI
│   │   │   └── chat/     # AI chatbot interface
│   │   ├── lib/          # Utilities and API clients
│   │   └── types/        # TypeScript definitions
│   └── README.md
│
├── backend/              # FastAPI application
│   ├── src/
│   │   ├── models/       # SQLModel schemas
│   │   ├── services/     # Business logic
│   │   ├── api/routes/   # FastAPI routes
│   │   ├── mcp/          # MCP server and tools
│   │   ├── agents/       # OpenAI Agents SDK
│   │   └── middleware/   # JWT verification
│   └── README.md
│
├── docker-compose.yml   # Local development orchestration
└── README.md           # This file
```

## 🚀 Quick Start

### Prerequisites
- Node.js 20+ and pnpm 8+
- Python 3.13+ and UV
- Docker (for local PostgreSQL)
- Neon PostgreSQL account (for production)
- OpenAI API key (for Phase III chatbot)

### Environment Setup

#### Frontend
Create `frontend/.env.local`:
```env
BETTER_AUTH_SECRET=your-shared-secret
BETTER_AUTH_URL=http://localhost:3000
NEXT_PUBLIC_API_URL=http://localhost:8000
NEXT_PUBLIC_OPENAI_DOMAIN_KEY=your-domain-key
```

#### Backend
Create `backend/.env`:
```env
BETTER_AUTH_SECRET=your-shared-secret
DATABASE_URL=postgresql://user:pass@localhost:5432/kitabkosh
OPENAI_API_KEY=sk-proj-your-key
CORS_ORIGINS=http://localhost:3000
```

### Running Locally

#### Option 1: Docker Compose (Recommended)
```bash
docker-compose up
```
This starts:
- Frontend: http://localhost:3000
- Backend: http://localhost:8000
- PostgreSQL: localhost:5432

#### Option 2: Manual Setup

**Backend:**
```bash
cd backend
uv sync
uvicorn src.main:app --reload
```

**Frontend:**
```bash
cd frontend
pnpm install
pnpm dev
```

## 📚 Features

### Phase II Features ✅
- ✅ User authentication (signup, signin, signout)
- ✅ Book CRUD operations via web interface
- ✅ Responsive dashboard with statistics
- ✅ Reading calendar and progress tracking
- ✅ User profile management
- ✅ JWT-based stateless authentication
- ✅ User data isolation (100% secure)

### Phase III Features ✅
- ✅ AI-powered conversational interface
- ✅ Natural language book management
- ✅ MCP tools for standardized operations
- ✅ Stateless chat architecture
- ✅ Conversation history persistence
- ✅ Priority-based book addition
- ✅ Interactive welcome popup

## 🔐 Security

- **JWT Authentication**: Stateless token-based auth
- **User Isolation**: All queries filter by `user_id`
- **Path Validation**: User ID in path must match JWT
- **Input Validation**: Pydantic models (backend), TypeScript (frontend)
- **SQL Injection Protection**: SQLModel uses parameterized queries

## 📡 API Endpoints

### Task Management
- `GET /api/{user_id}/tasks` - List all books
- `POST /api/{user_id}/tasks` - Create book
- `GET /api/{user_id}/tasks/{id}` - Get book details
- `PUT /api/{user_id}/tasks/{id}` - Update book
- `PATCH /api/{user_id}/tasks/{id}` - Toggle completion
- `DELETE /api/{user_id}/tasks/{id}` - Delete book

### Chat 
- `POST /api/{user_id}/chat` - Send message & get AI response

## 🤖 MCP Tools

The MCP server exposes these tools for AI agent:
- `add_book` - Create new book
- `list_books` - Retrieve books
- `complete_book` - Mark book as read
- `delete_book` - Remove book
- `update_book` - Modify book details

- **Frontend Guide**: `frontend/README.md`
- **Backend Guide**: `backend/README.md`

## 🧪 Testing

### Backend
```bash
cd backend
pytest
```

### Frontend
```bash
cd frontend
pnpm test
pnpm test:e2e
```

## 🙏 Acknowledgments

Built with:
- Next.js
- FastAPI
- OpenAI Agents SDK
- Better Auth
- Neon PostgreSQL

