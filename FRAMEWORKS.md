# FRAMEWORKS.md — HaldisB2B Technology Stack Standards
## Recommended Frameworks & Technologies for All Projects

> **Mission**  
> Establish consistent technology choices across all HaldisB2B projects to maximize developer productivity, maintainability, and AI-assisted development efficiency.

---

## 🚨 **ARCHITECTURAL FOUNDATION FIRST**

**📋 MANDATORY BEFORE SELECTING ANY FRAMEWORK:**
- ✅ **READ**: `SOFTWARE-ARCHITECTURE-LAYERS.md` for architectural principles
- ✅ **UNDERSTAND**: Four-layer architecture requirements
- ✅ **ENSURE**: All framework choices support proper layer separation
- ✅ **VALIDATE**: Framework selection respects architectural boundaries

**🎯 Framework Selection Rule:**
Every framework must support the four-layer architecture (Presentation, Application, Data, Infrastructure) and enable clean separation of concerns. If a framework encourages mixing layers, it's the wrong choice for HaldisB2B.

---

## Current Framework Analysis

Based on analysis of existing repositories:

### Currently Used (Approved ✅)
**Frontend Frameworks:**
- React 18 (prompt-management-system, TinkerBell)
- TypeScript 5+ (all projects)
- Vite (prompt-management-system, TinkerBell)

**State Management:**
- Zustand (prompt-management-system, TinkerBell)
- XState (TinkerBell - for complex state machines)

**Styling:**
- Tailwind CSS 3+ (prompt-management-system, TinkerBell)
- Framer Motion (TinkerBell - animations)

**Backend/API:**
- Supabase (prompt-management-system)
- Model Context Protocol (MCP_web_scraper)

**Package Management:**
- PNPM (preferred - TinkerBell, MCP_web_scraper)
- Yarn Berry (NJN)
- NPM (fallback)

---

## Recommended Framework Stack (Architecture-Aligned)

### ⭐ Core Technologies (Use These)

#### Presentation Layer Technologies
```yaml
Language: TypeScript 5+
Framework: React 18+
Build Tool: Vite
Styling: Tailwind CSS 3+
Package Manager: PNPM (preferred)
Architecture Focus: Pure UI components, no business logic
```

#### Application Layer Technologies
```yaml
Backend Framework: Node.js + Express/Fastify
API Design: REST + OpenAPI/Swagger specs
Business Logic: Service classes with clear interfaces
Authentication: JWT + OAuth 2.0
Validation: Zod for type-safe validation
Architecture Focus: Business logic, service coordination
```

#### Data Layer Technologies
```yaml
Primary Database: PostgreSQL (via Supabase)
ORM/Query Builder: Prisma or Drizzle
Caching: Redis for session/application cache
Object Storage: Supabase Storage or AWS S3
Architecture Focus: Data persistence, integrity, caching
```

#### Infrastructure Layer Technologies
```yaml
Containerization: Docker + Docker Compose
Orchestration: Kubernetes (when needed)
CI/CD: GitHub Actions
Infrastructure as Code: Terraform
Monitoring: Prometheus + Grafana
Architecture Focus: Deployment, scaling, observability
```

#### Text Editing & Rich Content (Presentation Layer)
```yaml
Rich Text Editor: Lexical (Meta)  # NEW RECOMMENDATION
Markdown Processing: unified + remark + rehype
PDF Processing: pdf-parse
File Handling: react-dropzone
Architecture Note: UI-only, business logic in Application Layer
```

#### State Management (Presentation Layer Only)
```yaml
Simple State: Zustand (UI state only)
Complex State Machines: XState (UI workflows only)
Server State: TanStack Query (React Query)
Forms: React Hook Form + Zod
Architecture Note: UI state only, business state in Application Layer
```

#### UI/UX Libraries (Presentation Layer)
```yaml
Icons: Lucide React
Animations: Framer Motion
Date Handling: date-fns
Utility Functions: clsx + tailwind-merge
Architecture Note: Presentation concerns only
```

#### Testing & Quality (All Layers)
```yaml
Test Framework: Vitest
Component Testing: Testing Library
E2E Testing: Playwright
Coverage: Vitest Coverage
Linting: ESLint + TypeScript ESLint
Formatting: Prettier
Pre-commit: Husky + lint-staged
Architecture Note: Test each layer independently
```

#### Development Tools (Infrastructure Layer)
```yaml
Monorepo: PNPM Workspaces
Type Generation: Supabase CLI
Bundle Analysis: Built into Vite
Dev Server: Vite Dev Server
Architecture Note: Development infrastructure only
```

---

## Architectural Framework Guidelines

### Presentation Layer Framework Rules
```yaml
✅ ALLOWED:
  - React components (pure UI)
  - State management for UI state only
  - Event handlers that call Application Layer APIs
  - Client-side validation for UX
  - Animation and visual effects

❌ FORBIDDEN:
  - Business logic in components
  - Direct database calls
  - External service integration
  - Complex calculations
  - Data transformation logic
```

### Application Layer Framework Rules
```yaml
✅ ALLOWED:
  - Express/Fastify for API endpoints
  - Service classes for business logic
  - Authentication and authorization
  - Data validation and transformation
  - External service integration

❌ FORBIDDEN:
  - UI-specific logic
  - Direct DOM manipulation
  - Client-side specific code
  - Database implementation details
  - Infrastructure concerns
```

### Data Layer Framework Rules
```yaml
✅ ALLOWED:
  - Prisma/Drizzle for database access
  - Redis for caching
  - Data validation at persistence layer
  - Query optimization
  - Data migration tools

❌ FORBIDDEN:
  - Business logic in procedures
  - UI concerns in data models
  - External service calls
  - Authentication logic
  - Presentation formatting
```

### Infrastructure Layer Framework Rules
```yaml
✅ ALLOWED:
  - Docker for containerization
  - GitHub Actions for CI/CD
  - Terraform for IaC
  - Monitoring and logging tools
  - Deployment automation

❌ FORBIDDEN:
  - Business logic in deployment scripts
  - UI concerns in infrastructure
  - Data manipulation in CI/CD
  - Application-specific logic
  - Direct business process automation
```

---

## Framework Specifications

### Text Editing - Lexical Framework (Presentation Layer)

**Recommended for:** Markdown-Notebook, text projects, any rich text editing needs

```typescript
// Installation
npm install lexical @lexical/react @lexical/markdown

// Basic setup for your text projects
import { $getRoot, $getSelection } from 'lexical';
import { $createHeadingNode } from '@lexical/rich-text';
import { $convertFromMarkdownString } from '@lexical/markdown';

// ARCHITECTURE: Lexical handles UI only
// Business logic (save, transform) goes to Application Layer
const TextEditor = () => {
  const handleSave = (content: string) => {
    // Call Application Layer API
    documentService.saveDocument(content);
  };
  
  return <LexicalEditor onSave={handleSave} />;
};
```

**Why Lexical:**
- Meta-built, production-ready
- Excellent TypeScript support
- Extensible plugin architecture
- Markdown support out of the box
- Great for AI-assisted text editing
- **Architectural Fit**: Pure Presentation Layer tool

### State Management - Zustand vs XState (Presentation Layer Only)

**Use Zustand when:**
- Simple UI state (modals, selected items)
- Client-side user preferences
- Presentation-layer coordination

**Use XState when:**
- Complex UI workflows (multi-step forms)
- UI state machines with transitions
- Need visual state diagrams for UI flows

**❌ Do NOT use for:**
- Business logic state
- Server data caching (use TanStack Query)
- Cross-service coordination

### Application Layer Service Pattern

```typescript
// services/documentService.ts (Application Layer)
export class DocumentService {
  async saveDocument(content: string, userId: string) {
    // Business logic: validation, processing
    const processedContent = this.processContent(content);
    
    // Call Data Layer
    return await documentRepository.save(processedContent, userId);
  }
  
  private processContent(content: string): ProcessedDocument {
    // Business logic only
    return { /* processed content */ };
  }
}

// React component (Presentation Layer)
const DocumentEditor = () => {
  const saveDocument = async (content: string) => {
    // UI calls Application Layer only
    await documentService.saveDocument(content, user.id);
  };
  
  return <LexicalEditor onSave={saveDocument} />;
};
```

### Styling - Tailwind CSS Philosophy (Presentation Layer)

```typescript
// Design system approach
const tokens = {
  colors: {
    primary: 'blue-600',
    secondary: 'gray-600',
    accent: 'emerald-500'
  },
  spacing: {
    section: 'py-12 px-6',
    card: 'p-6'
  }
}

// ARCHITECTURE: Styling is pure Presentation Layer
// No business logic in CSS classes
const Card = ({ data }: { data: BusinessData }) => {
  // Business logic handled by Application Layer
  const processedData = useApplicationService(data);
  
  // UI rendering only
  return (
    <div className="p-6 bg-white rounded-lg shadow">
      {processedData.display}
    </div>
  );
};
```

---

## ❌ Frameworks to Avoid (Architectural Violations)

### Presentation Layer Violations
- **Create React App** - Use Vite instead
- **Styled-components** - Mixes styling with logic, AI-unfriendly
- **Angular** - Too opinionated, encourages layer mixing
- **Next.js API routes** - Mixes presentation with application logic

### Application Layer Violations
- **Direct ORM in React components** - Violates layer separation
- **Business logic in React hooks** - Wrong architectural layer
- **Database calls in UI components** - Bypasses Application Layer

### Anti-Architectural Patterns
- **Monolithic frameworks** that encourage layer mixing
- **ORMs that generate UI** - Violates separation
- **Frameworks without clear boundaries** - Makes architecture unclear

---

## Framework Decision Matrix (Architecture-Aware)

| Category | Framework | Architectural Layer | Pros | Cons | Use When |
|----------|-----------|-------------------|------|------|----------|
| Text Editing | **Lexical** | Presentation | Meta-built, extensible | Learning curve | Rich text UI |
| State Management | **Zustand** | Presentation | Simple, UI-focused | UI state only | UI state management |
| State Management | **XState** | Presentation | Visual, deterministic | Learning curve | Complex UI workflows |
| API Layer | **Express** | Application | Simple, flexible | Manual setup | Business logic APIs |
| Database | **Prisma** | Data | Type-safe, migrations | Learning curve | Data persistence |
| Styling | **Tailwind** | Presentation | Utility-first, AI-friendly | Large bundle | All UI styling |
| Animation | **Framer Motion** | Presentation | Declarative, React-native | Bundle size | UI animations |

---

## Project-Specific Recommendations (Architecture-Compliant)

### Markdown-Notebook Project
```yaml
Presentation Layer:
  - React + TypeScript + Vite
  - Lexical with markdown plugin
  - Zustand for UI state
  - Tailwind CSS + custom editor styles

Application Layer:
  - Express.js for document APIs
  - Document processing services
  - User authentication services

Data Layer:
  - PostgreSQL for document storage
  - IndexedDB for local cache
  - Optional Supabase for sync

Infrastructure Layer:
  - Docker for containerization
  - GitHub Actions for CI/CD
```

### NJN (Note-taking App)  
```yaml
Presentation Layer:
  - React + TypeScript + Vite  
  - Lexical with rich text plugins
  - XState for note UI workflows
  - Tailwind CSS + whimsical animations

Application Layer:
  - Note management services
  - Search and organization logic
  - Real-time sync coordination

Data Layer:
  - Supabase with real-time capabilities
  - Full-text search indexing

Infrastructure Layer:
  - Vercel for deployment
  - Supabase for backend infrastructure
```

### MCP Servers
```yaml
Application Layer:
  - TypeScript + Node.js
  - Express.js or Fastify
  - Model Context Protocol SDK
  
Data Layer:
  - Appropriate data store per MCP service
  
Infrastructure Layer:
  - Docker containers
  - Testing with Vitest + Playwright
  - Build with tsup or esbuild
```

### Virtual Pet (TinkerBell)
```yaml
Presentation Layer:
  - React + TypeScript + Vite
  - PixiJS for graphics rendering
  - XState for pet UI behavior
  - Framer Motion for UI animations

Application Layer:
  - Pet behavior engine services
  - Game state management
  - Achievement/progress tracking

Data Layer:
  - Local storage for pet state
  - IndexedDB for game data

Infrastructure Layer:
  - Static site deployment
  - Asset optimization pipeline
```

---

## Architecture-Compliant Migration Strategy

### Phase 1: Layer Separation Audit
- Identify current layer violations
- Document architectural debt
- Plan layer separation approach

### Phase 2: Framework Alignment  
- Migrate frameworks to correct layers
- Implement proper layer boundaries
- Establish API contracts between layers

### Phase 3: Standardization
- Unified build tools per layer
- Shared component libraries (Presentation)
- Common service patterns (Application)
- Standard data access patterns (Data)

### Phase 4: Validation
- Architectural compliance testing
- Layer dependency validation
- Performance verification

---

## Framework Evaluation Criteria (Architecture-First)

When considering new frameworks, evaluate:

### ✅ Architectural Compatibility
- **Clear layer assignment** - Framework belongs to specific layer
- **Boundary respect** - Doesn't encourage layer mixing
- **Interface clarity** - Clear APIs between layers
- **Separation support** - Enables clean architecture

### ✅ AI-Friendly Criteria
- Clear, predictable API surface
- Excellent TypeScript support
- Good documentation with examples
- Declarative vs imperative patterns
- JSON-serializable configuration

### ✅ Development Velocity  
- Fast hot reload/dev server
- Good debugging tools
- IDE/editor support
- Rich ecosystem
- Active community

### ❌ Architectural Red Flags
- **Layer mixing encouraged** - Framework promotes mixing concerns
- **Unclear boundaries** - Framework spans multiple layers
- **Tight coupling** - Framework creates dependencies across layers
- **Architectural lock-in** - Hard to replace without major refactoring

---

## Implementation Guidelines (Architecture-First)

### New Project Setup
```bash
# 1. FIRST: Define architectural layers
mkdir -p src/{presentation,application,data,infrastructure}

# 2. Standard project initialization
npm create vite@latest project-name -- --template react-ts
cd project-name

# 3. Install layer-appropriate dependencies
# Presentation Layer
npm install tailwindcss @tailwindcss/typography
npm install zustand lucide-react clsx tailwind-merge
npm install lexical @lexical/react @lexical/markdown

# Application Layer  
npm install express zod cors helmet
npm install @types/express @types/cors

# Data Layer
npm install prisma @prisma/client
npm install redis

# Infrastructure Layer
npm install -D vitest @testing-library/react
npm install -D eslint prettier husky lint-staged
```

### Architecture-Compliant Project Structure
```typescript
src/
  presentation/           # Presentation Layer
    components/          # UI components only
    hooks/              # UI state hooks only
    stores/             # UI state management
    styles/             # Styling and design
    
  application/            # Application Layer
    services/           # Business logic services
    api/               # API route handlers
    auth/              # Authentication logic
    validation/        # Business rule validation
    
  data/                   # Data Layer
    repositories/      # Data access patterns
    models/           # Data models and schemas
    migrations/       # Database migrations
    cache/           # Caching implementations
    
  infrastructure/         # Infrastructure Layer
    config/           # Environment configuration
    monitoring/       # Logging and metrics
    deployment/       # Docker, CI/CD configs
    testing/         # Test utilities
    
  shared/                # Shared utilities (use sparingly)
    types/            # Shared TypeScript types
    constants/        # Shared constants
    utils/           # Pure utility functions
```

---

## Monitoring and Updates (Architecture-Aware)

### Framework Health Metrics
- **Architectural compliance** - Layer boundary violations
- Bundle size impact per layer
- Development build times per layer
- Developer satisfaction scores
- Bug report frequency by layer

### Update Schedule
- **Monthly**: Security updates across all layers
- **Quarterly**: Minor version updates with architecture review
- **Annually**: Major version evaluations with architecture impact assessment
- **Ad-hoc**: Critical security patches

---

## Architecture Compliance Validation

### Framework Selection Checklist
- [ ] Framework clearly belongs to single architectural layer
- [ ] Framework doesn't encourage cross-layer dependencies
- [ ] Framework supports clean API boundaries
- [ ] Framework enables independent layer testing
- [ ] Framework allows layer replacement without cascading changes

### Code Review Framework Questions
- [ ] Does this framework usage respect layer boundaries?
- [ ] Are there any inappropriate cross-layer dependencies?
- [ ] Can this layer be tested independently?
- [ ] Would changing this framework affect other layers?
- [ ] Are API contracts properly defined?

---

## Getting Help

### Architecture-Specific Resources
- **Layer Boundaries**: Consult `SOFTWARE-ARCHITECTURE-LAYERS.md`
- **Framework Questions**: Create issue in HaldisB2B/.github
- **Architecture Reviews**: Schedule with architecture team

### Framework-Specific Resources
- **Lexical**: [Official Playground](https://playground.lexical.dev/)
- **Tailwind**: [Tailwind UI Components](https://tailwindui.com/)
- **Zustand**: [GitHub Examples](https://github.com/pmndrs/zustand)
- **XState**: [State Machine Visualizer](https://stately.ai/)

---

## Decision Log

**v1.1 (January 2025)**: Added mandatory architectural compliance requirements
- All framework choices must respect four-layer architecture
- Framework selection criteria updated for architectural compatibility
- Project structure aligned with architectural layers

**v1.0 (September 2025)**: Initial framework standards based on existing project analysis
- Established Lexical as standard for text editing
- Confirmed React + TypeScript + Vite as core stack  
- Standardized on Zustand for simple state management

**Next Review**: March 2025

---

*Framework choices at HaldisB2B must respect architectural boundaries. Every framework must support clean separation of concerns and enable independent layer evolution.*