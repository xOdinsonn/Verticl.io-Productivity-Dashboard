# Social Productivity System – High‑Level Architecture

```mermaid
graph TB

  %% ─────────────── Social Platforms ───────────────
  subgraph "Social Platforms"
    IG[Instagram]
    YT[YouTube]
    PT[Pinterest]
    LI[LinkedIn]
    TW[X / Twitter]
    GF[Google Feed]
    FB[Facebook]
  end

  %% ─────────────── Capture & Processing ───────────────
  subgraph "Capture & Processing"
    WH[Social Capture Webhook]
    N8N[n8n Automation Engine]
    AI[OpenAI Task Generation]
    AUTO_TAG[Auto‑Tagging Engine]
  end

  %% ─────────────── Airtable Database ───────────────
  subgraph "Airtable Database"
    SAVES[(Social Saves)]
    TASKS[(Tasks)]
    PROJECTS[(Projects)]
    NOTES[(Notes)]
    PROMPTS[(AI Prompts)]
    FOCUS[(Focus Sessions)]
  end

  %% ─────────────── User Interfaces ───────────────
  subgraph "User Interfaces"
    INBOX[Unified Inbox]
    KANBAN[Kanban Board]
    TIMELINE[Timeline / Gantt]
    DASHBOARD[Project Dashboard]
    NOTES_HUB[Notes Hub]
  end

  %% ─────────────── External Services ───────────────
  subgraph "External Services"
    GCAL[Google Calendar]
    EMAIL[Email Integration]
    WHIM[Whimsical Boards]
    RAIN[Raindrop.io]
  end

  %% ─────────────── AI & Automation ───────────────
  subgraph "AI & Automation"
    SOP_REC[SOP Auto Recorder]
    BACKLINK[Backlink Engine]
    DIGEST[Weekly Digest]
  end

  %% ─────────────── User ───────────────
  USER(User)

  %% -------- 1. User shares content ----------
  USER --> IG
  USER --> YT
  USER --> PT
  USER --> LI
  USER --> TW
  USER --> GF
  USER --> FB

  %% -------- 2. Social → Capture ----------
  IG -- "Share" --> WH
  YT -- "Share" --> WH
  PT -- "Share" --> WH
  LI -- "Share" --> WH
  TW -- "Share" --> WH
  GF -- "Share" --> WH
  FB -- "Share" --> WH

  %% -------- 3. Capture & Processing ----------
  WH --> N8N
  N8N --> AUTO_TAG --> SAVES
  N8N --> AI
  AI --> PROMPTS
  AI --> TASKS

  %% -------- 4. Data Relationships ----------
  SAVES --> TASKS
  SAVES --> PROJECTS
  SAVES --> NOTES
  TASKS --> PROJECTS
  TASKS --> FOCUS
  PROJECTS --> NOTES

  %% -------- 5. Interfaces ----------
  SAVES --> INBOX
  TASKS --> INBOX
  NOTES --> INBOX
  TASKS --> KANBAN
  TASKS --> TIMELINE
  PROJECTS --> TIMELINE
  PROJECTS --> DASHBOARD
  FOCUS --> DASHBOARD
  NOTES --> NOTES_HUB

  %% -------- 6. External Sync ----------
  TASKS -- "Sync Due Dates" --> GCAL
  GCAL -- "Calendar Events" --> TASKS
  EMAIL -- "Follow‑up Detection" --> N8N
  N8N -- "Create Follow‑up" --> TASKS
  PROJECTS -- "Visual Planning" --> WHIM
  SAVES -- "Bookmark Sync" --> RAIN

  %% -------- 7. Automation & Insights ----------
  TASKS --> SOP_REC
  SOP_REC -- "Pattern Detection" --> N8N
  SAVES --> BACKLINK
  TASKS --> BACKLINK
  NOTES --> BACKLINK
  PROJECTS --> BACKLINK
  DASHBOARD --> DIGEST
  FOCUS --> DIGEST
  DIGEST -- "Weekly Summary" --> EMAIL

  %% -------- 8. User consumes UI ----------
  USER --> INBOX
  USER --> KANBAN
  USER --> TIMELINE
  USER --> DASHBOARD
  USER --> NOTES_HUB
