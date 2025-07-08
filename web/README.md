# NLW Agents

Um projeto desenvolvido durante o evento NLW (Next Level Week) da Rocketseat.

## 🚀 Tecnologias Utilizadas

### Frontend
- **React 19.1.0** - Biblioteca principal para construção da interface
- **TypeScript** - Superset do JavaScript com tipagem estática
- **Vite** - Build tool e bundler moderno
- **React Router DOM** - Roteamento para aplicações React

### Styling
- **Tailwind CSS 4.1.11** - Framework CSS utility-first
- **Radix UI** - Componentes primitivos acessíveis
- **Lucide React** - Biblioteca de ícones
- **Shadcn/ui** - Sistema de componentes baseado em Radix UI

### Utilitários
- **TanStack Query** - Gerenciamento de estado assíncrono
- **Class Variance Authority** - Utilitário para variações de classes CSS
- **clsx & tailwind-merge** - Utilitários para manipulação de classes CSS

### Ferramentas de Desenvolvimento
- **Biome** - Linter e formatter JavaScript/TypeScript
- **Ultracite** - Configuração base para Biome

## 📁 Estrutura do Projeto

```
src/
├── components/
│   └── ui/          # Componentes UI reutilizáveis
├── lib/             # Utilitários e configurações
├── pages/           # Páginas da aplicação
├── app.tsx          # Componente principal
├── main.tsx         # Ponto de entrada
└── index.css        # Estilos globais
```

## 🛠️ Padrões de Projeto

- **Component Composition** - Uso de Radix UI e Shadcn/ui para componentes compostos
- **Atomic Design** - Organização dos componentes UI
- **Path Mapping** - Alias `@/` para facilitar imports
- **CSS-in-JS** - Utility-first com Tailwind CSS

## ⚙️ Setup e Configuração

### Pré-requisitos
- Node.js (versão 18 ou superior)
- npm ou yarn

### Instalação

1. Clone o repositório
2. Instale as dependências:
```bash
npm install
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

## 🔧 Configurações Técnicas

- **TSConfig**: Configuração otimizada para Vite
- **Path Aliases**: `@/` aponta para `./src`
- **Biome**: Configuração com Ultracite preset
- **Tailwind**: Integração via plugin do Vite