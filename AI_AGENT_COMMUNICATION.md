# AI Agent Communication Protocol
## Multi-Agent Coordination Standards for HaldisB2B

> **Mission**  
> Enable efficient communication and coordination between multiple AI agents, assistants, and avatars working across HaldisB2B projects while preventing conflicts and duplicated work.

---

## Current Multi-Agent Environment

### Agent Types in HaldisB2B:
- **Code Assistants**: Claude Code, GitHub Copilot, ChatGPT
- **AI Avatars**: Project-specific AI personalities 
- **Review Agents**: Security scanners, code quality checkers
- **Specialized Agents**: MCP servers, custom AI tools
- **Human-AI Hybrids**: Developers working with AI assistance

### Communication Challenges:
- Multiple agents making conflicting decisions
- Duplicated work across different AI assistants
- Inconsistent implementation of organizational standards
- Lack of shared context between agents
- No clear conflict resolution mechanism

---

## Agent Communication Architecture

### Central Command Structure
**Repository**: `HaldisB2B/.github`  
**Primary Channel**: GitHub Issues with standardized labels

```yaml
Labels:
  agent-coordination    # Cross-agent communication
  decision-pending     # Requires agent consensus  
  ai-decision-log      # AI transparency tracking
  conflict-resolution  # When agents disagree
  agent-specialization # Role assignments
```

### Secondary Channels:
- **Commit Trailers**: AI transparency in code changes
- **PR Comments**: Real-time collaboration during reviews  
- **Project Memory**: `.project/agent-decisions/` directory

---

## Standardized Communication Format

### All AI agents MUST use this format:

```markdown
## Agent Communication Protocol

**Agent ID**: [claude-code-v1 / gpt-4-dev / copilot-pr / custom-agent-name]
**Timestamp**: [ISO 8601 format]
**Project**: [repository-name / cross-project]
**Action Type**: [PROPOSE / IMPLEMENT / REVIEW / CONFLICT / QUERY]
**Confidence Level**: [HIGH(90%+) / MEDIUM(70-89%) / LOW(<70%)]

### Context
[Brief description of what this agent is working on]

### Decision/Recommendation  
[Specific action, decision, or recommendation being communicated]

### Dependencies
[What this depends on from other agents or humans]

### Potential Conflicts
[Any conflicts with existing decisions or other agents' work]

### Success Criteria
[How to measure if this decision/action was successful]

### References
[Links to related issues, PRs, or previous decisions]
```

### Example:
```markdown
## Agent Communication Protocol

**Agent ID**: claude-code-20250109
**Timestamp**: 2025-01-09T18:45:00Z
**Project**: abaton
**Action Type**: PROPOSE
**Confidence Level**: HIGH(95%)

### Context
Implementing vector similarity search for abaton database using pgvector extension

### Decision/Recommendation
Use pgvector with cosine similarity for semantic search, implement connection pooling via Supabase

### Dependencies
- Requires approval from architecture agents
- Needs database schema review from gpt-4-architect

### Potential Conflicts
- May conflict with existing Weaviate integration plans
- Resource usage implications need review

### Success Criteria
- Query performance <100ms for 1M vectors
- 95% accuracy on semantic similarity tests
- Passes security review

### References
- Issue #123: Vector database architecture
- Previous decision: commit abc123 (Weaviate evaluation)
```

---

## Agent Decision Hierarchy

### Decision Authority Levels:

```
┌─────────────────────────────────────┐
│  HUMAN ARCHITECTURE DECISIONS       │ ← FINAL AUTHORITY
│  (Strategic, business impact)        │
├─────────────────────────────────────┤
│  SENIOR AI AGENT CONSENSUS          │ ← 3+ agents must agree
│  (Framework choices, patterns)       │
├─────────────────────────────────────┤  
│  INDIVIDUAL AGENT DECISIONS         │ ← Within established patterns
│  (Implementation details)            │
├─────────────────────────────────────┤
│  AUTOMATED DECISIONS                │ ← Linting, formatting, etc.
│  (Non-controversial changes)        │
└─────────────────────────────────────┘
```

### Escalation Rules:
- **Confidence < 70%**: Must seek consensus from other agents
- **Framework changes**: Requires senior agent consensus
- **Security implications**: Must include human review
- **Cross-project impact**: Requires coordination agent approval

---

## Agent Coordination Workflow

### Before Making Major Decisions:

1. **Context Check**
   ```bash
   # Check existing decisions
   Search issues: label:ai-decision-log project:current-project
   Read: .project/agent-decisions/recent-decisions.md
   Review: Previous agent communications in PR comments
   ```

2. **Intent Declaration** 
   ```markdown
   Create GitHub issue with:
   - Title: "[AGENT] Propose: [Brief description]"
   - Label: agent-coordination
   - Use standard communication format
   ```

3. **Conflict Window**
   ```yaml
   Wait time: 30 minutes (urgent) / 4 hours (normal) / 24 hours (major)
   Monitor: Other agents flagging conflicts
   ```

4. **Proceed or Negotiate**
   ```yaml
   No conflicts: Proceed with implementation
   Conflicts found: Enter conflict resolution process
   ```

### Conflict Resolution Process:

1. **Identify Conflict Type**
   - Technical disagreement
   - Resource allocation
   - Framework/pattern inconsistency
   - Timeline/priority mismatch

2. **Resolution Methods**
   ```yaml
   Evidence-based: Provide benchmarks, examples, data
   Consensus-building: Involve additional agents
   Human escalation: For strategic decisions
   Compromise solution: Find middle ground
   ```

3. **Document Resolution**
   - Update original issue with resolution
   - Add to `.project/memory.md` for future reference
   - Create decision record in agent-decisions directory

---

## Agent Specialization & Roles

### Primary Agent Roles:

**Architecture Agents** (Strategic Decision Makers)
```yaml
Responsibilities:
  - Framework and technology choices
  - Cross-project pattern establishment  
  - Major architectural decisions
Requirements:
  - Must achieve consensus with other architecture agents
  - Document all decisions with rationale
Examples: Claude-Code, GPT-4-Architect, Senior-AI-Assistant
```

**Implementation Agents** (Tactical Executors)
```yaml
Responsibilities:
  - Code implementation within established patterns
  - Feature development following specifications
  - Bug fixes and maintenance tasks
Constraints:
  - Must follow established architectural patterns
  - Cannot change frameworks without escalation
Examples: GitHub-Copilot, Claude-Dev, Implementation-Assistant
```

**Review Agents** (Quality Assurance)
```yaml
Responsibilities:
  - Code quality checking
  - Security vulnerability detection
  - Compliance with organizational standards
Authority:
  - Can flag issues and block deployments
  - Cannot override architectural decisions
  - Must provide specific remediation guidance
Examples: Security-Scanner, Code-Quality-Agent, Compliance-Checker
```

**Coordination Agents** (Communication Facilitators)
```yaml
Responsibilities:
  - Manage cross-agent communication
  - Resolve conflicts between agents
  - Maintain agent decision logs
  - Monitor for duplicated work
Special Powers:
  - Can call for consensus votes
  - Can escalate to human review
Examples: Project-Manager-AI, Agent-Coordinator, Communication-Hub
```

---

## Efficient Communication Patterns

### ✅ **DO: Maximize Efficiency**

**Shared Context First**
```bash
# Before any decision, agents must:
1. Read HaldisB2B/.github repository
2. Check project-specific .project/memory.md
3. Review recent agent-coordination issues
4. Scan commit trailers for recent AI decisions
```

**Decision Inheritance**
```yaml
Pattern: "Building on [previous-agent-decision]"
Benefit: Maintains consistency and reduces conflicts
Example: "Building on GPT-4-Architect decision #456 for database layer"
```

**Specialization Respect**
```yaml
Pattern: Defer to specialized agents in their domain
Example: Implementation agent consults Architecture agent for framework choice
Result: Faster decisions, fewer conflicts
```

**Proactive Conflict Prevention**
```yaml
Pattern: "Potential conflict check: [describe scenario]"
Timing: Before implementation, during planning
Result: Prevents rework and conflicting implementations
```

### ❌ **DON'T: Anti-Patterns to Avoid**

**Silent Overriding**
```yaml
Problem: Changing previous agent's decisions without communication
Solution: Always declare intent and provide rationale
```

**Duplicate Documentation**
```yaml
Problem: Each agent creating separate docs
Solution: Contribute to centralized documentation
```

**Framework Wars**
```yaml
Problem: Different agents choosing different frameworks
Solution: Establish consensus through architecture agents
```

**Context Ignorance**  
```yaml
Problem: Making decisions without checking existing context
Solution: Mandatory context check before major decisions
```

---

## Implementation Tracking

### Agent Decision Logging

Every agent decision must be logged:

```bash
# In .project/agent-decisions/
YYYY-MM-DD-agent-decision-NNN.md

# Example: 2025-01-09-claude-code-001.md
```

### Commit Trailer Format
```bash
git commit -m "Implement vector similarity search

Add pgvector integration with cosine similarity for semantic search.
Connection pooling handled via Supabase client configuration.

AI-Agent-ID: claude-code-20250109
Builds-On: gpt-4-architect-decision-456  
Decision-Confidence: 95%
Conflicts-Resolved: none

🤖 Generated with Claude Code
Co-Authored-By: Claude <noreply@anthropic.com>"
```

### PR Communication Format
```markdown
## Agent Review Protocol

**Reviewing Agent**: [agent-id]
**Review Type**: [APPROVE / REQUEST_CHANGES / COMMENT]
**Focus Areas**: [security / performance / standards-compliance]

### Findings
[Specific issues or approvals]

### Recommendations  
[Actionable next steps]

### Escalation
[If human review needed, specify why]
```

---

## Success Metrics

### Communication Efficiency
- **Decision Speed**: Time from proposal to implementation
- **Conflict Rate**: Percentage of decisions requiring conflict resolution
- **Rework Percentage**: How often agent decisions need to be changed
- **Context Accuracy**: How well agents understand existing decisions

### Quality Outcomes
- **Consistency Score**: How well agents follow established patterns
- **Standards Compliance**: Percentage of agent decisions following HaldisB2B standards
- **Cross-Agent Learning**: How effectively agents build on each other's work

### Target Metrics
```yaml
Decision Speed: <24 hours for normal decisions
Conflict Rate: <10% of all agent decisions
Rework Percentage: <5% of implementations
Standards Compliance: >95% of agent decisions
```

---

## Emergency Protocols

### When Agents Disagree
1. **Immediate**: Flag with `conflict-resolution` label
2. **Document**: Each agent states their position with evidence
3. **Escalate**: Involve coordination agent or human review
4. **Resolve**: Implement agreed solution and document learnings

### When Agents Make Contradictory Changes
1. **Detect**: Review agents monitor for conflicts
2. **Rollback**: Revert to last consistent state if necessary
3. **Investigate**: Determine root cause of communication breakdown
4. **Prevent**: Update communication protocols to prevent recurrence

### When Agent Communication Fails
1. **Human Override**: Designated human makes final decision
2. **Protocol Review**: Assess and improve communication standards
3. **Agent Training**: Update agent instructions and examples

---

## Getting Started

### For New AI Agents
1. Read this entire document
2. Review existing agent decisions in issues
3. Introduce yourself with agent-coordination issue
4. Start with small, low-risk decisions
5. Gradually build trust and take on larger decisions

### For Existing Agents  
1. Retrofit existing decisions into standard format
2. Begin using communication protocol immediately
3. Identify your specialization area
4. Establish coordination patterns with other agents

### For Humans Managing Agents
1. Monitor agent-coordination issues regularly
2. Provide feedback on decision quality
3. Escalate conflicts that agents cannot resolve
4. Update protocols based on observed patterns

---

## Living Protocol

This communication protocol evolves based on:
- **Agent feedback**: What works, what doesn't
- **Conflict patterns**: Common sources of disagreement  
- **Efficiency metrics**: Speed and quality of decisions
- **Technology changes**: New AI capabilities and tools

**Update Schedule**:
- **Weekly**: Review recent conflicts and resolutions
- **Monthly**: Analyze efficiency metrics and adjust protocols
- **Quarterly**: Major protocol updates based on learnings

---

*Effective AI-to-AI communication is the foundation of scalable AI-assisted development. When agents coordinate well, the whole organization moves faster.*