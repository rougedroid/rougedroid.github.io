---
title: Financial Data Pipeline & Ingestion Engine
date: 2026-07-05
description: This project page covers the engineering details of a financial data backend built to ingest raw SEC filings and earnings metrics. The project evolved from a content-focused financial news concept into a heavy infrastructure-building exercise, utilizing AI generation for rapid backend assembly while the overall database design and API sync lagged behind.
summary: This project page covers the engineering details of a financial data backend built to ingest raw SEC filings and earnings metrics. The project evolved from a content-focused financial news concept into a heavy infrastructure-building exercise, utilizing AI generation for rapid backend assembly while the overall database design and API sync lagged behind.
tags:
  - python
  - dataprocessing
categories:
  - Programming
  - delayed
  - product
---
## Project Intent

- Build a scalable, real-time backend capable of parsing SEC filings and extracting core financial metrics.
- Establish a continuous data ingestion loop utilizing WebSockets and background workers for live price and document updates.
- Optimize operational speed by leveraging AI tools to generate complex boilerplates, authentication systems, and API structures.
- Project has been **postponed/paused** as of mid-2026 to prioritize academic requirements (JEE), leaving a highly functional data engine awaiting a frontend overhaul.

## System Architecture

### The Bloomberg-First Backend

Instead of starting with user features, the system's development prioritized core, heavy financial plumbing:

- **Ingestion & Parsing:** Background workers designed to fetch SEC filings, parse their contents, run metric extraction logic, and commit the structured results to a company database.
- **Cache & Real-Time Sync:** A Redis layer caching high-frequency queries paired with a WebSocket broadcasting architecture to push real-time stock prices.
- **The "Accidental" Dashboard:** A temporary UI generated quickly via AI to verify the data layers. This inadvertently shifted the project's direction from a "news-first summaries app" to a comprehensive "company-first financial dashboard."

```
[Raw SEC Filings / Market WebSockets] 
              │
              ▼
    [Background Workers] ──► [Redis Cache]
              │                  │
              ▼                  ▼
      [PostgreSQL DB] ───► [AI-Generated Dashboard]
```

## Limitations

### Database & Structural Debt

- **The AI Co-Pilot Penalty:** While using AI accelerated backend generation and successfully glued disparate components (Redis, workers, auth) together, it resulted in a classic _"Copilot Crash."_ Without a disciplined, human-designed schema plan, the database architecture grew organically into a messy, unusable web.
- **API & Route Mismatch:** The backend evolved so fast that the generated frontend quickly lost compatibility. The system currently suffers from missing API routes and half-implemented user authentication flows.
- **High Maintenance Overhead:** Altering a single feature now requires deep contextual mapping across tables, relationships, repository layers, and caching rules, making the backend difficult to modify without a complete schema refactor.

### Data Provider Roadblocks

- **The Free-Tier Wall:** Extensive testing across providers (Finnhub, Polygon, Alpaca, TwelveData, AlphaVantage) proved that affordable financial data is heavily restricted—lacking either websocket access, live fundamentals, or historical filings without cost-prohibitive licensing.

## Project Outcomes

- Successfully built a highly complex, multi-service financial data pipeline from scratch.
- Understood the requirements of a financial tool.
- Learned the architectural dangers of letting AI generate large-scale systems without pre-planning the core database schemas.
- ✘ Failed to deliver the original user-facing personalized financial news experience.
- ✘ Failed to maintain API synchronization, leaving the frontend completely broken and out of step with backend routes.
- **Again, this is only paused, it WILL continue development in a few weeks.**

## Future Plan

The project is currently sitting on ice while life priorities take precedence. When the code is unpaused, the next phase will avoid adding any new backend subsystems entirely.

The immediate checklist requires pulling down the database, drafting a clean relational schema from scratch, fixing the broken user auth routes, and cleanly mapping the API so a proper frontend can finally leverage the data pipeline.

---
## Repositories
1. The backend ( messy ): https://github.com/rougedroid/TickerFactsBackend/
2. The Landing Page ( with demo ): https://rougedroid.github.io/TickerFactsLanding/index.html
