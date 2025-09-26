# Documentation Naming Conventions

## Philosophy: Remove Barriers, Add Value

**Core Principle**: Documentation naming should help, not hinder creation.

## Naming Patterns

### Standard Pattern (Recommended)
```
document-name.md
user-guide.md
architecture.md
api-contracts.md
```

### When Versioning is Needed
```
user-guide-v2.md          # Major updates
user-guide-phase1.md      # Phase-based
user-guide-2024-09-11.md  # Date-specific context
```

### When NOT to Use Complex Names
- ❌ `user-guide-v1.2.3-2024-09-11-sequential-003-final-draft.md`
- ❌ Required prefixes that slow down creation
- ❌ Sequential numbering across all docs (impossible with parallel work)

## Automatic Organization Instead

### 1. Git-Based Timestamps
Every commit provides:
- Creation date
- Author
- Change sequence
- Version history

### 2. Document Metadata (Optional)
```markdown
---
created: 2024-09-11
author: AI Developer Instance 3
project: prompt-management-system
type: user-guide
version: 1.0
---
```

### 3. Index Files for Navigation
```markdown
# Project Documentation Index

## User Guides
- [Admin User Guide](admin-user-guide.md) - Created: 2024-09-11
- [Developer Guide](developer-guide.md) - Created: 2024-09-10

## Architecture
- [System Architecture](architecture.md) - Updated: 2024-09-11
- [Phase 1 Architecture](phase1-architecture.md) - Created: 2024-09-08
```

## Implementation Guidelines

### For AI Developers
1. **Just create the document** - Use descriptive names
2. **Add metadata if helpful** - Front matter is optional
3. **Update indexes when convenient** - Not required for each doc

### For Document Reviewers
1. **Git log provides sequence** - `git log --oneline --follow filename.md`
2. **Rename if needed** - Can be done without breaking links
3. **Create indexes periodically** - Batch organize when useful

## Examples from Current Projects

### Good Examples
```
✅ admin-user-guide.md
✅ software-architecture.md  
✅ ai-development-process.md
✅ api-contracts/authentication.md
✅ phase1-architecture.md
```

### When Dating is Useful
```
✅ migration-plan-2024-09-11.md (time-sensitive)
✅ quarterly-review-2024-q3.md (periodic)
✅ incident-report-2024-09-11.md (event-based)
```

## Benefits of This Approach

### ✅ Low Barrier to Entry
- No complex naming rules to remember
- AI developers can focus on content
- Fast document creation

### ✅ Natural Organization
- Git provides automatic versioning
- Metadata available when needed
- Human-readable names

### ✅ Scalable
- Works with parallel development
- Doesn't break with team growth
- Easy to reorganize later

## Auto-Organization Tools

### Repository Level
- `find . -name "*.md" -exec ls -la {} \;` - List all docs with dates
- `git log --name-only --pretty=format:"%h %ad %s" --date=short` - Commit history

### Document Level  
- Front matter extraction scripts
- Automatic index generation
- Link checking and updates

## Migration Strategy for Existing Docs

1. **Keep existing names** - Don't rename unless problematic
2. **Add metadata gradually** - When touching documents anyway  
3. **Create indexes organically** - As projects need them
4. **Use git for history** - Existing timestamps preserved

---

**Result**: Documentation that's easy to create, find, and organize without artificial barriers.

---

**Alignment Note**: These conventions complement the AI-assisted development practices outlined in `AI_ASSISTED_CODING_FOUNDATION.md` by removing administrative overhead from documentation creation while maintaining discoverability and organization.