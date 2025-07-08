# NLW Agents

Projeto desenvolvido durante o evento da **Rocketseat** para criação de uma aplicação web com sistema de salas.

## 🚀 Tecnologias

### Backend
- **Node.js** com TypeScript
- **Fastify** - Framework web
- **Drizzle ORM** - ORM para banco de dados
- **PostgreSQL** - Banco de dados
- **Docker** - Containerização

### Frontend
- **React** com TypeScript
- **Vite** - Build tool
- **TailwindCSS** - Estilização
- **React Router** - Roteamento
- **TanStack Query** - Gerenciamento de estado

## 📋 Pré-requisitos

- Node.js 18+
- Docker e Docker Compose
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
docker-compose up -d
```

### 5. Execute as migrações
```bash
cd server
make migrate
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
├── server/          # Backend da aplicação
│   ├── src/
│   │   ├── db/      # Configuração do banco
│   │   ├── http/    # Rotas da API
│   │   └── ...
│   └── docker/      # Configuração Docker
└── web/             # Frontend da aplicação
    ├── src/
    │   ├── pages/   # Páginas da aplicação
    │   ├── components/ # Componentes reutilizáveis
    │   └── ...
    └── public/
```

## 🎯 Funcionalidades

- ✅ Listagem de salas
- ✅ Visualização de detalhes da sala
- 🔄 Criação de salas (em desenvolvimento)

---

Desenvolvido durante o evento da Rocketseat