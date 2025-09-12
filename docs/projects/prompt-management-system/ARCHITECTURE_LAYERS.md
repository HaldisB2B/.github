# ARCHITECTURE_LAYERS.md - System Architecture Overview

## Core Architecture Layers

### 1. Presentation Layer (React + TypeScript)
- **Components**: Reusable UI components with Tailwind CSS
- **Hooks**: Custom hooks for data fetching and state management
- **Pages**: Route-based page components
- **Store**: Zustand for global state management

### 2. Service Layer (Business Logic)
- **PromptService**: CRUD operations and business rules
- **EmbeddingService**: AI embedding generation and vector operations
- **ClusteringService**: Semantic clustering with transparency
- **SearchService**: Multi-modal search (vector + text + tags)
- **AIDecisionService**: Logging and explaining AI decisions

### 3. Data Access Layer (Supabase Integration)
- **Database**: PostgreSQL with Row Level Security
- **Vector Storage**: pgvector for embedding similarity search
- **Authentication**: Supabase Auth with GitHub OAuth
- **Storage**: File uploads and media management
- **Real-time**: Live updates for collaborative features

### 4. External Integration Layer
- **OpenAI API**: Embedding generation and AI processing
- **File Processing**: PDF, JSON, text file handling
- **GitHub Integration**: Repository and user data sync

## Data Flow Architecture
```
User Input → React Components → Service Layer → Supabase → AI Services
     ↓                                              ↓
UI Updates ← State Management ← Business Logic ← Data Response
```

## Security Architecture
- **Authentication**: OAuth 2.0 with JWT tokens
- **Authorization**: Row Level Security policies
- **Data Protection**: Encrypted at rest and in transit
- **AI Transparency**: All AI decisions logged and auditable

---

**Migration Note**: Original 37-line architecture overview created through AI-assisted development with human oversight. Migrated 2024-09-11 following HaldisB2B AI Developer Documentation Migration process.