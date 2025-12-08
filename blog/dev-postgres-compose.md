---
title: Compose file for PostgreSQL in development
date: 2025-12-07
updated: 2025-12-07
slug: dev-postgres-compose
---
Is it just me, or does everyone else also need a PostgreSQL database for like 15 different projects? And it always ends up being a pain having to open a browser and grab a `compose.yml` of our favourite elephant database. And I know you're just going to say just keep a template, well, you know what? I'm way too lazy and forgetful to do that, so here's my template just for you.

First, set up your `.env`:

```
DATABASE_URL=postgres://postgres@postgres:localhost:5432/postgres
```

Then, create your `compose.yml`:

```
services:
  postgres:
    image: postgres:18-alpine
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
      POSTGRES_DB: postgres
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql

volumes:
  postgres_data:
```
