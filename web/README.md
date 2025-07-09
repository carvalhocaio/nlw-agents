# NLW Agents

**Let me Ask** - Um projeto desenvolvido durante o evento NLW (Next Level Week) da Rocketseat.

Uma aplicação de perguntas e respostas com inteligência artificial, onde os usuários podem criar salas, fazer perguntas e receber respostas geradas por IA.

## ✨ Funcionalidades

- 🏠 **Criação de Salas** - Crie salas personalizadas para organizar suas perguntas
- � **Lista de Salas** - Visualize e acesse rapidamente salas criadas recentemente
- ❓ **Sistema de Perguntas** - Faça perguntas e receba respostas da IA
- 🎨 **Interface Moderna** - Design responsivo e tema dark
- 📱 **Navegação Intuitiva** - Roteamento fluido entre páginas

## �🚀 Tecnologias Utilizadas

### Frontend
- **React 19.1.0** - Biblioteca principal para construção da interface
- **TypeScript** - Superset do JavaScript com tipagem estática
- **Vite** - Build tool e bundler moderno
- **React Router DOM** - Roteamento para aplicações React

### Formulários & Validação
- **React Hook Form** - Gerenciamento de formulários performático
- **Zod** - Validação de esquemas TypeScript-first
- **Hookform Resolvers** - Integração entre React Hook Form e Zod

### Styling
- **Tailwind CSS 4.1.11** - Framework CSS utility-first
- **Radix UI** - Componentes primitivos acessíveis
- **Lucide React** - Biblioteca de ícones
- **Shadcn/ui** - Sistema de componentes baseado em Radix UI
- **tw-animate-css** - Extensão de animações para Tailwind

### Utilitários
- **TanStack Query** - Gerenciamento de estado assíncrono e cache
- **Day.js** - Manipulação de datas com suporte a PT-BR
- **Class Variance Authority** - Utilitário para variações de classes CSS
- **clsx & tailwind-merge** - Utilitários para manipulação de classes CSS

### Ferramentas de Desenvolvimento
- **Biome** - Linter e formatter JavaScript/TypeScript
- **Ultracite** - Configuração base para Biome

## 📁 Estrutura do Projeto

```
src/
├── components/
│   ├── ui/                    # Componentes UI reutilizáveis (Shadcn/ui)
│   ├── create-room-form.tsx   # Formulário de criação de salas
│   ├── question-form.tsx      # Formulário para fazer perguntas
│   ├── question-item.tsx      # Componente para exibir perguntas/respostas
│   └── room-list.tsx          # Lista de salas criadas
├── http/
│   ├── types/                 # Tipos TypeScript para API
│   ├── use-create-room.ts     # Hook para criar salas
│   └── use-rooms.ts           # Hook para listar salas
├── lib/
│   ├── dayjs.ts              # Configuração Day.js PT-BR
│   └── utils.ts              # Utilitários (cn function)
├── pages/
│   ├── create-room.tsx       # Página inicial com criação de salas
│   └── room.tsx              # Página da sala com perguntas
├── app.tsx                   # Componente principal com roteamento
├── main.tsx                  # Ponto de entrada
└── index.css                 # Estilos globais e tema
```

## 🎯 Funcionalidades Implementadas

### 🏠 Página Inicial (`/`)
- **Criação de Salas**: Formulário com validação para nome e descrição
- **Lista de Salas**: Visualização de salas recentes com:
  - Data de criação (relativa)
  - Número de perguntas
  - Navegação rápida para salas

### 🏠 Página da Sala (`/room/:roomId`)
- **Formulário de Perguntas**: Validação de 10-500 caracteres
- **Visualização de Respostas**: Interface para perguntas e respostas da IA
- **Navegação**: Botão de voltar e link para gravação de áudio
- **Estados de Loading**: Indicadores visuais para geração de respostas

### 🔧 Componentes Principais
- **CreateRoomForm**: Formulário com React Hook Form + Zod
- **QuestionForm**: Sistema de perguntas com validação
- **QuestionItem**: Exibição de perguntas/respostas com estados
- **RoomList**: Lista dinâmica com TanStack Query

## 🛠️ Padrões de Projeto

- **Component Composition** - Uso de Radix UI e Shadcn/ui para componentes compostos
- **Atomic Design** - Organização dos componentes UI
- **Custom Hooks** - Hooks personalizados para lógica de negócio (HTTP)
- **Form Handling** - React Hook Form com validação Zod
- **Type Safety** - TypeScript com tipagem estrita
- **Path Mapping** - Alias `@/` para facilitar imports
- **CSS-in-JS** - Utility-first com Tailwind CSS
- **State Management** - TanStack Query para estado assíncrono

## ⚙️ Setup e Configuração

### Pré-requisitos
- Node.js (versão 18 ou superior)
- npm ou yarn
- Servidor backend rodando em `http://localhost:3333`

### Instalação

1. Clone o repositório
2. Instale as dependências:
```bash
npm install
```

3. Inicie o servidor de desenvolvimento:
```bash
npm run dev
```

### Scripts Disponíveis

```bash
# Executar em modo de desenvolvimento
npm run dev

# Build para produção
npm run build

# Preview da build de produção
npm run preview

# Formatar código
make format
```

### Configuração do Ambiente

O projeto utiliza:
- **Vite** como bundler com hot reload
- **Tailwind CSS** para estilização
- **TypeScript** para tipagem
- **Biome** para linting e formatação
- **TanStack Query** para cache e sincronização

### API Endpoints

A aplicação se conecta com os seguintes endpoints:

```typescript
// Listar salas
GET /rooms

// Criar sala
POST /rooms
Content-Type: application/json
{
  "name": "string",
  "description": "string"
}
```

### Estrutura de Componentes

O projeto segue o padrão do **Shadcn/ui**:
- Componentes base em `src/components/ui/`
- Configuração em `components.json`
- Estilos base em `src/index.css`

## 🎨 Design System

- **Base Color**: Zinc
- **CSS Variables**: Habilitadas
- **Style**: New York (Shadcn/ui)
- **Icons**: Lucide React
- **Theme**: Dark mode por padrão
- **Animations**: tw-animate-css integrado

## 🔧 Configurações Técnicas

- **TSConfig**: Configuração otimizada para Vite
- **Path Aliases**: `@/` aponta para `./src`
- **Biome**: Configuração com Ultracite preset
- **Tailwind**: Integração via plugin do Vite
- **Strict Mode**: TypeScript com verificações rigorosas
- **Hot Reload**: Desenvolvimento com recarga automática