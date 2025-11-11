# 🎯 MASTER PROJECT LIST

**Last Updated:** November 10, 2025  
**Owner:** Tyrrell Foster  
**Purpose:** Single source of truth for all projects, shared between Claude and Gemini

---

## 📊 Quick Status Overview

- 🟢 **Active:** 3 projects (Home Server, Workflow, Dashboard)
- 🟡 **Planned:** 9 projects
- 🔵 **Research:** 2 projects
- ⚪ **Brainstorming:** 2 projects
- 🔴 **On Hold:** 1 project (Skylight)

---

## 🟢 ACTIVE PROJECTS

### P1: Home Server Build
**Status:** 🟢 ACTIVE | **Priority:** HIGH  
**Started:** November 2025

**Goal:**  
Convert i5-8400 desktop into 24/7 home server for self-hosting services.

**Hardware:**
- i5-8400 Desktop (8GB RAM, SSD)
- CyberPower CP825AVRLCD UPS
- Running Ubuntu Server 24.04 LTS

**Features to Implement:**
- ✅ Ubuntu Server 24.04 LTS
- SSH access
- Tailscale VPN
- Docker containerization
- Pi-hole (DNS-level ad blocking)
- Plex Media Server (migrated from Power Dev)
- Recipe management app (Tandoor/Mealie)
- AI Router/Manager app

**Current Phase:** Phase 1, Step 1 - Installing Ubuntu Server 24.04 LTS

**Next Action:**
- Complete Ubuntu Server installation on SSD
- Document SSH setup process

**Dependencies:**
- None (foundation for other projects)

**Enables:**
- P7: Recipe Management (hosting)
- P5: AI Router/Manager (hosting)
- P11: Plex Migration (hosting)
- P10: MyPandora (hosting)

**AI Tool Suggestions:**
- Planning/Architecture: Claude Pro
- Troubleshooting: Gemini CLI (terminal-based server work)
- Documentation: Either Claude or Gemini

**Related Projects:** P7, P5, P11, P10

---

### P2: Personal Workflow Optimization
**Status:** 🟢 ACTIVE RESEARCH | **Priority:** HIGH  
**Started:** November 2025

**Goal:**  
Finalize 2-phone system and build robust workflow for task management and idea capture.

**Hardware:**
- Personal: Samsung Fold 6 (Spectrum Mobile)
- Work: Samsung Galaxy S24 5G (Verizon)
- Wearable: Garmin Fenix 8

**Current System:**
- Tasks: OneNote/Outlook (evaluating)
- Calendar: Outlook (work), Google Calendar (personal)
- Notes: OneNote (work), looking for personal solution

**Research Questions:**
- Best task management approach (Outlook Tasks vs. OneNote vs. Dashboard)
- Voice-to-task capture workflow (Gemini, Bixby, Garmin)
- Cross-device sync strategy
- Integration with P3: Life OS Dashboard

**Next Action:**
- Define task capture workflow (voice → where does it go?)
- Test Gemini voice assistant on Fold 6
- Determine if Dashboard replaces or complements Outlook

**Dependencies:**
- P3: Dashboard (may replace task system)
- P12: Voice-to-Task (extends this workflow)

**Enables:**
- P12: Voice-to-Task & Home Control

**AI Tool Suggestions:**
- Workflow design: Claude Pro (strategic planning)
- Gemini integration testing: Gemini Pro (native Google ecosystem)
- Quick experiments: Gemini CLI

**Related Projects:** P3, P12

---

### P3: Life OS Dashboard
**Status:** 🟢 ACTIVE (with Claude) | **Priority:** HIGH  
**Started:** November 2025 (migrating from earlier Replit version)

**Goal:**  
Central productivity hub for habits, tasks, reminders, meal planning, grocery lists, calendar integration, and family coordination.

**Tech Stack:**
- **Current:** Next.js 16, TypeScript, Tailwind CSS, Prisma ORM, SQLite, NextAuth.js
- **Previous:** Python/Flask on Replit (~3,500 lines)

**Current State:**
- ✅ Phase 1: Foundation (Next.js setup)
- ✅ Phase 2: Core functionality (habits CRUD)
- ✅ Phase 3: Authentication (Google OAuth)
- 🎯 Phase 4: Item Model Migration (NEXT)

**Phase 4 Details:**
- Migrate from simplified Habit model to unified Item model
- Item types: habits, tasks, reminders, meals
- Preserve 3 existing test habits
- Enable future features (tasks, reminders, meal planning)

**Planned Features:**
- Health tracking integration
- Fitness program tracking
- Recipe integration (from P7)
- Family sharing/multi-user
- Calendar integration (Google Calendar)
- Voice input via AI Assistant (from P5)

**Next Action:**
- Execute Phase 4: Habit → Item model migration
- Use Claude Code for implementation
- Test that existing habits still work

**Dependencies:**
- None (standalone for now)

**Enables:**
- P2: Workflow (becomes task management system)
- P7: Recipe Management (provides data to dashboard)
- P5: AI Router (provides AI interface to dashboard)

**AI Tool Suggestions:**
- Strategic planning: Claude Pro
- Implementation: Claude Code (web or VS Code)
- Codebase analysis: Gemini CLI
- Quick questions: Gemini Code Assist (in VS Code)

**Repository:** github.com/fostertt/dashboard  
**Documentation:** See LIFE_OS_DASHBOARD.md in docs repo

**Related Projects:** P2, P5, P7

---

## 🟡 PLANNED / HIGH-PRIORITY PROJECTS

### P4: Garage Cleanout
**Status:** 🟡 PLANNED | **Priority:** MEDIUM  
**Type:** Physical project

**Goal:**  
Clear and organize garage to create dedicated workout space.

**Why It Matters:**  
Physical dependency for health & fitness goals tracked in P3: Dashboard.

**Next Action:**
- Schedule cleanout weekend
- Identify items to donate/trash/keep
- Plan storage solutions

**Dependencies:**
- None (but blocks fitness routine)

**Enables:**
- Better tracking of fitness in P3: Dashboard (when space is ready)

**AI Tool Suggestions:**
- Planning/organization: Claude Pro or Gemini Pro
- Garage layout design: Claude Pro (can generate ideas)

**Related Projects:** P3

---

### P5: AI Router/Manager
**Status:** 🟡 HIGH-PRIORITY, PLANNED | **Priority:** HIGH  
**Started:** Concept phase

**Goal:**  
Build intelligent routing system to manage multiple AI services (Claude, Gemini, local LLM) with rate limit awareness and calendar integration.

**Features:**
- Route prompts to appropriate AI (Claude for reasoning, Gemini for data, local for privacy)
- Track rate limits across services
- Calendar-aware for proactive suggestions
- Cost tracking and optimization
- Integration with P3: Dashboard (voice interface)

**Tech Stack:**
- Next.js
- API integrations: Claude API, Gemini API, local LLM
- Hosted on P1: Home Server

**Next Action:**
- Design routing logic (which AI for what task?)
- Map out rate limits for each service
- Sketch basic UI

**Dependencies:**
- P1: Home Server (hosting)

**Enables:**
- P3: Dashboard (AI interface)
- P12: Voice-to-Task (AI backend)
- Better cost management across AI services

**AI Tool Suggestions:**
- Architecture design: Claude Pro (complex system design)
- Implementation: Mix of Claude Code and Gemini Code Assist
- API testing: Gemini CLI

**Budget Notes:**
- Claude API: ~$5-10/month for light use
- Gemini API: Included with AI Pro subscription (potentially free)
- Could save money by routing appropriately

**Related Projects:** P1, P3, P12

---

### P8: Deck Finishing
**Status:** 🟡 PLANNED | **Priority:** MEDIUM  
**Type:** Physical project

**Goal:**  
Complete final detail and finishing work on deck.

**Next Action:**
- List remaining tasks
- Schedule completion date
- Purchase any needed materials

**Dependencies:** None

**AI Tool Suggestions:**
- Project planning: Claude or Gemini
- Material calculations: Either AI

---

### P9: Small Home Fixes
**Status:** 🟡 PLANNED | **Priority:** MEDIUM  
**Type:** Physical project

**Goal:**  
Knock out high-visibility home maintenance tasks.

**Task List:**
1. Caulk 1/2 bath
2. Caulk fireplace  
3. Install door on master bath water closet

**Next Action:**
- Purchase caulk and supplies
- Schedule DIY day

**Dependencies:** None

**AI Tool Suggestions:**
- How-to guides: Gemini Pro (can search for tutorials)
- Material lists: Either AI

---

### P11: Plex Migration
**Status:** 🟡 PLANNED | **Priority:** MEDIUM  

**Goal:**  
Migrate Plex Media Server from Power Dev desktop to home server, preserving Plex Pass and watch history.

**Current Setup:**
- Running on Power Dev Desktop (32GB RAM, GTX 1080)
- Plex Pass active
- Extensive watch history database
- Media library location: [TBD - document current location]

**Migration Plan:**
1. Backup Plex database and metadata
2. Install Plex on P1: Home Server
3. Transfer media files (or set up network share)
4. Restore database to preserve watch history
5. Update Plex Pass to new server
6. Test playback on all devices

**Next Action:**
- Document current Plex setup (media location, settings)
- Research Plex migration best practices
- Plan downtime window

**Dependencies:**
- P1: Home Server (must be operational)

**Benefits:**
- Reduce streaming costs (goal: cut subscriptions)
- 24/7 availability (vs desktop that shuts down)
- Free up Power Dev for P6: AI/LLM work

**AI Tool Suggestions:**
- Migration planning: Claude Pro
- Troubleshooting: Gemini CLI (terminal-based server work)
- Finding tutorials: Gemini Pro (web search)

**Related Projects:** P1, P6

---

### P12: Voice-to-Task & Home Control
**Status:** 🟡 PLANNED | **Priority:** MEDIUM  

**Goal:**  
Use voice assistants and wearables for hands-free task capture and smart home control.

**Hardware:**
- Samsung Fold 6 (Gemini assistant, Bixby)
- Garmin Fenix 8 (voice commands)
- Smart home devices (existing setup)

**Use Cases:**
- "Add milk to grocery list" → appears in P3: Dashboard
- "Remind me to call mom at 3pm" → creates reminder
- "What's on my calendar tomorrow?" → reads from Outlook/Google
- "Turn off bedroom lights" → controls smart home
- Voice input while driving, working out, cooking

**Integration Points:**
- P2: Workflow (how voice commands flow)
- P3: Dashboard (receives task data)
- P5: AI Router (processes voice → appropriate action)

**Next Action:**
- Test Gemini voice assistant capabilities on Fold 6
- Research Garmin voice command options
- Design voice → task workflow

**Dependencies:**
- P2: Workflow definition
- P3: Dashboard (for task/reminder storage)
- P5: AI Router (optional but ideal)

**AI Tool Suggestions:**
- Workflow design: Claude Pro
- Gemini integration: Gemini Pro (native ecosystem)
- Testing: Hands-on with devices

**Related Projects:** P2, P3, P5

---

### P13: NFL Web Scraping Tool
**Status:** 🟡 PLANNED | **Priority:** LOW  

**Goal:**  
Build Python tool to scrape, store, and analyze NFL stats including gambling data (for analysis, not gambling).

**Tech Stack:**
- Python
- Web scraping (BeautifulSoup/Scrapy)
- Database (PostgreSQL or SQLite)
- Data analysis (Pandas, potentially ML models)

**Data Sources:**
- NFL official stats
- Pro Football Reference
- ESPN
- Betting odds (for modeling, not actual gambling)

**Use Cases:**
- Data analysis and modeling
- Prediction algorithms
- Discover interesting patterns
- Learning exercise in data science

**Next Action:**
- Research legal/ethical web scraping practices
- Identify best data sources
- Design database schema

**Dependencies:**
- Could host on P1: Home Server (optional)

**AI Tool Suggestions:**
- Python coding: Claude Code or Gemini Code Assist
- Data analysis strategy: Claude Pro
- Web scraping troubleshooting: Gemini CLI

**Related Projects:** P1 (hosting), P6 (could use for ML practice)

---

### P15: Repurpose Hardware
**Status:** 🟡 PLANNED / 🔴 SOME ON HOLD | **Priority:** LOW  

**Goal:**  
Find productive uses for collection of spare hardware.

**Hardware Inventory & Ideas:**

**Surface Go (P2):**
- Potential: Family hub with DAKboard
- Potential: Dedicated display for P3: Dashboard
- Status: 🟡 Planned
- Next: Decide between DAKboard vs Dashboard display

**Skylight Calendar (P1):**
- Original idea: Replace with DAKboard
- Status: 🔴 On Hold (Surface Go may replace this need)

**Raspberry Pis (P6):**
- 1x Pi 2
- 2x Pi 3B+
- 1x Pi Zero W
- Potential: Learning projects, sensor stations, mini servers
- Status: 🟡 Planned for tinkering

**Old Tablets (P10):**
- 2x Fire Tablets (toolbox installed, limited capability)
- 1x Lenovo Tablet (stripped down)
- Potential: Dashboard displays, dedicated app screens
- Status: 🟡 Brainstorming

**Samsung Galaxy S7 Tablets:**
- 1x Large
- 1x Normal size
- Potential: Better candidates for dashboard displays
- Status: 🟡 Planned

**Old Kindles (P10):**
- E-ink displays
- Potential: Status displays, calendar, simple dashboards
- Status: ⚪ Brainstorming (low priority)

**Spare Phones:**
- Moto G (status uncertain)
- Pixel 6 (status uncertain)
- Potential: Dedicated smart home controller, security camera
- Status: ⚪ Brainstorming

**Next Action:**
- Test Samsung tablets as dashboard displays
- Research DAKboard for Surface Go
- Inventory and test spare phones

**Dependencies:**
- P3: Dashboard (provides content for displays)
- P1: Home Server (could serve dashboard to devices)

**AI Tool Suggestions:**
- Hardware project ideas: Claude Pro or Gemini Pro
- Pi programming: Claude Code or Gemini Code Assist
- Troubleshooting: Gemini CLI

**Related Projects:** P1, P3, P6

---

## 🔵 RESEARCH PHASE

### P6: AI/LLM Experimentation
**Status:** 🔵 RESEARCH PHASE | **Priority:** MEDIUM  

**Goal:**  
Run and experiment with local LLMs on Power Dev desktop.

**Hardware:**
- Power Dev Desktop
- OS: Windows 10 Pro / WSL2
- CPU: High-end (adequate)
- RAM: 32GB
- Current GPU: GTX 1080 (8GB VRAM)
- PSU: 850W Platinum P2 (supports upgrades)

**Current Limitation:**  
GTX 1080 has only 8GB VRAM - insufficient for larger models.

**GPU Upgrade Research:**
- RTX 3060 12GB (~$250-300 used)
- RTX 4060 Ti 16GB (~$450-500)
- Budget: TBD
- Goal: Run 13B+ models locally

**Use Cases:**
- Privacy-focused AI (local processing)
- Experimenting with model fine-tuning
- Learning about LLM architectures
- Feeding into P5: AI Router (local option)

**Next Action:**
- Research GPU market prices
- Determine budget for upgrade
- Test current setup with smaller models (7B)
- Learn Ollama or LM Studio

**Dependencies:**
- P11: Plex Migration (frees up this machine)

**Enables:**
- P5: AI Router (adds local LLM option)
- Learning/experimentation with AI

**AI Tool Suggestions:**
- GPU research: Gemini Pro (price tracking, comparisons)
- LLM setup help: Claude Pro (technical guidance)
- Troubleshooting: Gemini CLI

**Related Projects:** P5, P11

---

### P7: Recipe Management System
**Status:** 🔵 RESEARCH PHASE | **Priority:** MEDIUM  

**Goal:**  
Find or build system to save, search, and manage recipes.

**Requirements:**
- Save recipes from web, AI chats, photos
- Search by ingredients, cuisine, meal type
- Generate grocery lists
- Integration with P3: Dashboard
- Mobile-friendly (kitchen access)

**Research: Buy vs Build**

**Self-Hosted Options:**
- Tandoor Recipes (feature-rich, active development)
- Mealie (simpler, clean UI)
- Both can run in Docker on P1: Home Server

**Build Custom:**
- Integrate directly into P3: Dashboard
- Full control over features
- More development time

**Next Action:**
- Test Tandoor Recipes in Docker
- Test Mealie in Docker
- Compare features vs. building custom
- Decide: self-hosted app or dashboard module?

**Dependencies:**
- P1: Home Server (hosting for self-hosted option)
- P3: Dashboard (integration target)

**Enables:**
- P3: Dashboard (meal planning feature)
- Better meal planning and grocery management

**AI Tool Suggestions:**
- App comparison: Claude Pro (detailed analysis)
- Docker setup: Gemini CLI (terminal work)
- Custom build planning: Claude Pro

**Related Projects:** P1, P3

---

## ⚪ BRAINSTORMING / LOW PRIORITY

### P10: MyPandora Media Server
**Status:** ⚪ BRAINSTORMING | **Priority:** LOW  

**Goal:**  
Create unified music experience using local library + YouTube for discovery.

**Current Pain Points:**
- Pandora: Limited control, ads, repetitive
- YouTube Music: Great discovery, poor playlisting
- Local library: Full control but static

**Vision:**
- Local music via Plexamp or Navidrome
- YouTube integration for discovery
- Smart playlisting (better than Pandora)
- Unified interface

**Tech Stack:**
- Navidrome or Plexamp (local music server)
- YouTube API or scraping
- Custom web interface
- Hosted on P1: Home Server

**Next Action:**
- Research feasibility
- Test Navidrome vs Plexamp
- Investigate YouTube API limitations

**Dependencies:**
- P1: Home Server (hosting)
- P11: Plex Migration (if using Plexamp)

**AI Tool Suggestions:**
- Architecture brainstorming: Claude Pro
- API research: Gemini Pro
- Implementation: Claude Code

**Related Projects:** P1, P11

---

### P14: Replit Utilization Strategy
**Status:** ⚪ BRAINSTORMING | **Priority:** LOW  

**Goal:**  
Identify high-value uses for 3-month Replit Pro subscription.

**Replit Pro Features:**
- AI agent for coding
- Always-on deployments (no sleep)
- Boosted compute
- Private repls

**Potential Uses:**
- Prototyping new features for P3: Dashboard
- Building P5: AI Router prototype
- Quick experiments and learning
- Small utility apps

**After 3 Months:**
- Migrate important projects elsewhere
- Evaluate if Pro worth continuing
- Likely drop to free tier

**Next Action:**
- Test Replit AI agent with small project
- Identify 1-2 experiments to run during Pro period

**AI Tool Suggestions:**
- Strategy: Claude Pro (prioritization)
- Replit usage: Replit's own AI agent

**Related Projects:** Could prototype for P3, P5, P7, P13

---

## 🆕 NEW PROJECTS (from today)

### P16: Context Management System
**Status:** 🟢 ACTIVE | **Priority:** HIGH  
**Started:** November 10, 2025

**Goal:**  
Maintain shared context between Claude, Gemini, and self across all projects.

**Components:**
- This master project list (PROJECT_MASTER_LIST.md)
- Key decision documents in ~/projects/docs/
- GitHub repo for version control
- Memory systems in Claude & Gemini
- Selective chat archiving (major breakthroughs only)

**Strategy:**
- Master docs live in GitHub
- Both Claude and Gemini reference same files
- Updates flow: You edit → Push to GitHub → Both AIs see latest
- Archive only critical sessions (not everything)

**Next Action:**
- Push this file to ~/projects/docs/ on GitHub
- Test referencing it in both Claude and Gemini chats
- Archive today's major planning session

**Dependencies:** None

**Enables:** All projects (better context management)

**AI Tool Suggestions:**
- Document creation: Claude Pro (this file!)
- Gemini sync testing: Gemini Pro
- Maintenance: Whoever you're talking to

**Related Projects:** ALL (foundational)

---

## 📊 Priority Matrix

### Work On Next (High Impact, Ready to Start):
1. **P3: Dashboard Phase 4** - Migration unblocks future features
2. **P1: Home Server** - Foundation for multiple projects
3. **P2: Workflow** - Daily productivity impact

### High Priority But Needs Planning:
4. **P5: AI Router** - High value but complex
5. **P7: Recipe Management** - Finish research first

### Good for Later:
6. **P4: Garage** - Physical project, schedule when ready
7. **P11: Plex** - After server is stable
8. **P6: AI/LLM** - After budget decision on GPU

### Lower Priority:
9. **P12: Voice** - Nice to have, not critical
10. **P13: NFL** - Fun project, no urgency
11. **P15: Hardware** - As time allows
12. **P8, P9: Home fixes** - Batch these together

### Brainstorming:
13. **P10: MyPandora** - Explore when inspired
14. **P14: Replit** - Opportunistic use

---

## 🔗 Project Dependencies Map

```
P1: Home Server (Foundation)
├── P5: AI Router (needs hosting)
├── P7: Recipe Management (needs hosting)
├── P11: Plex Migration (migrates TO server)
└── P10: MyPandora (needs hosting)

P3: Dashboard (Hub)
├── P2: Workflow (may replace task system)
├── P5: AI Router (provides AI interface)
├── P7: Recipe Management (provides data)
└── P12: Voice (provides input method)

P2: Workflow (Daily Driver)
├── P3: Dashboard (may integrate)
└── P12: Voice (extends workflow)

P6: AI/LLM (Learning)
├── P11: Plex Migration (frees up hardware)
└── P5: AI Router (adds local option)
```

---

## 💰 Budget Tracking

**Monthly AI Costs:**
- Claude Pro: $20/month
- Google AI Pro: $20/month
- Occasional Claude credits: ~$10-30/month
- **Total: $40-70/month**

**Hardware Budget Items:**
- GPU upgrade for P6: $250-500 (one-time, TBD)
- UPS for server: ✅ Already have
- Server storage: May need expansion later

**Replit Pro:**
- Free for 3 months (promo)
- Then: Likely drop to free tier

---

## 📝 AI Tool Usage Guide

**Claude Pro (Strategic Planning):**
- P3: Dashboard architecture
- P5: AI Router design
- Complex project planning
- Document creation (like this!)

**Claude Code (Implementation):**
- P3: Dashboard coding
- P5: AI Router coding
- P7: Custom recipe app (if building)

**Gemini Pro (Research & Google Ecosystem):**
- P2: Workflow with Google services
- P6: GPU research and prices
- P7: Recipe app comparison

**Gemini CLI (Terminal Work):**
- P1: Server setup and troubleshooting
- P6: LLM installation
- Codebase analysis

**Gemini Code Assist (Quick Coding):**
- Simple implementations in VS Code
- Quick fixes
- When saving Claude tokens

---

## 🎯 Success Metrics

**Weekly:**
- At least 1 project has forward progress
- No project completely stalled for 2+ weeks
- Time spent on projects tracked

**Monthly:**
- 1-2 projects completed or advanced significantly
- Budget staying within $40-70 for AI tools
- This list updated with learnings

**Quarterly:**
- Home server operational
- Dashboard feature-complete (habits, tasks, reminders)
- At least 3 other projects completed

---

## 📖 Document Change Log

**2025-11-10:** 
- Initial comprehensive master list created
- Merged inputs from Claude and Gemini contexts
- Added cross-references and dependencies
- Added P16: Context Management System
- Established as single source of truth

---

## 🔗 Related Documents

- **LIFE_OS_DASHBOARD.md** - Detailed dashboard project documentation
- **MULTI_AGENT_STRATEGY.md** - How to use AI tools effectively
- **GEMINI_CLI_SETUP_CORRECTED.md** - Gemini CLI installation guide
- **CLAUDE_MD_INTEGRATION.md** - Claude + Gemini integration

---

**This document is maintained collaboratively between Tyrrell, Claude, and Gemini.**  
**Always reference the latest version in GitHub before making project decisions.**
