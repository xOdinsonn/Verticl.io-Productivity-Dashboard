graph TB
    %% Social Input Layer
    subgraph "Social Platforms"
        IG[Instagram]
        YT[YouTube]
        PT[Pinterest]
        LI[LinkedIn]
        TW[X/Twitter]
        GF[Google Feed]
        FB[Facebook]
    end
    
    %% Capture Layer
    subgraph "Capture & Processing"
        WH[Social Capture Webhook]
        N8N[n8n Automation Engine]
        AI[OpenAI Task Generation]
    end
    
    %% Data Layer
    subgraph "Airtable Database"
        SAVES[(Social Saves)]
        TASKS[(Tasks)]
        PROJECTS[(Projects)]
        NOTES[(Notes)]
        PROMPTS[(AI Prompts)]
        FOCUS[(Focus Sessions)]
    end
    
    %% Interface Layer
    subgraph "User Interfaces"
        INBOX[Unified Inbox]
        KANBAN[Kanban Task Board]
        TIMELINE[Timeline/Gantt View]
        DASHBOARD[Project Dashboard]
        NOTES_HUB[Notes Hub]
    end
    
    %% External Integrations
    subgraph "External Services"
        GCAL[Google Calendar]
        EMAIL[Email Integration]
        WHIM[Whimsical Boards]
        RAIN[Raindrop.io]
    end
    
    %% Automation & Intelligence
    subgraph "AI & Automation"
        AUTO_TAG[Auto-Tagging Engine]
        SOP_REC[SOP Auto Recorder]
        BACKLINK[Backlink Engine]
        DIGEST[Weekly Digest]
    end
    
    %% User Actions
    USER[User] --> IG
    USER --> YT
    USER --> PT
    USER --> LI
    USER --> TW
    USER --> GF
    USER --> FB
    
    %% Social to Capture Flow
    IG -.->|Share Action| WH
    YT -.->|Share Action| WH
    PT -.->|Share Action| WH
    LI -.->|Share Action| WH
    TW -.->|Share Action| WH
    GF -.->|Share Action| WH
    FB -.->|Share Action| WH
    
    %% Processing Flow
    WH --> N8N
    N8N --> AUTO_TAG
    AUTO_TAG --> SAVES
    N8N --> AI
    AI --> PROMPTS
    AI --> TASKS
    
    %% Data Relationships
    SAVES --> TASKS
    SAVES --> PROJECTS
    SAVES --> NOTES
    TASKS --> PROJECTS
    TASKS --> FOCUS
    PROJECTS --> NOTES
    
    %% Interface Access
    SAVES --> INBOX
    TASKS --> INBOX
    NOTES --> INBOX
    
    TASKS --> KANBAN
    TASKS --> TIMELINE
    PROJECTS --> TIMELINE
    
    PROJECTS --> DASHBOARD
    FOCUS --> DASHBOARD
    
    NOTES --> NOTES_HUB
    
    %% External Integration Flows
    TASKS -.->|Sync Due Dates| GCAL
    GCAL -.->|Calendar Events| TASKS
    
    EMAIL -.->|Follow-up Detection| N8N
    N8N -.->|Create Follow-up| TASKS
    
    PROJECTS -.->|Visual Planning| WHIM
    SAVES -.->|Bookmark Sync| RAIN
    
    %% Automation Flows
    TASKS --> SOP_REC
    SOP_REC -.->|Pattern Detection| N8N
    
    SAVES --> BACKLINK
    TASKS --> BACKLINK
    NOTES --> BACKLINK
    PROJECTS --> BACKLINK
    
    DASHBOARD --> DIGEST
    FOCUS --> DIGEST
    DIGEST -.->|Weekly Summary| EMAIL
    
    %% User Interaction
    USER --> INBOX
    USER --> KANBAN
    USER --> TIMELINE
    USER --> DASHBOARD
    USER --> NOTES_HUB
    
    %% Styling
    classDef socialPlatform fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    classDef capture fill:#f3e5f5,stroke:#4a148c,stroke-width:2px
    classDef database fill:#e8f5e8,stroke:#1b5e20,stroke-width:2px
    classDef interface fill:#fff3e0,stroke:#e65100,stroke-width:2px
    classDef external fill:#fce4ec,stroke:#880e4f,stroke-width:2px
    classDef automation fill:#f1f8e9,stroke:#33691e,stroke-width:2px
    classDef user fill:#ffebee,stroke:#b71c1c,stroke-width:3px
    
    class IG,YT,PT,LI,TW,GF,FB socialPlatform
    class WH,N8N,AI capture
    class SAVES,TASKS,PROJECTS,NOTES,PROMPTS,FOCUS database
    class INBOX,KANBAN,TIMELINE,DASHBOARD,NOTES_HUB interface
    class GCAL,EMAIL,WHIM,RAIN external
    class AUTO_TAG,SOP_REC,BACKLINK,DIGEST automation
    class USER user