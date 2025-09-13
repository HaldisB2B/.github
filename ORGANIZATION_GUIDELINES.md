# HaldisB2B Organization Guidelines

## Repository Ownership Rules

### CRITICAL: Repository Organization Structure

**Shamdon Personal Repositories:**
- Owner: `Shamdon` 
- Purpose: Personal projects, experiments, individual work
- Examples: Personal tools, learning projects, individual demos

**HaldisB2B Organization Repositories:**
- Owner: `HaldisB2B`
- Purpose: Company projects, team collaboration, business systems
- Examples: CI/CD systems, internal tools, client projects

### ⚠️ NEVER MIX OWNERSHIP

**❌ WRONG:**
```
Shamdon/haldisb2b-nextgen-cicd    # HaldisB2B project in personal repo
HaldisB2B/peter-personal-tool     # Personal project in company org
```

**✅ CORRECT:**
```
HaldisB2B/nextgen-cicd           # Company CI/CD in company org
Shamdon/my-personal-tool         # Personal tool in personal repo
```

## Repository Creation Checklist

Before creating any repository, ask:

1. **Who owns this project?**
   - Individual: → `Shamdon`
   - Company: → `HaldisB2B`

2. **Who will maintain it?**
   - Personal responsibility: → `Shamdon`
   - Team responsibility: → `HaldisB2B`

3. **What's the business context?**
   - Personal learning/tools: → `Shamdon`
   - Business operations: → `HaldisB2B`

## Enforcement

### For AI Agents and Developers

When creating repositories, **ALWAYS**:

1. **Identify the owner** before creating
2. **Double-check organization** before pushing code
3. **Verify repository location** in first commit message

### Repository Names

**HaldisB2B repositories:**
- Use descriptive, business-focused names
- Examples: `nextgen-cicd`, `prompt-management-system`, `abaton`

**Personal repositories:**
- Use personal preference naming
- Keep separate from business context

## Recovery Procedures

### If Wrong Organization is Used

1. **IMMEDIATE:** Stop further commits to wrong location
2. **CREATE:** New repository in correct organization  
3. **TRANSFER:** Content to correct location
4. **UPDATE:** All documentation and references
5. **DELETE:** Repository from wrong location (after verification)

## Documentation Requirements

Every HaldisB2B repository **MUST** include:

- Clear ownership in README
- Business context and purpose
- Emergency contact information
- Contribution guidelines

---

## Examples

### ✅ Correct Repository Organization

```yaml
Personal Projects (Shamdon):
  - Shamdon/my-dotfiles
  - Shamdon/learning-rust
  - Shamdon/personal-website
  
Business Projects (HaldisB2B):
  - HaldisB2B/nextgen-cicd
  - HaldisB2B/prompt-management-system
  - HaldisB2B/abaton
```

### ❌ Common Mistakes to Avoid

- Putting company projects in personal repos
- Mixing personal and business code
- Unclear ownership in repository names
- Missing organization context in documentation

---

*This document exists because repository organization mistakes waste time and create confusion. Follow these rules religiously.*