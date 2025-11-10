# 🚀 QUICK START GUIDE - Using These Documents

**Last Updated:** November 10, 2025  
**Purpose:** How to use these planning documents with different AI tools  
**For:** You (Tyrrell) when starting any work session

---

## 📚 Document Overview

You have these documents:

1. **[MASTER_ROADMAP.md](./MASTER_ROADMAP.md)** - Bird's eye view of all projects
2. **[MULTI_AI_WORKFLOW.md](./MULTI_AI_WORKFLOW.md)** - How to orchestrate multiple AIs
3. **[CONTEXT_KEEPER.md](./CONTEXT_KEEPER.md)** - Chat archive system (stop-gap + full app)
4. **[LIFE_OS_DASHBOARD.md](./LIFE_OS_DASHBOARD.md)** - Dashboard project details
5. **[QUICK_START_GUIDE.md](./QUICK_START_GUIDE.md)** - This file!

---

## 🎯 Common Scenarios

### **Scenario 1: "I Need to Plan Something"**

**Use:** Claude (Web) in this project

**Steps:**
1. Start new chat in "Life OS Dashboard" project
2. Provide context:
   ```
   I'm working on [project name]. Here's the current state:
   [Paste relevant section from MASTER_ROADMAP.md or project doc]
   
   I need to: [what you want to do]
   ```
3. Get strategic advice, breakdowns, tradeoff analysis
4. At end of session: Archive chat to Context Keeper

**Example:**
```
I'm working on Life OS Dashboard. Currently at Phase 3 (auth complete).
Need to plan Phase 4 (Item model migration).

Current state:
- 3 habits in Habit table
- Empty Item table ready
- Old Flask code has reference implementation

Should I migrate now or build more features first? What's the tradeoff?
```

---

### **Scenario 2: "I Need to Implement Something"**

**Use:** Claude Code

**Steps:**
1. Open Claude Code session
2. Provide implementation context:
   ```
   Continuing [project name] - [current phase]
   
   Task: [specific implementation task]
   
   Context:
   - Repository: [repo URL]
   - Branch: [branch name]
   - Current state: [brief state]
   
   Implementation plan: [paste from planning session with Claude]
   
   Ready to start?
   ```
3. Let Claude Code work
4. Pull changes: `git pull origin master`
5. Test locally
6. Archive session to Context Keeper

**Example:** See "Phase 4 Jump-Off Document" in LIFE_OS_DASHBOARD.md

---

### **Scenario 3: "Is Feature X in My Codebase?"**

**Use:** Gemini CLI

**Steps:**
1. Open terminal in your project
2. Run query:
   ```bash
   gemini -p "@src/ @lib/ Is [feature] implemented?"
   ```
3. Gemini analyzes entire codebase
4. Use findings to inform next steps

**Example:**
```bash
cd ~/projects/dashboard
gemini -p "@app/ @components/ Is dark mode implemented anywhere?"
```

---

### **Scenario 4: "I Forgot What I Was Working On"**

**Use:** Context Keeper (when built) or markdown archives

**Steps:**
1. Search your archives:
   - **Git:** `grep -r "topic" ~/context-archive/chats/`
   - **VS Code:** Open archive folder, use search
   - **Context Keeper app:** Use search feature
2. Find relevant past conversation
3. Read to remember context
4. Continue work with that context

---

### **Scenario 5: "Starting a New Project"**

**Steps:**
1. Read MASTER_ROADMAP.md - add new project
2. Create project-specific doc (like LIFE_OS_DASHBOARD.md)
3. Start planning chat with Claude (web)
4. Archive that planning session
5. Create implementation plan
6. Take to Claude Code or appropriate tool

---

## 🤖 Which AI to Use When

### **Quick Decision Tree:**

```
Need to PLAN or DECIDE?
└─> Claude (Web)

Need to IMPLEMENT in code?
└─> Claude Code

Need to ANALYZE large codebase?
└─> Gemini CLI

Need to BUILD standalone tool?
└─> Replit (with AI)

Need to FIND past work?
└─> Context Keeper / grep archives

Need to COORDINATE projects?
└─> Claude (Web) + MASTER_ROADMAP.md
```

---

## 💬 How to Start Chats

### **With Claude (Web) - Planning**

**Template:**
```
[PROJECT] - [What I need]

Quick context:
[2-3 sentence state]

Current task: [What you need help with]

[Any relevant details]
```

**Real Example:**
```
Life OS Dashboard - Planning Phase 4

Quick context:
Family productivity hub. Next.js app. Phase 3 (auth) complete. 
Have 3 test habits using temporary Habit model.

Current task: Decide if I should migrate to Item model now or later

Item model enables tasks/reminders/meals. Migration is easy now 
(3 habits) but will be hard later (100+ items). What's the best approach?
```

---

### **With Claude Code - Implementation**

**Template:**
```
Continuing [PROJECT] - [Phase/Task]

TASK: [Specific implementation]

CONTEXT:
- Repository: [URL]
- Branch: [branch]
- Current state: [1-2 sentences]

TARGET STATE: [What should exist after]

STEPS: [If you have a plan]
1. [Step 1]
2. [Step 2]

Ready to start?
```

**Real Example:** See LIFE_OS_DASHBOARD.md "Phase 4 Jump-Off Document"

---

### **With Gemini CLI - Analysis**

**Just run the command:**
```bash
gemini -p "@src/ Your question about the codebase?"
```

---

## 📂 Where Things Live

### **Planning Documents**
**Location:** Wherever you save these files (recommend: `~/projects/docs/`)

**How to Use:**
- Keep them updated as projects evolve
- Reference them when starting sessions
- Copy relevant sections to AI chats
- Version control them (git)

---

### **Chat Archives**
**Location:** `~/context-archive/` or `~/projects/context-archive/`

**Structure:**
```
context-archive/
├── chats/
│   ├── claude/
│   │   └── 2025-11-10_multi-ai-workflow-planning.md
│   ├── claude-code/
│   │   └── 2025-11-09_dashboard-phase3-auth.md
│   └── gemini/
└── extracted/
    ├── commands/
    ├── snippets/
    └── decisions/
```

---

### **Project Code**
**Location:** `~/projects/[project-name]/`

**Common projects:**
- `~/projects/dashboard/` - Life OS Dashboard
- `~/projects/context-keeper/` - Chat archive app (future)
- [Your other projects]

---

## 🔄 Typical Work Session Flow

### **Starting Work:**

```
1. Check MASTER_ROADMAP.md
   └─> What am I working on? What's the priority?

2. Open relevant project doc
   └─> What's the current state? What's next?

3. Decide which AI to use
   └─> Planning? Implementation? Analysis?

4. Start chat with context
   └─> Use templates above

5. Do the work
   └─> Follow AI guidance, iterate

6. Archive the session
   └─> Copy chat to Context Keeper

7. Update project docs
   └─> Update current state, decisions made

8. Commit changes (if code)
   └─> git add . && git commit -m "What you did"
```

---

### **Example: Adding a Feature**

```
Session Start (10 min):
├─> Read LIFE_OS_DASHBOARD.md (current state)
├─> Start chat with Claude (web): "I want to add feature X"
└─> Plan approach, get implementation steps

Implementation (1-2 hours):
├─> Open Claude Code
├─> Paste implementation plan
├─> Let Claude Code work
├─> Pull changes: git pull origin master
├─> Test locally: npm run dev
└─> Fix any issues with Claude Code

Wrap Up (10 min):
├─> Archive both chats (planning + implementation)
├─> Update LIFE_OS_DASHBOARD.md (what's done, what's next)
├─> Commit: git add . && git commit -m "Added feature X"
└─> Push: git push origin master
```

---

## 🔍 Finding Information Fast

### **Question: "What was that command for...?"**

**Answer:**
```bash
# If using git archive
grep -r "command topic" ~/context-archive/chats/

# If using Context Keeper app
[Use search feature when built]

# If in project docs
grep -r "command" ~/projects/docs/
```

---

### **Question: "What did Claude Code say about...?"**

**Answer:**
```bash
# Search Claude Code archives
grep -r "topic" ~/context-archive/chats/claude-code/

# Or use VS Code search
# Open ~/context-archive in VS Code
# Ctrl+Shift+F / Cmd+Shift+F
# Search for topic in chats/claude-code/
```

---

### **Question: "What's the current state of project X?"**

**Answer:**
1. Open `[PROJECT].md` file
2. Look at "Current State" section
3. Check "Decision Log" for key decisions
4. Review "Phase Summaries" for history

---

## 📝 Keeping Documents Updated

### **When to Update:**

**MASTER_ROADMAP.md:**
- ✅ When priorities change
- ✅ When adding new project
- ✅ Weekly review (check progress)

**MULTI_AI_WORKFLOW.md:**
- ✅ When discovering better workflow
- ✅ When adding new AI tool
- ✅ When finding useful command

**CONTEXT_KEEPER.md:**
- ✅ When changing archive process
- ✅ After building app features

**[PROJECT].md:**
- ✅ After completing a phase
- ✅ When making key decisions
- ✅ After troubleshooting sessions
- ✅ When discovering useful commands

---

### **How to Update:**

```
1. Open document in editor

2. Find relevant section

3. Add/update content

4. Save file

5. If using git:
   git add docs/
   git commit -m "Update docs: [what you changed]"
   git push
```

---

## 🎯 Success Indicators

### **You're Using This Well When:**

- ✅ Can start any AI session in < 2 minutes
- ✅ Don't repeat yourself explaining context
- ✅ Can find past work in < 30 seconds
- ✅ Know which AI to use without thinking
- ✅ Update docs naturally without friction
- ✅ New sessions build on past sessions

### **Signs You Need to Adjust:**

- ❌ Still spending 10+ minutes explaining context
- ❌ Can't find that conversation from last week
- ❌ Using wrong AI for tasks (wasting time)
- ❌ Docs are out of date (not useful)
- ❌ Repeating same troubleshooting

**If you see these signs:** Review MULTI_AI_WORKFLOW.md and iterate on your process

---

## 💡 Pro Tips

### **Tip 1: Start Small**
Don't try to use everything at once:
1. Week 1: Use templates, archive important chats
2. Week 2: Update project docs after sessions
3. Week 3: Use Gemini CLI for analysis
4. Week 4: Review and refine process

---

### **Tip 2: Use Aliases**
Add to your `.bashrc` or `.zshrc`:

```bash
# Quick access to docs
alias docs="cd ~/projects/docs && code ."

# Quick search of archives
alias searchch="grep -r"

# Start dev environment
alias dashdev="cd ~/projects/dashboard && npm run dev"
```

---

### **Tip 3: Weekly Review**
Every Sunday (or your preferred day):
1. Review MASTER_ROADMAP.md (5 min)
2. Update project docs with week's progress (10 min)
3. Archive any un-archived important chats (10 min)
4. Plan next week's priorities (5 min)

**Total:** 30 minutes keeps everything organized

---

### **Tip 4: Tag Consistently**
Use consistent tags in archives:
- `#planning` - Strategic planning sessions
- `#implementation` - Coding sessions
- `#troubleshooting` - Debugging
- `#decision` - Important decisions made
- `#solved` - Problems that were solved
- `#blocked` - Currently blocked on something
- `#reference` - Useful reference material

Makes search SO much easier!

---

### **Tip 5: Context Over Completion**
When archiving chats:
- Don't worry about making it perfect
- Focus on capturing context and key decisions
- You can always search full transcript later
- Summary > perfectionism

---

## 🚨 Common Mistakes to Avoid

### **Mistake 1: Not Providing Context**
❌ Bad: "Help me add dark mode"
✅ Good: "Life OS Dashboard (Next.js). Need dark mode. Current setup: Tailwind CSS. Where should I start?"

---

### **Mistake 2: Using Wrong AI**
❌ Don't: Ask Claude Code to plan your architecture
❌ Don't: Ask Claude (web) to edit files
❌ Don't: Skip Gemini CLI for large codebase questions

✅ Do: Follow decision tree in MULTI_AI_WORKFLOW.md

---

### **Mistake 3: Not Archiving**
❌ "I'll remember this" - You won't
✅ Archive immediately after session while context is fresh

---

### **Mistake 4: Outdated Docs**
❌ Docs from 3 weeks ago with wrong current state
✅ Update docs at end of each session (2 minutes)

---

### **Mistake 5: Over-engineering**
❌ Spending 2 hours creating perfect archive system
✅ Use stop-gap, iterate based on real needs

---

## 📋 Checklists

### **Before Starting Work:**
- [ ] Know which project I'm working on
- [ ] Know current state (read project doc)
- [ ] Know what I want to accomplish
- [ ] Chosen right AI for the task
- [ ] Have context ready to paste

---

### **After Completing Work:**
- [ ] Archive important chats
- [ ] Update project doc (current state, decisions)
- [ ] Commit code changes (if applicable)
- [ ] Note any blockers or next steps
- [ ] Capture useful commands/snippets

---

### **Weekly Review:**
- [ ] Review MASTER_ROADMAP.md
- [ ] Update all project docs
- [ ] Archive any un-archived chats
- [ ] Clean up command library
- [ ] Plan next week

---

## 🔗 Related Documents

- **[MASTER_ROADMAP.md](./MASTER_ROADMAP.md)** - Overall project organization
- **[MULTI_AI_WORKFLOW.md](./MULTI_AI_WORKFLOW.md)** - AI orchestration guide
- **[CONTEXT_KEEPER.md](./CONTEXT_KEEPER.md)** - Chat archive system
- **[LIFE_OS_DASHBOARD.md](./LIFE_OS_DASHBOARD.md)** - Dashboard project

---

## 🎬 Next Steps

1. ✅ Read this guide (you're doing it!)
2. ⬜ Set up Context Keeper stop-gap (15 min)
3. ⬜ Archive this planning session (5 min)
4. ⬜ Try one workflow with a real task
5. ⬜ Update docs after that task
6. ⬜ Iterate based on what works

---

**Remember:** These documents exist to HELP you, not burden you. Start simple, use what's useful, ignore what's not. The goal is efficiency and capturing knowledge, not perfection.

**You got this!** 🚀

---

**Questions?** Start a chat with Claude (web) and ask! That's what we're here for.
