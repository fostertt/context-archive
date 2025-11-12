# 🗺️ MASTER ROADMAP - Multi-Project Organization

**Last Updated:** November 10, 2025  
**Purpose:** Organize all active initiatives, show dependencies, and guide AI handoffs

---

## 📋 Current State Snapshot

- **AI Tools in Use:** Claude (web), Claude Code, Gemini CLI, ChatGPT, Replit Pro
- **Active Projects:** Life OS Dashboard, Context Keeper (planned), Home Server
- **Main Pain Point:** Context fragmentation across multiple AIs
- **Promo Credits:** Claude Code ($250 until Nov 18), Replit Pro, Gemini CLI (300 queries/90 days)

---

## 🎯 Track Priority & Dependencies

```
┌─────────────────────────────────────────────────────────────┐
│  TRACK 3: Multi-AI Workflow (DO FIRST) ⭐                   │
│  Status: PLANNING                                            │
│  Blocks: Everything else - establishes how to work          │
└─────────────────────────────────────────────────────────────┘
                              ↓
        ┌─────────────────────────────────────────┐
        │  TRACK 2: Context Keeper (DO SECOND) ⭐  │
        │  Status: DESIGN PHASE                    │
        │  - Stop-gap process (immediate)          │
        │  - Full app build (when ready)           │
        └─────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────┐
│  TRACK 1: Life OS Dashboard (READY WHEN YOU ARE)            │
│  Status: Phase 3 complete, Phase 4 ready to start           │
│  Dependency: Needs Context Keeper running for chat archive  │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│  TRACK 4: Home Server (BACKGROUND/AS NEEDED)                │
│  Status: Active and working, being managed elsewhere        │
│  Note: May be used for file storage if needed               │
└─────────────────────────────────────────────────────────────┘
```

---

## 📚 Track Summaries

### **Track 3: Multi-AI Workflow** 🔥 DO FIRST
**File:** `MULTI_AI_WORKFLOW.md`

**Goal:** Establish clear workflows for orchestrating multiple AIs efficiently

**Deliverables:**
- ✅ AI Usage Matrix (which AI for what task)
- ✅ Context handoff templates
- ✅ Gemini CLI + Claude Code workflow
- ✅ Command reference library
- ✅ Documentation standards

**Why First:** Solves context fragmentation for ALL projects

**Timeline:** 1-2 hours to design, then implement incrementally

---

### **Track 2: Context Keeper** 🔥 DO SECOND
**File:** `CONTEXT_KEEPER.md`

**Goal:** Archive and search all AI chats across platforms

**Two Phases:**

**Phase A: Stop-Gap Process (IMMEDIATE)**
- Manual process for archiving chats
- Folder structure for organization
- Naming conventions
- Basic search strategy
- Timeline: 15 minutes to set up

**Phase B: Full App Build (WHEN READY)**
- Replit-hosted web app
- Full-text search
- Auto-tagging and extraction
- Context summary generation
- Command library extraction
- Timeline: 4-6 hours to build initial version

**Why Second:** Solves immediate pain point, enables better AI usage

**Storage Decision Point:** 
- ⬜ GitHub repo (versioned, searchable)
- ⬜ OneDrive/Google Drive (accessible anywhere)
- ⬜ Home server (self-hosted)
- ⬜ Replit storage (lives with app)

---

### **Track 1: Life OS Dashboard** ⏸️ READY WHEN YOU ARE
**File:** `LIFE_OS_DASHBOARD.md`

**Current Status:** 
- ✅ Phase 1-3 complete (foundation, core features, auth)
- 🎯 Phase 4: Habit → Item model migration (next up)
- 📦 3 test habits in database
- 👤 User: Tyrrell Foster (tyrrellfoster@gmail.com)

**What's Needed:**
- Phase 4 jump-off document for Claude Code
- Decision: Do Item migration now vs. build more features first

**Dependencies:**
- Should have Context Keeper running to archive this work
- Multi-AI workflow established for efficient development

**Timeline:** Phase 4 estimated 2-3 hours implementation

**Repository:** github.com/fostertt/dashboard

---

### **Track 4: Home Server** 🔧 BACKGROUND
**Status:** Active and working, managed in separate chat/context

**Current Setup:**
- Pi-hole (265k blocked domains)
- Planning: NAS, Plex, Vaultwarden

**Potential Use Cases:**
- File storage for Context Keeper archives
- Self-hosting Context Keeper app (future)
- Development file sharing

**Action:** No immediate work needed unless required for other tracks

---

## 🚦 Decision Points

### **Decision Point 1: Context Keeper Storage** (Track 2)
**When:** During stop-gap setup  
**Options:**
1. GitHub repo in `~/context-archive/` (recommended for versioning)
2. Cloud storage (OneDrive/Drive) for easy access
3. Home server for privacy
4. Hybrid: Local + cloud backup

**Recommendation:** GitHub repo - searchable, versioned, accessible from any machine

---

### **Decision Point 2: Context Keeper Feature Scope** (Track 2)
**When:** Before building full app  
**Must Have:**
- ✅ Chat import (copy/paste)
- ✅ Full-text search
- ✅ Tag by: project, AI, date, topic

**Nice to Have:**
- 🔲 Command extraction & library
- 🔲 Context summary generation
- 🔲 AI usage tracking
- 🔲 Cost/token estimation (manual input OK)

**Decision:** Prioritize must-haves first, add nice-to-haves incrementally

---

### **Decision Point 3: Life OS Dashboard Phase 4** (Track 1)
**When:** After Context Keeper is operational  
**Options:**
1. Do Item migration now (clean slate, easier)
2. Build more features with Habit model, migrate later (faster features)

**Factors:**
- Current: 3 test habits (low migration cost)
- Future: 100+ items (high migration cost)
- Item model enables: tasks, reminders, meal planning

**Recommendation:** Do migration now while dataset is small

---

## 📅 Suggested Execution Order

### **This Week (Immediate)**
1. ✅ Review and finalize Multi-AI Workflow doc (30 min)
2. ✅ Implement stop-gap Context Keeper process (15 min)
3. ✅ Test workflow with a real chat archive (15 min)
4. ✅ Archive this planning session as first test case

### **This Week (When Ready)**
5. 📋 Design Context Keeper app database schema (1 hour)
6. 🏗️ Build Context Keeper MVP on Replit (3-4 hours)
7. 📝 Archive all existing important chats

### **Next Week (When Ready)**
8. 🎯 Execute Life OS Dashboard Phase 4 with Claude Code
9. 📊 Use new workflow to manage the Phase 4 work
10. 🔄 Iterate on Context Keeper based on real usage

---

## 🎯 Success Metrics

**Track 3 Success:**
- ✅ Can bring any AI up to speed in < 2 minutes
- ✅ No repeated "explain the project again" conversations
- ✅ Clear decision on which AI to use for each task type

**Track 2 Success:**
- ✅ Can find any past conversation in < 30 seconds
- ✅ All important chats archived and searchable
- ✅ Can generate context summaries for new AI chats

**Track 1 Success:**
- ✅ Item model migration complete
- ✅ All 3 test habits preserved and working
- ✅ Ready to build tasks, reminders, meal planning features

---

## 🔗 Related Documents

- **[MULTI_AI_WORKFLOW.md](./MULTI_AI_WORKFLOW.md)** - How to orchestrate AIs effectively
- **[CONTEXT_KEEPER.md](./CONTEXT_KEEPER.md)** - Chat archive system design
- **[LIFE_OS_DASHBOARD.md](./LIFE_OS_DASHBOARD.md)** - Dashboard project details
- **[QUICK_START_GUIDE.md](./QUICK_START_GUIDE.md)** - How to use these docs with AIs

---

## 💡 Notes for Future You

**Why This Order Matters:**
- Track 3 (workflow) teaches you HOW to work efficiently
- Track 2 (archive) captures WHAT you learn
- Track 1 (dashboard) is WHERE you apply it
- Track 4 (server) is INFRASTRUCTURE when needed

**When to Revisit This Roadmap:**
- Before starting any new project
- When switching between AI tools
- Weekly review to track progress
- When adding new tools/workflows

**Remember:**
- Not everything needs to be perfect before starting
- Stop-gap solutions are valuable
- Iterate based on real usage
- The goal is efficiency, not perfection

---

**Next Step:** Review `MULTI_AI_WORKFLOW.md` to establish working patterns 🚀
