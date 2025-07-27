flowchart TB
  %% Social Input Layer
  subgraph SocialPlatforms["Social Platforms"]
    IG[Instagram]
    YT[YouTube]
    PT[Pinterest]
    LI[LinkedIn]
    TW[X / Twitter]
    GF[Google Feed]
    FB[Facebook]
  end

  %% Capture Layer
  subgraph CaptureProcessing["Capture & Processing"]
    WH[Social Capture Webhook]
    N8N[n8n Automation Engine]
    AI[OpenAI Task Generation]
  end

  %% Data Layer
  subgraph AirtableDB["Airtable Database"]
    SAVES[(Social Saves)]
    TASKS[(Tasks)]
    PROJECTS[(Projects)]
    NOTES[(Notes)]
    PROMPTS[(AI Prompts)]
    FOCUS[(Focus Sessions)]
  end

  %% Interface Layer
  subgraph UserInterfaces["User Interfaces"]
    INBOX[Unified Inbox]
    KANBAN[Kanban Task Board]
    TIMELINE[Timeline / Gantt View]
    DASHBOARD[Project Dashboard]
    NOTES_HUB[Notes Hub]
  end

  %% External Integrations
  subgraph ExternalServices["External Services"]
    GCAL[Google Calendar]
    EMAIL[Email Integration]
    WHIM[Whimsical Boards]
    RAIN[Raindrop.io]
  end

  %% AI & Automation
  subgraph AIAutomation["AI & Automation"]
    AUTO_TAG[Auto‑Tagging Engine]
    SOP_REC[SOP Auto Recorder]
    BACKLINK[Backlink Engine]
    DIGEST[Weekly Digest]
  end

  %% User Entity
  USER[User]

  %% User → Social
  USER --> IG & YT & PT & LI & TW & GF & FB

  %% Social → Capture
  IG -. "Share" .-> WH
  YT -. "Share" .-> WH
  PT -. "Share" .-> WH
  LI -. "Share" .-> WH
  TW -. "Share" .-> WH
  GF -. "Share" .-> WH
  FB -. "Share" .-> WH

  %% Processing
  WH --> N8N
  N8N --> AUTO_TAG --> SAVES
  N8N --> AI
  AI --> PROMPTS & TASKS

  %% Data Relationships
  SAVES --> TASKS & PROJECTS & NOTES
  TASKS --> PROJECTS & FOCUS
  PROJECTS --> NOTES

  %% Interfaces
  SAVES & TASKS & NOTES --> INBOX
  TASKS --> KANBAN & TIMELINE
  PROJECTS --> TIMELINE & DASHBOARD
  FOCUS --> DASHBOARD
  NOTES --> NOTES_HUB

  %% External Sync
  TASKS -. "Sync Due Dates" .-> GCAL
  GCAL -. "Calendar Events" .-> TASKS
  EMAIL -. "Follow‑up Detection" .-> N8N
  N8N -. "Create Follow‑up" .-> TASKS
  PROJECTS -. "Visual Planning" .-> WHIM
  SAVES -. "Bookmark Sync" .-> RAIN

  %% Automation & Insights
  TASKS --> SOP_REC -. "Pattern Detection" .-> N8N
  SAVES & TASKS & NOTES & PROJECTS --> BACKLINK
  DASHBOARD & FOCUS --> DIGEST -. "Weekly Summary" .-> EMAIL

  %% User Interaction
  USER --> INBOX & KANBAN & TIMELINE & DASHBOARD & NOTES_HUB

  %% Styling
  classDef social fill:#e1f5fe,stroke:#01579b,stroke-width:2px;
  classDef capture fill:#f3e5f5,stroke:#4a148c,stroke-width:2px;
  classDef database fill:#e8f5e8,stroke:#1b5e20,stroke-width:2px;
  classDef interface fill:#fff3e0,stroke:#e65100,stroke-width:2px;
  classDef external fill:#fce4ec,stroke:#880e4f,stroke-width:2px;
  classDef automation fill:#f1f8e9,stroke:#33691e,stroke-width:2px;
  classDef user fill:#ffebee,stroke:#b71c1c,stroke-width:3px;

  class IG,YT,PT,LI,TW,GF,FB social
  class WH,N8N,AI capture
  class SAVES,TASKS,PROJECTS,NOTES,PROMPTS,FOCUS database
  class INBOX,KANBAN,TIMELINE,DASHBOARD,NOTES_HUB interface
  class GCAL,EMAIL,WHIM,RAIN external
  class AUTO_TAG,SOP_REC,BACKLINK,DIGEST automation
  class USER user
