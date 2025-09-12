# [PROJECT NAME] - AI Development Project Specification Template

## Mission Statement
[Brief mission statement describing the AI-enhanced project goals]

## The Sacred Rules (Override All Others)
1. **When in doubt, don't deploy**
2. **When AI seems confident, verify twice**  
3. **When metrics decline, stop and reassess**
4. **Be brutally honest - no sugar-coating, no false positives**

## Project-Specific Context

### Technology Vision
[Description of how AI enhances the core functionality]

### Strategic Constraints
**Development Philosophy**: 
- AI assists but never decides alone
- Every AI recommendation includes confidence scores and reasoning
- Human oversight at every critical decision point
- Radical transparency in AI decision-making process

**Quality Gates**:
- All AI decisions must be explainable
- User can override any AI suggestion
- System works perfectly without AI (graceful degradation)
- No black box decision making

### Success Definition
[Clear definition of what success looks like for this AI-enhanced project]

## Technical Architecture

### Frontend Foundation
```yaml\nFramework: React 18+ with TypeScript\nBuild Tool: Vite\nStyling: Tailwind CSS\nState Management: Zustand\n```

### AI Integration Strategy
```yaml\n[AI Service]: [Purpose and implementation approach]\n[Vector Operations]: [Similarity search, embeddings, etc.]\n[Decision Framework]: [How AI decisions are made and explained]\n```

### Data Architecture
```yaml\nPrimary Database: Supabase (PostgreSQL)\nVector Storage: [Vector database solution]\nAuthentication: Supabase Auth\nStorage: [File/media storage solution]\n```

## AI Transparency Framework

### Decision Explanation Requirements
Every AI decision must include:
1. **What** was decided
2. **Why** it was decided (reasoning)
3. **How confident** the AI is (0-100 score)
4. **What alternatives** were considered
5. **How users can** provide feedback or override

### Example Implementation
```typescript\ninterface AIDecisionExplanation {\n  decision: string\n  reasoning: string\n  confidence: number\n  alternatives: string[]\n  feedbackPrompt: string\n  overrideInstructions: string\n}\n```

## Development Phases

### Phase 1: Foundation\n- [ ] Basic React + TypeScript + Vite setup\n- [ ] Database integration and authentication\n- [ ] Core CRUD operations\n- [ ] Basic UI components\n\n### Phase 2: AI Integration\n- [ ] AI service integration\n- [ ] Decision transparency framework\n- [ ] User feedback collection\n- [ ] AI decision logging\n\n### Phase 3: Intelligence\n- [ ] Advanced AI features\n- [ ] Performance optimization\n- [ ] User experience refinement\n- [ ] Analytics and monitoring\n\n## Success Metrics & KPIs\n\n### User Experience Metrics\n- **[Core Metric]**: [Target measurement]\n- **AI Acceptance**: [User acceptance rate for AI decisions]\n- **User Satisfaction**: [Self-reported satisfaction scores]\n\n### Technical Metrics\n- **Performance**: [Response times, uptime targets]\n- **AI Accuracy**: [Accuracy measurements for AI features]\n- **Quality Assurance**: [Bug rates, security metrics]\n\n### Business Value Metrics\n- **Productivity**: [Measurable productivity improvements]\n- **Adoption**: [User adoption and engagement rates]\n- **Innovation**: [New capabilities enabled by AI]\n\n---\n\n**Template Usage**: This template extracted from successful AI development project. Adapt sections as needed for your specific project requirements while maintaining the core AI transparency and quality principles.\n\n**Source**: Based on HaldisB2B prompt-management-system project documentation (709 lines of proven AI development practices)."