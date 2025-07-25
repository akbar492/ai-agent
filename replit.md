# AI Generative Agent System

## Overview

This is a comprehensive full-stack application that combines a local AI generative agent system with a modern web interface. The system provides natural language processing, code generation, mathematical calculation, and model training capabilities through both a Python backend and a React frontend.

The application follows a modular architecture where the AI agent system (written in Python) serves as the core intelligence layer, while the web interface (React/TypeScript) provides user interaction and visualization capabilities.

## User Preferences

Preferred communication style: Simple, everyday language.

## Recent Changes

**July 17, 2025**: Created comprehensive setup process and documentation
- Created detailed setup guide (SETUP_GUIDE.md) with step-by-step instructions
- Added quick installation guide (INSTALLATION.md) for rapid deployment
- Created automated setup scripts (ai_agent/setup.py, ai_agent/download_models.py)
- Added comprehensive README.md with usage examples and troubleshooting
- Created database seeding script (server/seed.ts) with sample data
- Added authentication utilities (server/auth.ts)
- Enhanced project with installation automation and user-friendly documentation

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite with custom configuration
- **UI Library**: Radix UI components with shadcn/ui styling
- **Styling**: Tailwind CSS with custom design tokens
- **State Management**: TanStack Query for server state management
- **Routing**: Wouter for lightweight client-side routing

### Backend Architecture
- **Web Server**: Express.js with TypeScript
- **AI System**: Python-based modular AI agent with multiple specialized components
- **API Layer**: RESTful API with Flask integration for AI operations
- **Database**: PostgreSQL with Drizzle ORM
- **Database Provider**: Neon Database (@neondatabase/serverless)

### AI Agent System Components
- **Core Modules**:
  - NLP Processor: Natural language understanding using spaCy and NLTK
  - Code Generator: Safe code generation and execution
  - Math Calculator: Mathematical problem solving
  - Conversation Manager: Context and memory management
- **Models**:
  - Intent Recognizer: User intent classification
  - Text Classifier: Document categorization
  - Code Completion: Intelligent code suggestions
- **Training System**: Model training and evaluation framework
- **Safety Layer**: Sandboxed code execution with security restrictions

## Key Components

### Data Flow
1. **User Input**: React frontend captures user interactions
2. **API Layer**: Express.js routes requests to appropriate handlers
3. **AI Processing**: Python AI agent processes requests using specialized modules
4. **Response Generation**: AI system returns structured responses
5. **UI Updates**: React components update based on AI responses

### Database Schema
- **Users**: Basic user management with username/password authentication
- **AI Schemas**: Structured schemas for messages, AI responses, chat sessions, and model information
- **Migration System**: Drizzle migrations for database schema management

### Security Features
- **Safe Code Execution**: Sandboxed environment with restricted modules and functions
- **Input Validation**: Zod schemas for type-safe data validation
- **Memory Limits**: Configurable memory and timeout restrictions
- **Module Restrictions**: Whitelist of allowed Python modules

### UI Components
- **Chat Interface**: Real-time conversation with the AI agent
- **Code Editor**: Interactive code editing and execution
- **Model Trainer**: Interface for training and managing AI models
- **System Status**: Real-time monitoring of AI system health

## External Dependencies

### Frontend Dependencies
- **UI Components**: Radix UI primitives for accessible components
- **State Management**: TanStack Query for API state management
- **Styling**: Tailwind CSS with PostCSS processing
- **Form Handling**: React Hook Form with Zod validation
- **Icons**: Lucide React icon library

### Backend Dependencies
- **Web Framework**: Express.js with TypeScript support
- **Database**: Drizzle ORM with PostgreSQL dialect
- **AI Libraries**: spaCy, NLTK, scikit-learn, numpy for machine learning
- **Security**: Input validation and sandboxed execution

### Development Tools
- **Build System**: Vite with React plugin and error overlay
- **Type Checking**: TypeScript with strict configuration
- **Code Quality**: ESLint and Prettier (implied by shadcn/ui setup)
- **Development Server**: Hot module replacement with Vite

## Deployment Strategy

### Development Environment
- **Local Development**: Vite dev server for frontend, tsx for backend hot reload
- **Database**: Neon Database with connection pooling
- **AI System**: Local Python environment with model caching

### Production Build
- **Frontend**: Vite build with optimized bundles
- **Backend**: esbuild compilation for Node.js deployment
- **Database**: Production PostgreSQL with connection pooling
- **AI Models**: Persistent model storage and caching

### Environment Configuration
- **Database**: Environment-based connection strings
- **AI Models**: Configurable model paths and settings
- **Security**: Environment-specific security configurations

### Scalability Considerations
- **Model Caching**: In-memory model caching with memory limits
- **Database Pooling**: Connection pooling for database efficiency
- **API Rate Limiting**: Configurable request throttling
- **Resource Monitoring**: Memory and CPU usage tracking

The system is designed to be self-contained and can run entirely locally, making it suitable for development environments or private deployments where data privacy is important.