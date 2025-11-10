# 🏠 LIFE OS DASHBOARD - Project Documentation

**Last Updated:** November 10, 2025  
**Purpose:** Family productivity hub (habits, tasks, reminders, calendar, meal planning)  
**Status:** Phase 3 Complete ✅ | Phase 4 Ready 🎯

---

## 📋 Quick Facts

- **What:** Personal/family productivity dashboard with unified task management
- **Tech Stack:** Next.js 16, TypeScript, Tailwind CSS, Prisma ORM, SQLite, NextAuth.js
- **Auth:** Google OAuth (working)
- **Repository:** github.com/fostertt/dashboard
- **Current Branch:** master
- **Latest Commit:** 7be807b (Phase 3 complete)
- **User:** Tyrrell Foster (tyrrellfoster@gmail.com)

---

## 🎯 Project Vision

A unified family productivity system that replaces multiple apps:
- **Habit tracking** (Habitica replacement)
- **Task management** (Todoist replacement)
- **Reminders** (Apple Reminders replacement)
- **Calendar integration** (Google Calendar view)
- **Meal planning** (Custom feature)

**Key Principle:** One item model for everything (tasks, habits, reminders, meals)

---

## ✅ Current State (Phase 3 Complete)

### **What's Working:**
- ✅ Next.js 16 foundation with TypeScript
- ✅ Tailwind CSS styling
- ✅ Prisma ORM with SQLite database
- ✅ Google OAuth authentication (NextAuth.js)
- ✅ User sessions persist across refreshes
- ✅ Protected routes and API endpoints
- ✅ Basic habit tracker functionality
- ✅ CRUD operations for habits
- ✅ Completion persistence (database-backed)
- ✅ Interactive Today and Week views
- ✅ Form validation & error handling
- ✅ Toast notifications
- ✅ Loading states

### **What's in Database:**
- ✅ `users` table (you: tyrrellfoster@gmail.com)
- ✅ `accounts` table (Google OAuth link)
- ✅ `sessions` table (your current session)
- ✅ `habits` table (3 test habits) ← **Will migrate these**
- ✅ `items` table (empty, ready) ← **Migration destination**
- ✅ `families` table (multi-tenant ready but unused)
- ✅ `family_users` table (multi-tenant ready but unused)

**Database Location:** `prisma/habits.db`

---

## 🏗️ Architecture Decisions

### **Item Model Philosophy**
Based on successful Flask/Replit implementation:

**Unified Model:**
```typescript
Item {
  id: string
  itemType: 'habit' | 'task' | 'reminder' | 'meal'
  title: string
  description?: string
  
  // Habit-specific
  frequency?: 'daily' | 'weekly' | 'custom'
  completions?: Completion[]
  
  // Task-specific
  dueDate?: Date
  priority?: 'low' | 'medium' | 'high'
  completed?: boolean
  
  // Reminder-specific
  reminderDate?: Date
  reminderTime?: Time
  
  // Meal-specific
  mealType?: 'breakfast' | 'lunch' | 'dinner' | 'snack'
  recipe?: string
  
  // Common
  userId: string
  familyId?: string
  createdAt: Date
  updatedAt: Date
}
```

**Why This Works:**
- Single source of truth for all productivity items
- Flexible enough for different types
- Type discriminator (`itemType`) keeps logic clean
- Easy to query across types ("Show me everything due today")
- Natural fit for unified calendar view

---

### **Multi-Tenant Structure (Ready, Not Active)**

**Family-based:**
- Each user belongs to one or more families
- Items can be personal or family-shared
- Permissions handled at family level

**Current Status:**
- Schema exists
- Not currently used (single-user mode)
- Ready to activate when needed

---

## 📊 Phase Summaries

### **Phase 1: Foundation** ✅ Complete
**Goal:** Set up modern Next.js stack

**Accomplished:**
- Next.js 16 with App Router
- TypeScript configuration
- Tailwind CSS setup
- Prisma ORM + SQLite
- Basic Habit model (temporary)
- Development environment configured

**Duration:** ~2 hours  
**Challenges:** None significant

---

### **Phase 2: Core Functionality** ✅ Complete
**Goal:** Build working habit tracker

**Accomplished:**
- Database-backed completion persistence
- Interactive Today view
- Week view with navigation
- CRUD operations for habits
- Form validation
- Toast notifications
- Loading states
- Error handling

**Duration:** ~3 hours  
**Challenges:** State management for completions

---

### **Phase 3: Authentication** ✅ Complete
**Goal:** Add Google OAuth

**Accomplished:**
- NextAuth.js integration
- Google OAuth provider
- Session management
- Protected routes
- Protected API endpoints
- Auth state persistence

**Duration:** ~4 hours  
**Challenges:** 
- Initial auth loop (resolved by new OAuth secret)
- Session persistence debugging
- Environment variable configuration

**Key Learnings:**
- Always use fresh OAuth secrets
- Test session persistence across refreshes
- Protected routes need `getServerSession`

---

### **Phase 4: Item Model Migration** 🎯 NEXT
**Goal:** Migrate from Habit model to unified Item model

**Why Now:**
- Only 3 test habits to migrate (easy)
- Enables future features (tasks, reminders, meals)
- Cleaner architecture going forward
- Cheaper to migrate now than later

**What Needs to Happen:**
1. Create data migration script (habits → items)
2. Update Prisma schema to prioritize Item model
3. Update API routes (`/api/habits/*` → `/api/items/*`)
4. Update UI components to use Item model
5. Add `itemType` filtering
6. Test that existing habits still work
7. Verify completions are preserved

**Estimated Duration:** 2-3 hours

**Reference:** Old Flask/Replit code has Item model implementation

---

### **Phase 5: Task Management** 📅 Future
**Goal:** Add task functionality using Item model

**Features:**
- Create tasks with due dates
- Priority levels
- Task completion
- Filter by status (active/completed)
- Calendar view integration

---

### **Phase 6: Reminders** 🔔 Future
**Goal:** Add reminder system

**Features:**
- Time-based reminders
- Notification system
- Recurring reminders
- Integration with habits/tasks

---

### **Phase 7: Meal Planning** 🍽️ Future
**Goal:** Add meal planning features

**Features:**
- Weekly meal calendar
- Recipe storage
- Grocery list generation
- Family meal sharing

---

### **Phase 8: Calendar Integration** 📆 Future
**Goal:** Google Calendar integration

**Features:**
- Read-only view of Google Calendar events
- Unified timeline view (items + calendar)
- Sync habits/tasks to calendar (optional)

---

## 🔧 Technical Details

### **Environment Setup**

**Required Environment Variables:**
```bash
# Database
DATABASE_URL="file:./prisma/habits.db"

# NextAuth
NEXTAUTH_URL="http://localhost:3000"
NEXTAUTH_SECRET="[your-secret]"

# Google OAuth
GOOGLE_CLIENT_ID="[your-client-id]"
GOOGLE_CLIENT_SECRET="[your-client-secret]"
```

**Location:** `.env` (not committed to Git)

---

### **Common Development Commands**

```bash
# Start development server
npm run dev

# Clear cache and restart
rm -rf .next && npm run dev

# Database operations
npx prisma studio              # View/edit database in browser
npx prisma generate            # Regenerate Prisma client
npx prisma db push             # Push schema changes to DB
npx prisma migrate dev         # Create migration file

# Git workflow
git status                     # Check changes
git add .                      # Stage all
git commit -m "Message"        # Commit
git push origin master         # Push to GitHub
git pull origin master         # Pull latest

# Check authentication state
node scripts/check-auth-state.js  # Custom script

# Verify environment
cat .env | grep -v SECRET      # Check env vars (hide secrets)
```

---

### **Project Structure**

```
dashboard/
├── app/                      # Next.js App Router
│   ├── api/                  # API routes
│   │   ├── auth/            # NextAuth routes
│   │   └── habits/          # Habit CRUD (will become /items)
│   ├── dashboard/           # Main app pages
│   │   ├── page.tsx         # Today view
│   │   └── week/            # Week view
│   ├── layout.tsx           # Root layout
│   └── page.tsx             # Landing/auth page
├── components/              # React components
│   ├── HabitCard.tsx
│   ├── HabitForm.tsx
│   └── ...
├── lib/                     # Utilities
│   ├── prisma.ts            # Prisma client
│   └── auth.ts              # Auth utilities
├── prisma/
│   ├── schema.prisma        # Database schema
│   └── habits.db            # SQLite database
├── public/                  # Static assets
├── .env                     # Environment variables (not in Git)
├── .gitignore
├── next.config.js
├── package.json
├── tailwind.config.ts
└── tsconfig.json
```

---

### **Current Prisma Schema (Relevant Parts)**

```prisma
model User {
  id            String    @id @default(cuid())
  name          String?
  email         String?   @unique
  emailVerified DateTime?
  image         String?
  accounts      Account[]
  sessions      Session[]
  habits        Habit[]    // Will become items
  items         Item[]     // Migration target
  familyUsers   FamilyUser[]
}

model Habit {
  id          String   @id @default(cuid())
  title       String
  description String?
  frequency   String   @default("daily")
  userId      String
  user        User     @relation(fields: [userId], references: [id])
  completions HabitCompletion[]
  createdAt   DateTime @default(now())
  updatedAt   DateTime @updatedAt
}

model Item {
  id           String   @id @default(cuid())
  itemType     String   // 'habit' | 'task' | 'reminder' | 'meal'
  title        String
  description  String?
  
  // Habit fields
  frequency    String?
  
  // Task fields
  dueDate      DateTime?
  priority     String?
  completed    Boolean  @default(false)
  
  // Reminder fields
  reminderDate DateTime?
  
  // Meal fields
  mealType     String?
  recipe       String?
  
  userId       String
  user         User     @relation(fields: [userId], references: [id])
  familyId     String?
  family       Family?  @relation(fields: [familyId], references: [id])
  
  completions  ItemCompletion[]
  
  createdAt    DateTime @default(now())
  updatedAt    DateTime @updatedAt
}
```

---

## 🚀 Phase 4 Jump-Off Document

### **For Claude Code Implementation**

When ready to start Phase 4, use this prompt:

```
Continuing Life OS Dashboard development. Phase 3 (Google OAuth authentication) 
is complete and committed to master.

TASK: Phase 4 - Migrate from Habit model to unified Item model

CONTEXT:
- Repository: github.com/fostertt/dashboard
- Branch: master
- Latest commit: 7be807b
- Current user: Tyrrell Foster (tyrrellfoster@gmail.com)
- Test data: 3 habits in database that must be preserved

CURRENT STATE:
- Using simplified Habit model temporarily
- Item model exists in schema but is empty
- All UI and API routes use Habit model
- Completions are tied to Habit via HabitCompletion model

TARGET STATE:
- Item model is primary
- Habit model deprecated (can keep for reference)
- All 3 test habits migrated to items table
- All completions preserved and linked correctly
- API routes support itemType filtering
- UI supports multiple item types (start with habits)

MIGRATION PLAN:
1. Create data migration script:
   - Read all habits from database
   - Create corresponding Item records (itemType: 'habit')
   - Migrate completions: HabitCompletion → ItemCompletion
   - Verify data integrity
   - Run migration in transaction (all or nothing)

2. Update Prisma schema:
   - Prioritize Item model
   - Keep Habit model for reference (optional)
   - Ensure proper relations

3. Update API routes:
   - /api/habits/route.ts → support Item model
   - Add itemType filtering
   - Maintain backward compatibility during transition
   - OR: Create new /api/items routes

4. Update UI components:
   - Update queries to use Item model
   - Filter by itemType: 'habit'
   - Update type definitions
   - Test Today view
   - Test Week view

5. Testing checklist:
   - [ ] All 3 habits appear in Today view
   - [ ] Can complete habits
   - [ ] Completions persist
   - [ ] Week view shows habits
   - [ ] Can create new habits
   - [ ] Can edit habits
   - [ ] Can delete habits

TECHNICAL NOTES:
- SQLite database: prisma/habits.db
- Current habits have: id, title, description, frequency, userId, completions
- Item model adds: itemType discriminator
- Preserve all timestamps (createdAt, updatedAt)

REFERENCE:
- Old Flask/Replit code used Item model successfully
- Similar migration done before (can reference patterns)

Ready to start? Please begin with Step 1: Create migration script.
```

---

## 🐛 Troubleshooting Guide

### **Authentication Issues**

**Problem:** Auth loop (redirects continuously)
**Solution:**
1. Generate new NEXTAUTH_SECRET: `openssl rand -base64 32`
2. Update `.env`
3. Restart dev server
4. Clear browser cookies

**Problem:** "Session is undefined"
**Solution:**
1. Verify NEXTAUTH_SECRET in `.env`
2. Check NEXTAUTH_URL matches current URL
3. Use `getServerSession` in Server Components
4. Use `useSession` in Client Components

---

### **Database Issues**

**Problem:** "Prisma Client not found"
**Solution:**
```bash
npx prisma generate
```

**Problem:** Schema changes not applying
**Solution:**
```bash
npx prisma db push
npx prisma generate
npm run dev
```

**Problem:** Need to reset database
**Solution:**
```bash
rm prisma/habits.db
npx prisma db push
# Re-authenticate to create user
```

---

### **Development Issues**

**Problem:** Changes not showing up
**Solution:**
```bash
rm -rf .next
npm run dev
```

**Problem:** Type errors after schema changes
**Solution:**
```bash
npx prisma generate
# Restart TypeScript server in VS Code
```

---

## 📚 References

### **Original Flask/Replit Code**
- Had unified Item model
- Used itemType discriminator
- Supported habits, tasks, reminders
- ~3,500 lines of Python
- **Location:** [Mention if you have this code accessible]

### **Key Documentation**
- Next.js 16: https://nextjs.org/docs
- Prisma: https://www.prisma.io/docs
- NextAuth.js: https://next-auth.js.org/
- Tailwind CSS: https://tailwindcss.com/docs

---

## 🎯 Future Feature Wishlist

**Short Term:**
- [ ] Dark mode toggle
- [ ] Habit streaks display
- [ ] Quick add (⌘K command palette)
- [ ] Habit categories/tags
- [ ] Week view: prev/next navigation buttons

**Medium Term:**
- [ ] Task management (using Item model)
- [ ] Reminders with notifications
- [ ] Mobile responsive improvements
- [ ] Export data (JSON/CSV)

**Long Term:**
- [ ] Meal planning
- [ ] Google Calendar integration
- [ ] Family sharing (activate multi-tenant)
- [ ] Habit statistics/analytics
- [ ] Gamification (points, levels)

---

## 📝 Decision Log

### **Decision: Use Unified Item Model**
**Date:** November 2025  
**Reasoning:** 
- Original Flask app proved this works well
- More flexible than separate models
- Easier to query across types
- Natural for unified calendar view
- Single source of truth

**Alternatives Considered:**
- Separate models (Habit, Task, Reminder) - More normalized but harder to query
- Inheritance with base Item - Complex with Prisma

---

### **Decision: SQLite for Database**
**Date:** November 2025  
**Reasoning:**
- Simple file-based
- Perfect for personal/family use
- Easy to backup
- No server needed
- Can migrate to Postgres later if needed

---

### **Decision: Google OAuth Only**
**Date:** November 2025  
**Reasoning:**
- Family all uses Google
- Simpler than email/password
- No password management
- Trusted provider
- Can add other providers later

---

## 🔗 Related Documents

- **[MASTER_ROADMAP.md](./MASTER_ROADMAP.md)** - Overall project organization
- **[MULTI_AI_WORKFLOW.md](./MULTI_AI_WORKFLOW.md)** - How to work with AIs
- **[CONTEXT_KEEPER.md](./CONTEXT_KEEPER.md)** - Chat archive system
- **[QUICK_START_GUIDE.md](./QUICK_START_GUIDE.md)** - Using these docs

---

## 💡 Notes for Future You

**When Returning to This Project:**
1. Read this document first
2. Check current phase status
3. Review last commit messages
4. Test auth still works (run `npm run dev`)
5. Review `DATABASE.db` in Prisma Studio

**Before Starting Phase 4:**
1. Ensure Context Keeper is set up (archive the work)
2. Create new Claude Code session
3. Use Phase 4 jump-off document above
4. Test locally after Claude Code makes changes
5. Archive the session when complete

**Remember:**
- You're at Phase 3 complete
- Next is Item model migration
- Only 3 habits to migrate (easy now, harder later)
- Old Flask code has reference implementation
- Multi-tenant is ready but not active

---

**Last Session:** November 9, 2025 - Completed Phase 3 (Auth)  
**Next Session:** Phase 4 - Item Model Migration (when ready)  
**Status:** ✅ Stable, ready for Phase 4

---

🚀 Ready to continue building when you are!
