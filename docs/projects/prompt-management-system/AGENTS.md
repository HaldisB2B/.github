# AGENTS.md — Prompt Management System
## AI-Powered Prompt Organization with Semantic Clustering

> **Mission**  
> Build an intelligent prompt repository that uses AI for semantic clustering, connection discovery, and natural language search while maintaining complete transparency of AI decisions.

---

## The Sacred Rules (Override All Others)

1. **When in doubt, don't deploy**
2. **When AI seems confident, verify twice**  
3. **When metrics decline, stop and reassess**
4. **Be brutally honest - no sugar-coating, no false positives**

---

## Project-Specific Context

### Technology Vision
Build a sophisticated prompt management system that combines the power of modern web technologies with AI intelligence, creating a seamless experience for organizing, discovering, and reusing prompts.

**Core Innovation**: Use AI not just for execution, but for organization—semantic clustering that finds connections humans miss while keeping every AI decision transparent and reviewable.

### Strategic Constraints

**Development Philosophy**: 
- AI assists but never decides alone
- Every AI recommendation includes confidence scores and reasoning
- Human oversight at every critical decision point
- Radical transparency in AI decision-making process

**Quality Gates**:
- All AI clustering decisions must be explainable
- User can override any AI suggestion
- System works perfectly without AI (graceful degradation)
- No black box decision making

### Success Definition
Create a system where finding the right prompt is faster than writing a new one, where AI helps discover unexpected connections between prompts, and where the organization system evolves intelligently with use.

---

## Technical Architecture

### Frontend Foundation
```yaml
Framework: React 18+ with TypeScript
Build Tool: Vite (fast, modern, excellent dev experience)
Styling: Tailwind CSS (utility-first, AI-friendly)
State Management: Zustand (simple, TypeScript-first)
```

### AI Integration Strategy
```yaml
Semantic Analysis: OpenAI Embeddings + Custom clustering
Similarity Search: Vector similarity with configurable thresholds
Connection Discovery: Graph analysis of prompt relationships
Search Enhancement: Natural language to structured queries
```

### Data Architecture
```yaml
Primary Database: Supabase (PostgreSQL + real-time)
Vector Storage: Supabase Vector/pgvector
File Storage: Supabase Storage
Authentication: Supabase Auth
```

### Intelligence Layer
```yaml
Clustering Engine: Custom algorithm with explainable results
Semantic Search: Embedding-based with fallback to text search
Connection Detection: Graph algorithms + similarity scoring
Recommendation Engine: Usage patterns + semantic similarity
```

---

## Development Workflow

### AI-Assisted Development Rules

**Code Generation**:
- Use AI for boilerplate and patterns
- Always review AI-generated code for security
- Test all AI suggestions against requirements
- Document any AI-generated patterns for team learning

**Architecture Decisions**:
- AI provides options and analysis
- Humans make all architectural choices
- Document reasoning for major technology choices
- Keep AI suggestions for future reference

**Quality Assurance**:
- AI-generated code follows same review process
- Extra scrutiny for complex AI-suggested solutions
- Performance testing for all AI-enhanced features
- Security review for any AI-integration points

### Git Workflow
```bash
# Standard branching
feature/semantic-clustering
feature/prompt-search
feature/ai-explanations

# Commit format
type(scope): description

feat(clustering): add semantic prompt clustering with explanations
fix(search): improve vector similarity threshold handling
docs(ai): document AI decision transparency requirements
```

### Testing Strategy
```yaml
Unit Tests: Vitest + Testing Library
Integration Tests: Custom test helpers for AI components
E2E Tests: Playwright for full user workflows
AI Testing: Specific tests for AI decision transparency
Performance Tests: Vector search performance benchmarks
```

---

## Specific Implementation Requirements

### Semantic Clustering System

**Requirements**:
- Group related prompts automatically
- Explain clustering decisions in human terms
- Allow user override of any clustering decision
- Provide confidence scores for all groupings

**Implementation Approach**:
```typescript
interface ClusterDecision {
  promptIds: string[]
  reasoning: string
  confidence: number
  userOverridable: true
  alternativeGroupings?: ClusterDecision[]
}

interface ClusterExplanation {
  decisionReasoning: string
  keyFactors: string[]
  confidenceBreakdown: {
    semanticSimilarity: number
    usagePatterns: number
    userFeedback: number
  }
}
```

**Transparency Requirements**:
- Every clustering decision must include human-readable reasoning
- Users can see what factors influenced each decision
- Alternative groupings suggested when confidence is low
- Clear indication when AI is "uncertain" vs "confident"

### Intelligent Search System

**Requirements**:
- Natural language query understanding
- Vector similarity search with explainable results
- Fallback to traditional text search
- Search suggestions based on user patterns

**Example Implementation**:
```typescript
interface SearchResult {
  prompt: Prompt
  matchType: 'semantic' | 'text' | 'tag' | 'usage'
  relevanceScore: number
  matchExplanation: string
  suggestedRelated: Prompt[]
}

interface SearchExplanation {
  queryInterpretation: string
  searchStrategy: 'vector' | 'hybrid' | 'fallback'
  resultsReasoning: string
  alternativeQueries?: string[]
}
```

### Connection Discovery Engine

**Purpose**: Find unexpected relationships between prompts that users might miss

**Requirements**:
- Surface interesting connections between seemingly unrelated prompts
- Explain why connections were suggested
- Allow users to confirm or dismiss connections
- Learn from user feedback to improve suggestions

**Implementation Pattern**:
```typescript
interface PromptConnection {
  sourcePrompt: string
  targetPrompt: string
  connectionType: 'semantic' | 'usage' | 'temporal' | 'user-pattern'
  strength: number
  explanation: string
  userFeedback?: 'confirmed' | 'dismissed' | 'modified'
}
```

---

## User Experience Design

### Core Principles

**Discoverability Over Organization**:
- Finding prompts should be effortless
- AI helps surface relevant prompts proactively  
- Multiple discovery methods (search, browse, recommendations)
- Serendipitous discovery of useful connections

**Transparency Over Black Box**:
- Always show why AI made suggestions
- Provide confidence indicators
- Allow users to understand and override AI decisions
- Clear feedback loop for improving AI suggestions

**Speed Over Perfection**:
- Fast prompt creation and editing
- Instant search results
- Efficient bulk operations
- Keyboard shortcuts for power users

### Interface Components

**Smart Search Bar**:
- Auto-completes with semantic understanding
- Shows search strategy being used
- Provides alternative search approaches
- Explains why results were selected

**Clustering Visualization**:
- Visual representation of prompt relationships
- Interactive cluster exploration
- Cluster reasoning displayed on hover
- Drag-and-drop for manual cluster adjustment

**Connection Suggestions Panel**:
- Proactive suggestions for related prompts
- Explanation for each suggestion
- One-click to explore connections
- Feedback mechanism to improve suggestions

---

## AI Transparency Framework

### Decision Explanation Requirements

Every AI decision must include:

1. **What** was decided
2. **Why** it was decided (reasoning)
3. **How confident** the AI is (0-100 score)
4. **What alternatives** were considered
5. **How users can** provide feedback or override

### Example Transparency Interface
```typescript
interface AIDecisionExplanation {
  decision: string
  reasoning: string
  confidence: number
  alternatives: string[]
  feedbackPrompt: string
  overrideInstructions: string
}

// Usage example
const clusteringExplanation: AIDecisionExplanation = {
  decision: "Grouped 5 prompts about 'code review' together",
  reasoning: "All prompts contain similar semantic concepts around code quality, feedback, and improvement suggestions",
  confidence: 87,
  alternatives: [
    "Split into 'automated code review' and 'human code review' subgroups",
    "Merge with broader 'development process' cluster"
  ],
  feedbackPrompt: "Does this grouping make sense for your workflow?",
  overrideInstructions: "Drag prompts to different groups or create new clusters"
}
```

---

## Performance & Quality Standards

### AI Performance Metrics

**Clustering Quality**:
- User acceptance rate of AI clustering suggestions
- Time saved vs manual organization
- False positive rate (inappropriate groupings)
- User override frequency and patterns

**Search Effectiveness**:
- Query success rate (user finds what they need)
- Search-to-use conversion rate
- Average time to find relevant prompts
- User satisfaction with search explanations

**Connection Discovery Value**:
- User engagement with suggested connections
- Confirmed connection rate
- User-initiated connection creation rate
- Overall prompt reuse improvement

### Technical Performance Targets

**Response Times**:
- Search results: < 500ms
- Clustering updates: < 2 seconds
- Connection suggestions: < 1 second
- UI responsiveness: < 100ms for all interactions

**Accuracy Requirements**:
- Semantic search relevance: > 85%
- Clustering user acceptance: > 70%
- Connection suggestion value: > 60%
- Zero false security positives in AI decisions

---

## Development Phases

### Phase 1: Foundation (Completed)
- [x] Basic React + TypeScript + Vite setup
- [x] Supabase integration and authentication
- [x] Basic prompt CRUD operations
- [x] Simple search functionality
- [x] Core UI components with Tailwind

### Phase 2: AI Integration (Current)
- [ ] OpenAI embeddings integration
- [ ] Vector similarity search implementation
- [ ] Basic semantic clustering
- [ ] AI decision transparency framework
- [ ] User feedback collection system

### Phase 3: Intelligence (Planned)
- [ ] Advanced clustering algorithms
- [ ] Connection discovery engine
- [ ] Natural language query processing
- [ ] Usage pattern analysis
- [ ] Recommendation system

### Phase 4: Optimization (Future)
- [ ] Performance optimization for large prompt sets
- [ ] Advanced visualization features
- [ ] Collaboration features
- [ ] API for external integrations
- [ ] Mobile-responsive optimizations

---

## Security & Privacy

### AI Data Handling

**Prompt Content Security**:
- All prompts encrypted at rest
- Vector embeddings stored separately from content
- No prompt content sent to AI services for clustering decisions
- Local embedding generation when possible

**Privacy Preserving AI**:
- User behavior analysis anonymized
- No personal information in AI training data
- Clear opt-out mechanisms for AI features
- Transparent data usage policies

### Authentication & Access Control

**User Management**:
- Supabase Auth with secure token handling
- Role-based access control for shared prompts
- Audit logging for sensitive operations
- Secure sharing and collaboration features

---

## Success Metrics & KPIs

### User Experience Metrics
- **Time to Find**: Average time to locate a specific prompt
- **Discovery Rate**: Percentage of users who discover useful new prompts
- **Reuse Rate**: Frequency of prompt reuse vs creating new ones
- **User Satisfaction**: Self-reported satisfaction with AI assistance

### Technical Metrics
- **System Performance**: Response times, uptime, scalability
- **AI Accuracy**: Clustering success, search relevance, connection value
- **User Adoption**: Feature usage rates, feedback submission rates
- **Quality Assurance**: Bug rates, security incident rates

### Business Value Metrics
- **Productivity Gain**: Measured improvement in prompt-related workflows
- **Content Quality**: Quality of prompts created using the system
- **Collaboration Enhancement**: Team sharing and reuse patterns
- **Innovation Support**: New prompt creation and experimentation rates

---

## Learning & Iteration

### Continuous Improvement Process

**User Feedback Integration**:
- Regular surveys on AI decision quality
- A/B testing of AI algorithms
- User behavior analysis for feature priorities
- Community feedback incorporation

**AI System Evolution**:
- Model performance monitoring and updates
- Algorithm refinement based on user patterns
- New AI capability integration as available
- Bias detection and mitigation strategies

**Development Process Refinement**:
- Code review process effectiveness
- AI-assisted development workflow optimization
- Quality assurance process improvement
- Documentation and knowledge sharing enhancement

---

*This document serves as the single source of truth for the Prompt Management System. All development decisions should align with these principles and requirements.*

**Last Updated**: 2024-09-11  
**Version**: 2.0  
**Next Review**: 2024-12-11

---

## Migration Note

**Original Documentation Created**: AI-assisted development with human oversight  
**Migration Date**: 2024-09-11  
**Migration Process**: HaldisB2B AI Developer Documentation Migration v1.0  
**Original Repository**: HaldisB2B/prompt-management-system  
**Total Lines**: 409 lines (original AGENTS.md)  

This document represents comprehensive AI development practices and architectural decisions created through AI-assisted development with thorough human review and validation.