# Verticl.io-Productivity-Dashboard

> A no-code Airtable workspace that ingests your social bookmarks, auto-generates actionable tasks with n8n + LLM, and displays everything in a kanban & planning dashboard—so you can validate the workflow before investing in a full custom app.

## 🎯 Problem Statement

As a busy professional juggling family, full-time work (Mon-Thu), and an AI automation business, I need a centralized system to:
- Track where I left off in business plans across different days
- Organize bookmarks and saves from multiple social platforms (YouTube, Instagram, Pinterest, Google mobile feed)
- Convert social discoveries into actionable tasks and project development
- Maintain productivity momentum with limited time (Fri-Sun available for business)

## 🏗️ Development Phases

### Phase 1: MVP Validation (Current)
**Tech Stack:** Airtable Base + n8n + Raindrop.io + Whimsical + Google Workspace
- [ ] Set up Airtable base structure
- [ ] Configure n8n automation workflows  
- [ ] Implement social bookmark capture
- [ ] Create basic dashboard views
- [ ] Test workflow with real usage

### Phase 2: Productized Service
- [ ] Refine automation based on Phase 1 learnings
- [ ] Create template for other users
- [ ] Develop onboarding flow
- [ ] Build simple landing page

### Phase 3: Native Applications
- [ ] iPhone app (mobile-first design)
- [ ] Desktop companion app
- [ ] Full feature set implementation

## 📁 Repository Structure

```
├── README.md                           # Project overview and documentation
├── docs/
│   ├── development-methodology.md      # AI-assisted development approach
│   ├── phase-1/                       # Phase 1 documentation
│   │   ├── weekly-reports/             # Progress tracking
│   │   ├── setup-guides/               # Installation instructions
│   │   └── lessons-learned/            # Development insights
│   ├── phase-2/                       # Phase 2 planning (future)
│   └── phase-3/                       # Phase 3 planning (future)
├── phase-1-mvp/                       # MVP development files
│   ├── airtable/                      # Database configurations
│   ├── n8n-workflows/                 # Automation workflows
│   ├── integrations/                  # Third-party setups
│   └── deployment/                    # Setup and deployment
├── .github/
│   ├── ISSUE_TEMPLATE/                # Issue templates by phase
│   └── workflows/                     # CI/CD (future)
├── phase-2-service/                   # Service development (future)
└── phase-3-native/                    # Native apps (future)
```

### Current Development Focus
🎯 **Phase 1 MVP** - All active development in `phase-1-mvp/` directory
📚 **Documentation** - Comprehensive methodology and progress tracking in `docs/`
🔧 **AI-Assisted** - Development approach documented in `docs/development-methodology.md`

## ✨ Core Features

### Social Capture & Integration
- **Platform Recognition**: Visual frame overlay showing source platform (X, Instagram, etc.)
- **Social Sharing Integration**: iOS share sheet integration for seamless bookmark capture
- **Multi-Platform Support**: YouTube, Instagram, Pinterest, Google mobile feed, LinkedIn, Facebook, X
- **Auto-Tagging**: Automatic categorization using hashtags and content analysis

### AI-Powered Planning
- **Smart Task Generation**: Convert social saves into actionable tasks using LLM
- **Project Integration**: Pinterest-style dropdown system for categorizing saves into existing projects
- **Planning Systems**: Complete system templates users can add to projects
- **Suggestion Algorithm**: Smart recommendations for save placement across multiple projects

### Productivity Management
- **Unified Inbox**: Time-ordered view of saves, tasks, and notes with bulk triage
- **Kanban Task Board**: Drag-and-drop task management (To-Do → Doing → Done)
- **Timeline/Gantt View**: Visual project scheduling across weeks
- **Multiple Projects**: Support for various industries, hobbies, and initiatives

### Collaboration & Notes
- **Multiplayer Planning**: Co-op development with multiple stakeholders  
- **Integrated Note-Taking**: Notes that connect with saves, bookmarks, and projects
- **Feature Integration**: Seamless connection between notes, AI, calendar, email
- **Backlink Engine**: Automatic relationship discovery between records

### Calendar & Email Integration
- **Smart Scheduling**: AI detection of calendar events and email integration
- **Conflict Resolution**: Schedule optimization and conflict identification  
- **Email Integration**: Send emails from app or launch external email client

## 🛠️ Technical Implementation

### Airtable Base Structure
```
Tables:
├── saves (social bookmarks)
├── tasks (actionable items)  
├── projects (ongoing initiatives)
├── notes (linked documentation)
├── prompts (AI prompt library)
├── sops (standard operating procedures)
└── focus_logs (productivity tracking)
```

### n8n Automation Workflows
- Social capture webhook endpoints
- Auto-tagging and thumbnail extraction
- Task generation from saves
- Calendar synchronization
- Email follow-up detection
- Weekly insight digest generation

### Key Integrations
- **Raindrop.io**: Bookmark management
- **Whimsical**: Visual planning boards
- **Google Workspace**: Calendar and email sync
- **OpenAI**: Task generation and insights
- **Social Platforms**: Share sheet integration

## 📱 Mobile-First Design Philosophy

### iOS Share Integration  
- Appears in share suggestions across all social platforms
- One-tap save to dashboard
- Automatic platform detection and tagging

### Progressive Feature Depth
- **Mobile**: Core capture and triage functions
- **Desktop**: Advanced planning, analysis, and management

## 🔧 Setup Instructions

### Prerequisites
- Airtable account (Pro plan recommended)
- n8n instance (cloud or self-hosted)
- Google Workspace account
- OpenAI API access

### Quick Start
1. **Copy Airtable Base**: Use the [base schema](airtable/base-schema.json) and [example data](airtable/example-data.csv) to create your workspace.
2. **Import n8n Workflows**: Import the [JSON files](n8n-workflows/) into your n8n instance.
3. **Configure API Keys**: Follow the [setup guide](docs/setup-guide.md).
4. **Test Social Capture**: Trigger the [social-capture workflow](n8n-workflows/social-capture.json) using the provided webhook URL.
5. **Customize Dashboard**: Adjust the [interface configs](airtable/interface-configs/) to match your workflow.

## 📁 Repository Structure

```
├── README.md
├── docs/
│   ├── setup-guide.md
│   ├── user-manual.md
│   ├── api-reference.md
│   └── troubleshooting.md
├── airtable/
│   ├── base-schema.json
│   ├── example-data.csv
│   └── interface-configs/
│       └── README.md
├── n8n-workflows/
│   ├── README.md
│   ├── calendar-sync.json
│   ├── social-capture.json
│   ├── task-generation.json
│   └── weekly-digest.json
├── ios-shortcuts/
│   └── placeholder.shortcut
├── browser-extension/
│   ├── content.js
│   ├── manifest.json
│   └── popup.html
├── templates/
│   ├── project-templates/
│   │   └── example-project-template.md
│   ├── prompt-library/
│   │   └── example-prompt.txt
│   └── sop-templates/
│       └── example-sop.md
└── assets/
    ├── demo-videos/
    ├── logos/
    └── screenshots/
```

## 🎯 Roadmap

### Phase 1 Milestones (Next 3 Months)
- [ ] Complete Airtable base setup
- [ ] Deploy core n8n workflows
- [ ] Test social capture from 3+ platforms
- [ ] Validate daily workflow usage
- [ ] Document lessons learned

### Phase 2 Goals (Months 4-6)
- [ ] Create user onboarding flow
- [ ] Build simple marketing site
- [ ] Get 10 beta users testing system
- [ ] Refine based on feedback

### Phase 3 Vision (6+ Months)
- [ ] Native iOS app development
- [ ] Desktop application
- [ ] Advanced AI features
- [ ] Team collaboration tools

## 📊 Success Metrics

- **Daily Usage**: Consistent capture of 5+ social saves
- **Task Completion**: 80%+ of generated tasks marked as done
- **Time Savings**: Reduce "where did I leave off" confusion by 90%
- **Project Progress**: Measurable advancement on 2-3 key business initiatives

## 🧠 Development Methodology

TBD – This section outlines the overall approach for AI-assisted development across three phases.

## 📖 Detailed Methodology Documentation

For comprehensive information about the AI-assisted development approach used in this project, see:

**[Development Methodology Documentation](docs/development-methodology.md)**

This document covers:
- Three-phase development strategy
- AI tool selection and usage patterns
- Sean Kochel's 8-Step Vibe Code System implementation
- Quality assurance and validation processes
- Weekly development workflow
- Lessons learned framework

The methodology is continuously updated based on real-world development experience and community feedback.

## 🤝 Contributing

This is currently a personal productivity system, but feedback and suggestions are welcome! Open an issue to discuss:
- Feature ideas
- Technical improvements  
- Workflow optimizations
- Integration suggestions

## 📄 License

MIT License - Feel free to adapt this system for your own productivity needs.

---

**Note**: This repository documents a real productivity system in active development. Features and implementations will evolve based on actual usage and effectiveness.
