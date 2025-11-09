```mermaid
flowchart LR
  %% ------------------- SOURCES -------------------
  subgraph A["AI Platforms (sensors)"]
    direction TB
    A1[User Interactions\n(prompts, clicks, edits)]
    A2[System Telemetry\n(latency, errors, device)]
    A3[Content Signals\n(images, text, links)]
  end

  %% ------------------- DATA PIPELINE -------------------
  subgraph B["Data Pipeline"]
    direction TB
    B1[Ingest & Stream]
    B2[Clean & Normalize]
    B3[Anonymize/Pseudonymize]
    B4[Feature Engineering]
  end

  A1 --> B1
  A2 --> B1
  A3 --> B1
  B1 --> B2 --> B3 --> B4

  %% ------------------- FEATURES -------------------
  subgraph C["Derived Signals"]
    direction TB
    C1[Curiosity Index]
    C2[Sentiment & Mood]
    C3[Bias / Value Map]
    C4[Skills & Adoption Velocity]
    C5[Network Influence Score]
  end
  B4 --> C1
  B4 --> C2
  B4 --> C3
  B4 --> C4
  B4 --> C5

  %% ------------------- DEMOGRAPHIC INTEL -------------------
  subgraph D["Demographic Intelligence"]
    direction TB
    D1[Population Models]
    D2[Hotspots & Trends]
    D3[Resilience / Stability Index]
  end
  C1 --> D1
  C2 --> D1
  C3 --> D1
  C4 --> D1
  C5 --> D1
  D1 --> D2
  D1 --> D3

  %% ------------------- STRATEGIC LEVERAGE -------------------
  subgraph E["Strategic Leverage"]
    direction TB
    E1[Policy & Investment Targeting]
    E2[Comms & Narrative Design]
    E3[Intelligence Dashboards]
    E4[Risk / Early-Warning Systems]
  end
  D2 --> E1
  D3 --> E2
  D1 --> E3
  D3 --> E4

  %% ------------------- FUTURE WARFARE MODES -------------------
  subgraph F["Future Warfare"]
    direction TB
    F1[Cognitive / Influence Ops]
    F2[Information Defense]
    F3[Economic & Supply Chain Actions]
    F4[Cyber / Automated Response]
  end
  E2 --> F1
  E3 --> F2
  E1 --> F3
  E4 --> F4

  %% ------------------- GOVERNANCE / ETHICS -------------------
  subgraph G["Governance & Guardrails"]
    direction TB
    G1[Data Sovereignty]
    G2[Privacy by Design]
    G3[Auditability & Red-Team]
    G4[Safety Policies & Transparency]
  end
  G1 --- B3
  G2 --- B2
  G3 --- E3
  G4 --- E2

  %% Feedback loops
  F1 -. influence .-> A1
  F2 -. hardening .-> B2
  F3 -. secondary effects .-> D2
  F4 -. threat intel .-> E4

```
