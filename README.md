# HaldisB2B Organization Standards & Templates

## Complete Development Documentation Hub

<!-- 
Author: HaldisB2B Leadership + Claude Code Assistant
Date: 2025-01-13
Purpose: Central navigation and overview of all HaldisB2B development standards
Status: FOUNDATIONAL DOCUMENTATION - Entry point for all team members
-->

> **🎯 Mission**  
> This repository contains ALL foundational standards, principles, and guidelines that govern how HaldisB2B builds software. Every team member and AI agent must understand and follow these principles.  
> In addition, it includes organization-wide GitHub templates and profile information to ensure consistency and professionalism across all projects.

---

## 🚨 **MANDATORY READING ORDER**

**📋 FOR ALL TEAM MEMBERS (HUMAN AND AI):**

### **1. 🏗️ ARCHITECTURE FIRST (CRITICAL)**
**[`SOFTWARE-ARCHITECTURE-LAYERS.md`](SOFTWARE-ARCHITECTURE-LAYERS.md)**
- **Status**: MANDATORY - Non-negotiable organizational principle
- **Purpose**: Four-layer architecture that governs ALL development
- **Read Time**: 30 minutes
- **Why Critical**: Defines how we build software at HaldisB2B

### **2. 🤖 DEVELOPMENT STANDARDS**
**[`AGENTS.md`](AGENTS.md)**
- **Status**: MANDATORY - Universal development standards
- **Purpose**: AI-assisted development patterns and quality requirements
- **Read Time**: 25 minutes
- **Why Critical**: Combines strategic directives with tactical execution

### **3. 🔧 TECHNOLOGY STACK**
**[`FRAMEWORKS.md`](FRAMEWORKS.md)**
- **Status**: MANDATORY - Technology selection standards
- **Purpose**: Approved frameworks and technology choices
- **Read Time**: 20 minutes
- **Why Critical**: Ensures consistency across all projects

### **4. 🛠️ DEVELOPMENT TOOLS**
**[`TOOLS.md`](TOOLS.md)**
- **Status**: MANDATORY - Comprehensive toolchain standards
- **Purpose**: Approved development tools and best practices
- **Read Time**: 20 minutes
- **Why Critical**: Establishes standard development environment

---

## 📁 Repository Structure & Template Overview

### 🏢 Organization Profile
- `profile/README.md` - Organization profile displayed on GitHub

### 📋 Issue Templates
- `.github/ISSUE_TEMPLATE/` - Standardized issue templates
  - `bug_report.yml` - Bug report template
  - `feature_request.yml` - Feature request template
  - `general.yml` - General issue template
  - `config.yml` - Issue template configuration

### 🔄 Pull Request Templates
- `.github/PULL_REQUEST_TEMPLATE.md` - Standardized PR template

### ⚙️ Workflow Templates
- `workflow-templates/` - Reusable GitHub Actions workflows
  - `nodejs-ci.yml` - Node.js CI/CD pipeline
  - `python-ci.yml` - Python CI/CD pipeline
  - `code-quality.yml` - Code quality and security analysis

---

## 📋 **Quick Reference Summary**

### Core Architectural Principles
```yaml
Foundation: Four-layer architecture (MANDATORY)
Layers:
  - Presentation: UI components, user interactions
  - Application: Business logic, APIs, services
  - Data: Persistence, caching, data management
  - Infrastructure: Deployment, monitoring, platform
Rule: Each layer must be independently modifiable
```

### Technology Stack (Primary)
```yaml
Frontend: React 18 + TypeScript 5+ + Vite + Tailwind CSS
State: Zustand (simple) + XState (complex workflows)
Backend: Node.js + Express/Fastify + TypeScript
Database: PostgreSQL (via Supabase)
Package Manager: PNPM (primary)
Text Editing: Lexical (Meta framework)
Testing: Vitest + Testing Library + Playwright
```

### AI Development Tools (Required)
```yaml
Primary: GitHub Copilot ($10/month Pro)
Secondary: Claude Code ($200/month for complex tasks)
Alternative: Cursor IDE ($20/month Pro)
Specification: GitHub Spec Kit (open source)
```

### Infrastructure & DevOps
```yaml
Containers: Docker + Docker Compose
CI/CD: GitHub Actions (primary)
IaC: Terraform + Ansible
Monitoring: Prometheus + Grafana
Cloud: AWS (primary), Google Cloud Platform (alternative)
```

---

## 🎯 Purpose

These templates and standards help maintain consistency across all HaldisB2B repositories by providing:

- **Standardized Issue Reporting**: Clear formats for bug reports, feature requests, and general issues
- **Consistent PR Process**: Comprehensive pull request templates with checklists
- **Ready-to-Use Workflows**: Battle-tested CI/CD pipelines for common technologies
- **Professional Organization Profile**: Welcoming introduction to HaldisB2B for visitors
- **Foundational Documentation**: Key standards and architectural principles for all contributors

---

## 🚀 Usage

All templates in this repository are automatically available across the HaldisB2B organization:

- **Issue Templates**: Available when creating new issues in any repository
- **PR Templates**: Automatically populated when creating pull requests
- **Workflow Templates**: Available in the Actions tab when setting up workflows
- **Organization Profile**: Displayed on the HaldisB2B organization page

---

## 🤖 Development Workflow Overview

### Sacred Rules (Override All Others)
1. **When in doubt, don't deploy**
2. **When AI seems confident, verify twice**
3. **When metrics decline, stop and reassess**
4. **Be brutally honest - no sugar-coating, no false positives**
5. **🆕 ARCHITECTURAL COMPLIANCE IS MANDATORY**

### Development Process
```yaml
1. Architecture: Ensure compliance with four-layer principles
2. Specification: Write what and why before how (GitHub Spec Kit)
3. Implementation: Types → Tests → Architecture (TTA)
4. Quality: 90%+ test coverage + security scanning
5. Deployment: Staging → Production with automated rollback
```

---

## 🤝 Contributing

To improve these templates or standards:

1. Fork this repository
2. Make your changes
3. Test the templates in a test repository
4. Submit a pull request with your improvements

---

## 👥 For Human Developers

### Onboarding Checklist
- [ ] Read all four mandatory documents (Architecture → Agents → Frameworks → Tools)
- [ ] Set up development environment per TOOLS.md
- [ ] Configure approved frameworks per FRAMEWORKS.md
- [ ] Install GitHub Copilot and GitHub Spec Kit
- [ ] Practice architectural compliance on sample project
- [ ] Attend weekly coordination sessions

### Daily Development
- [ ] Validate architectural layer assignment for your work
- [ ] Use approved tools and frameworks only
- [ ] Follow TTA workflow (Types → Tests → Architecture)
- [ ] Include AI transparency in all commits
- [ ] Maintain 90%+ test coverage
- [ ] Validate layer boundaries in code reviews

---

## 📊 Success Metrics & Compliance

### Architectural Health KPIs
- **Layer Separation Score**: Measured by dependency analysis
- **API Contract Stability**: Breaking changes per quarter
- **Service Independence**: Deployment frequency per service
- **System Resilience**: Mean time to recovery (MTTR)
- **Developer Productivity**: Time from idea to production

### Quality Gates (All Projects)
- ✅ Architectural compliance validation
- ✅ 90%+ test coverage on core functionality
- ✅ All AI decisions documented with confidence scores
- ✅ Security scanning with zero critical vulnerabilities
- ✅ Performance benchmarks within acceptable thresholds

### DORA Metrics Tracking
- **Deployment Frequency**: Should increase with AI assistance
- **Lead Time**: Should decrease with AI assistance
- **Change Failure Rate**: Must not increase despite AI usage
- **Mean Time to Recovery**: Must not increase

---

## 📞 Getting Help & Support

### Architecture Questions
- **Primary**: Create issue in this repository with `architecture` label
- **Emergency**: Contact architecture team directly
- **Review**: Schedule architectural review session

### Development Standards
- **Framework Questions**: Reference FRAMEWORKS.md or create issue
- **Tool Issues**: Reference TOOLS.md or create issue
- **AI Development**: Reference AGENTS.md or create issue

### Process Issues
- **Specification Problems**: GitHub Spec Kit documentation
- **Quality Gates**: Create issue with `quality` label
- **Compliance Violations**: Create issue with `compliance` label

---

## 🔄 Document Maintenance

### Update Schedule
- **Monthly**: Security updates and tool version bumps
- **Quarterly**: Framework and tool evaluations
- **Bi-annually**: Major architectural principle reviews
- **Continuously**: AI agent contributions and improvements

### Change Process
1. **Propose changes** via GitHub issues with detailed rationale
2. **Architecture review** for any foundational changes
3. **Team consensus** on significant modifications
4. **Documentation update** with version tracking
5. **Team notification** of approved changes

### Version History
- **v1.2 (January 2025)**: Added SOFTWARE-ARCHITECTURE-LAYERS.md as mandatory foundation
- **v1.1 (January 2025)**: Integrated comprehensive TOOLS.md with AI-driven updates
- **v1.0 (September 2025)**: Initial consolidated standards from 7 repositories

---

## 🚀 Quick Start for New Projects

### 1. Architecture Planning
```bash
# Read architectural principles first
open SOFTWARE-ARCHITECTURE-LAYERS.md

# Plan your layer assignment
# - Which layers will your project use?
# - How will layers communicate?
# - What are the API contracts?
```

### 2. Project Setup
```bash
# Initialize with GitHub Spec Kit
uvx --from git+https://github.com/github/spec-kit.git specify init <PROJECT_NAME>

# Set up approved stack
npm create vite@latest <PROJECT_NAME> -- --template react-ts
cd <PROJECT_NAME>
npm install

# Add HaldisB2B standard dependencies
pnpm install tailwindcss zustand lucide-react clsx tailwind-merge
pnpm install zod react-hook-form @hookform/resolvers
pnpm install -D vitest @testing-library/react eslint prettier
```

### 3. Development Process
```bash
# Specify what you're building
/specify [Your feature description focusing on what and why]

# Plan technical implementation
/plan [Your tech choices from FRAMEWORKS.md]

# Break down into tasks
/tasks

# Implement with architectural compliance
# Remember: Types → Tests → Architecture
```

---

## 📁 *Standardizing excellence and architectural compliance across HaldisB2B repositories.*

---
*"In the race between AI capabilities and engineering wisdom, we choose to run faster together - with proper architectural boundaries."*

**— HaldisB2B Development Standards v1.2**