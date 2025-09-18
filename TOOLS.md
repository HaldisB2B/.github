# TOOLS.md — HaldisB2B Development Tools Standards
## Comprehensive Toolchain for Modern Development (Q4 2024)

<!-- 
Author: Claude Code Assistant  
Date: 2025-01-13
Purpose: Comprehensive development tools standards with auto-update mechanisms
Last Research: Q4 2024 tool landscape analysis
Update Frequency: Quarterly or when significant changes occur
-->

> **Mission**  
> Establish standard development tools across all HaldisB2B projects to maximize productivity, ensure consistency, and leverage the latest technological advances while maintaining stability.

---

## 🚨 **ARCHITECTURAL FOUNDATION REQUIRED**

**📋 MANDATORY BEFORE USING ANY TOOLS:**
- ✅ **READ**: `SOFTWARE-ARCHITECTURE-LAYERS.md` for architectural principles
- ✅ **UNDERSTAND**: Four-layer architecture (Presentation, Application, Data, Infrastructure)
- ✅ **VALIDATE**: All tool choices support proper layer separation
- ✅ **ENSURE**: Tools enable clean architectural boundaries

**🎯 Tool Selection Rule:**
Every tool must support the four-layer architecture and not encourage mixing of concerns across layers. Tools that promote architectural violations are NOT approved for HaldisB2B projects.

---

## 🔄 **AGENT UPDATE INSTRUCTIONS** 

**📋 For AI Agents Reading This Document:**

**MANDATORY ACTIONS WHEN USING THIS DOCUMENT:**
1. **Verify Currency**: Check if tools mentioned are still current (compare with latest releases/versions)
2. **Research Missing Tools**: If you encounter excellent tools not listed here, research and suggest additions
3. **Update Suggestions**: Add suggestions to the [Tool Suggestions](#-tool-suggestions-agent-contributions) section
4. **Flag Outdated Items**: Mark any outdated information you discover
5. **Performance Validation**: If you have experience with tools not listed, evaluate them against our criteria
6. **🆕 ARCHITECTURAL VALIDATION**: Ensure all tool suggestions respect layer boundaries

**RESEARCH VALIDATION CHECKLIST:**
- [ ] Check tool release dates and current versions
- [ ] Verify community adoption and maintenance status  
- [ ] Validate performance claims with recent benchmarks
- [ ] Confirm compatibility with our existing stack
- [ ] Assess security and enterprise readiness
- [ ] **🆕 VALIDATE**: Tool supports architectural layer separation

---

## 📊 **Current Tool Status (Updated Q4 2024)**

### **Research Date**: December 2024
### **Next Review Due**: March 2025
### **Major Changes Since Last Update**: 
- GitHub Spec Kit officially released
- Bun gaining significant adoption
- AI coding tools with model switching capabilities
- Enhanced CI/CD platform features
- **🆕 Architectural compliance requirements** added

---

## 🎯 **Tool Categories & Recommendations (Architecture-Aligned)**

### **1. 🤖 AI Development Tools (Critical Priority)**

#### **AI Coding Assistants (Choose Primary + Secondary)**

**🥇 Primary Recommendation: GitHub Copilot** *(Updated Nov 2024)*
```yaml
Tier: Enterprise Standard
Cost: $10/month Pro, Free tier available
Key Features:
  - Model switching (GPT-4o, Claude 3.5, Gemini 2.0)
  - Agent Mode for sweeping changes
  - Enhanced code review capabilities
  - 12,000 completions/month on free tier
Integration: Native VS Code, Visual Studio, JetBrains
Best For: Team collaboration, autocomplete, documentation
Architectural Layer: All layers (with proper context)
Architecture Support: ✅ Respects layer boundaries when properly prompted
```

**🥈 Secondary Option: Claude Code** *(For Complex Tasks)*
```yaml
Tier: Advanced/Enterprise
Cost: $200/month (Claude Pro required)
Key Features:
  - 200,000 token context window
  - MCP (Model Context Protocol) integration
  - Autonomous development capabilities
  - Superior algorithm design and code rewriting
Best For: Architectural work, complex refactoring, system design
Architectural Layer: Primarily Application and Infrastructure layers
Architecture Support: ✅ Excellent for architectural planning and layer design
```

**🥉 Alternative: Cursor IDE** *(For Teams)*
```yaml
Tier: Professional
Cost: $20/month Pro, $40/month Business
Key Features:
  - Cursor Agent with semantic search
  - Multi-model support (GPT-4o, o1, Claude 3.5)
  - Built-in terminal commands and file handling
  - Team collaboration features
Best For: Teams requiring integrated IDE experience
Architectural Layer: Primarily Presentation and Application layers
Architecture Support: ✅ Good layer awareness with proper configuration
```

### **2. 📝 IDEs & Code Editors (Presentation Layer Tools)**

#### **Primary IDEs (Choose Based on Stack)**

**Visual Studio Code** *(Universal Standard)*
```yaml
Status: ✅ Approved - Primary
Cost: Free
Extensions Ecosystem: 50,000+ extensions
AI Integration: Native Copilot, Cursor compatibility
Best For: Web development, TypeScript, React projects
Architectural Layer: Presentation Layer (UI development)
Architecture Support: ✅ Excellent with proper workspace organization
Required Extensions:
  - ES Lint + Prettier
  - TypeScript
  - Tailwind CSS IntelliSense
  - GitLens
```

**JetBrains Rider** *(For .NET Projects)*
```yaml
Status: ✅ Approved - .NET Standard
Cost: $139/year
Performance: Superior for large .NET solutions
Best For: Enterprise .NET development, complex solutions
Architectural Layer: Application Layer (.NET services)
Architecture Support: ✅ Strong architectural tooling
```

**Cursor IDE** *(AI-Native Option)*
```yaml
Status: 🧪 Testing Phase
Cost: $20/month Pro
Features: AI-first design, agent mode
Best For: AI-heavy development workflows
Architectural Layer: All layers with AI assistance
Architecture Support: 🧪 Under evaluation
```

### **3. 📦 Package Management (Updated Dec 2024)**

#### **Performance Rankings (Latest Benchmarks)**

**🥇 PNPM** *(Recommended Primary)*
```yaml
Status: ✅ Primary Recommendation
Performance: Fastest for large projects, 70% less disk space
Disk Usage: Shared dependency model
Monorepo Support: Excellent built-in support
Best For: Large-scale projects, monorepos, team environments
Install: npm install -g pnpm
Architectural Layer: Infrastructure Layer (dependency management)
Architecture Support: ✅ Excellent monorepo support for layer separation
```

**🥈 Bun** *(Performance Leader, Limited Platform)*
```yaml
Status: 🧪 Evaluation Phase
Performance: Fastest runtime and package manager
Limitations: No stable Windows support yet
Features: All-in-one runtime, bundler, test runner
Best For: macOS/Linux development, performance-critical projects
Note: Monitor for Windows stability before full adoption
Architectural Layer: Infrastructure Layer (runtime and tooling)
Architecture Support: 🧪 Under evaluation for architectural compatibility
```

**🥉 NPM** *(Fallback Standard)*
```yaml
Status: ✅ Approved Fallback
Compatibility: Universal Node.js support
Best For: Maximum compatibility, simple projects
Performance: Slower than alternatives but universally supported
Architectural Layer: Infrastructure Layer (basic dependency management)
Architecture Support: ✅ Universal compatibility
```

### **4. 🚀 CI/CD & DevOps Platforms (Infrastructure Layer)**

#### **CI/CD Platforms (Tier 1)**

**GitHub Actions** *(Primary Platform)*
```yaml
Status: ✅ Primary Standard
Integration: Native GitHub repository integration
Features:
  - Workflow automation
  - Multi-OS support (Ubuntu, Windows, macOS)
  - Extensive marketplace of actions
  - Built-in security scanning
Cost: Free for public repos, generous free tier for private
Best For: GitHub-hosted projects, standard CI/CD workflows
Architectural Layer: Infrastructure Layer (deployment and automation)
Architecture Support: ✅ Supports layer-specific build and deployment
```

**GitLab CI/CD** *(Full DevOps Platform)*
```yaml
Status: ✅ Approved Alternative
Features: Full DevOps lifecycle platform
Strengths: Integrated repo to deploy pipeline
Best For: Organizations requiring complete DevOps platform
Architectural Layer: Infrastructure Layer (complete DevOps)
Architecture Support: ✅ Strong architectural separation support
```

**Jenkins** *(Enterprise Self-Hosted)*
```yaml
Status: ✅ Approved for Enterprise
Type: Self-hosted automation server
Plugins: 1,000+ available plugins
Best For: Complex enterprise environments, custom workflows
Maintenance: Requires dedicated DevOps team
Architectural Layer: Infrastructure Layer (enterprise automation)
Architecture Support: ✅ Highly configurable for layer-specific workflows
```

#### **Container & Orchestration (Infrastructure Layer)**

**Docker** *(Containerization Standard)*
```yaml
Status: ✅ Essential Tool
Purpose: Application containerization
Integration: Universal platform support
Best For: Consistent development/production environments
Architectural Layer: Infrastructure Layer (application packaging)
Architecture Support: ✅ Excellent for layer isolation and deployment
```

**Kubernetes** *(Orchestration Leader)*
```yaml
Status: ✅ Production Standard
Purpose: Container orchestration at scale
Learning Curve: Steep but essential for scale
Best For: Microservices, cloud-native applications
Tools: kubectl, Helm, ArgoCD for GitOps
Architectural Layer: Infrastructure Layer (container orchestration)
Architecture Support: ✅ Designed for microservices architectural patterns
```

### **5. 🏗️ Infrastructure as Code (Infrastructure Layer)**

**Terraform** *(IaC Leader)*
```yaml
Status: ✅ Primary IaC Tool
Approach: Declarative infrastructure configuration
Cloud Support: AWS, Azure, GCP, and 3,000+ providers
Best For: Multi-cloud infrastructure management
Alternative: AWS CloudFormation (AWS-only)
Architectural Layer: Infrastructure Layer (infrastructure definition)
Architecture Support: ✅ Supports infrastructure for all architectural layers
```

**Ansible** *(Configuration Management)*
```yaml
Status: ✅ Approved
Purpose: Server configuration and automation
Approach: Agentless automation
Best For: Server setup, application deployment automation
Architectural Layer: Infrastructure Layer (configuration automation)
Architecture Support: ✅ Supports layer-specific configuration management
```

### **6. 📊 Monitoring & Observability (Infrastructure Layer)**

**Prometheus + Grafana** *(Monitoring Stack)*
```yaml
Status: ✅ Standard Monitoring Stack
Prometheus: Time-series metrics collection
Grafana: Visualization and dashboarding
Best For: Cloud-native applications, Kubernetes environments
Cost: Open source
Architectural Layer: Infrastructure Layer (system monitoring)
Architecture Support: ✅ Can monitor all architectural layers independently
```

**ELK Stack** *(Logging & Search)*
```yaml
Components: Elasticsearch, Logstash, Kibana
Status: ✅ Approved for Log Management
Best For: Centralized logging, log analysis
Alternative: EFK (Fluentd instead of Logstash)
Architectural Layer: Infrastructure Layer (log aggregation)
Architecture Support: ✅ Layer-aware logging and analysis
```

### **7. 📋 Specification-Driven Development (All Layers)**

**🆕 GitHub Spec Kit** *(Revolutionary Addition)*
```yaml
Status: 🆕 Newly Released (2024)
Purpose: Specification-driven development with AI
Process: Specify → Plan → Tasks → Implement
Integration: Claude Code, GitHub Copilot, Gemini CLI
Cost: Open source
Installation: uvx --from git+https://github.com/github/spec-kit.git specify init
Best For: AI-assisted development, complex feature development
Architectural Layer: All layers (specification spans architecture)
Architecture Support: ✅ EXCELLENT - Designed for specification-driven architecture
```

**OpenAPI/Swagger** *(API Specification)*
```yaml
Status: ✅ API Standard
Purpose: API design and documentation
Tools: Swagger Editor, Postman, Insomnia
Best For: API-first development, team collaboration
Architectural Layer: Application Layer (API contracts)
Architecture Support: ✅ Defines clear boundaries between layers
```

### **8. 🔧 Development Utilities (Layer-Specific)**

**Git + GitHub CLI** *(Infrastructure Layer)*
```yaml
Version Control: Git (essential)
GitHub Integration: gh CLI for repository management
Authentication: Git Credential Manager recommended
Best Practices: Conventional commits, semantic versioning
Architectural Layer: Infrastructure Layer (version control)
Architecture Support: ✅ Universal support for all layers
```

**Database Tools** *(Data Layer)*
```yaml
PostgreSQL: Primary database recommendation
Tools: pgAdmin, DBeaver, TablePlus
ORMs: Prisma (TypeScript), Drizzle (lightweight alternative)
Architectural Layer: Data Layer (database management)
Architecture Support: ✅ Designed for data layer isolation
```

**API Testing** *(Application Layer)*
```yaml
Primary: Postman (team collaboration)
Alternative: Insomnia (developer-focused)
CLI: curl, HTTPie
Automation: Newman (Postman CLI)
Architectural Layer: Application Layer (API testing)
Architecture Support: ✅ Tests Application Layer API contracts
```

---

## 📈 **Tool Selection Criteria (Architecture-First)**

### **Evaluation Framework**
1. **🆕 ARCHITECTURAL COMPATIBILITY** - Supports layer separation
2. **Performance & Speed** - Benchmark against alternatives
3. **Community Adoption** - Active development and support
4. **Integration Capability** - Works with existing stack
5. **Learning Curve** - Team adoption feasibility
6. **Cost Effectiveness** - Value for investment
7. **Security & Compliance** - Enterprise readiness
8. **Future Viability** - Long-term sustainability

### **🆕 Architectural Decision Matrix Template**
```yaml
Tool: [Name]
Architectural Layer: [Presentation|Application|Data|Infrastructure|Cross-Layer]
Score (1-10):
  Architecture Compliance: ___
  Performance: ___
  Community: ___
  Integration: ___
  Learning: ___
  Cost: ___
  Security: ___
  Future: ___
Total: ___/80
Status: ✅ Approved | 🧪 Testing | ❌ Rejected
Architecture Support: [Excellent|Good|Limited|Poor]
```

---

## 🔄 **Tool Suggestions (Agent Contributions)**

> **AI Agents**: Add your tool discoveries and experiences here!

### **🆕 Updated Format for Suggestions**
```yaml
Tool Name: [Name]
Category: [Development/CI-CD/Monitoring/etc.]
Architectural Layer: [Presentation|Application|Data|Infrastructure|Cross-Layer]
Suggested By: [Agent Name]
Date: [YYYY-MM-DD]
Experience Level: [Extensive/Moderate/Limited]
Key Benefits:
  - [Benefit 1]
  - [Benefit 2]
Performance Notes: [Your experience]
Architectural Compliance: [How well it respects layer boundaries]
Comparison: [How it compares to current tools]
Recommendation: [Replace existing/Additional option/Evaluation needed]
```

### **Current Suggestions Queue**

**[Placeholder for agent contributions - agents should add suggestions here]**

**Example Entry:**
```yaml
Tool Name: Biome
Category: Code Formatting/Linting
Architectural Layer: Infrastructure (Development Tools)
Suggested By: [Agent Name]
Date: 2024-12-13
Experience Level: Moderate
Key Benefits:
  - Single tool replacing ESLint + Prettier
  - 20x faster than ESLint
  - Native TypeScript support
Performance Notes: Significantly faster linting and formatting
Architectural Compliance: Excellent - pure development tool, no layer mixing
Comparison: Could replace ESLint + Prettier combination
Recommendation: Evaluation needed for team adoption
```

---

## ⚠️ **Tool Update Alerts**

### **Recently Deprecated/Changed**
- **Yarn 1.x**: Moving toward Yarn 2+ with breaking changes
- **Node-sass**: Replaced by Dart Sass (sass package)
- **TSLint**: Deprecated in favor of ESLint with TypeScript support

### **Emerging Tools to Watch**
- **Bun**: Monitor Windows stability for potential adoption
- **Deno**: Alternative Node.js runtime with built-in TypeScript
- **Biome**: ESLint + Prettier replacement
- **Turborepo**: Monorepo build system optimization

### **🆕 Architectural Alerts**
- **Tools that encourage layer mixing**: Avoid frameworks that blur architectural boundaries
- **All-in-one solutions**: Evaluate carefully for architectural compliance
- **New AI tools**: Validate they understand and respect layer separation

### **Security Alerts**
- **NPM Package Security**: Regular audit with `npm audit` 
- **Docker Base Images**: Keep updated for security patches
- **Dependency Scanning**: GitHub Dependabot enabled by default

---

## 🚀 **Implementation Roadmap (Architecture-Aware)**

### **Phase 1: Core Tools (Immediate)**
- [ ] Standardize on PNPM for package management
- [ ] GitHub Copilot for all team members
- [ ] GitHub Actions for CI/CD
- [ ] Docker for containerization
- [ ] **🆕 Establish architectural compliance validation**

### **Phase 2: Advanced Tools (Month 2)**
- [ ] Implement GitHub Spec Kit for new features
- [ ] Set up Prometheus/Grafana monitoring
- [ ] Terraform for infrastructure management
- [ ] API testing standardization
- [ ] **🆕 Layer-specific tool optimization**

### **Phase 3: Optimization (Month 3)**
- [ ] Evaluate Bun for performance gains
- [ ] Advanced CI/CD pipeline optimization
- [ ] Team training on specification-driven development
- [ ] Tool performance analysis and refinement
- [ ] **🆕 Architectural compliance monitoring and improvement**

---

## 🏗️ **Architectural Tool Organization**

### **Presentation Layer Tools**
```yaml
Primary: VS Code, React DevTools, Browser DevTools
Testing: Storybook, Chromatic, Percy
Styling: Tailwind Play, Figma
State: Redux DevTools, Zustand DevTools
```

### **Application Layer Tools**
```yaml
API Development: Postman, Insomnia, Thunder Client
Testing: Jest, Vitest, Supertest
Documentation: Swagger UI, Stoplight
Debugging: Node.js Inspector, Winston logs
```

### **Data Layer Tools**
```yaml
Database: pgAdmin, DBeaver, TablePlus
Migrations: Prisma Studio, Drizzle Studio
Testing: pg-mem, testcontainers
Monitoring: pgHero, pg_stat_statements
```

### **Infrastructure Layer Tools**
```yaml
Containers: Docker Desktop, Portainer
Orchestration: kubectl, k9s, Lens
IaC: Terraform Cloud, Atlantis
Monitoring: Grafana, Prometheus, Jaeger
```

---

## 📚 **Training & Resources (Architecture-Focused)**

### **Essential Learning Paths**
1. **Architectural Foundations**: `SOFTWARE-ARCHITECTURE-LAYERS.md`
2. **GitHub Spec Kit**: [Official Documentation](https://github.com/github/spec-kit)
3. **PNPM**: [Migration Guide](https://pnpm.io/motivation)
4. **GitHub Actions**: [Workflow Documentation](https://docs.github.com/en/actions)
5. **Docker**: [Best Practices Guide](https://docs.docker.com/develop/dev-best-practices/)

### **Team Onboarding Checklist**
- [ ] **🆕 Read and understand SOFTWARE-ARCHITECTURE-LAYERS.md**
- [ ] Install primary tools (VS Code, PNPM, Docker)
- [ ] Configure GitHub Copilot
- [ ] Access to monitoring dashboards
- [ ] GitHub Spec Kit training session
- [ ] CI/CD pipeline overview
- [ ] **🆕 Architectural compliance training**

---

## 🔍 **Tool Validation Commands (Architecture-Aware)**

### **Quick Tool Status Check**
```bash
# Package manager version
pnpm --version

# Docker status
docker --version
docker compose version

# GitHub CLI
gh --version

# Node.js and npm baseline
node --version
npm --version

# AI tools status
code --version  # VS Code
# GitHub Copilot status in VS Code extensions

# NEW: Architecture validation
# Check if tools respect layer boundaries
pnpm arch:validate  # If available
```

### **Performance Benchmarking**
```bash
# PNPM install speed test
time pnpm install

# Docker build performance
time docker build .

# CI/CD pipeline duration
# Check in GitHub Actions tab

# NEW: Layer-specific performance
pnpm build:presentation  # UI build time
pnpm test:application   # API test time
pnpm migrate:data      # Database migration time
```

---

## 🏆 **Success Metrics (Architecture-Aware)**

### **Tool Adoption KPIs**
- **Setup Time**: New project from 0 to running < 15 minutes
- **CI/CD Pipeline**: Build + test + deploy < 10 minutes
- **Developer Satisfaction**: Tool effectiveness survey scores
- **Performance**: Build times, test execution speed
- **Security**: Zero critical vulnerabilities in dependencies
- **🆕 Architectural Compliance**: Layer boundary violations per project

### **🆕 Architectural Health Metrics**
- **Layer Separation Score**: Tool compliance with architectural boundaries
- **Cross-Layer Dependencies**: Number of inappropriate tool dependencies
- **Tool Architectural Debt**: Tools that encourage layer violations
- **Layer Independence**: Ability to change tools in one layer without affecting others

### **Quarterly Review Process**
1. **Performance Analysis**: Benchmark current vs. alternative tools
2. **Security Audit**: Vulnerability scanning and dependency updates
3. **Team Feedback**: Developer experience and productivity assessment
4. **Industry Trends**: Research emerging tools and practices
5. **Cost Analysis**: Tool licensing and efficiency evaluation
6. **🆕 Architectural Review**: Tool compliance with layer separation principles

---

## 📞 **Support & Updates**

### **Tool Issues & Questions**
- **GitHub Issues**: Create issues in respective tool repositories
- **Internal Documentation**: Update this document with discoveries
- **Team Knowledge Sharing**: Weekly tool tips and tricks sessions
- **🆕 Architectural Questions**: Reference SOFTWARE-ARCHITECTURE-LAYERS.md or create architecture review request

### **Update Process**
1. **Quarterly Reviews**: Comprehensive tool evaluation
2. **Security Updates**: Monthly dependency and tool updates
3. **Agent Contributions**: Continuous suggestions and improvements
4. **Emergency Updates**: Critical security or performance issues
5. **🆕 Architectural Reviews**: Validation of tool compliance with layer principles

---

**Last Updated**: 2025-01-13  
**Next Review**: 2025-04-13  
**Maintained By**: HaldisB2B Development Team + AI Agents

---

*"The right tools don't make you a better developer, but they get out of your way so you can focus on solving real problems while respecting architectural boundaries."*