# NLW Agents

<div align="center">
  <img src=".github/screenshot-1.png" alt="Application Home Page" width="800px">
  <img src=".github/screenshot-2.png" alt="Question Room Page" width="800px">
</div>

**Let me Ask** - A complete web application with AI-powered Q&A system developed during Rocketseat's NLW event.

An intelligent question and answer application where users can create custom rooms, ask questions, and receive AI-generated responses powered by Google Gemini.

## Tech Stack

### Backend
- **Node.js** with TypeScript
- **Fastify** - High-performance web framework
- **Drizzle ORM** - Type-safe ORM for TypeScript
- **PostgreSQL** with pgvector - Vector database for semantic search
- **Google Gemini AI** - AI for transcription and answer generation
- **Zod** - Schema validation
- **Docker** - Containerization
- **Turborepo** - Monorepo build system
- **pnpm** - Fast, disk space efficient package manager

### Frontend
- **React 19** with TypeScript
- **Vite** - Modern build tool
- **TailwindCSS 4** - Utility-first CSS framework
- **React Router DOM** - Routing with audio recording support
- **TanStack Query** - Async state management
- **React Hook Form** - Form management
- **Shadcn/ui** - Component system
- **Web APIs** - MediaRecorder for audio recording
- **Lucide React** - Icons

## Prerequisites

- Node.js 18+
- Docker and Docker Compose
- **Google Gemini API Key** (for AI features)
- pnpm

## Installation

### 1. Clone the repository
```bash
git clone <repository-url>
cd nlw-agents
```

### 2. Install dependencies
```bash
pnpm install
```

### 3. Configure environment variables
```bash
cd server
cp .env-example .env
# Add your Google Gemini API key to the .env file
# GEMINI_API_KEY=your_key_here
```

### 4. Start the database
```bash
cd server
docker compose up -d
```

### 5. Run migrations
```bash
pnpm db:migrate
```

### 6. Seed the database (optional)
```bash
pnpm db:seed
```

## Running the Project

### Development
```bash
pnpm dev
```

This will start both backend and frontend in parallel using Turborepo.

### Build
```bash
pnpm build
```

The application will be available at:
- **Frontend**: http://localhost:5173
- **Backend**: http://localhost:3333

## Project Structure

```
nlw-agents/
├── server/                    # Backend application
│   ├── src/
│   │   ├── db/
│   │   │   ├── schema/        # Database schemas (rooms, questions, audio-chunks)
│   │   │   ├── migrations/    # Database migrations
│   │   │   └── connection.ts  # PostgreSQL + pgvector connection
│   │   ├── http/
│   │   │   └── routes/        # REST API routes (rooms, questions, audio)
│   │   ├── services/
│   │   │   └── gemini.ts      # Google Gemini AI integration
│   │   ├── env.ts             # Environment configuration
│   │   └── server.ts          # Main server
│   ├── docker/                # Docker configuration
│   └── docker-compose.yml     # PostgreSQL + pgvector
└── web/                       # Frontend application
    ├── src/
    │   ├── components/
    │   │   ├── ui/            # Shadcn/ui components
    │   │   ├── create-room-form.tsx
    │   │   ├── question-form.tsx
    │   │   ├── question-item.tsx
    │   │   └── room-list.tsx
    │   ├── http/              # API hooks and types
    │   ├── lib/               # Utilities (dayjs, utils)
    │   ├── pages/             # Application pages
    │   │   ├── create-room.tsx
    │   │   ├── room.tsx
    │   │   └── record-room-audio.tsx # Recording page
    │   └── app.tsx            # Main routing
    └── public/
```

## Implemented Features

### Room System
- **Create rooms** with name and description
- **List rooms** with summary information
- **Navigate between rooms** with dynamic routing
- **Question counter** per room
- **Creation date** with relative formatting

### Question System
- **Question form** with validation (10-500 characters)
- **Q&A interface** with AI
- **Visual states** for answer loading
- **Question history** organized by date
- **Answer generation** with Google Gemini AI

### Audio & AI System
- **Real-time audio recording** via Web APIs
- **Automatic transcription** with Google Gemini AI
- **Upload in 5-second chunks** for processing
- **Vector embeddings** for semantic search
- **Contextual search** in audio transcriptions
- **Context-based answers** from recorded lessons

### Modern Interface
- **Complete Design System** with Shadcn/ui
- **Dark theme** by default
- **Reusable components** (Cards, Buttons, Forms)
- **Full responsiveness**
- **Smooth animations** and transitions

### Complete REST API
- **Room CRUD** (Create, Read)
- **Question CRUD** (Create, Read)
- **Audio upload and processing** with AI
- **Semantic search** with vector embeddings
- **Validation** with Zod
- **End-to-end TypeScript** typing
- **CORS** configured for development

## API Endpoints

### Rooms
- `GET /health` - Health check
- `GET /rooms` - List all rooms with question counter
- `POST /rooms` - Create a new room

### Questions
- `GET /rooms/:roomId/questions` - List questions from a room
- `POST /rooms/:roomId/questions` - Create new question

### Audio & AI
- `POST /rooms/:roomId/audio` - Audio upload with automatic transcription
- **Processing**: Transcription → Embeddings → Vector storage

## Available Scripts

```bash
pnpm dev          # Start development servers
pnpm build        # Build all packages
pnpm db:generate  # Generate migrations
pnpm db:migrate   # Run migrations
pnpm db:seed      # Seed database with test data
pnpm db:studio    # Open Drizzle Studio
pnpm format       # Format code
```

## Environment Configuration

### Environment Variables (Backend)
```env
# server/.env
PORT=3333
DATABASE_URL="postgresql://docker:docker@localhost:5432/agents"
GEMINI_API_KEY="your_gemini_api_key"
```

### Database
The project uses PostgreSQL with the pgvector extension for AI vector support:
- **Image**: `pgvector/pgvector:pg17`
- **User**: `docker`
- **Password**: `docker`
- **Database**: `agents`
- **Port**: `5432`

## Design System

### UI Components
- **Shadcn/ui** with custom theme
- **Radix UI** as primitive base
- **Tailwind CSS** for styling
- **Lucide React** for consistent icons

### Theme & Colors
- **Dark theme** by default
- **Palette**: Zinc as base color
- **Typography**: Optimized font system
- **Spacing**: Tailwind grid system

## Application Pages

### Home Page (`/`)
- **Grid layout** with two columns
- **Room creation form** (left)
- **Recent rooms list** (right)
- **Quick navigation** to existing rooms

### Room Page (`/room/:roomId`)
- **Header** with navigation and audio button
- **Question form** with validation
- **Questions and answers list**
- **Loading states** for AI
- **Integrated audio recording** link

### Recording Page (`/room/:roomId/audio`)
- **Real-time audio recording**
- **Recording controls** (start/pause)
- **Automatic upload** in 5-second chunks
- **Browser compatibility** verification
- **AI processing** (transcription + embeddings)

## Data Flow

1. **Room creation**: Form → API → Database → List update
2. **Listing**: TanStack Query cache → Optimized rendering
3. **Questions**: Validation → API → Database → Answer interface
4. **Audio recording**: MediaRecorder → Chunks → Upload → Gemini AI → Transcription → Embeddings → PostgreSQL
5. **Contextual answers**: Question → Semantic search → Context → Gemini AI → Answer
6. **Navigation**: React Router → Lazy loading → SEO optimized

## AI Integration

### Google Gemini AI
- **Model**: `gemini-2.5-flash` for transcription and answers
- **Embeddings**: `text-embedding-004` for semantic search
- **Transcription**: Audio to text conversion in Portuguese
- **Answer generation**: Based on transcription context
- **Vector search**: PostgreSQL + pgvector for semantic search

### Audio Processing Flow
1. **Capture**: MediaRecorder API (WebM, 64kbps)
2. **Upload**: 5-second chunks via FormData
3. **Transcription**: Google Gemini AI
4. **Embeddings**: Text vectorization
5. **Storage**: PostgreSQL with pgvector
6. **Search**: Semantic similarity for contextual answers

## Monorepo Structure

This project uses:
- **Turborepo** - For build orchestration and caching
- **pnpm workspaces** - For dependency management
- **Shared configurations** - TypeScript, ESLint, Biome

### Benefits
- **Parallel execution** of tasks
- **Intelligent caching** for faster builds
- **Dependency management** across packages
- **Optimized CI/CD** pipeline

## License

This project was developed during Rocketseat's NLW event.

---

<div align="center">
  Made during NLW Agents
</div>
