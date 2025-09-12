# QODER_CONFIG.md - Development Configuration Standards

## Project Configuration Standards

### TypeScript Configuration
```json
{
  "compilerOptions": {
    "strict": true,
    "noUncheckedIndexedAccess": true,
    "exactOptionalPropertyTypes": true
  }
}
```

### Code Quality Standards
- **ESLint**: Strict TypeScript rules, no 'any' types allowed
- **Prettier**: Consistent code formatting across team
- **Husky**: Pre-commit hooks for quality gates
- **Vitest**: Unit and integration testing requirements

### Development Workflow
1. **Feature Branch**: Always branch from main
2. **Commit Messages**: Conventional commits format
3. **Code Review**: Required for all changes
4. **Testing**: 80%+ coverage for new features

### AI Development Guidelines
- **Transparency**: All AI decisions must be explainable
- **Confidence Scoring**: Every AI suggestion includes confidence level
- **Human Override**: Users can always override AI decisions
- **Audit Trail**: All AI interactions logged for review

### Performance Standards
- **Bundle Size**: < 500KB initial load
- **Core Web Vitals**: LCP < 2.5s, CLS < 0.1
- **Search Response**: < 500ms for vector similarity
- **AI Processing**: < 2s for clustering operations

### Security Requirements
- **Input Validation**: Zod schemas for all user inputs
- **Data Sanitization**: XSS protection on all content
- **Rate Limiting**: API endpoints protected
- **Audit Logging**: Security events tracked

### Testing Standards
- **Unit Tests**: All services and utilities
- **Integration Tests**: API and database interactions
- **E2E Tests**: Critical user workflows
- **AI Testing**: Specific tests for AI decision quality

---

**Migration Note**: Original 45-line configuration standards created through AI-assisted development with human oversight. Migrated 2024-09-11 following HaldisB2B AI Developer Documentation Migration process.