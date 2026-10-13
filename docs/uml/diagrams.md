\# UML-диаграммы системы Flowra



\## 1. Диаграмма компонентов (Component Diagram)

```mermaid

graph TD

&#x20;   subgraph Client\_Layer \["Client Layer (Frontend)"]

&#x20;       UI\["Web / Mobile App (Next.js / Flutter)"]

&#x20;       TG\["Telegram Mini App"]

&#x20;   end



&#x20;   subgraph Backend\_Layer \["Backend Layer (Render / FastAPI)"]

&#x20;       GW\["API Gateway / Controller"]

&#x20;       SCHED\["Schedule Engine (MILP / Heuristic)"]

&#x20;       NLP\["AI NLP Service (Parser)"]

&#x20;   end



&#x20;   subgraph Data\_Layer \["Data Layer (Supabase)"]

&#x20;       DB\[(PostgreSQL DB)]

&#x20;       CACHE\[(Redis Cache)]

&#x20;   end



&#x20;   subgraph External\_Services \["External Services"]

&#x20;       LLM\["GPTunnel / AI Studio (LLM API)"]

&#x20;       GCAL\["Google Calendar API"]

&#x20;   end



&#x20;   UI -->|HTTPS / REST| GW

&#x20;   TG -->|HTTPS / REST| GW

&#x20;   GW --> SCHED

&#x20;   GW --> NLP

&#x20;   NLP -->|HTTPS| LLM

&#x20;   GW -->|TCP / SQL| DB

&#x20;   SCHED -->|Cache Port| CACHE

&#x20;   GW -->|Sync OAuth2| GCAL

