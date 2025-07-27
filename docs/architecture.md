# High-Level Architecture

```mermaid
graph TD
    A[Social Platforms] -->|Share URL| B[Social Capture Webhook]
    B --> C[n8n Automation]
    C -->|Enrich & Auto-Tag| D[Airtable Saves Table]
    D --> E[Unified Inbox]
    E --> F[Kanban Task Board]
    F --> G[SOP Auto Recorder]
    G --> H[SOP Draft Queue]
    
    C -->|Generate Tasks| I[Tasks Table]
    I --> F
    
    D -->|Link to| J[Notes Hub]
    J --> F
    
    F -->|Completed Tasks| K[Focus Logs]
    K --> L[Dashboard Metrics]
    
    I -->|Due Dates| M[Calendar Bridge]
    M -->|Sync with| N[Google Calendar]
    
    O[Email Integration] -->|Follow-up Detection| C
    C -->|Create Follow-up| I
    
    P[Weekly Digest] -->|Compile Stats| L
    P -->|Send Summary| Q[Email Notification]