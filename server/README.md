# NLW Agents

API REST desenvolvida durante o evento NLW da Rocketseat para gerenciamento de salas e sistema de
perguntas em tempo real.

## 🚀 Tecnologias

- **Node.js** - Runtime JavaScript
- **TypeScript** - Superset do JavaScript com tipagem estática
- **Fastify** - Framework web rápido e eficiente
- **Drizzle ORM** - ORM type-safe para TypeScript
- **PostgreSQL** - Banco de dados relacional com extensão pgvector
- **Zod** - Biblioteca de validação e parsing de schemas
- **Biome** - Linter e formatador de código
- **WebSocket** - Comunicação em tempo real
- **Google Gemini AI** - IA para transcrição de áudio e geração de embeddings
- **Vector Database** - Busca semântica com embeddings

## 📋 Pré-requisitos

- Node.js 18+
- Docker e Docker Compose
- Chave da API do Google Gemini

## 🔧 Setup

1. **Clone o repositório**
```bash
git clone <url-do-repositorio>
cd server
```

2. **Instale as dependências**
```bash
npm install
```

3. **Configure as variáveis de ambiente**
```bash
cp .env-example .env
# Adicione sua chave da API do Google Gemini no arquivo .env
# GEMINI_API_KEY=sua_chave_aqui
```

4. **Inicie o banco de dados**
```bash
docker-compose up -d
```

5. **Execute as migrações**
```bash
make migrate
```

6. **Popule o banco (opcional)**
```bash
make seed
```

## 🚀 Execução

### Desenvolvimento
```bash
npm run dev
```

### Produção
```bash
npm start
```

## 📡 Endpoints

### Salas
- `GET /health` - Health check
- `GET /rooms` - Lista todas as salas
- `POST /rooms` - Cria uma nova sala
- `GET /rooms/:roomId` - Busca uma sala específica

### Perguntas
- `POST /rooms/:roomId/messages` - Cria uma nova pergunta
- `GET /rooms/:roomId/messages` - Lista perguntas da sala
- `PATCH /rooms/:roomId/messages/:messageId/react` - Adiciona reação a pergunta
- `DELETE /rooms/:roomId/messages/:messageId/react` - Remove reação da pergunta
- `PATCH /rooms/:roomId/messages/:messageId/answer` - Marca pergunta como respondida

### Áudio
- `POST /rooms/:roomId/audio` - Upload e transcrição de áudio com IA

## 🛠️ Scripts Disponíveis

- `npm run dev` - Servidor em modo desenvolvimento
- `npm run db:seed` - Popula o banco com dados de teste
- `make generate` - Gera migrações do Drizzle
- `make migrate` - Executa migrações
- `make studio` - Abre o Drizzle Studio
- `make format` - Formata código com Biome

## 🏗️ Padrões Utilizados

- **Type Safety** - TypeScript com validação Zod
- **Environment Variables** - Configuração via `.env`
- **Database Migrations** - Controle de versão do schema
- **Code Formatting** - Biome para consistência
- **WebSocket Integration** - Comunicação em tempo real
- **RESTful API** - Padrão REST para endpoints HTTP
- **Vector Search** - Busca semântica com embeddings
- **AI Integration** - Transcrição automática de áudio com Gemini