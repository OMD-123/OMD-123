<div align="center">

# 🚀 GitHub-like Platform

**A full-stack, production-ready Git hosting platform built with the MERN stack**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js](https://img.shields.io/badge/Node.js-18%2B-green.svg)](https://nodejs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5%2B-blue.svg)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-18%2B-61DAFB.svg)](https://reactjs.org/)
[![Express](https://img.shields.io/badge/Express.js-4%2B-black.svg)](https://expressjs.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-6%2B-green.svg)](https://www.mongodb.com/)
[![Redis](https://img.shields.io/badge/Redis-7%2B-red.svg)](https://redis.io/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

*A scalable platform inspired by GitHub with native Git storage, CI/CD pipelines, webhooks, real-time collaboration, and intelligent code search.*

</div>

---

## ✨ Features

| Category | Capabilities |
|----------|-------------|
| **🗂 Repository Management** | Create, clone, fork, delete, archive, transfer |
| **📝 Git Operations** | Native `nodegit` — commit, branch, merge, tag, rebase, blame, history |
| **🔄 CI/CD Pipelines** | BullMQ-backed pipelines with stages, parallel jobs, artifacts, caching |
| **🔗 Webhooks** | Event-driven HTTP callbacks + real-time Socket.io delivery |
| **🔍 Code Search** | Full-text search across repos, commits, files (MongoDB text indexes) |
| **👥 Collaboration** | Real-time notifications, @mentions, activity feeds |
| **🔐 Authentication** | JWT + refresh tokens, OAuth (GitHub, GitLab), 2FA ready |
| **🎨 Code Editor** | Monaco Editor with syntax highlighting, diff view, LSP support |

---

## 🏗 Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        FRONTEND (React 18 + TS)                 │
│  ┌─────────┐ ┌──────────┐ ┌─────────┐ ┌────────┐ ┌──────────┐  │
│  │ Pages   │ │ Components│ │ Redux   │ │ Socket │ │ Monaco   │  │
│  │ /Routes │ │ /UI Kit  │ │ Store   │ │ Client │ │ Editor   │  │
│  └────┬────┘ └────┬─────┘ └────┬────┘ └────┬───┘ └────┬─────┘  │
└───────│────────────│───────────│────────────│──────────│────────┘
        │            │           │            │          │
        ▼            ▼           ▼            ▼          ▼
┌─────────────────────────────────────────────────────────────────┐
│                      BACKEND (Express + TS)                     │
│  ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────────┐   │
│  │ Auth   │ │ Git    │ │ CI/CD  │ │ Webhook│ │ CodeSearch │   │
│  │ Module │ │ Module │ │ Module │ │ Module │ │ Module     │   │
│  └────┬───┘ └────┬───┘ └────┬───┘ └────┬───┘ └──────┬─────┘   │
└───────│──────────│──────────│──────────│────────────│─────────┘
        │          │          │          │            │
        ▼          ▼          ▼          ▼            ▼
┌─────────────────────────────────────────────────────────────────┐
│                         DATA LAYER                              │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────────┐   │
│  │ MongoDB  │  │ Redis    │  │ Git Repos│  │ BullMQ       │   │
│  │ (Meta)   │  │ (Cache/  │  │ (nodegit)│  │ (Queues)     │   │
│  │          │  │  PubSub) │  │          │  │              │   │
│  └──────────┘  └──────────┘  └──────────┘  └──────────────┘   │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🛠 Tech Stack

### Backend
| Technology | Version | Purpose |
|------------|---------|---------|
| **Node.js** | 18+ | Runtime |
| **TypeScript** | 5+ | Type safety |
| **Express.js** | 4+ | HTTP framework |
| **MongoDB + Mongoose** | 6+ | Metadata & search |
| **Redis + BullMQ** | 7+ | Caching, queues, pub/sub |
| **Socket.io** | 4+ | Real-time communication |
| **nodegit** | Latest | Native Git operations |
| **JWT + zod** | Latest | Auth & validation |

### Frontend
| Technology | Version | Purpose |
|------------|---------|---------|
| **React** | 18+ | UI framework |
| **TypeScript** | 5+ | Type safety |
| **Vite** | 5+ | Build tool |
| **Redux Toolkit** | 2+ | State management |
| **React Router** | 6+ | Routing |
| **Monaco Editor** | Latest | Code editing |
| **Socket.io Client** | 4+ | Real-time |
| **Axios** | 1+ | HTTP client |

---

## 🚀 Quick Start

### Prerequisites
- **Node.js** 18+
- **MongoDB** 6+
- **Redis** 7+
- **Git** 2.30+

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/yourusername/github-like-platform.git
cd github-like-platform

# 2. Backend setup
cd backend
npm install
cp .env.example .env
# Edit .env with your configuration

# 3. Frontend setup
cd ../frontend
npm install
cp .env.example .env
# Edit .env with your configuration

# 4. Start infrastructure
docker-compose up -d  # MongoDB + Redis

# 5. Start development servers
# Terminal 1 - Backend
cd backend && npm run dev

# Terminal 2 - Frontend
cd frontend && npm run dev
```

### Environment Variables

**Backend** (`.env`)
```env
# Server
PORT=5000
NODE_ENV=development

# Database
MONGODB_URI=mongodb://localhost:27017/gitplatform
REDIS_HOST=localhost
REDIS_PORT=6379

# Auth
JWT_SECRET=your_super_secret_key_min_32_chars
JWT_REFRESH_SECRET=your_refresh_secret_min_32_chars
JWT_EXPIRY=15m
JWT_REFRESH_EXPIRY=7d

# Frontend URL (CORS)
FRONTEND_URL=http://localhost:5173

# Git
GIT_STORAGE_PATH=./git-repositories

# Email (optional)
SMTP_HOST=smtp.example.com
SMTP_PORT=587
SMTP_USER=your@email.com
SMTP_PASS=your_password
```

**Frontend** (`.env`)
```env
VITE_API_URL=http://localhost:5000/api
VITE_WS_URL=ws://localhost:5000
VITE_APP_NAME=GitPlatform
```

---

## 📡 API Reference

### Authentication
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/auth/register` | Register new user |
| `POST` | `/api/auth/login` | Login user |
| `POST` | `/api/auth/refresh` | Refresh access token |
| `GET` | `/api/auth/me` | Get current user |
| `POST` | `/api/auth/logout` | Logout |

### Repositories
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/repositories` | List repositories (paginated) |
| `POST` | `/api/repositories` | Create repository |
| `GET` | `/api/repositories/:id` | Get repository |
| `PATCH` | `/api/repositories/:id` | Update repository |
| `DELETE` | `/api/repositories/:id` | Delete repository |
| `POST` | `/api/repositories/:id/fork` | Fork repository |
| `GET` | `/api/repositories/:id/contents/:commitId/*` | Get file tree/contents |
| `GET` | `/api/repositories/:id/commits` | List commits |
| `GET` | `/api/repositories/:id/commits/:sha` | Get commit details |
| `GET` | `/api/repositories/:id/search?q=query` | Search code |

### CI/CD
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/ci-cd/pipelines` | Create pipeline |
| `GET` | `/api/ci-cd/pipelines` | List pipelines |
| `GET` | `/api/ci-cd/pipelines/:id` | Get pipeline |
| `POST` | `/api/ci-cd/pipelines/:id/trigger` | Trigger run |
| `GET` | `/api/ci-cd/runs/:id` | Get run status/logs |

### Webhooks
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/webhooks` | Create webhook |
| `GET` | `/api/webhooks` | List webhooks |
| `DELETE` | `/api/webhooks/:id` | Delete webhook |
| `GET` | `/api/webhooks/:id/deliveries` | View delivery history |

---

## 🧪 Testing

```bash
# Backend tests
cd backend
npm run test          # Unit + integration
npm run test:watch    # Watch mode
npm run test:coverage # Coverage report

# Frontend tests
cd frontend
npm run test
npm run test:e2e      # Cypress/Playwright
```

---

## 📁 Project Structure

```
github-like-platform/
├── backend/
│   ├── src/
│   │   ├── config/           # Configuration
│   │   ├── modules/
│   │   │   ├── auth/         # JWT, OAuth, 2FA
│   │   │   ├── git/          # nodegit operations
│   │   │   ├── ci-cd/        # Pipeline engine
│   │   │   ├── webhook/      # Event delivery
│   │   │   └── search/       # Code search
│   │   ├── middleware/       # Error, validation, rate-limit
│   │   ├── utils/            # Helpers
│   │   ├── app.ts            # Express setup
│   │   └── server.ts         # Entry point
│   ├── tests/                # Unit + integration
│   └── Dockerfile
│
├── frontend/
│   ├── src/
│   │   ├── pages/            # Route components
│   │   ├── components/       # Reusable UI
│   │   ├── store/            # Redux slices
│   │   ├── hooks/            # Custom hooks
│   │   ├── services/         # API clients
│   │   ├── types/            # TS interfaces
│   │   ├── App.tsx
│   │   └── main.tsx
│   └── Dockerfile
│
├── docker-compose.yml
├── .github/workflows/        # CI/CD
└── README.md
```

---

## 🤝 Contributing

We welcome contributions! Please read our [Contributing Guide](CONTRIBUTING.md) first.

### Quick Contribution Checklist
- [ ] Fork the repository
- [ ] Create a feature branch (`git checkout -b feature/amazing-feature`)
- [ ] Write tests for new functionality
- [ ] Ensure all tests pass (`npm run test`)
- [ ] Follow code style (`npm run lint`)
- [ ] Submit a Pull Request

### Good First Issues
Look for issues tagged `good first issue` or `help wanted`.

---

## 📸 Screenshots

> *Add screenshots here showing:*
> - Dashboard with repository list
> - File browser with Monaco editor
> - CI/CD pipeline visualization
> - Real-time notifications
> - Code search results

---

## 🗺 Roadmap

- [ ] **Pull Requests & Code Reviews** — Diff view, comments, approvals
- [ ] **Issue Tracking** — Labels, milestones, project boards
- [ ] **GitHub Actions Compatibility** — Import `.github/workflows`
- [ ] **Package Registry** — npm, Docker, Maven packages
- [ ] **Security Scanning** — SAST, dependency audit
- [ ] **Performance Analytics** — Repository insights
- [ ] **AI Code Assistant** — Copilot-like suggestions

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

---

## 👤 Author

**Om Dandagvhal**  
B.Tech CS '27 | Full-Stack Developer | Open Source Contributor

[![GitHub](https://img.shields.io/badge/GitHub-OMD--123-181717?logo=github)](https://github.com/OMD-123)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Om%20Dandagvhal-0A66C2?logo=linkedin)](https://linkedin.com/in/om-dandagvhal)
[![Email](https://img.shields.io/badge/Email-omd4485%40gmail.com-D14836?logo=gmail)](mailto:omd4485@gmail.com)

---

<div align="center">

**⭐ Star this repo if you find it useful!**

</div>