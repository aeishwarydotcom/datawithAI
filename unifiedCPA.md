```mermaid
flowchart LR
  U[Business User / Founder] --> UI[Web App\n(React + Tailwind)]
  UI --> API[API Layer\n(FastAPI)]

  API --> ACCT["Accounting Engine\n(Journals / Periods / COA)"]
  API --> AI["AI Layer\n(Classification + RAG)"]
  API --> INTEG["Connectors\n(Plaid, Stripe, OCR)"]

  ACCT --> DB[(PostgreSQL RDS)]
  AI --> DB
  INTEG --> DB

  API --> OBS["Observability\n(Logs / Metrics)"]



```
