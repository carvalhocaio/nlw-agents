# NLW Agents

API REST desenvolvida durante o evento NLW da Rocketseat para gerenciamento de salas.

## 🚀 Tecnologias

- **Node.js** - Runtime JavaScript
- **TypeScript** - Superset do JavaScript com tipagem estática
- **Fastify** - Framework web rápido e eficiente
- **Drizzle ORM** - ORM type-safe para TypeScript
- **PostgreSQL** - Banco de dados relacional
- **Zod** - Biblioteca de validação e parsing de schemas
- **Biome** - Linter e formatador de código

## 📋 Pré-requisitos

- Node.js 18+
- Docker e Docker Compose

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

- `GET /health` - Health check
- `GET /rooms` - Lista todas as salas

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