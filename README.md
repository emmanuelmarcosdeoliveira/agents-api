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
- [Configuração e Setup](#configuração-e-setup)
- [Scripts Disponíveis](#scripts-disponíveis)
- [Exemplos de Uso da API](#exemplos-de-uso-da-api)
- [Créditos](#créditos)

## Sobre o Projeto

O **Let Me Ask** é uma API backend para gerenciamento de salas (rooms), desenvolvida em Node.js com Fastify, Drizzle ORM e PostgreSQL, seguindo boas práticas de tipagem, validação e organização de código.

## Tecnologias e Bibliotecas

- **Node.js** (TypeScript)
- **Fastify**: Framework web rápido e eficiente
- **@fastify/cors**: Suporte a CORS
- **fastify-type-provider-zod**: Tipagem e validação de schemas com Zod
- **Zod**: Validação de dados e variáveis de ambiente
- **Drizzle ORM**: ORM moderno para PostgreSQL
- **drizzle-kit**: Migrations e geração de schemas
- **drizzle-seed**: Seed de dados para o banco
- **PostgreSQL**: Banco de dados relacional
- **Biome**: Linter e formatter
- **Ultracite**: Utilitários de desenvolvimento

## Padrões de Projeto

- **Type-safe**: Uso extensivo de TypeScript e Zod para validação e tipagem
- **Modularização**: Separação clara entre rotas, banco de dados e configuração
- **Environment-driven**: Configuração via variáveis de ambiente validadas
- **Migrations e Seeds**: Controle de versão do banco e popularização de dados

## Configuração e Setup

1. **Clone o repositório**

   ```bash
   git clone https://github.com/emmanuelmarcosdeoliveira/agents-back-end.git
   cd agents-back-end
   ```

2. **Instale as dependências**

   ```bash
   npm install
   ```

3. **Configure as variáveis de ambiente**  
   Crie um arquivo `.env` na raiz com:

   ```
   PORT=3333
   DATABASE_URL=postgresql://usuario:senha@localhost:5432/letmeask
   ```

4. **Configure o banco de dados**

   - Certifique-se de ter um banco PostgreSQL rodando.
   - Ajuste o `DATABASE_URL` conforme seu ambiente.

5. **Rode as migrations e seeds**

   ```bash
   # Gere as migrations (se necessário)
   npx drizzle-kit generate:pg
   # Popule o banco com dados de exemplo
   npm run db:seed
   ```

6. **Inicie o servidor**
   ```bash
   npm run dev
   ```

## Scripts Disponíveis

- `npm run dev` — Inicia o servidor em modo desenvolvimento com hot reload
- `npm start` — Inicia o servidor em modo produção
- `npm run db:seed` — Popula o banco de dados com dados de exemplo

## Exemplos de Uso da API

- **Health check**
  ```
  GET http://localhost:3333/health
  ```
- **Listar salas**
  ```
  GET http://localhost:3333/rooms
  ```

## Créditos

Projeto desenvolvido por **Emmanuel Oliveira | OFS**  
Todos os créditos para a [Rocketseat](https://rocketseat.com.br/)
