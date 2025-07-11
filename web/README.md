# NLW Agents

**Let me Ask** - Um projeto desenvolvido durante o evento NLW (Next Level Week) da Rocketseat.

Uma aplicação de perguntas e respostas com inteligência artificial, onde os usuários podem criar salas, fazer perguntas e receber respostas geradas por IA.

## ✨ Funcionalidades

- 🏠 **Criação de Salas** - Crie salas personalizadas para organizar suas perguntas
- 📋 **Lista de Salas** - Visualize e acesse rapidamente salas criadas recentemente
- ❓ **Sistema de Perguntas** - Faça perguntas e receba respostas da IA
- 🎙️ **Gravação de Áudio** - Grave perguntas por áudio com transcrição automática
- 🤖 **Respostas em Tempo Real** - Interface dinâmica com estados de carregamento
- 🎨 **Interface Moderna** - Design responsivo e tema dark
- 📱 **Navegação Intuitiva** - Roteamento fluido entre páginas
- ⚡ **Atualizações Otimistas** - Interface reativa sem esperar resposta do servidor

## 🚀 Tecnologias Utilizadas

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
- **@types/dom-speech-recognition** - Tipagem para Web Speech API

## 📁 Estrutura do Projeto

```
src/
├── components/
│   ├── ui/                    # Componentes UI reutilizáveis (Shadcn/ui)
│   ├── create-room-form.tsx   # Formulário de criação de salas
│   ├── question-form.tsx      # Formulário para fazer perguntas
│   ├── question-item.tsx      # Componente para exibir perguntas/respostas
│   ├── question-list.tsx      # Lista de perguntas da sala
│   └── room-list.tsx          # Lista de salas criadas
├── http/
│   ├── types/                 # Tipos TypeScript para API
│   ├── use-create-room.ts     # Hook para criar salas
│   ├── use-rooms.ts           # Hook para listar salas
│   ├── use-create-question.ts # Hook para criar perguntas
│   └── use-room-questions.ts  # Hook para listar perguntas da sala
├── lib/
│   ├── dayjs.ts               # Configuração Day.js PT-BR
│   └── utils.ts               # Utilitários (cn function)
├── pages/
│   ├── create-room.tsx        # Página inicial com criação de salas
│   ├── room.tsx               # Página da sala com perguntas
│   └── record-room-audio.tsx  # Página de gravação de áudio
├── app.tsx                    # Componente principal com roteamento
├── main.tsx                   # Ponto de entrada
└── index.css                  # Estilos globais e tema
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
- **Lista de Perguntas**: Visualização dinâmica de todas as perguntas da sala
- **Respostas da IA**: Interface para perguntas e respostas com:
  - Estados de carregamento com spinner
  - Exibição condicional de respostas
  - Timestamps relativos
- **Navegação**: Botão de voltar e link para gravação de áudio
- **Atualizações Otimistas**: Interface reativa que atualiza imediatamente

### 🎙️ Página de Gravação (`/room/:roomId/audio`)
- **Gravação de Áudio**: Captura de áudio do microfone
- **Upload Automático**: Envio em chunks de 5 segundos
- **Controles de Gravação**: Iniciar/pausar gravação
- **Verificação de Suporte**: Detecção de compatibilidade do navegador
- **Configurações Otimizadas**: 
  - Cancelamento de eco
  - Supressão de ruído
  - Taxa de amostragem 44.1kHz
  - Bitrate 64kbps

### 🔧 Componentes Principais
- **CreateRoomForm**: Formulário com React Hook Form + Zod
- **QuestionForm**: Sistema de perguntas com validação e estados
- **QuestionItem**: Exibição de perguntas/respostas com estados dinâmicos
- **QuestionList**: Lista otimizada com TanStack Query
- **RoomList**: Lista dinâmica com cache automático

## 🛠️ Padrões de Projeto

- **Component Composition** - Uso de Radix UI e Shadcn/ui para componentes compostos
- **Atomic Design** - Organização dos componentes UI
- **Custom Hooks** - Hooks personalizados para lógica de negócio (HTTP)
- **Optimistic Updates** - Atualizações otimistas no TanStack Query
- **Form Handling** - React Hook Form com validação Zod
- **Type Safety** - TypeScript com tipagem estrita
- **Path Mapping** - Alias `@/` para facilitar imports
- **CSS-in-JS** - Utility-first com Tailwind CSS
- **State Management** - TanStack Query para estado assíncrono
- **Media Capture** - Web APIs para gravação de áudio
- **Error Handling** - Tratamento de erros em mutations

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

// Listar perguntas de uma sala
GET /rooms/:roomId/questions

// Criar pergunta em uma sala
POST /rooms/:roomId/questions
Content-Type: application/json
{
  "question": "string"
}

// Upload de áudio para uma sala
POST /rooms/:roomId/audio
Content-Type: multipart/form-data
{
  "file": Blob // arquivo audio.webm
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

## 🚀 Próximos Passos

- [x] ✅ **Implementar gravação de áudio**
- [x] ✅ **Adicionar sistema de perguntas completo**
- [x] ✅ **Implementar atualizações otimistas**
- [x] ✅ **Criar interface para respostas da IA**
- [ ] 🔄 **Adicionar WebSocket para real-time**
- [ ] 📱 **Melhorar responsividade mobile**
- [ ] 🔐 **Implementar sistema de autenticação**
- [ ] 🧪 **Adicionar testes unitários**
- [ ] 🎨 **Implementar modo claro/escuro**

## 🎙️ Funcionalidades de Áudio

### Gravação de Áudio
- **MediaRecorder API**: Gravação nativa do navegador
- **Chunks de 5s**: Upload automático a cada 5 segundos
- **Formato WebM**: Codec otimizado para web
- **Configurações Avançadas**:
  - Echo cancellation habilitado
  - Noise suppression ativo
  - Sample rate: 44.1kHz
  - Audio bitrate: 64kbps

### Compatibilidade
- Verificação automática de suporte do navegador
- Fallback graceful para navegadores sem suporte
- Interface responsiva para diferentes dispositivos

## ⚡ Performance e Otimizações

### TanStack Query
- **Cache Inteligente**: Reduz chamadas desnecessárias à API
- **Optimistic Updates**: Interface reativa sem esperar servidor
- **Background Refetch**: Sincronização automática em background
- **Error Boundaries**: Tratamento robusto de erros

### Estado da Aplicação
- **Real-time Updates**: Interface atualiza em tempo real
- **Loading States**: Indicadores visuais para todas as operações
- **Error Handling**: Rollback automático em caso de falha
- **Type Safety**: Tipagem completa end-to-end