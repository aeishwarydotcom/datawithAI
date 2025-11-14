```mermaid
flowchart LR
  U[Business User]
  UI[Web App - React]
  API[API Layer - FastAPI]
  ACCT[Accounting Engine]
  AI[AI Layer]
  INTEG[Connectors]
  DB[(PostgreSQL RDS)]
  OBS[Observability]

  U --> UI
  UI --> API
  API --> ACCT
  API --> AI
  API --> INTEG
  ACCT --> DB
  AI --> DB
  INTEG --> DB
  API --> OBS




```
