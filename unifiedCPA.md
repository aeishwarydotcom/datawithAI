```mermaid
flowchart TD
  %% System/Service Architecture
  subgraph Client
    UI[React + Tailwind + Redux]
  end

  UI -->|JWT/OAuth2| API[FastAPI Gateway]

  subgraph Core Services
    AE[MYC-1 Accounting Engine]
    DI[MYC-4 Ingestion]
    RECO[MYC-15 Reconciliation]
    CLOSE[MYC-22 Close Engine]
    TAX[MYC-16 Tax Bridge (lite)]
    RULES[MYC-3 Rule Engine]
    FX[MYC-6 FX Engine]
    RPT[Reporting (TB/P&L/BS)]
    AI[MYC-18 AI Layer (RAG + Classifier)]
  end

  API --> AE
  API --> DI
  API --> RECO
  API --> CLOSE
  API --> TAX
  AE --> RPT
  RULES --> AE
  FX --> AE
  AI --> DI
  AI --> AE

  subgraph Data
    RDS[(Postgres RDS\nOLTP + RLS)]
    VEC[(pgvector\nGAAP/IFRS indexes)]
    S3[(S3 Documents)]
    METRICS[(CloudWatch/Prometheus/Grafana)]
  end

  AE <--> RDS
  DI <--> S3
  AI <--> VEC
  RECO <--> RDS
  CLOSE <--> RDS
  TAX <--> RDS
  API --> METRICS
  AE --> METRICS
  DI --> METRICS
  RECO --> METRICS

  subgraph Integrations
    PLAID[Plaid/Finicity]
    STRIPE[Stripe/Square]
    OCR[AWS Textract / Azure Form Recognizer / Google Doc AI]
    IRS[IRS / FIRS\n(e-file later)]
  end

  DI --> PLAID
  DI --> STRIPE
  DI --> OCR
  TAX -.exports/forms.-> IRS

```
