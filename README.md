# 🧠 AI Classroom Notes Generator

> **B.Tech CSE Mini Project** — Transform audio lectures into structured AI-powered study notes.

## 🚀 Tech Stack

| Layer      | Technology                        |
|------------|-----------------------------------|
| Frontend   | React.js (Vite) + Tailwind CSS    |
| Backend    | Node.js + Express.js              |
| Database   | MongoDB Atlas + Mongoose          |
| Auth       | JWT (JSON Web Tokens)             |
| AI         | OpenAI Whisper + GPT-3.5 Turbo   |
| PDF Export | jsPDF + jsPDF-AutoTable           |

## 📁 Project Structure

```
ai-classroom-notes-generator/
├── server/                    # Express.js Backend
│   ├── index.js               # App entry point
│   ├── models/
│   │   ├── User.model.js      # Mongoose User schema
│   │   └── Note.model.js      # Mongoose Note schema
│   ├── controllers/
│   │   ├── auth.controller.js # Register/Login/Me
│   │   ├── note.controller.js # Upload/CRUD/Search
│   │   └── user.controller.js # Profile/Stats
│   ├── routes/
│   │   ├── auth.routes.js
│   │   ├── note.routes.js
│   │   └── user.routes.js
│   ├── middleware/
│   │   ├── auth.middleware.js  # JWT guard
│   │   ├── error.middleware.js # Global error handler
│   │   └── upload.middleware.js# Multer config
│   └── services/
│       └── ai.service.js      # Whisper + GPT calls
│
├── client/                    # React Frontend
│   ├── src/
│   │   ├── pages/
│   │   │   ├── LandingPage.jsx
│   │   │   ├── LoginPage.jsx
│   │   │   ├── RegisterPage.jsx
│   │   │   ├── DashboardPage.jsx
│   │   │   ├── UploadPage.jsx
│   │   │   ├── NotesListPage.jsx
│   │   │   ├── NoteDetailPage.jsx
│   │   │   ├── SearchPage.jsx
│   │   │   └── ProfilePage.jsx
│   │   ├── components/
│   │   │   ├── Navbar.jsx
│   │   │   ├── NoteCard.jsx
│   │   │   ├── LoadingSpinner.jsx
│   │   │   └── ProtectedRoute.jsx
│   │   ├── context/AuthContext.jsx
│   │   ├── services/
│   │   │   ├── api.js
│   │   │   └── noteService.js
│   │   └── utils/pdfGenerator.js
│   └── package.json
│
├── .env                       # Environment variables
└── package.json
```

## ⚙️ Setup & Installation

### Prerequisites
- Node.js v18+
- MongoDB Atlas account (free tier works)
- OpenAI API key (optional — uses mock data if not set)

### 1. Configure Environment

Edit `.env` in the project root:
```env
MONGODB_URI=mongodb+srv://your_user:your_password@cluster0.xxxxx.mongodb.net/ai-classroom-notes
JWT_SECRET=your_super_long_random_secret
OPENAI_API_KEY=sk-your-openai-key   # Optional for demo
```

### 2. Install Dependencies

```bash
# Install backend dependencies
npm install

# Install frontend dependencies
cd client && npm install
```

### 3. Run the Application

**Terminal 1 — Backend:**
```bash
npm run dev
# Server runs at http://localhost:5000
```

**Terminal 2 — Frontend:**
```bash
cd client && npm run dev
# Client runs at http://localhost:5173
```

## 🔑 REST API Endpoints

### Auth
| Method | Route                  | Access  | Description       |
|--------|------------------------|---------|-------------------|
| POST   | /api/auth/register     | Public  | Register user     |
| POST   | /api/auth/login        | Public  | Login user        |
| GET    | /api/auth/me           | Private | Get current user  |

### Notes
| Method | Route                    | Access  | Description           |
|--------|--------------------------|---------|-----------------------|
| POST   | /api/notes/upload        | Private | Upload + generate notes |
| GET    | /api/notes               | Private | Get all notes (paginated) |
| GET    | /api/notes/search?q=...  | Private | Full-text search      |
| GET    | /api/notes/:id           | Private | Get single note       |
| PATCH  | /api/notes/:id/favorite  | Private | Toggle favorite       |
| DELETE | /api/notes/:id           | Private | Delete note           |

### Users
| Method | Route                     | Access  | Description      |
|--------|---------------------------|---------|------------------|
| GET    | /api/users/stats          | Private | Dashboard stats  |
| PUT    | /api/users/profile        | Private | Update profile   |
| PUT    | /api/users/change-password| Private | Change password  |

## 🌟 Features

- **AI Transcription** — OpenAI Whisper converts lecture audio to text
- **Smart Notes** — GPT-3.5 generates Summary, Key Points, Important Q&A, Keywords
- **PDF Export** — Download formatted notes with one click
- **Full-text Search** — Search across title, subject, transcript, keywords
- **JWT Authentication** — Secure registration and login
- **Responsive UI** — Works on desktop and mobile
- **Dark Theme** — Modern AI-themed design with animated gradients
- **Demo Mode** — Works without OpenAI key using realistic mock data
