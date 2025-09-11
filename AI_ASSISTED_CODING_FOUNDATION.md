# AI-Assisted Coding Foundation
## Organizational Best Practices & Development Standards

### Introduction

AI changes how fast we can code, not how well we must code. This living document defines our practices for AI-assisted development—practices born from real implementation, not theory. These aren't constraints; they're force multipliers that turn AI's raw speed into sustainable velocity.

Every directive here exists because something broke without it. Follow them to ship faster while sleeping better.

*This document evolves faster than scientific consensus - we outrun peer review by necessity.*

---

## The Sacred Rules

Three rules override all others:

1. **When in doubt, don't deploy**
2. **When AI seems confident, verify twice**
3. **When metrics decline, stop and reassess**

---

## Strategic Directives

### 1. Specifications Are Code
**Write the what and why before the how.**

Create executable specifications using GitHub Spec Kit (`uvx --from git+https://github.com/github/spec-kit.git specify init`) or equivalent. AI with clear intent produces reliable code. AI with vague requirements produces believable nonsense. The spec is your single source of truth—version it, review it, enforce it.

### 2. Types → Tests → Architecture (TTA)
**This order matters. This order is law.**

- **Types First**: Define every interface, schema, and data shape before writing logic. Types are contracts that prevent AI from inventing impossible states.
- **Tests Second**: Write failing tests that define success. Tests aren't just validation—they're executable specifications that survive refactoring.
- **Architecture Third**: Document decisions after code works. ADRs capture why you built what you built, not what you wished you'd built.

Each step ratchets correctness. Skip none.

### 3. 100 Lines Per PR Maximum
**Smaller changes = faster ships + fewer breaks.**

Hard limit: 100 lines. Sweet spot: 50 lines. Stack PRs for larger features. A 50-line PR merges 40% faster and breaks 85% less often than a 250-line PR. AI reasons better about focused changes. Reviewers actually review small changes.

### 4. Context Never Dies
**AI forgets everything. Your codebase must remember.**

Maintain three context layers:
- `.project/constitution.md` - Immutable principles and constraints
- `.project/memory.md` - Patterns discovered, mistakes made, lessons learned
- `.project/prompts/` - Successful prompts that produced production code

Update memory weekly. Update constitution quarterly. Version everything.

### 5. Four-Hour Task Maximum
**If it takes longer than half a day, it's too big.**

Decompose ruthlessly:
- Each task = one PR
- Each PR = one test file
- Each test file = one concern
- Each concern = reviewable in 15 minutes

Complexity is the enemy of AI-assisted development.

---

## Code Organization & Quality

### Module Structure
- Never use nested functions - always use class methods or module-level functions
- Keep imports at module level - NO LOCAL IMPORTS inside functions
- Follow single responsibility principle for functions and classes
- Use meaningful, descriptive names for variables, functions, and classes

### Import Standards
- Group imports: standard library, third-party, local modules
- Use absolute imports when possible
- Avoid wildcard imports (`from module import *`)
- Sort imports alphabetically within groups

### Error Handling
- Use specific exception types, avoid bare `except:` clauses
- Handle errors at the appropriate level - don't catch and ignore
- Include meaningful error messages with context

### Performance Considerations
- Avoid premature optimization
- Use appropriate data structures (dict for lookups, set for membership)
- Consider memory usage for large datasets
- Profile before optimizing

---

## Documentation & Communication

### Code Comments
- Comments should explain "why", not "what" unless the logic is non-obvious
- Don't add comments above self-documenting code
- Use docstrings for public functions and classes
- Remove TODO comments before committing - create issues instead

### Communication Style
- Be terse but informative in commit messages and PR descriptions
- Avoid emoji in commit messages, PR titles, and code comments
- Write natural, flowing text - avoid structured bullet points in commits
- Avoid "LLM tells" - no **Heading** - description format in communications

### Documentation Levels
**Comments (in-code):**
- Explain "why" decisions were made
- Clarify non-obvious business logic
- Document assumptions and constraints

**External Documentation:**
- Architecture decisions and system overview
- API specifications and usage examples
- Deployment and operational procedures
- User guides and integration examples

---

## AI Integration & Context Management

### 6. Connect AI to Reality via MCP
**Live documentation beats stale memory.**

Deploy Model Context Protocol servers or equivalent:
- Context7 for lightweight memory graphs
- Custom MCP servers for your APIs and docs
- Gitingest for repository comprehension

No more hallucinated endpoints. No more fictional methods. Real-time truth.

### 7. Prompts Are Assets
**Yesterday's prompt is tomorrow's productivity.**

Successful prompts go in `.project/prompts/` with:
- What it accomplished
- Which model it targeted
- Success criteria
- Example output

Good prompts are intellectual property. Treat them as such.

### 8. Error Messages Are Context
**"It doesn't work" helps nobody. Stack traces help everyone.**

When requesting AI fixes, always provide:
- Full error message
- Stack trace
- Failing test name
- Expected vs actual behavior
- What you already tried

Specific problems get specific solutions.

### 9. Vibe Code in Quarantine
**Exploration has different rules than exploitation.**

Vibe coding (rapid, unreviewed AI generation) is powerful for prototypes. Rules:
- 8-hour maximum time box
- Separate `prototype/` branches
- Clear "DO NOT DEPLOY" markers
- Must be rewritten with TTA discipline for production
- Extract patterns to memory, discard the code

Weekend hackathon rules don't apply to weekday production.

---

## Security & Operations

### 10. Security Scanning at Write-Time
**Not after commit. Not in review. At write-time.**

Four layers of defense:
1. Pre-commit hooks: Secrets, formatting, linting
2. CI pipeline: SAST, dependency audit, license check
3. Pre-merge: Security team review for auth/crypto/data access (or automated equivalent for small teams)
4. Production: Runtime security monitoring

AI doesn't think like an attacker. You must.

### Security in Code
- Never commit secrets, API keys, or passwords
- Validate and sanitize user inputs
- Use parameterized queries for database operations
- Follow principle of least privilege

### 11. Staging Is Not Optional
**Production is sacred. AI never touches it directly.**

Mandatory flow: Local → CI → Staging → Production
- Staging matches production exactly
- 24-hour minimum staging soak
- Automated smoke tests before promotion
- Rollback plan before deployment

Break this rule once, explain to customers forever.

### 12. Observable By Default
**If you can't see it, you can't fix it.**

Every service implements:
- Structured logging (with correlation IDs)
- Distributed tracing (OpenTelemetry or equivalent)
- Business metrics (not just technical)
- Health endpoints (with dependency checks)
- Error tracking (with user impact assessment)

Observability isn't optional—it's part of the definition of done.

### 13. Fail Fast, Recover Faster
**When AI breaks things (it will), detection speed matters.**

Implement:
- Feature flags for instant rollback
- Canary deployments (5% → 25% → 50% → 100%)
- Automated rollback on SLO breach
- Circuit breakers for external dependencies
- Graceful degradation patterns

The question isn't if AI will create bugs, but how fast you'll catch them.

---

## Testing & Quality Assurance

### Testing Philosophy
- Write tests before implementing complex logic
- Use descriptive test names that explain the scenario
- Mock external dependencies in unit tests
- Aim for high test coverage but focus on critical paths

### 14. Boring Is Beautiful
**Novel solutions are technical debt in disguise.**

Direct AI to:
- Follow existing patterns
- Use standard library functions
- Implement conventional approaches
- Avoid clever optimizations

Boring code is debuggable at 3 AM.

---

## Human Oversight & Decision Making

### 15. Humans Own Architecture
**AI proposes implementations. Humans decide architectures.**

ADRs must be human-authored after human discussion. AI can:
- Generate options with trade-offs
- Analyze performance implications
- Find prior art and patterns

AI cannot:
- Make strategic technical decisions
- Evaluate business context
- Predict sociological effects on the team

### 16. Review Like It's Human Code
**Because bad code is bad code, regardless of author.**

Review criteria don't change for AI:
- Does it solve the stated problem?
- Will someone understand it in six months?
- Does it handle edge cases?
- Is it testable?
- Does it follow our patterns?

The only difference: review more carefully, because AI lies convincingly.

---

## Measurement & Continuous Improvement

### 17. DORA Metrics Are Your Compass
**What gets measured gets improved.**

Track religiously:
- **Deployment Frequency**: Should increase with AI
- **Lead Time**: Should decrease with AI
- **Change Failure Rate**: Must not increase (if it does, add reviews)
- **Mean Time to Recovery**: Must not increase (if it does, improve observability)

If metrics worsen with AI, you're using AI wrong.

---

## Implementation Roadmap

**Week 1**: Specs (#1), Memory (#4), Staging (#11), Security scanning (#10)

**Week 2**: TTA workflow (#2), Small PRs (#3), Task decomposition (#5)

**Week 3**: MCP deployment (#6), Observability (#12), DORA metrics (#17)

**Week 4**: Prompt library (#7), Review process (#16), Feature flags (#13)

**Ongoing**: Pattern evolution (#14), Documentation, Continuous improvement

---

## Success Metrics

**You're succeeding when:**
- Deployment frequency increases while failure rate decreases
- Developers spend more time on architecture than syntax
- Security vulnerabilities are caught before commit
- New team members are productive in days, not weeks
- 3 AM pages become rare, then extinct

**You're failing when:**
- Debugging time exceeds development time
- The same bugs resurface repeatedly
- Developers fear deployments
- Technical debt grows faster than features
- Customers find bugs before tests do

---

## Living Document Protocol

This document evolves with our understanding of AI-assisted development:

- **Weekly**: Update `.project/memory.md` with new patterns and lessons
- **Monthly**: Review metrics and adjust tactical practices
- **Quarterly**: Reassess strategic directives based on data
- **Continuously**: Capture successful prompts and techniques

**Version History:**
- v1.0 (September 2025): Initial strategic framework + tactical practices merge
- Next review: December 2025

---

## Final Wisdom

AI is a power tool, not a replacement for thought. It makes good developers faster and bad developers dangerous. These practices ensure you stay in the first category.

Start with the fundamentals. Measure everything. Adjust based on data, not opinion. What works for Google might not work for you, but these principles are universal.

Remember: The goal isn't to use AI everywhere—it's to use AI where it multiplies human capability without dividing code quality.

*This document is law until data proves otherwise. Update it based on metrics, not feelings.*

---

*In the race between AI capabilities and engineering wisdom, we choose to run faster together.*