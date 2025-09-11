# FRAMEWORKS.md — HaldisB2B Technology Stack Standards
## Recommended Frameworks & Technologies for All Projects

> **Mission**  
> Establish consistent technology choices across all HaldisB2B projects to maximize developer productivity, maintainability, and AI-assisted development efficiency.

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

## Recommended Framework Stack

### ⭐ Core Technologies (Use These)

#### Frontend Development
```yaml
Language: TypeScript 5+
Framework: React 18+
Build Tool: Vite
Styling: Tailwind CSS 3+
Package Manager: PNPM (preferred)
```

#### Text Editing & Rich Content
```yaml
Rich Text Editor: Lexical (Meta)  # NEW RECOMMENDATION
Markdown Processing: unified + remark + rehype
PDF Processing: pdf-parse
File Handling: react-dropzone
```

#### State Management
```yaml
Simple State: Zustand
Complex State Machines: XState
Server State: TanStack Query (React Query)
Forms: React Hook Form + Zod
```

#### UI/UX Libraries
```yaml
Icons: Lucide React
Animations: Framer Motion
Date Handling: date-fns
Utility Functions: clsx + tailwind-merge
```

#### Backend & Database
```yaml
Backend-as-a-Service: Supabase (preferred)
Database: PostgreSQL (via Supabase)
Real-time: Supabase Realtime
Authentication: Supabase Auth
Storage: Supabase Storage
```

#### Testing & Quality
```yaml
Test Framework: Vitest
Component Testing: Testing Library
E2E Testing: Playwright
Coverage: Vitest Coverage
Linting: ESLint + TypeScript ESLint
Formatting: Prettier
Pre-commit: Husky + lint-staged
```

#### Development Tools
```yaml
Monorepo: PNPM Workspaces
Type Generation: Supabase CLI
Bundle Analysis: Built into Vite
Dev Server: Vite Dev Server
```

---

## Framework Specifications

### Text Editing - Lexical Framework

**Recommended for:** Markdown-Notebook, text projects, any rich text editing needs

```typescript
// Installation
npm install lexical @lexical/react @lexical/markdown

// Basic setup for your text projects
import { $getRoot, $getSelection } from 'lexical';
import { $createHeadingNode } from '@lexical/rich-text';
import { $convertFromMarkdownString } from '@lexical/markdown';
```

**Why Lexical:**
- Meta-built, production-ready
- Excellent TypeScript support
- Extensible plugin architecture
- Markdown support out of the box
- Great for AI-assisted text editing

### State Management - Zustand vs XState

**Use Zustand when:**
- Simple global state
- Straightforward data flow
- Quick prototypes

**Use XState when:**
- Complex workflows (like TinkerBell pet behavior)
- State machines with multiple transitions
- Need visual state diagrams

### Styling - Tailwind CSS Philosophy

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
```

---

## ❌ Frameworks to Avoid

### Outdated/Problematic
- **Create React App** - Use Vite instead
- **Moment.js** - Use date-fns instead  
- **Lodash (full library)** - Use specific functions or native JS
- **Bootstrap** - Use Tailwind CSS instead
- **jQuery** - Modern React patterns instead
- **Webpack (directly)** - Use Vite instead

### Too Complex for Our Use Cases
- **Next.js** - Unless specifically need SSR
- **Gatsby** - Unless specifically need static site generation
- **Redux/Redux Toolkit** - Use Zustand instead for most cases
- **MobX** - Adds unnecessary complexity

### AI-Unfriendly
- **Styled-components** - AI struggles with CSS-in-JS
- **Emotion** - Similar issues to styled-components
- **Angular** - Too verbose for AI-assisted development

---

## Framework Decision Matrix

| Category | Framework | Pros | Cons | Use When |
|----------|-----------|------|------|----------|
| Text Editing | **Lexical** | Meta-built, extensible, TS support | Learning curve | Rich text, markdown editing |
| Text Editing | Draft.js | Mature, Facebook-built | Heavier, older architecture | Complex text editing needs |
| Text Editing | TinyMCE | Feature-rich, mature | Heavy, licensing complexity | Enterprise requirements |
| State Management | **Zustand** | Simple, lightweight, TS-first | Less tooling than Redux | Most projects |
| State Management | **XState** | Visual, deterministic | Learning curve | Complex workflows |
| State Management | Redux Toolkit | Mature ecosystem | Verbose, complex | Large apps with multiple devs |
| Styling | **Tailwind** | Utility-first, AI-friendly | Large CSS bundle | All projects |
| Styling | CSS Modules | Scoped styles | More configuration | Component-specific styles |
| Animation | **Framer Motion** | Declarative, React-optimized | Bundle size | UI animations |
| Animation | React Spring | Physics-based | More complex API | Physics simulations |

---

## Project-Specific Recommendations

### Markdown-Notebook Project
```yaml
Core: React + TypeScript + Vite
Text Editor: Lexical with markdown plugin
State: Zustand for global state
Persistence: IndexedDB + optional Supabase sync
Styling: Tailwind CSS + custom editor styles
```

### NJN (Note-taking App)  
```yaml
Core: React + TypeScript + Vite  
Text Editor: Lexical with rich text plugins
State: Zustand + XState for note workflows
Backend: Supabase with real-time sync
Styling: Tailwind CSS + whimsical animations
```

### MCP Servers
```yaml
Core: TypeScript + Node.js
Framework: Express.js or Fastify
Protocol: Model Context Protocol SDK
Testing: Vitest + Playwright
Build: tsup or esbuild
```

### Virtual Pet (TinkerBell)
```yaml
Core: React + TypeScript + Vite
Graphics: PixiJS (primary) + SVG fallback  
State: XState (pet behavior) + Zustand (global)
Animation: Framer Motion + PixiJS tweens
Audio: Web Audio API
```

---

## Migration Strategy

### Phase 1: Standardize Build Tools
- Migrate all projects to Vite
- Standardize on PNPM workspaces
- Unified TypeScript configurations

### Phase 2: UI Framework Alignment  
- Implement Tailwind CSS across all projects
- Create shared component library
- Standardize on Lucide React for icons

### Phase 3: Advanced Features
- Integrate Lexical into text-heavy projects
- Implement unified state management patterns
- Add comprehensive testing setup

### Phase 4: Developer Experience
- Unified development commands
- Shared ESLint/Prettier configurations  
- Consistent project structures

---

## Framework Evaluation Criteria

When considering new frameworks, evaluate:

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

### ✅ Production Readiness
- Performance characteristics
- Bundle size implications
- Browser compatibility
- Stability and maintenance
- Security track record

### ❌ Red Flags
- Poor TypeScript support
- Imperative APIs that confuse AI
- Heavy runtime dependencies
- Frequent breaking changes
- Complex configuration requirements

---

## Implementation Guidelines

### New Project Setup
```bash
# Standard project initialization
npm create vite@latest project-name -- --template react-ts
cd project-name
npm install

# Add standard dependencies
npm install tailwindcss @tailwindcss/typography
npm install zustand @tanstack/react-query
npm install lucide-react clsx tailwind-merge
npm install zod react-hook-form @hookform/resolvers

# Text editing projects
npm install lexical @lexical/react @lexical/markdown

# Development dependencies
npm install -D vitest @testing-library/react @testing-library/jest-dom
npm install -D eslint prettier husky lint-staged
```

### Framework Integration Patterns
```typescript
// Standard app structure
src/
  components/     # Reusable UI components
  hooks/         # Custom React hooks
  lib/           # Utilities and configurations
  stores/        # Zustand stores
  types/         # TypeScript type definitions
  pages/         # Page components
  styles/        # Global styles and Tailwind
```

---

## Monitoring and Updates

### Framework Health Metrics
- Bundle size impact
- Development build times
- Developer satisfaction scores
- Bug report frequency
- Community activity

### Update Schedule
- **Monthly**: Security updates
- **Quarterly**: Minor version updates  
- **Annually**: Major version evaluations
- **Ad-hoc**: Critical security patches

---

## Version Compatibility Matrix

| Framework | Minimum Version | Recommended | Notes |
|-----------|----------------|-------------|-------|
| Node.js | 18.0.0 | 20.x LTS | Required for all projects |
| TypeScript | 5.0.0 | 5.2+ | Strict mode enabled |
| React | 18.0.0 | 18.2+ | Concurrent features |
| Vite | 5.0.0 | 5.x latest | Fast dev server |
| Tailwind | 3.3.0 | 3.4+ | Latest features |
| Lexical | 0.12.0 | Latest stable | Text editing |

---

## Getting Help

### Framework-Specific Resources
- **Lexical**: [Official Playground](https://playground.lexical.dev/)
- **Tailwind**: [Tailwind UI Components](https://tailwindui.com/)
- **Zustand**: [GitHub Examples](https://github.com/pmndrs/zustand)
- **XState**: [State Machine Visualizer](https://stately.ai/)

### Internal Guidelines
- Check existing projects for implementation patterns
- Consult AGENTS.md for project-specific requirements
- Create proof-of-concept before committing to new frameworks

---

## Decision Log

**v1.0 (September 2025)**: Initial framework standards based on existing project analysis
- Established Lexical as standard for text editing
- Confirmed React + TypeScript + Vite as core stack  
- Standardized on Zustand for simple state management

**Next Review**: December 2025

---

*This document guides framework choices to maximize AI-assisted development productivity while maintaining code quality and developer happiness.*