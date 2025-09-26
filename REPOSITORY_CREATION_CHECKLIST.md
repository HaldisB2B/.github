# Repository Creation Checklist - HaldisB2B

## 🚨 BEFORE Creating Any Repository

### Step 1: Ownership Validation

**Ask these questions FIRST:**

- [ ] Is this a HaldisB2B business project?
- [ ] Will this be maintained by the HaldisB2B team?
- [ ] Does this serve a business purpose?
- [ ] Is this NOT a personal/learning project?

**If ANY answer is NO → Create in personal account (Shamdon)**
**If ALL answers are YES → Create in HaldisB2B organization**

### Step 2: Repository Information

- [ ] **Name**: Clear, business-focused naming
- [ ] **Description**: Includes "HaldisB2B" and business purpose
- [ ] **Visibility**: Private for internal projects
- [ ] **Organization**: `HaldisB2B` (not personal account)

### Step 3: Initial Setup

- [ ] **README.md**: Must include HaldisB2B context
- [ ] **package.json**: Use `@haldisb2b/` scope if applicable
- [ ] **LICENSE**: Appropriate for business use
- [ ] **Ownership validation**: Add workflow template

## ✅ Repository Creation Template

```bash
# 1. Verify organization
echo "Creating repository in: HaldisB2B organization"

# 2. Repository name format
echo "Repository name: descriptive-business-name"

# 3. Description template
echo "Description: [Business purpose] for HaldisB2B - [Brief description]"

# Example:
# Name: nextgen-cicd
# Description: Next-generation CI/CD system for HaldisB2B - Emergency-first philosophy
```

## 📋 Post-Creation Checklist

### Immediate (First Commit)

- [ ] Add ownership validation workflow
- [ ] Verify package.json scope (@haldisb2b)
- [ ] Confirm README mentions HaldisB2B
- [ ] Check repository is in correct organization

### Documentation Updates

- [ ] Update all internal documentation
- [ ] Add to organization repository list
- [ ] Verify all links point to correct location
- [ ] Update any automated systems

### Team Notification

- [ ] Inform team of new repository
- [ ] Share access permissions
- [ ] Document purpose and ownership
- [ ] Add to relevant project tracking

## 🚫 Common Mistakes to Avoid

### Wrong Organization

```bash
# ❌ WRONG
Shamdon/haldisb2b-project-name

# ✅ CORRECT  
HaldisB2B/project-name
```

### Mixed Context

```bash
# ❌ WRONG - Business project in personal repo
Shamdon/company-ci-cd-system

# ❌ WRONG - Personal project in business org
HaldisB2B/peter-personal-experiments

# ✅ CORRECT - Clear separation
HaldisB2B/nextgen-cicd
Shamdon/my-learning-project
```

### Missing Business Context

```bash
# ❌ WRONG - No business context
"A cool project"

# ✅ CORRECT - Clear business purpose
"Authentication service for HaldisB2B client applications"
```

## 🔧 Automation and Enforcement

### Workflow Template

Copy `.github/workflow-templates/ownership-validation.yml` to any new repository to automatically validate ownership.

### Package.json Template

```json
{
  "name": "@haldisb2b/repository-name",
  "description": "[Purpose] for HaldisB2B - [Description]",
  "author": "HaldisB2B Team",
  "private": true
}
```

### README Template

```markdown
# HaldisB2B [Project Name]

## Business Context
This project serves [business purpose] for HaldisB2B.

## Organization
- **Owner**: HaldisB2B
- **Team**: [Team name]
- **Purpose**: [Business purpose]
```

## 📞 Emergency Procedures

### If Wrong Organization Used

1. **STOP** further commits to wrong location
2. **CREATE** issue in HaldisB2B/.github
3. **REQUEST** proper repository creation
4. **TRANSFER** content once created
5. **DELETE** misplaced repository after verification

### If Mixed Content Found

1. **IDENTIFY** personal vs business content
2. **SEPARATE** into appropriate repositories
3. **UPDATE** all documentation and links
4. **VERIFY** team has correct access

## 📖 References

- [Organization Guidelines](ORGANIZATION_GUIDELINES.md)
- [Workflow Templates](workflow-templates/)
- [Organization Profile](profile/README.md)

---

**Remember: 10 seconds of validation prevents hours of cleanup.**