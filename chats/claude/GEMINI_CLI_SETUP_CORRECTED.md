# 🔧 GEMINI CLI SETUP GUIDE (CORRECTED)

**Last Updated:** November 10, 2025  
**Purpose:** Install official Google Gemini CLI safely  
**Priority:** 🔥 DO THIS FIRST

---

## ✅ What Gemini CLI Actually Is

**Official tool from Google** (announced June 2025)
- GitHub: https://github.com/google-gemini/gemini-cli
- Installed via npm (Node.js package manager)
- Open source and actively maintained

**What you get FREE with Google login:**
- 60 requests per minute
- 1,000 requests per day  
- Gemini 2.5 Pro model
- 1M token context window
- No API key needed!

---

## 🚀 Installation (30 Minutes)

### **Step 1: Install Node.js** (if needed)

**Check if you have Node.js:**
```bash
node --version
```

**If you see v18 or higher:** ✅ You're good, skip to Step 2

**If not, install Node.js 20:**

**On Ubuntu/Pop!_OS (your Surface Book):**
```bash
# Add Node.js 20 repository
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -

# Install Node.js
sudo apt-get install -y nodejs

# Verify
node --version  # Should show v20.x.x
npm --version   # Should show 10.x.x
```

**On Windows/WSL2 (your desktop):**
```bash
# Inside WSL2, same commands as above
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs
```

---

### **Step 2: Install Gemini CLI**

```bash
# Install globally
npm install -g @google/gemini-cli

# Verify installation
gemini --version
# Should show version number (e.g., 0.6.0 or higher)

# Check where it's installed
which gemini
# Should show path like: /usr/local/bin/gemini or ~/.npm-global/bin/gemini
```

**If you get permission errors:**
```bash
# Option A: Use sudo (quick but not ideal)
sudo npm install -g @google/gemini-cli

# Option B: Configure npm to install globally without sudo (better)
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
npm install -g @google/gemini-cli
```

---

### **Step 3: First Launch & Authentication**

```bash
# Launch Gemini CLI
gemini
```

**What happens:**

1. **Choose Theme**
   - You'll see theme options (light/dark/etc)
   - Use arrow keys to select
   - Press Enter

2. **Select Authentication Method**
   - You'll see options:
     - Login with Google (FREE - 60/min, 1000/day) ← **Choose this!**
     - API Key
     - Vertex AI
   - Select "Login with Google"
   - Press Enter

3. **Browser Opens**
   - Signs you into Google account
   - Grant permissions
   - You'll see success message

4. **Back in Terminal**
   - Gemini CLI is ready!
   - You'll see a prompt waiting for input

**Your session is now authenticated!** ✅

---

### **Step 4: Test It Works**

**Test 1: Simple Query**
```bash
# In the Gemini CLI prompt:
What's 2 + 2?
```

Should respond quickly with "4"

**Test 2: Code Analysis**
```bash
# Navigate to a project first (in a new terminal):
cd ~/projects/dashboard

# Then run Gemini CLI:
gemini

# In the prompt:
Analyze @package.json and tell me what dependencies this project uses
```

The `@` syntax lets you reference files!

**Test 3: Directory Analysis**
```bash
# In Gemini CLI:
@src/ What's the structure of this directory?
```

**If all 3 tests work:** You're golden! 🎉

---

## 📊 Verifying Your Free Quota

**Check your usage:**
```bash
# In Gemini CLI, type:
/stats
```

Should show something like:
```
Requests today: 5 / 1000
Requests this minute: 2 / 60
Model: gemini-2.5-pro
```

**This confirms:**
- ✅ You're using Google login (free tier)
- ✅ Not burning Google Cloud credits
- ✅ Have 1,000 daily requests
- ✅ Using Gemini 2.5 Pro

---

## 💡 How to Use Gemini CLI

### **Basic Usage:**

**Interactive Mode** (like ChatGPT in terminal):
```bash
# Just run:
gemini

# Then chat normally:
> How do I center a div in CSS?
> Explain async/await in JavaScript
> Help me debug this error: [paste error]
```

**Single Prompt Mode**:
```bash
# Quick one-off query:
gemini -p "Explain what Next.js is"
```

**File Analysis**:
```bash
# Reference files with @:
gemini

> @src/app/page.tsx Explain what this component does
> @package.json What are the main dependencies?
> @prisma/schema.prisma Show me the database models
```

**Directory Analysis**:
```bash
gemini

> @src/ Summarize the code structure
> @app/api/ List all API endpoints
> @components/ Show me all React components
```

**Multiple Files**:
```bash
gemini

> @src/main.ts @package.json How do these relate?
```

**Entire Project**:
```bash
# In your project directory:
gemini

> @./ Give me a complete project overview
```

---

### **Special Commands:**

In Gemini CLI, type `/` to see all commands:

```
/help          - Show all commands
/stats         - Show usage statistics
/auth          - Change authentication method
/model         - Switch Gemini model
/chat          - Start a conversation
/clear         - Clear conversation history
/exit or Ctrl+C - Exit Gemini CLI
```

---

## 🎯 Using with Your Projects

### **Life OS Dashboard Analysis:**

```bash
cd ~/projects/dashboard
gemini

> @prisma/schema.prisma What models exist?
> @app/api/ List all API routes and what they do
> @components/ Which components handle user interaction?
> Is dark mode implemented anywhere in @src/ @components/?
```

### **Pre-Implementation Research:**

```bash
gemini

> @src/ @app/ Is authentication implemented? Show me how
> @app/api/ Is there rate limiting on any endpoints?
> @components/ Are there any TODO comments?
```

### **Architecture Understanding:**

```bash
gemini

> @./ Explain the overall architecture of this Next.js app
> How does the authentication flow work in @app/api/auth/?
> What's the database schema in @prisma/schema.prisma?
```

---

## 🔌 Integration with Gemini Code Assist

**The Connection:**
- Gemini CLI and Gemini Code Assist share technology
- They share the **same quota** (1,000/day combined)
- Both use Google Auth with your AI Pro subscription

**What this means:**
```
100 Gemini CLI queries +
200 Gemini Code Assist queries =
300 / 1000 daily quota used

Still have 700 left!
```

**You can use both!** Just track combined usage.

---

## ⚠️ Important: Cost Protection

### **You're Using FREE Tier (Good!):**

✅ When you see "Login with Google" → FREE  
✅ 60 requests/minute  
✅ 1,000 requests/day  
✅ No charges to Google Cloud  
✅ $300 credit untouched  

### **What to AVOID:**

❌ **Don't use "API Key" option** unless you specifically need it  
❌ API Key = Usage-based billing  
❌ API Key = Your $300 credit gets used  
❌ Can rack up $500 bills if not careful  

**Stick with "Login with Google"!**

---

### **Verify You're Safe:**

```bash
# In Gemini CLI:
/auth
```

Should show: **"Signed in via Google"** or similar

**If it shows API Key:** Switch back!
```bash
/auth
# Select "Login with Google"
# Complete authentication again
```

---

## 🛡️ Setting Up Monitoring

### **Weekly Check (Sundays):**

```bash
# Check Gemini CLI usage
gemini
/stats

# Look at:
# - Requests today: Should be < 1000
# - Model: Should be gemini-2.5-pro
```

**Also check Google Cloud billing:**
```
Visit: console.cloud.google.com/billing
Should show: $0.00 spent (or minimal)
$300 credit: Untouched
```

**If you're spending money:** You switched to API key mode by mistake!

---

### **Set Billing Alerts (Just in Case):**

```
1. Go to: console.cloud.google.com/billing/alerts
2. Create alert for $10, $50, $100
3. Email: your-email@gmail.com
```

Even though you shouldn't hit these with Google Auth, good to have safety net.

---

## 🎓 Next Steps

### **Now that Gemini CLI is installed:**

1. **Read:** MULTI_AGENT_STRATEGY.md
   - Learn when to use Gemini CLI vs other tools
   - Understand optimal workflows

2. **Read:** CLAUDE_MD_INTEGRATION.md
   - Set up Claude Code to auto-call Gemini CLI
   - Get best of both worlds

3. **Install:** Gemini Code Assist in VS Code
   - Open VS Code
   - Extensions → Search "Gemini Code Assist"
   - Install and sign in with Google

4. **Try:** Jules (optional)
   - Visit: jules.google.com
   - See: JULES_EVALUATION.md

---

## 🐛 Troubleshooting

### **Problem: "gemini: command not found"**

**Solution:**
```bash
# Check if npm global bin is in PATH
npm config get prefix
# Should show something like /usr/local or ~/.npm-global

# Add to PATH if needed
echo 'export PATH="$(npm config get prefix)/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc

# Try again
gemini --version
```

---

### **Problem: "Permission denied" during npm install**

**Solution:**
```bash
# Configure npm for user installs
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc

# Try install again
npm install -g @google/gemini-cli
```

---

### **Problem: Node.js version too old**

**Solution:**
```bash
# Remove old Node.js
sudo apt-get remove nodejs

# Install Node.js 20
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs

# Verify
node --version  # Should be v20.x.x
```

---

### **Problem: Authentication fails in browser**

**Solution:**
```bash
# Try again
gemini
# Select "Login with Google"

# If still failing:
# 1. Check internet connection
# 2. Try different browser (copy URL manually)
# 3. Disable VPN if using one
# 4. Check Google account isn't blocked
```

---

### **Problem: Getting billed / using $300 credit**

**Solution:**
```bash
# Switch to Google Auth immediately!
gemini
/auth
# Select "Login with Google"
# Complete authentication

# Verify
/stats
# Should show free tier limits (60/min, 1000/day)
```

---

## ✅ Installation Complete Checklist

After following this guide:

- [ ] Node.js 20+ installed
- [ ] Gemini CLI installed globally
- [ ] `gemini --version` works
- [ ] Authenticated with "Login with Google"
- [ ] `/stats` shows free tier (60/min, 1000/day)
- [ ] Tested file analysis with `@`
- [ ] Google Cloud billing shows $0
- [ ] Billing alerts set up

**If all checked:** You're ready to use Gemini CLI! 🚀

---

## 🔗 Related Documents

- **[MULTI_AGENT_STRATEGY.md](./MULTI_AGENT_STRATEGY.md)** - When to use Gemini CLI vs other tools
- **[CLAUDE_MD_INTEGRATION.md](./CLAUDE_MD_INTEGRATION.md)** - Auto-calling magic
- **[START_HERE.md](./START_HERE.md)** - Overall system guide

---

## 💡 Pro Tips

**Tip 1: Use Gemini CLI Liberally**
```
It's FREE (1,000/day)!
Don't overthink it
Use for codebase exploration
Save Claude tokens
```

**Tip 2: The @ Syntax is Your Friend**
```bash
@file.ts              # Single file
@directory/           # Whole directory
@file1.ts @file2.ts   # Multiple files
@./                   # Entire project
```

**Tip 3: Check Stats Daily**
```bash
gemini
/stats

# Know your usage
# Stay under 1,000/day
# All good? Keep using it!
```

**Tip 4: Combine with Other Tools**
```
Gemini CLI: Analysis ("What exists?")
Claude Pro: Strategy ("Should I do X or Y?")
Claude Code or Gemini Code Assist: Implementation
```

**Tip 5: Use in VS Code Terminal**
```bash
# Open VS Code
# Open integrated terminal
# Run: gemini

# Now you have Gemini right in your editor!
```

---

## 🎉 You're All Set!

Gemini CLI is now installed and authenticated safely with Google login (free tier).

**You can now:**
- Analyze entire codebases instantly
- Ask questions about your code
- Get implementation ideas
- Verify features exist
- All with 1,000 free requests per day!

**Next:** Read MULTI_AGENT_STRATEGY.md to learn how to orchestrate this with your other AI tools! 🚀
