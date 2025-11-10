# 🔗 CLAUDE.md INTEGRATION GUIDE

**Last Updated:** November 10, 2025  
**Purpose:** Set up Claude Code to automatically use Gemini CLI for analysis  
**Status:** Optional but Powerful

---

## 🎯 What This Does

**The Magic:**
- Claude Code can automatically call Gemini CLI
- Gemini analyzes large codebases (doesn't use Claude tokens!)
- Claude Code gets findings and implements (efficient token use)
- You get best of both worlds automatically

**Before Integration:**
```
You: "Claude Code, implement feature X"
Claude Code: Reads entire codebase → Uses tons of tokens → Implements
```

**After Integration:**
```
You: "Claude Code, implement feature X"
Claude Code: "I'll use Gemini CLI to analyze first..."
Gemini CLI: Analyzes codebase → Returns findings (free!)
Claude Code: Uses findings → Implements (minimal tokens!)
```

---

## 🤔 Should You Set This Up?

### **Yes, Set It Up If:**
```
✅ Working on large projects (> 1000 files)
✅ Want hands-off efficiency
✅ Budget-conscious (save Claude tokens)
✅ Comfortable with automation
✅ Trust Claude to make good decisions
```

### **No, Skip It If:**
```
❌ Small projects (overkill)
❌ Want manual control over every step
❌ Still learning how each tool works
❌ Prefer explicit tool usage
```

### **My Recommendation:**
Start without it (learn each tool manually), then add after 2-3 weeks when you understand the workflow.

---

## 📋 What is CLAUDE.md?

**CLAUDE.md** is a special file that Claude Code reads for project-specific instructions.

**Location:**
```
Your project root:
~/projects/dashboard/CLAUDE.md
```

**Purpose:**
- Tell Claude Code how to work on THIS specific project
- Project conventions, patterns, preferences
- Tool integration instructions
- Custom workflows

**Claude Code automatically looks for and reads this file!**

---

## 🚀 Setting Up Auto-Call Integration

### **Step 1: Create CLAUDE.md**

```bash
# Navigate to your project
cd ~/projects/dashboard

# Create the file
touch CLAUDE.md
```

---

### **Step 2: Add Gemini CLI Instructions**

Open `CLAUDE.md` in your editor and add:

```markdown
# Project: Life OS Dashboard

## Using Gemini CLI for Large Codebase Analysis

When analyzing large codebases or multiple files that might exceed context limits, use the Gemini CLI with its massive context window. Use `gemini -p` to leverage Google Gemini's large context capacity.

### When to Use Gemini CLI

Use `gemini -p` when you need to:
- Analyze entire directories or large portions of the codebase
- Verify if specific features, patterns, or implementations exist
- Understand project-wide architecture
- Find patterns across multiple files
- Work with files totaling more than 100KB
- Gather information before implementing changes

### File and Directory Inclusion Syntax

Use the `@` syntax to include files and directories in your Gemini prompts. Paths are relative to the project root:

#### Examples:

**Single file analysis:**
```bash
gemini -p "@src/main.py Explain this file's purpose and structure"
```

**Multiple files:**
```bash
gemini -p "@package.json @src/index.js Analyze the dependencies used in the code"
```

**Entire directory:**
```bash
gemini -p "@src/ Summarize the architecture of this codebase"
```

**Multiple directories:**
```bash
gemini -p "@src/ @tests/ Analyze test coverage for the source code"
```

**Current directory and all subdirectories:**
```bash
gemini -p "@./ Give me an overview of this entire project"
```

**Alternative flag:**
```bash
gemini --all_files -p "Analyze the project structure and dependencies"
```

### Implementation Verification Examples

**Check if a feature is implemented:**
```bash
gemini -p "@src/ @lib/ Has dark mode been implemented in this codebase? Show me the relevant files and functions"
```

**Verify authentication implementation:**
```bash
gemini -p "@src/ @middleware/ Is JWT authentication implemented? List all auth-related endpoints and middleware"
```

**Check for specific patterns:**
```bash
gemini -p "@src/ Are there any React hooks that handle WebSocket connections? List them with file paths"
```

**Verify error handling:**
```bash
gemini -p "@src/ @api/ Is proper error handling implemented for all API endpoints? Show examples"
```

**Check for rate limiting:**
```bash
gemini -p "@backend/ @middleware/ Is rate limiting implemented for the API? Show the implementation details"
```

**Verify caching strategy:**
```bash
gemini -p "@src/ @lib/ @services/ Is Redis caching implemented? List all cache-related functions"
```

**Check for security measures:**
```bash
gemini -p "@src/ @api/ Are SQL injection protections implemented? Show how user inputs are sanitized"
```

**Verify test coverage:**
```bash
gemini -p "@src/payment/ @tests/ Is the payment processing module fully tested? List all test cases"
```

### Important Notes

- Paths in @ syntax are relative to your current working directory (project root)
- The CLI will include file contents directly in the context
- No need for --yolo flag for read-only analysis
- Gemini's context window can handle entire codebases that would overflow Claude's context
- When checking implementations, be specific about what you're looking for to get accurate results
- Always analyze with Gemini BEFORE starting implementation to avoid wasting tokens

### Workflow

1. **First:** Use Gemini CLI to understand what exists
2. **Then:** Plan implementation based on findings
3. **Finally:** Implement the changes

This approach saves Claude tokens and provides comprehensive analysis before writing code.
```

---

### **Step 3: Add Project-Specific Context**

Continue in `CLAUDE.md` with your project details:

```markdown
## Project Overview

- **Name:** Life OS Dashboard
- **Tech Stack:** Next.js 16, TypeScript, Tailwind CSS, Prisma ORM, SQLite
- **Auth:** Google OAuth via NextAuth.js
- **Current Phase:** Phase 3 complete (auth working)
- **Next Phase:** Phase 4 - Migrate Habit model to Item model

## Key Files

- `app/api/` - API routes
- `app/dashboard/` - Main dashboard pages
- `components/` - React components
- `lib/prisma.ts` - Prisma client
- `prisma/schema.prisma` - Database schema

## Current User

- Tyrrell Foster (tyrrellfoster@gmail.com)
- 3 test habits in database

## Code Conventions

- Use TypeScript strict mode
- Tailwind for all styling
- Prisma for all database operations
- Server components by default, client components only when needed
- Error handling with try-catch and proper error messages

## Before Making Changes

1. Use Gemini CLI to verify current state
2. Check if feature already exists
3. Understand existing patterns
4. Then propose implementation approach
```

---

### **Step 4: Test It Works**

**Open Claude Code (web or VS Code) in your project:**

```
Test query:
"I want to add dark mode. Can you check if anything related to dark mode 
already exists in the codebase?"

Expected behavior:
Claude Code reads CLAUDE.md → Sees Gemini CLI instructions → 
Runs: gemini -p "@src/ @components/ Is dark mode implemented?" → 
Gets results → Tells you: "Gemini CLI found no dark mode. Here's where to add it..."
```

**If Claude Code uses Gemini CLI automatically:** ✅ Working!

**If Claude Code doesn't use Gemini CLI:** Claude might not have triggered it. You can explicitly request:
```
"Use Gemini CLI to check if dark mode is implemented, following the 
instructions in CLAUDE.md"
```

---

## 🎛️ Customizing the Integration

### **Making It More Aggressive**

If you want Claude Code to ALWAYS use Gemini first:

Add to `CLAUDE.md`:
```markdown
## IMPORTANT: Always Analyze First

Before implementing ANY feature or making significant changes:
1. MUST use Gemini CLI to analyze relevant code
2. MUST report findings before proposing implementation
3. MUST verify nothing conflicts with existing code

This is REQUIRED, not optional.
```

---

### **Making It More Selective**

If you want manual control:

Add to `CLAUDE.md`:
```markdown
## Gemini CLI Usage

Gemini CLI is available for analysis. Use it when:
- I explicitly request: "Check with Gemini..."
- You determine analysis would save significant tokens
- Working with > 50 files

Don't use automatically unless I ask.
```

---

### **Project-Specific Queries**

Add common queries you'll need:

```markdown
## Common Gemini CLI Queries for This Project

### Check Authentication
```bash
gemini -p "@app/api/auth/ @lib/auth.ts Is authentication properly implemented?"
```

### Verify Database Schema
```bash
gemini -p "@prisma/schema.prisma What models exist and their relationships?"
```

### Find All API Routes
```bash
gemini -p "@app/api/ List all API endpoints and what they do"
```

### Check for TODOs
```bash
gemini -p "@./ Find all TODO, FIXME, or HACK comments"
```

Use these as templates when exploring the codebase.
```

---

## 📊 Monitoring the Integration

### **How to Tell It's Working:**

**In Claude Code chat, you'll see:**
```
"Let me use Gemini CLI to analyze the codebase first..."

[Runs Gemini CLI command]

"Gemini CLI reports: [findings]

Based on this analysis, here's my implementation plan..."
```

**Check Gemini usage:**
```bash
gemini /stats
```

You should see increased usage when Claude Code is working.

---

### **Troubleshooting:**

**Problem: Claude Code not using Gemini CLI**

**Solution 1: Be explicit**
```
"Following CLAUDE.md instructions, use Gemini CLI to check..."
```

**Solution 2: Check CLAUDE.md exists**
```bash
ls -la ~/projects/dashboard/CLAUDE.md
```

**Solution 3: Restart Claude Code session**
- Close and reopen Claude Code
- It re-reads CLAUDE.md on startup

---

**Problem: Gemini CLI not installed**

**Solution:**
```bash
# Install Gemini CLI first
pip install google-generativeai --break-system-packages

# Configure with Google Auth
gemini config --use-google-auth

# Verify
gemini --version
```

See: GEMINI_COMPLETE_SETUP.md

---

**Problem: Claude Code can't access Gemini CLI**

**Solution:**
Gemini CLI needs to be in PATH. Check:
```bash
which gemini
```

If not found, add to PATH or use full path in CLAUDE.md:
```bash
/home/youruser/.local/bin/gemini -p "..."
```

---

## 💰 Token Savings Analysis

### **Example Scenario: Adding Dark Mode**

**Without Integration:**
```
Claude Code approach:
1. Read all components (~100 files)
2. Read all styles (~50 files)
3. Analyze patterns
4. Implement dark mode

Tokens used: ~200,000+ (reading all files)
Cost: Significant Claude tokens
```

**With Integration:**
```
Claude Code with Gemini:
1. Gemini CLI: "@components/ @styles/ Is dark mode implemented?"
2. Gemini: "No dark mode. Here are the files that need changes..."
3. Claude Code: Read ONLY relevant files
4. Implement dark mode

Tokens used by Claude: ~20,000 (only relevant files)
Gemini CLI: Free!
Cost: 90% reduction in Claude tokens
```

---

### **Real-World Savings:**

Assuming you do 5 feature implementations per month:

**Without Integration:**
```
5 features × 200K tokens each = 1M tokens
= Heavy Claude usage
= Likely hit limits
= Need to buy more credits
```

**With Integration:**
```
5 features × 20K Claude tokens + Free Gemini = 100K tokens
= 90% reduction
= Rarely hit limits  
= Stay within free tier more
```

---

## 🔄 Workflow Examples

### **Workflow 1: Feature Development**

**You:**
```
"I want to add a 'habit streaks' feature that tracks consecutive completions. 
Can you help me implement this?"
```

**Claude Code (with CLAUDE.md):**
```
"Let me use Gemini CLI to check the current implementation first...

[Runs: gemini -p "@prisma/schema.prisma @app/api/ Explain habit tracking implementation"]

Gemini reports:
- Habit model exists with completions
- HabitCompletion tracks dates
- No streak calculation currently

Based on this, here's my plan:
1. Add streak calculation logic
2. Update Habit component to display streaks
3. Add API endpoint for streak data

Should I proceed?"
```

**Result:** 
- Comprehensive understanding before coding
- Efficient token usage
- Better implementation plan

---

### **Workflow 2: Bug Investigation**

**You:**
```
"Users report completions aren't saving. Can you investigate?"
```

**Claude Code (with CLAUDE.md):**
```
"I'll use Gemini CLI to analyze the completion flow...

[Runs: gemini -p "@app/api/completions/ @components/HabitCard.tsx Trace completion save flow"]

Gemini found:
- API route exists at /api/completions
- HabitCard calls API correctly
- Potential issue: Missing error handling in API route

Let me examine the specific API route code..."
```

**Result:**
- Quick identification of relevant files
- Focused investigation
- Faster bug fix

---

### **Workflow 3: Refactoring**

**You:**
```
"I want to refactor the Item model migration we discussed. 
What's the current state?"
```

**Claude Code (with CLAUDE.md):**
```
"Checking current state with Gemini CLI...

[Runs: gemini -p "@prisma/schema.prisma @app/api/ Show Habit and Item models and their usage"]

Current state:
- Habit model: Used in 15 files
- Item model: Exists but unused
- Migration script: Not found

Here's my refactoring plan based on this analysis:
1. Create migration script
2. Update these 15 files
3. Test migration

Shall I proceed with implementation?"
```

**Result:**
- Complete understanding of scope
- Realistic plan
- No surprises during implementation

---

## 🎯 Best Practices

### **Do's:**

✅ **Keep CLAUDE.md updated**
- Update when project structure changes
- Add new conventions as they emerge
- Remove outdated information

✅ **Be specific in Gemini queries**
- Good: "Is dark mode implemented?"
- Better: "Is dark mode implemented? Show files and approach used"

✅ **Review Gemini findings**
- Claude Code will share Gemini's output
- Verify it makes sense
- Correct if needed

✅ **Iterate on CLAUDE.md**
- Start simple
- Add more as you learn what works
- Remove what doesn't help

---

### **Don'ts:**

❌ **Don't make CLAUDE.md too long**
- Claude Code has to read it every session
- Keep it focused and relevant
- Aim for < 500 lines

❌ **Don't override safety practices**
- Don't tell Claude to skip reviews
- Don't disable error handling
- Keep best practices in place

❌ **Don't expect perfection**
- Claude might not always use Gemini when you want
- That's okay - you can request explicitly
- This is augmentation, not replacement

❌ **Don't forget Gemini has limits**
- 1,500 requests per day
- If hitting limits, be more selective
- Manual control when needed

---

## 🔗 Integration with Other Tools

### **Works With:**

✅ **Context Keeper**
- Archive sessions where Claude used Gemini
- Track which queries were most useful
- Learn from patterns

✅ **VS Code**
- Claude Code extension reads CLAUDE.md
- Gemini Code Assist can also reference it
- Shared project knowledge

✅ **Git**
- Commit CLAUDE.md to your repo
- Team members benefit from instructions
- Version control your AI instructions

---

### **Doesn't Work With:**

❌ **Claude Pro (web)**
- This is for Claude Code only
- Claude Pro can't execute Gemini CLI
- Different use case

❌ **Gemini Pro (web)**
- Can't read CLAUDE.md
- Separate tool
- Use for research instead

---

## 📈 Measuring Success

### **Week 1:**
```
Track:
- How often Claude uses Gemini
- Does it help or annoy?
- Token savings noticeable?

Adjust:
- More aggressive or more selective?
- Better queries in CLAUDE.md?
- Remove if not helping
```

### **Month 1:**
```
Evaluate:
- Did it save Claude tokens?
- Made development faster?
- Worth maintaining?

Decide:
- Keep and expand
- Keep as-is
- Simplify
- Remove
```

---

## 🚀 Quick Start Template

Want to start simple? Use this minimal CLAUDE.md:

```markdown
# Project: [Your Project Name]

## Tech Stack
[Your technologies]

## Use Gemini CLI for Analysis

Before implementing features or making large changes, use Gemini CLI to:
- Check if features already exist: `gemini -p "@src/ Is X implemented?"`
- Understand architecture: `gemini -p "@src/ Explain architecture"`
- Find relevant files: `gemini -p "@src/ Where is Y handled?"`

This saves tokens and provides better context.

## Code Conventions
[Your conventions]
```

Save this, test it, expand as needed!

---

## 🔗 Related Documents

- **[GEMINI_COMPLETE_SETUP.md](./GEMINI_COMPLETE_SETUP.md)** - Set up Gemini CLI first
- **[MULTI_AGENT_STRATEGY.md](./MULTI_AGENT_STRATEGY.md)** - Overall AI strategy
- **[CONTEXT_KEEPER.md](./CONTEXT_KEEPER.md)** - Archive your work
- **[MASTER_ROADMAP.md](./MASTER_ROADMAP.md)** - Project organization

---

## 💡 Final Thoughts

**This integration is OPTIONAL but powerful.**

**Start without it** - Learn how Claude Code and Gemini CLI work separately.

**Add it when** - You understand the workflow and want automation.

**The goal:** Best of both worlds - Claude's reasoning + Gemini's analysis.

**The result:** Efficient, token-conscious, comprehensive development.

---

**Questions?** Test it on a small project first. See what works for you. Iterate! 🚀
