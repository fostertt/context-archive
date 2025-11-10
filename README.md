# Personal AI Chat Archive

My searchable archive of conversations with various AI assistants.

## Structure
- `chats/` - Organized by AI tool
- `chats/by-project/` - Organized by project
- `extracted/` - Key commands, snippets, decisions

## Search Examples
```bash
# Find all chats mentioning "authentication"
grep -r "authentication" chats/

# Find chats from November
find chats/ -name "*2025-11*"

# Search specific AI
grep -r "rate limiting" chats/claude/
