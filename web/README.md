# NLW Agents - Web

**Let me Ask** - A modern web application developed during Rocketseat's NLW (Next Level Week) event.

An AI-powered question and answer application where users can create rooms, ask questions, and receive AI-generated responses.

## Features

- **Create Rooms** - Create custom rooms to organize your questions
- **Room List** - View and quickly access recently created rooms
- **Question System** - Ask questions and receive AI-powered answers
- **Audio Recording** - Record questions via audio with automatic transcription
- **Real-time Answers** - Dynamic interface with loading states
- **Modern Interface** - Responsive design with dark theme
- **Intuitive Navigation** - Smooth routing between pages
- **Optimistic Updates** - Reactive interface without waiting for server response

## Technologies

### Frontend
- **React 19.2.0** - Main library for building the interface
- **TypeScript** - JavaScript superset with static typing
- **Vite** - Modern build tool and bundler
- **React Router DOM** - Routing for React applications

### Forms & Validation
- **React Hook Form** - Performant form management
- **Zod** - TypeScript-first schema validation
- **Hookform Resolvers** - Integration between React Hook Form and Zod

### Styling
- **Tailwind CSS 4.1.17** - Utility-first CSS framework
- **Radix UI** - Accessible primitive components
- **Lucide React** - Icon library
- **Shadcn/ui** - Component system based on Radix UI
- **tw-animate-css** - Animation extension for Tailwind

### Utilities
- **TanStack Query** - Async state management and caching
- **Day.js** - Date manipulation with PT-BR support
- **Class Variance Authority** - CSS class variations utility
- **clsx & tailwind-merge** - CSS class manipulation utilities

### Development Tools
- **Biome** - JavaScript/TypeScript linter and formatter
- **Ultracite** - Base configuration for Biome
- **@types/dom-speech-recognition** - Web Speech API typing
- **pnpm** - Fast, disk space efficient package manager

## Project Structure

```
src/
├── components/
│   ├── ui/                    # Reusable UI components (Shadcn/ui)
│   ├── create-room-form.tsx   # Room creation form
│   ├── question-form.tsx      # Question asking form
│   ├── question-item.tsx      # Component to display questions/answers
│   ├── question-list.tsx      # Room questions list
│   └── room-list.tsx          # Created rooms list
├── http/
│   ├── types/                 # TypeScript types for API
│   ├── use-create-room.ts     # Hook to create rooms
│   ├── use-rooms.ts           # Hook to list rooms
│   ├── use-create-question.ts # Hook to create questions
│   └── use-room-questions.ts  # Hook to list room questions
├── lib/
│   ├── dayjs.ts               # Day.js PT-BR configuration
│   └── utils.ts               # Utilities (cn function)
├── pages/
│   ├── create-room.tsx        # Home page with room creation
│   ├── room.tsx               # Room page with questions
│   └── record-room-audio.tsx  # Audio recording page
├── app.tsx                    # Main component with routing
├── main.tsx                   # Entry point
└── index.css                  # Global styles and theme
```

## Implemented Features

### Home Page (`/`)
- **Room Creation**: Form with validation for name and description
- **Room List**: View recent rooms with:
  - Creation date (relative)
  - Number of questions
  - Quick navigation to rooms

### Room Page (`/room/:roomId`)
- **Question Form**: Validation for 10-500 characters
- **Question List**: Dynamic view of all room questions
- **AI Answers**: Question and answer interface with:
  - Loading states with spinner
  - Conditional answer display
  - Relative timestamps
- **Navigation**: Back button and audio recording link
- **Optimistic Updates**: Reactive interface that updates immediately

### Recording Page (`/room/:roomId/audio`)
- **Audio Recording**: Microphone audio capture
- **Automatic Upload**: Upload in 5-second chunks
- **Recording Controls**: Start/pause recording
- **Support Verification**: Browser compatibility detection
- **Optimized Settings**:
  - Echo cancellation
  - Noise suppression
  - Sample rate 44.1kHz
  - Bitrate 64kbps

### Main Components
- **CreateRoomForm**: Form with React Hook Form + Zod
- **QuestionForm**: Question system with validation and states
- **QuestionItem**: Question/answer display with dynamic states
- **QuestionList**: Optimized list with TanStack Query
- **RoomList**: Dynamic list with automatic caching

## Design Patterns

- **Component Composition** - Use of Radix UI and Shadcn/ui for composite components
- **Atomic Design** - UI component organization
- **Custom Hooks** - Custom hooks for business logic (HTTP)
- **Optimistic Updates** - Optimistic updates in TanStack Query
- **Form Handling** - React Hook Form with Zod validation
- **Type Safety** - TypeScript with strict typing
- **Path Mapping** - Alias `@/` to facilitate imports
- **CSS-in-JS** - Utility-first with Tailwind CSS
- **State Management** - TanStack Query for async state
- **Media Capture** - Web APIs for audio recording
- **Error Handling** - Error handling in mutations

## Setup and Configuration

### Prerequisites
- Node.js (version 18 or higher)
- pnpm
- Backend server running at `http://localhost:3333`

### Installation

1. Install dependencies:
```bash
pnpm install
```

2. Start the development server:
```bash
pnpm dev
```

### Available Scripts

```bash
# Run in development mode
pnpm dev

# Build for production
pnpm build

# Preview production build
pnpm preview

# Format code
pnpm format
```

### Environment Configuration

The project uses:
- **Vite** as bundler with hot reload
- **Tailwind CSS** for styling
- **TypeScript** for typing
- **Biome** for linting and formatting
- **TanStack Query** for caching and synchronization

### API Endpoints

The application connects to the following endpoints:

```typescript
// List rooms
GET /rooms

// Create room
POST /rooms
Content-Type: application/json
{
  "name": "string",
  "description": "string"
}

// List questions from a room
GET /rooms/:roomId/questions

// Create question in a room
POST /rooms/:roomId/questions
Content-Type: application/json
{
  "question": "string"
}

// Upload audio to a room
POST /rooms/:roomId/audio
Content-Type: multipart/form-data
{
  "file": Blob // audio.webm file
}
```

### Component Structure

The project follows the **Shadcn/ui** pattern:
- Base components in `src/components/ui/`
- Configuration in `components.json`
- Base styles in `src/index.css`

## Design System

- **Base Color**: Zinc
- **CSS Variables**: Enabled
- **Style**: New York (Shadcn/ui)
- **Icons**: Lucide React
- **Theme**: Dark mode by default
- **Animations**: tw-animate-css integrated

## Technical Configuration

- **TSConfig**: Optimized configuration for Vite
- **Path Aliases**: `@/` points to `./src`
- **Biome**: Configuration with Ultracite preset
- **Tailwind**: Integration via Vite plugin
- **Strict Mode**: TypeScript with strict checks
- **Hot Reload**: Development with automatic reload

## Audio Features

### Audio Recording
- **MediaRecorder API**: Native browser recording
- **5-second Chunks**: Automatic upload every 5 seconds
- **WebM Format**: Web-optimized codec
- **Advanced Settings**:
  - Echo cancellation enabled
  - Active noise suppression
  - Sample rate: 44.1kHz
  - Audio bitrate: 64kbps

### Compatibility
- Automatic browser support verification
- Graceful fallback for unsupported browsers
- Responsive interface for different devices

## Performance and Optimizations

### TanStack Query
- **Smart Cache**: Reduces unnecessary API calls
- **Optimistic Updates**: Reactive interface without waiting for server
- **Background Refetch**: Automatic background synchronization
- **Error Boundaries**: Robust error handling

### Application State
- **Real-time Updates**: Interface updates in real-time
- **Loading States**: Visual indicators for all operations
- **Error Handling**: Automatic rollback on failure
- **Type Safety**: Complete end-to-end typing

## Dependencies

### Production
- `@hookform/resolvers` - Validation resolvers for React Hook Form
- `@radix-ui/react-label` - Accessible label component
- `@radix-ui/react-slot` - Component composition utility
- `@tailwindcss/vite` - Tailwind integration for Vite
- `@tanstack/react-query` - Async state management
- `class-variance-authority` - CSS class variants
- `clsx` - Class name utility
- `dayjs` - Date manipulation
- `lucide-react` - Icon library
- `react` - UI library
- `react-dom` - React DOM renderer
- `react-hook-form` - Form management
- `react-router-dom` - Routing
- `tailwind-merge` - Tailwind class merger
- `tailwindcss` - CSS framework
- `zod` - Schema validation

### Development
- `@biomejs/biome` - Linter and formatter
- `@types/dom-speech-recognition` - Speech API types
- `@types/node` - Node.js type definitions
- `@types/react` - React type definitions
- `@types/react-dom` - React DOM type definitions
- `@vitejs/plugin-react` - React plugin for Vite
- `tw-animate-css` - Tailwind animations
- `typescript` - TypeScript compiler
- `ultracite` - Biome configuration preset
- `vite` - Build tool

## 📝 Notes

- The application requires the backend server running at `http://localhost:3333`
- Audio recording works best in modern browsers (Chrome, Firefox, Edge)
- The interface is optimized for desktop but works on mobile devices
- Dark theme is the default and only theme currently implemented

---

Part of the **NLW Agents** monorepo managed by Turborepo and pnpm.
