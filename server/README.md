# NLW Agents - Server

REST API developed during Rocketseat's NLW event for room management and real-time question system with AI-powered answers.

## Technologies

- **Node.js** - JavaScript runtime
- **TypeScript** - JavaScript superset with static typing
- **Fastify** - Fast and efficient web framework
- **Drizzle ORM** - Type-safe ORM for TypeScript
- **PostgreSQL** - Relational database with pgvector extension
- **Zod** - Schema validation and parsing library
- **Biome** - Code linter and formatter
- **Google Gemini AI** - AI for audio transcription and embeddings generation
- **Vector Database** - Semantic search with embeddings
- **pnpm** - Fast, disk space efficient package manager

## Prerequisites

- Node.js 18+
- Docker and Docker Compose
- Google Gemini API Key
- pnpm

## Setup

### 1. Install dependencies
```bash
pnpm install
```

### 2. Configure environment variables
```bash
cp .env-example .env
# Add your Google Gemini API key to the .env file
# GEMINI_API_KEY=your_key_here
```

### 3. Start the database
```bash
docker compose up -d
```

### 4. Run migrations
```bash
pnpm db:migrate
```

### 5. Seed the database (optional)
```bash
pnpm db:seed
```

## Running

### Development
```bash
pnpm dev
```

### Production
```bash
pnpm start
```

The server will be available at `http://localhost:3333`

## API Endpoints

### Rooms
- `GET /health` - Health check
- `GET /rooms` - List all rooms with question counter
- `POST /rooms` - Create a new room

**Create Room Request:**
```json
{
  "name": "string",
  "description": "string"
}
```

### Questions
- `GET /rooms/:roomId/questions` - List questions from a room
- `POST /rooms/:roomId/questions` - Create a new question

**Create Question Request:**
```json
{
  "question": "string (10-500 characters)"
}
```

### Audio
- `POST /rooms/:roomId/audio` - Upload and transcribe audio with AI

**Upload Audio Request:**
```
Content-Type: multipart/form-data
{
  "file": Blob // audio.webm file
}
```

## Available Scripts

```bash
pnpm dev          # Development server with hot reload
pnpm start        # Production server
pnpm db:generate  # Generate Drizzle migrations
pnpm db:migrate   # Run database migrations
pnpm db:seed      # Seed database with test data
pnpm db:studio    # Open Drizzle Studio
pnpm format       # Format code with Biome
```

## Project Structure

```
src/
├── db/
│   ├── schema/
│   │   ├── rooms.ts           # Room table schema
│   │   ├── questions.ts       # Questions table schema
│   │   ├── audio-chunks.ts    # Audio chunks with embeddings
│   │   └── index.ts           # Schema exports
│   ├── connection.ts          # Database connection
│   └── seed.ts                # Database seeding
├── http/
│   └── routes/
│       ├── create-room.ts
│       ├── get-rooms.ts
│       ├── create-question.ts
│       ├── get-room-questions.ts
│       └── upload-audio.ts
├── services/
│   └── gemini.ts              # Google Gemini AI integration
├── env.ts                      # Environment validation
└── server.ts                   # Main server
```

## Design Patterns

- **Type Safety** - Full TypeScript with Zod validation
- **Environment Variables** - Configuration via `.env` with validation
- **Database Migrations** - Version control for database schema
- **Code Formatting** - Biome for consistency
- **RESTful API** - REST pattern for HTTP endpoints
- **Vector Search** - Semantic search with embeddings
- **AI Integration** - Automatic audio transcription with Gemini
- **Dependency Injection** - Modular service architecture

## AI Integration

### Google Gemini AI
- **Model**: `gemini-2.5-flash` for transcription and answer generation
- **Embeddings**: `text-embedding-004` (768 dimensions) for semantic search
- **Audio Transcription**: Automatic conversion of audio to text in Portuguese
- **Answer Generation**: Context-based answers from transcriptions
- **Vector Search**: PostgreSQL + pgvector for semantic similarity

### Audio Processing Flow
1. Client uploads audio chunk (WebM format)
2. Server receives audio via multipart/form-data
3. Audio is sent to Gemini for transcription
4. Transcription text is converted to embeddings (768-dimensional vector)
5. Embeddings are stored in PostgreSQL with pgvector
6. When a question is asked, semantic search finds relevant context
7. Gemini generates answer based on found context

## Database Schema

### Rooms Table
```typescript
{
  id: uuid (primary key)
  name: text
  description: text
  createdAt: timestamp
}
```

### Questions Table
```typescript
{
  id: uuid (primary key)
  roomId: uuid (foreign key -> rooms.id)
  question: text
  answer: text (nullable)
  createdAt: timestamp
}
```

### Audio Chunks Table
```typescript
{
  id: uuid (primary key)
  roomId: uuid (foreign key -> rooms.id)
  transcription: text
  embeddings: vector(768)
  createdAt: timestamp
}
```

## Environment Variables

```env
PORT=3333
DATABASE_URL="postgresql://docker:docker@localhost:5432/agents"
GEMINI_API_KEY="your_gemini_api_key"
```

## Docker Configuration

The project includes Docker Compose configuration for PostgreSQL with pgvector:

```yaml
services:
  postgres:
    image: pgvector/pgvector:pg17
    ports:
      - "5432:5432"
    environment:
      POSTGRES_USER: docker
      POSTGRES_PASSWORD: docker
      POSTGRES_DB: agents
```

## Features

- Room management (CRUD)
- Question system with AI-generated answers
- Audio upload and transcription
- Vector embeddings for semantic search
- Context-based answer generation
- CORS enabled for development
- Type-safe database queries with Drizzle ORM
- Request validation with Zod
- Database migrations and seeding
- Health check endpoint

## Dependencies

### Production
- `@fastify/cors` - CORS support
- `@fastify/multipart` - File upload handling
- `@google/genai` - Google Gemini AI SDK
- `drizzle-orm` - Type-safe ORM
- `fastify` - Web framework
- `fastify-type-provider-zod` - Zod integration for Fastify
- `postgres` - PostgreSQL client
- `zod` - Schema validation

### Development
- `@biomejs/biome` - Linter and formatter
- `@types/node` - Node.js type definitions
- `drizzle-kit` - Migration toolkit
- `drizzle-seed` - Database seeding
- `typescript` - TypeScript compiler
- `ultracite` - Biome configuration preset

## Testing

The database can be seeded with test data:

```bash
pnpm db:seed
```

This will create:
- 5 sample rooms with generated names and descriptions
- 20 sample questions distributed across rooms

## Performance

- **Fastify** provides excellent performance with low overhead
- **Drizzle ORM** generates optimized SQL queries
- **pgvector** enables efficient vector similarity search
- **Connection pooling** for database optimization

## Notes

- Audio files should be in WebM format for best compatibility
- The vector dimension is fixed at 768 (Gemini embedding size)
- Database seeding excludes the `audio_chunks` table (vector type not supported by drizzle-seed)
- CORS is configured for `http://localhost:5173` (frontend development server)

---

Part of the **NLW Agents** monorepo managed by Turborepo and pnpm.
