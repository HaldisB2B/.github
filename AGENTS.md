# AGENTS.md — Master Template for AI-Assisted Development
## Universal Standards for All HaldisB2B Projects

> **Mission**  
> Establish organization-wide standards for AI-assisted development that turn AI's raw speed into sustainable velocity. This template combines strategic directives with tactical execution patterns discovered across all HaldisB2B projects.

---

## 🚨 **MANDATORY READING FIRST**

**📋 BEFORE STARTING ANY DEVELOPMENT:**
- ✅ **READ**: `SOFTWARE-ARCHITECTURE-LAYERS.md` - **MANDATORY** architectural principles
- ✅ **UNDERSTAND**: Four-layer architecture (Presentation, Application, Data, Infrastructure)
- ✅ **FOLLOW**: Separation of concerns for ALL code changes
- ✅ **VALIDATE**: Your work respects layer boundaries and API contracts

**🎯 Architecture Compliance:**
Every feature, every line of code, every AI decision must respect the four-layer architecture defined in `SOFTWARE-ARCHITECTURE-LAYERS.md`. This is NOT optional - it's how HaldisB2B builds software.

---

## The Sacred Rules (Override All Others)

1. **When in doubt, don't deploy**
2. **When AI seems confident, verify twice**  
3. **When metrics decline, stop and reassess**
4. **Be brutally honest - no sugar-coating, no false positives**
5. **🆕 ARCHITECTURAL COMPLIANCE IS MANDATORY** - All code must follow `SOFTWARE-ARCHITECTURE-LAYERS.md`

---

## Core Development Philosophy

### 0. Architecture First (NEW - CRITICAL)
**Every development decision must respect the four-layer architecture.**

- **Presentation Layer**: UI components, user interactions, client-side state only
- **Application Layer**: Business logic, API endpoints, service coordination
- **Data Layer**: Database operations, caching, data validation
- **Infrastructure Layer**: Deployment, monitoring, CI/CD, platform services

**🚨 VIOLATION DETECTION**: If your change affects multiple layers simultaneously, you're probably doing it wrong. Each layer must be independently modifiable.

### 1. Specifications Are Code
**Write the what and why before the how.**

- Create executable specifications using GitHub Spec Kit or equivalent
- AI with clear intent produces reliable code; AI with vague requirements produces believable nonsense
- The spec is your single source of truth—version it, review it, enforce it
- Every feature must have a specification in `/spec/` or `/docs/spec/`

### 2. Types → Tests → Architecture (TTA)
**This order matters. This order is law.**

- **Types First**: Define every interface, schema, and data shape before writing logic
- **Tests Second**: Write failing tests that define success
- **Architecture Third**: Document decisions after code works with ADRs

TypeScript projects: Strict mode enabled, no `any` types allowed.

### 3. AI Transparency & Brutal Honesty
**Every AI decision must be transparent and brutally honest.**

- Include confidence scores and reasoning for all AI recommendations
- Log all AI decisions in `ai_decisions` table or equivalent
- Never present uncertain information as fact
- Use phrases like "Based on available data..." or "This appears to..."
- When you don't know something, say so explicitly

### 4. Feature Flags Are Mandatory
**Everything cloud/external is opt-in via environment flags.**

- Default to local-first operation
- Cloud services behind feature flags (default OFF)
- No network calls unless user explicitly enables
- Format: `FEATURE_NAME_ENABLED=true/false`

---

## Project Structure & Organization

### Repository Standards
```
/spec/           # Executable specifications (SDD)
/docs/           # Architecture decisions and documentation  
/.project/       # Project-specific context
  constitution.md # Immutable principles
  memory.md      # Lessons learned, patterns discovered
  prompts/       # Successful prompts that produced production code
/tests/          # Test suites (unit, integration, E2E)
```

### Module Architecture
- Never use nested functions - use class methods or module-level functions
- Keep imports at module level - NO LOCAL IMPORTS inside functions
- Follow single responsibility principle
- Use meaningful, descriptive names
- **🆕 RESPECT LAYER BOUNDARIES** - No cross-layer imports without proper abstractions

### Import Standards
- Group imports: standard library, third-party, local modules
- Use absolute imports when possible
- Avoid wildcard imports (`from module import *`)
- Sort imports alphabetically within groups
- **🆕 LAYER VALIDATION** - Ensure imports respect architectural boundaries

---

## Architectural Compliance (NEW SECTION)

### Layer-Specific Rules

**Presentation Layer Rules:**
- ❌ NO business logic in components
- ❌ NO direct database calls
- ❌ NO external service integrations
- ✅ API calls to Application Layer only
- ✅ User interaction handling
- ✅ Client-side validation for UX

**Application Layer Rules:**
- ❌ NO UI-specific logic
- ❌ NO direct database manipulation
- ✅ Business logic implementation
- ✅ API endpoint definitions
- ✅ Service coordination
- ✅ Authentication/authorization

**Data Layer Rules:**
- ❌ NO business logic in procedures
- ❌ NO UI concerns
- ✅ Data persistence and retrieval
- ✅ Data validation and integrity
- ✅ Caching and optimization

**Infrastructure Layer Rules:**
- ❌ NO business logic
- ❌ NO UI concerns
- ✅ Deployment and scaling
- ✅ Monitoring and logging
- ✅ CI/CD pipeline management

### Architecture Validation Checklist
Before every commit:
- [ ] Code belongs to correct architectural layer
- [ ] No inappropriate cross-layer dependencies
- [ ] API contracts properly defined
- [ ] Business logic only in Application Layer
- [ ] UI logic only in Presentation Layer
- [ ] Data access properly abstracted

---

## Quality Assurance & Testing

### Testing Hierarchy
1. **Unit Tests**: Reducers, utilities, pure functions
2. **Integration Tests**: API contracts, database operations
3. **E2E Tests**: User workflows, critical paths
4. **Visual Regression**: UI components, layouts
5. **Security Tests**: Input validation, authentication flows
6. **🆕 Architecture Tests**: Layer boundary compliance

### Quality Gates
- Test coverage ≥90% on core functionality
- All tests pass before merge
- Security scanning at write-time (pre-commit hooks)
- Performance benchmarks within acceptable thresholds
- Accessibility compliance (no critical violations)
- **🆕 Architectural compliance validation**

### Error Handling
- Use specific exception types, avoid bare `except:` clauses
- Handle errors at appropriate level - don't catch and ignore
- Include meaningful error messages with context
- Log errors with correlation IDs for traceability
- **🆕 Handle errors at correct architectural layer**

---

## Security & Privacy Standards

### Security Layers
1. **Pre-commit hooks**: Secrets, formatting, linting
2. **CI pipeline**: SAST, dependency audit, license check  
3. **Pre-merge**: Security team review for auth/crypto/data access
4. **Production**: Runtime security monitoring

### Privacy Requirements
- Never commit secrets, API keys, or passwords
- Validate and sanitize all user inputs
- Use parameterized queries for database operations
- Follow principle of least privilege
- Implement row-level security where applicable

---

## AI Integration Patterns

### Context Management
**AI forgets everything. Your codebase must remember.**

Maintain three context layers:
- `.project/constitution.md` - Immutable principles and constraints
- `.project/memory.md` - Patterns discovered, mistakes made, lessons learned  
- `.project/prompts/` - Successful prompts that produced production code

### Architectural AI Guidance
When asking AI for help:
- Specify which architectural layer the work belongs to
- Ask AI to validate layer boundary compliance
- Request architectural decision rationale
- Verify AI suggestions against `SOFTWARE-ARCHITECTURE-LAYERS.md`

### Prompt Asset Management
Store successful prompts in `.project/prompts/` with:
- What it accomplished
- Which model it targeted
- Success criteria
- Example output
- **🆕 Architectural layer context**

### Error Context Protocol
When requesting AI fixes, always provide:
- Full error message and stack trace
- Failing test name
- Expected vs actual behavior
- What you already tried
- **🆕 Architectural layer being modified**

---

## Development Workflow

### Task Decomposition
- Maximum task size: 4 hours
- Each task = one PR
- Each PR ≤ 100 lines (sweet spot: 50 lines)
- Each concern = reviewable in 15 minutes
- **🆕 Each task should affect minimal architectural layers**

### Commit Standards
All commits must include trailers:
```
AI-Contribution-Percentage: XX%
AI-Tools-Used: ["Claude", "Copilot", etc.]
Human-Review-Status: "Reviewed by <name>"
Decision-Rationale: "Brief explanation"
Architecture-Layer: "Presentation|Application|Data|Infrastructure"
Layer-Compliance: "Validated against SOFTWARE-ARCHITECTURE-LAYERS.md"
```

### PR Requirements
- Descriptive title following conventional commits
- Natural, flowing description (avoid bullet points)
- Linked to specification or issue
- All quality gates passed
- **🆕 Architectural compliance statement**

---

## Deployment & Operations

### Staging Requirements
**Production is sacred. AI never touches it directly.**

Mandatory flow: Local → CI → Staging → Production
- Staging matches production exactly
- 24-hour minimum staging soak
- Automated smoke tests before promotion
- Rollback plan before deployment

### Observability Standards
Every service implements:
- Structured logging (with correlation IDs)
- Distributed tracing (OpenTelemetry or equivalent)
- Business metrics (not just technical)
- Health endpoints (with dependency checks)
- Error tracking (with user impact assessment)

### Failure Recovery
- Feature flags for instant rollback
- Canary deployments (5% → 25% → 50% → 100%)
- Automated rollback on SLO breach
- Circuit breakers for external dependencies
- Graceful degradation patterns

---

## Communication & Documentation

### Code Comments
- Explain "why", not "what" unless non-obvious
- Don't comment self-documenting code
- Use docstrings for public functions and classes
- Remove TODO comments before committing (create issues instead)
- **🆕 Document architectural decisions and layer justifications**

### Documentation Levels
**Comments (in-code):**
- Explain "why" decisions were made
- Clarify non-obvious business logic
- Document assumptions and constraints
- **🆕 Justify architectural layer placement**

**External Documentation:**
- Architecture decisions (ADRs)
- API specifications and usage examples
- Deployment and operational procedures
- User guides and integration examples

### Communication Style
- Be terse but informative
- Avoid emoji in commit messages and code comments
- Write natural, flowing text - avoid structured bullet points
- Avoid "LLM tells" - no **Heading** - description format

---

## Performance & Scalability

### Performance Guidelines
- Avoid premature optimization
- Use appropriate data structures (dict for lookups, set for membership)
- Profile before optimizing
- Implement caching at appropriate levels
- **🆕 Consider performance impact of layer separation**

### Scaling Considerations
- Design for horizontal scaling from day one
- Use connection pooling for databases
- Implement proper rate limiting
- Monitor resource utilization
- **🆕 Scale layers independently when possible**

---

## Project-Specific Sections

### For MCP Servers
- Follow Model Context Protocol rev. 2025-06-18
- Implement ethical defaults (robots obey, throttling)
- Provide LLM-ready outputs (Markdown + provenance)
- Include error codes: E_TIMEOUT, E_NETWORK, E_MAX_SIZE, etc.

### For Web Applications  
- TypeScript + React patterns
- State management with appropriate tools (Zustand, XState)
- Authentication via OAuth providers
- Database with proper indexing and migrations
- **🆕 Follow Presentation → Application → Data layer flow**

### For AI/ML Projects
- Feature flag all AI services (default OFF)
- Log all AI decisions with confidence scores
- Implement fallback for when AI services unavailable
- Version control for models and prompts

---

## DORA Metrics Tracking

Track religiously:
- **Deployment Frequency**: Should increase with AI
- **Lead Time**: Should decrease with AI  
- **Change Failure Rate**: Must not increase
- **Mean Time to Recovery**: Must not increase

If metrics worsen with AI, you're using AI wrong.

---

## Success Criteria

**You're succeeding when:**
- Deployment frequency increases while failure rate decreases
- Developers spend more time on architecture than syntax
- Security vulnerabilities caught before commit
- New team members productive in days, not weeks
- 3 AM pages become rare, then extinct
- **🆕 Architectural boundaries are naturally respected**
- **🆕 Layer modifications don't cause cascading changes**

**You're failing when:**
- Debugging time exceeds development time
- Same bugs resurface repeatedly
- Developers fear deployments
- Technical debt grows faster than features
- Customers find bugs before tests do
- **🆕 Changes in one layer break other layers**
- **🆕 Architectural principles are frequently violated**

---

## Living Document Protocol

This document evolves with our understanding:

- **Weekly**: Update `.project/memory.md` with lessons learned
- **Monthly**: Review metrics and adjust tactical practices  
- **Quarterly**: Reassess strategic directives based on data
- **Continuously**: Capture successful prompts and techniques
- **🆕 Architectural Reviews**: Monthly architectural compliance assessments

**Version History:**
- v2.1 (January 2025): Added mandatory architectural compliance requirements
- v2.0 (September 2025): Consolidated from 7 repositories + strategic foundation
- Next review: March 2025

---

## Implementation Commands

Standard commands across all projects:
```bash
# Development setup
pnpm install          # or npm install, yarn install
pnpm dev              # Start development server

# Quality checks
pnpm typecheck        # TypeScript validation
pnpm lint             # Linting and formatting
pnpm test             # Unit tests
pnpm test:e2e         # End-to-end tests
pnpm build            # Production build

# NEW: Architecture validation
pnpm arch:check       # Validate architectural compliance
pnpm arch:layers      # Analyze layer dependencies
```

Project-specific commands documented in local README.md.

---

## Final Wisdom

AI is a power tool, not a replacement for thought. It makes good developers faster and bad developers dangerous. These practices ensure you stay in the first category.

**Remember**: The goal isn't to use AI everywhere—it's to use AI where it multiplies human capability without dividing code quality or violating architectural principles.

**🚨 CRITICAL**: Every AI agent and human developer must read and follow `SOFTWARE-ARCHITECTURE-LAYERS.md`. Architecture compliance is not negotiable at HaldisB2B.

*This document is law until data proves otherwise. Be brutally honest in all interactions.*

---

*In the race between AI capabilities and engineering wisdom, we choose to run faster together - with proper architectural boundaries.*