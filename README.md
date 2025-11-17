# NLW Agents

**Let me Ask** - Projeto desenvolvido durante o evento da **Rocketseat** para criação de uma 
aplicação web completa com sistema de salas e perguntas com IA.

Uma aplicação de perguntas e respostas com inteligência artificial, onde os usuários podem criar 
salas personalizadas, fazer perguntas e receber respostas geradas por IA.

## 🚀 Tecnologias

### Backend
- **Node.js** com TypeScript
- **Fastify** - Framework web performático
- **Drizzle ORM** - ORM type-safe para TypeScript
- **PostgreSQL** com pgvector - Banco de dados com suporte a vetores
- **Google Gemini AI** - IA para transcrição e geração de respostas
- **Zod** - Validação de schemas
- **Docker** - Containerização

### Frontend
- **React 19** com TypeScript
- **Vite** - Build tool moderno
- **TailwindCSS 4** - Framework CSS utility-first
- **React Router DOM** - Roteamento com suporte a gravação de áudio
- **TanStack Query** - Gerenciamento de estado assíncrono
- **React Hook Form** - Gerenciamento de formulários
- **Shadcn/ui** - Sistema de componentes
- **Web APIs** - MediaRecorder para gravação de áudio
- **Lucide React** - Ícones

## 📋 Pré-requisitos

- Node.js 18+
- Docker e Docker Compose
- **Chave da API do Google Gemini** (para IA)
- npm ou yarn

## 🔧 Instalação

### 1. Clone o repositório
```bash
git clone <url-do-repositorio>
cd nlw-agents
```

### 2. Configure o backend
```bash
cd server
npm install
```

### 3. Configure o frontend
```bash
cd web
npm install
```

### 4. Configure o banco de dados
```bash
cd server
docker compose up -d
```

### 5. Execute as migrações
```bash
cd server
make migrate
```

### 6. Popule o banco (opcional)
```bash
cd server
make seed
```

## 🏃‍♂️ Executando o projeto

### Backend
```bash
cd server
make dev
```

### Frontend
```bash
cd web
npm run dev
```

A aplicação estará disponível em:
- **Frontend**: http://localhost:5173
- **Backend**: http://localhost:3333

## 📁 Estrutura do Projeto

```
nlw-agents/
├── server/                    # Backend da aplicação
│   ├── src/
│   │   ├── db/
│   │   │   ├── schema/        # Esquemas do banco (rooms, questions, audio-chunks)
│   │   │   ├── migrations/    # Migrações do banco
│   │   │   └── connection.ts  # Conexão com PostgreSQL + pgvector
│   │   ├── http/
│   │   │   └── routes/        # Rotas da API REST (rooms, questions, audio)
│   │   ├── services/
│   │   │   └── gemini.ts      # Integração com Google Gemini AI
│   │   ├── env.ts             # Configuração de ambiente
│   │   └── server.ts          # Servidor principal
│   ├── docker/                # Configuração Docker
│   └── docker-compose.yml     # PostgreSQL + pgvector
└── web/                       # Frontend da aplicação
    ├── src/
    │   ├── components/
    │   │   ├── ui/            # Componentes Shadcn/ui
    │   │   ├── create-room-form.tsx
    │   │   ├── question-form.tsx
    │   │   ├── question-item.tsx
    │   │   └── room-list.tsx
    │   ├── http/              # Hooks e tipos para API
    │   ├── lib/               # Utilitários (dayjs, utils)
    │   ├── pages/             # Páginas da aplicação
    │   │   ├── create-room.tsx
    │   │   ├── room.tsx
    │   │   └── record-room-audio.tsx # Página de gravação
    │   └── app.tsx            # Roteamento principal
    └── public/
```

## 🎯 Funcionalidades Implementadas

### ✅ Sistema de Salas
- **Criação de salas** com nome e descrição
- **Listagem de salas** com informações resumidas
- **Navegação entre salas** com roteamento dinâmico
- **Contador de perguntas** por sala
- **Data de criação** com formatação relativa

### ✅ Sistema de Perguntas
- **Formulário de perguntas** com validação (10-500 caracteres)
- **Interface de perguntas e respostas** com IA
- **Estados visuais** para carregamento de respostas
- **Histórico de perguntas** organizadas por data
- **Geração de respostas** com Google Gemini AI

### ✅ Sistema de Áudio e IA
- **Gravação de áudio** em tempo real via Web APIs
- **Transcrição automática** com Google Gemini AI
- **Upload em chunks** de 5 segundos para processamento
- **Embeddings vetoriais** para busca semântica
- **Busca contextual** em transcrições de áudio
- **Respostas baseadas em contexto** das aulas gravadas

### ✅ Interface Moderna
- **Design System** completo com Shadcn/ui
- **Tema dark** por padrão
- **Componentes reutilizáveis** (Cards, Buttons, Forms)
- **Responsividade** total
- **Animações** e transições suaves

### ✅ API REST Completa
- **CRUD de salas** (Create, Read)
- **CRUD de perguntas** (Create, Read)
- **Upload e processamento de áudio** com IA
- **Busca semântica** com embeddings vetoriais
- **Validação** com Zod
- **Tipagem** TypeScript end-to-end
- **CORS** configurado para desenvolvimento

## 📡 Endpoints da API

### Salas
- `GET /health` - Health check
- `GET /rooms` - Lista todas as salas com contador de perguntas
- `POST /rooms` - Cria uma nova sala

### Perguntas
- `GET /rooms/:roomId/questions` - Lista perguntas de uma sala
- `POST /rooms/:roomId/questions` - Cria nova pergunta

### Áudio e IA
- `POST /rooms/:roomId/audio` - Upload de áudio com transcrição automática
- **Processamento**: Transcrição → Embeddings → Armazenamento vetorial

## �️ Scripts Disponíveis

### Backend
```bash
npm run dev          # Servidor em desenvolvimento
npm run start        # Servidor em produção
npm run db:seed      # Popula banco com dados de teste
make generate        # Gera migrações
make migrate         # Executa migrações
make studio         # Abre Drizzle Studio
make format         # Formata código
```

### Frontend
```bash
npm run dev         # Servidor de desenvolvimento
npm run build       # Build para produção
npm run preview     # Preview da build
make format         # Formata código
```

## 🔧 Configuração do Ambiente

### Variáveis de Ambiente (Backend)
```env
# server/.env
PORT=3333
DATABASE_URL="postgresql://docker:docker@localhost:5432/agents"
GEMINI_API_KEY="sua_chave_da_api_do_gemini"
```

### Banco de Dados
O projeto utiliza PostgreSQL com a extensão pgvector para suporte a vetores de IA:
- **Imagem**: `pgvector/pgvector:pg17`
- **Usuário**: `docker`
- **Senha**: `docker`
- **Database**: `agents`
- **Porta**: `5432`

## 🎨 Design System

### Componentes UI
- **Shadcn/ui** com tema personalizado
- **Radix UI** como base primitiva
- **Tailwind CSS** para estilização
- **Lucide React** para ícones consistentes

### Tema e Cores
- **Tema dark** por padrão
- **Paleta**: Zinc como cor base
- **Tipografia**: Sistema de fontes otimizado
- **Espacamento**: Grid system do Tailwind

## 📱 Páginas da Aplicação

### 🏠 Página Inicial (`/`)
- **Grid layout** com duas colunas
- **Formulário de criação** de salas (esquerda)
- **Lista de salas** recentes (direita)
- **Navegação rápida** para salas existentes

### 🎯 Página da Sala (`/room/:roomId`)
- **Header** com navegação e botão de áudio
- **Formulário de perguntas** com validação
- **Lista de perguntas** e respostas
- **Estados de carregamento** para IA
- **Link para gravação** de áudio integrado

### 🎙️ Página de Gravação (`/room/:roomId/audio`)
- **Gravação de áudio** em tempo real
- **Controles de gravação** (iniciar/pausar)
- **Upload automático** em chunks de 5 segundos
- **Verificação de compatibilidade** do navegador
- **Processamento com IA** (transcrição + embeddings)

## 🔄 Fluxo de Dados

1. **Criação de sala**: Form → API → Database → Atualização da lista
2. **Listagem**: Cache TanStack Query → Renderização otimizada
3. **Perguntas**: Validação → API → Database → Interface de resposta
4. **Gravação de áudio**: MediaRecorder → Chunks → Upload → Gemini AI → Transcrição → Embeddings → PostgreSQL
5. **Respostas contextuais**: Pergunta → Busca semântica → Contexto → Gemini AI → Resposta
6. **Navegação**: React Router → Lazy loading → SEO otimizado

## 🤖 Integração com IA

### Google Gemini AI
- **Modelo**: `gemini-2.5-flash` para transcrição e respostas
- **Embeddings**: `text-embedding-004` para busca semântica
- **Transcrição**: Conversão de áudio para texto em português
- **Geração de respostas**: Baseada no contexto das transcrições
- **Busca vetorial**: PostgreSQL + pgvector para busca semântica

### Fluxo de Processamento de Áudio
1. **Captura**: MediaRecorder API (WebM, 64kbps)
2. **Upload**: Chunks de 5s via FormData
3. **Transcrição**: Google Gemini AI
4. **Embeddings**: Vetorização do texto
5. **Armazenamento**: PostgreSQL com pgvector
6. **Busca**: Similaridade semântica para respostas contextuais
