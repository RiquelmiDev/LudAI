# LudAI

Projeto backend desenvolvido com [NestJS](https://nestjs.com/) cujo intuito principal é utilizar o ChatGPT para recomendar jogos, além de oferecer gerenciamento de usuários, autenticação JWT, integração com IA (OpenAI) e recursos utilitários.

## Sumário

- [Visão Geral](#visão-geral)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Instalação](#instalação)
- [Configuração](#configuração)
- [Comandos Principais](#comandos-principais)
- [Testes](#testes)
- [Endpoints Principais](#endpoints-principais)

---

## Visão Geral

Este projeto oferece uma API RESTful para:

- Cadastro e autenticação de usuários com JWT
- Busca paginada de usuários
- Recomendação de jogos via integração com OpenAI
- Endpoints utilitários de data/hora

---

## Estrutura do Projeto

```
src/
│
├── ai/                  # Módulo de integração com IA (OpenAI)
│   ├── ai.controller.ts
│   ├── ai.service.ts
│   ├── dto/
│   └── entities/
│
├── users/               # Módulo de usuários e autenticação
│   ├── users.controller.ts
│   ├── users.service.ts
│   ├── users.module.ts
│   ├── auth.guard.ts
│   ├── public.decorator.ts
│   ├── encryption/
│   ├── dto/
│   └── entities/
│
├── shared/              # Serviços e DTOs compartilhados
│   ├── pagination.service.ts
│   ├── shared.module.ts
│   └── dto/
│
├── app.controller.ts    # Controller principal
├── app.module.ts        # Módulo raiz
├── app.service.ts
├── main.ts              # Bootstrap da aplicação
└── time.controller.ts   # Endpoints de data/hora
```

---

## Instalação

```bash
pnpm install
```

## Configuração

1. Renomeie o arquivo `.env.example` para `.env` na raiz do projeto.
2. Edite o arquivo `.env` e defina as variáveis necessárias, por exemplo:
    ```
    OPENAI_API_KEY=your_openai_key
    ```
3. Configure o banco de dados MySQL conforme `src/app.module.ts`.

---

## Comandos Principais

```bash
# Desenvolvimento
pnpm run start

# Modo watch
pnpm run start:dev

# Produção
pnpm run start:prod
```

---

## Testes

```bash
# Testes unitários
pnpm run test

# Testes e2e
pnpm run test:e2e

# Cobertura de testes
pnpm run test:cov
```

---

## Endpoints Principais

### Usuários

- `POST /users/signup` — Cadastro de usuário
- `POST /users/login` — Login e obtenção de token JWT
- `GET /users` — Busca paginada de usuários (autenticado)
- `GET /users/profile` — Perfil do usuário autenticado

### IA

- `POST /ai/games` — Recomendação de jogos via IA

### Utilitários

- `GET /tempo` — Data e hora atual
- `GET /tempo/apenas_data` — Apenas data
- `GET /tempo/apenas_hora` — Apenas hora

---
