# AI Generative Agent System - Setup Guide

## Overview

This guide will help you set up and run the local AI generative agent system. The system provides natural language processing, code generation, mathematical calculations, and model training capabilities through a modern web interface.

## Prerequisites

- Node.js 20 or higher
- Python 3.11 or higher
- PostgreSQL database (or use Neon Database)
- At least 4GB RAM (8GB recommended for model training)

## Quick Start

### 1. Clone and Install Dependencies

```bash
# Clone the repository
git clone <repository-url>
cd ai-generative-agent

# Install Node.js dependencies
npm install

# Install Python dependencies
pip install -r requirements.txt
```

### 2. Database Setup

If using PostgreSQL locally:
```bash
# Create database
createdb ai_agent_db

# Set environment variable
export DATABASE_URL="postgresql://username:password@localhost:5432/ai_agent_db"
```

For Neon Database (recommended):
- Sign up at https://neon.tech
- Create a new database
- Copy the connection string to your environment variables

### 3. Environment Configuration

Create a `.env` file in the root directory:
```env
# Database
DATABASE_URL=your_database_connection_string

# Optional: AI Model Configuration
AI_MODEL_PATH=./ai_agent/models/saved
AI_TRAINING_DATA_PATH=./ai_agent/data
```

### 4. Initialize the Database

```bash
# Run database migrations
npm run db:migrate

# Optional: Seed with sample data
npm run db:seed
```

### 5. Start the Application

```bash
# Start the full application (frontend + backend + AI agent)
npm run dev
```

The application will be available at `http://localhost:5000`

## System Architecture

### Frontend (React + TypeScript)
- **Port**: 5000 (served through Express)
- **Framework**: React 18 with Vite
- **UI**: Radix UI + Tailwind CSS
- **State Management**: TanStack Query

### Backend (Express + TypeScript)
- **Port**: 5000 (same as frontend)
- **Database**: PostgreSQL with Drizzle ORM
- **AI Integration**: Python Flask API

### AI Agent (Python)
- **Location**: `./ai_agent/`
- **Models**: spaCy, NLTK, scikit-learn
- **Features**: NLP, code generation, math calculations, model training

## Features Overview

### 1. Natural Language Chat
- Interactive conversation with AI agent
- Context-aware responses
- Memory management across sessions

### 2. Code Generation & Execution
- Generate code from natural language descriptions
- Safe code execution in sandboxed environment
- Support for Python, JavaScript, and TypeScript

### 3. Mathematical Calculator
- Solve complex mathematical expressions
- Support for algebra, calculus, and statistics
- Step-by-step solution explanations

### 4. Model Training
- Train custom AI models with your data
- Support for multiple model types:
  - Intent Recognition
  - Text Classification
  - Code Completion
  - Sentiment Analysis
  - Entity Recognition

### 5. System Monitoring
- Real-time model status
- Memory usage tracking
- Performance metrics

## Configuration

### AI Model Settings

Edit `ai_agent/config/settings.py`:

```python
# Model Configuration
MODEL_CACHE_SIZE = 5  # Number of models to keep in memory
MAX_MEMORY_MB = 2048  # Maximum memory usage for AI operations
TRAINING_TIMEOUT = 3600  # Training timeout in seconds

# Safety Settings
SAFE_EXECUTION_TIMEOUT = 30  # Code execution timeout
ALLOWED_MODULES = ['math', 'numpy', 'pandas']  # Whitelisted modules
```

### Web Interface Settings

Edit `server/index.ts` for backend configuration:

```typescript
// Server Configuration
const PORT = process.env.PORT || 5000;
const CORS_ORIGIN = process.env.CORS_ORIGIN || "http://localhost:5000";

// Database Configuration
const DB_URL = process.env.DATABASE_URL;
```

## Development Workflow

### Project Structure
```
├── ai_agent/                 # Python AI system
│   ├── core/                # Core AI modules
│   ├── models/              # AI model implementations
│   ├── training/            # Model training system
│   ├── utils/               # Utility functions
│   └── config/              # Configuration files
├── client/                  # React frontend
│   ├── src/                 # Source code
│   └── public/              # Static assets
├── server/                  # Express backend
│   ├── index.ts            # Main server file
│   ├── routes.ts           # API routes
│   └── ai_routes.py        # AI-specific routes
├── shared/                  # Shared types and schemas
└── package.json            # Dependencies and scripts
```

### Available Scripts

```bash
# Development
npm run dev                 # Start development server
npm run build              # Build for production
npm run preview            # Preview production build

# Database
npm run db:migrate         # Run database migrations
npm run db:seed            # Seed database with sample data
npm run db:reset           # Reset database

# AI Agent
npm run ai:train           # Train AI models
npm run ai:test            # Test AI functionality
npm run ai:deploy          # Deploy AI models
```

## Troubleshooting

### Common Issues

1. **Database Connection Failed**
   - Check DATABASE_URL environment variable
   - Ensure PostgreSQL is running
   - Verify connection credentials

2. **AI Models Not Loading**
   - Check Python dependencies are installed
   - Verify model files exist in `ai_agent/models/saved/`
   - Check memory usage and increase if needed

3. **Code Execution Errors**
   - Verify Python environment is properly configured
   - Check if required modules are whitelisted
   - Ensure safe execution environment is set up

4. **Frontend Build Errors**
   - Clear node_modules and reinstall: `rm -rf node_modules && npm install`
   - Check TypeScript configuration
   - Verify all imports are correct

5. **Port Already in Use**
   - Kill existing processes: `lsof -ti:5000 | xargs kill`
   - Or change port in environment variables

### Performance Optimization

1. **Memory Management**
   - Adjust `MODEL_CACHE_SIZE` based on available RAM
   - Use model unloading for unused models
   - Monitor memory usage in the web interface

2. **Database Performance**
   - Use connection pooling
   - Add indexes for frequently queried columns
   - Regular database maintenance

3. **Frontend Performance**
   - Enable React Query caching
   - Use code splitting for large components
   - Optimize bundle size with tree shaking

## Security Considerations

### Code Execution Safety
- All code runs in a sandboxed environment
- Limited module access (whitelist only)
- Timeout protection for long-running code
- Memory limits to prevent abuse

### Data Protection
- No external API calls without explicit configuration
- Local data storage only
- Session-based authentication
- Input validation on all endpoints

## Advanced Usage

### Custom Model Training

1. **Prepare Training Data**
   ```json
   {
     "intents": {
       "greeting": ["hello", "hi", "hey"],
       "goodbye": ["bye", "goodbye", "see you"]
     }
   }
   ```

2. **Train the Model**
   - Use the web interface Model Training tab
   - Or via command line: `npm run ai:train -- --model intent_recognizer --data training_data.json`

3. **Deploy and Test**
   - Models are automatically loaded after training
   - Test through the chat interface

### API Integration

The system provides RESTful APIs for external integration:

```bash
# Chat with AI
POST /api/ai/chat
{
  "message": "Hello, how are you?",
  "session_id": "unique_session_id"
}

# Execute code
POST /api/ai/code/execute
{
  "code": "print('Hello World')",
  "language": "python"
}

# Train model
POST /api/ai/models/train
{
  "model_type": "intent_recognizer",
  "data_source": "training_data.json",
  "parameters": {"epochs": 10}
}
```

## Support

For issues, questions, or contributions:
1. Check the troubleshooting section above
2. Review the system logs for error details
3. Consult the API documentation
4. Create an issue in the repository

## License

This project is licensed under the MIT License. See LICENSE file for details.