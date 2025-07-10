[![Node.js](https://img.shields.io/badge/Node.js-339933?logo=node.js&logoColor=fff&style=flat)](https://nodejs.org/)
[![Fastify](https://img.shields.io/badge/Fastify-000000?logo=fastify&logoColor=white&style=flat)](https://www.fastify.io/)
[![Drizzle ORM](https://img.shields.io/badge/Drizzle%20ORM-0A7EA3?style=flat)](https://orm.drizzle.team/)
[![Zod](https://img.shields.io/badge/Zod-3A7AFE?style=flat)](https://zod.dev/)
[![Biome](https://img.shields.io/badge/Biome-2D2A2E?style=flat)](https://biomejs.dev/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=fff&style=flat)](https://www.postgresql.org/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=fff&style=flat)](https://www.docker.com/)

# Let Me Ask

Desenvolvido por **Emmanuel Oliveira | OFS**

## 📑 Menu

- [Sobre o Projeto](#sobre-o-projeto)
- [Tecnologias e Bibliotecas](#tecnologias-e-bibliotecas)
- [Padrões de Projeto](#padrões-de-projeto)
- [Variáveis de Ambiente](#variáveis-de-ambiente)
- [Configuração e Setup](#configuração-e-setup)
- [Scripts Disponíveis](#scripts-disponíveis)
- [Exemplos de Uso da API](#exemplos-de-uso-da-api)
- [Créditos](#créditos)

## Sobre o Projeto

O **Let Me Ask** é uma API backend para gerenciamento de salas (rooms), perguntas e transcrição de áudios, desenvolvida em Node.js com Fastify, Drizzle ORM, PostgreSQL e integração com a API Gemini da Google para IA generativa e embeddings.

## Tecnologias e Bibliotecas

- **Node.js** (TypeScript)
- **Fastify**: Framework web rápido e eficiente
- **@fastify/cors**: Suporte a CORS
- **@fastify/multipart**: Upload de arquivos (áudio)
- **fastify-type-provider-zod**: Tipagem e validação de schemas com Zod
- **Zod**: Validação de dados e variáveis de ambiente
- **Drizzle ORM**: ORM moderno para PostgreSQL
- **drizzle-kit**: Migrations e geração de schemas
- **drizzle-seed**: Seed de dados para o banco
- **PostgreSQL**: Banco de dados relacional com extensão pgvector
- **pgvector**: Suporte a embeddings vetoriais
- **@google/genai**: Integração com Gemini API (IA generativa)
- **Biome**: Linter e formatter
- **Ultracite**: Utilitários de desenvolvimento
- **TypeScript**: Tipagem estática

## Padrões de Projeto

- **Type-safe**: Uso extensivo de TypeScript e Zod para validação e tipagem
- **Modularização**: Separação clara entre rotas, banco de dados, serviços e configuração
- **Environment-driven**: Configuração via variáveis de ambiente validadas
- **Migrations e Seeds**: Controle de versão do banco e popularização de dados
- **Integração com IA**: Uso de embeddings e geração de respostas contextuais via Gemini

## Variáveis de Ambiente

Crie um arquivo `.env` na raiz com as seguintes variáveis:

```
PORT=3333
DATABASE_URL=postgresql://usuario:senha@localhost:5432/agents
GEMINI_API_KEY=sua-chave-gemini
```

> **Dica:** Para rodar com Docker, use as credenciais do docker-compose.

## Configuração e Setup

### 1. Clone o repositório

```bash
git clone https://github.com/emmanuelmarcosdeoliveira/agents-api
cd agents-api
```

### 2. Instale as dependências

```bash
npm install
```

### 3. Configure o banco de dados

- **Via Docker:**

```bash
docker-compose up -d
```

O banco estará disponível em `postgresql://docker:docker@localhost:5432/agents`.

- **Manual:**
  - Instale o PostgreSQL e a extensão `pgvector`.
  - Crie o banco e configure o usuário.

### 4. Configure as variáveis de ambiente

Veja o exemplo acima e ajuste conforme seu ambiente.

### 5. Rode as migrations e seeds

```bash
# Gere as migrations (se necessário)
npx drizzle-kit generate
# Aplique as migrations
npx drizzle-kit migrate
# Popule o banco com dados de exemplo
npm run db:seed
```

### 6. Inicie o servidor

```bash
npm run dev
```

### 7. Lint e Format

```bash
npx biome check .
npx biome format .
```

## Scripts Disponíveis

- `npm run dev` — Inicia o servidor em modo desenvolvimento com hot reload
- `npm start` — Inicia o servidor em modo produção
- `npm run db:seed` — Popula o banco de dados com dados de exemplo
- `npx drizzle-kit generate` — Gera migrations a partir dos schemas
- `npx drizzle-kit migrate` — Aplica as migrations

## Exemplos de Uso da API

- **Health check**
  ```http
  GET http://localhost:3333/health
  ```
- **Listar salas**
  ```http
  GET http://localhost:3333/rooms
  ```
- **Criar sala**
  ```http
  POST http://localhost:3333/rooms
  Content-Type: application/json
  {
    "name": "Sala de teste",
    "description": "Essa é uma sala de testes"
  }
  ```
- **Listar perguntas de uma sala**
  ```http
  GET http://localhost:3333/rooms/{roomId}/questions
  ```
- **Criar pergunta em uma sala**
  ```http
  POST http://localhost:3333/rooms/{roomId}/questions
  Content-Type: application/json
  {
    "question": "O que é Vue.js e a sua diferença em relação ao Angular?"
  }
  ```
- **Upload de áudio para uma sala**
  ```http
  POST http://localhost:3333/rooms/{roomId}/audio
  Content-Type: multipart/form-data
  (enviar arquivo de áudio no campo 'file')
  ```

## Créditos

Projeto desenvolvido por **Emmanuel Oliveira | OFS**
Todos os créditos para a [Rocketseat](https://rocketseat.com.br/)
