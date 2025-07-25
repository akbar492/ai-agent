# AI Generative Agent System

A comprehensive local AI generative agent system with trainable models, natural language processing, code generation, and mathematical calculation capabilities. Built with React, Express, and Python.

## 🚀 Quick Start

### Prerequisites
- Node.js 20+
- Python 3.11+
- 4GB+ RAM (8GB recommended for training)

### Installation
```bash
# Clone the repository
git clone <repository-url>
cd ai-generative-agent

# Install dependencies
npm install

# Setup AI agent and database
python ai_agent/setup.py
python ai_agent/download_models.py

# Start the application
npm run dev
```

Open http://localhost:5000 to use the web interface.

## 🎯 Features

### 🗣️ Natural Language Chat
- Interactive conversation with AI agent
- Context-aware responses with memory
- Multiple conversation sessions
- Intent recognition and understanding

### 💻 Code Generation & Execution
- Generate code from natural language descriptions
- Safe code execution in sandboxed environment
- Support for Python, JavaScript, and TypeScript
- Real-time code validation and error handling

### 🧮 Mathematical Calculator
- Solve complex mathematical expressions
- Support for algebra, calculus, and statistics
- Step-by-step solution explanations
- Mathematical function recognition

### 🎓 Model Training
- Train custom AI models with your data
- Multiple model types:
  - Intent Recognition
  - Text Classification
  - Code Completion
  - Sentiment Analysis
  - Entity Recognition
- Real-time training progress monitoring

### 📊 System Monitoring
- Real-time model status dashboard
- Memory usage tracking
- Performance metrics
- Model accuracy monitoring

## 🏗️ Architecture

### Frontend (React + TypeScript)
- **Framework**: React 18 with Vite
- **UI Components**: Radix UI + Tailwind CSS
- **State Management**: TanStack Query
- **Routing**: Wouter
- **Forms**: React Hook Form + Zod validation

### Backend (Express + TypeScript)
- **Server**: Express.js with TypeScript
- **Database**: PostgreSQL with Drizzle ORM
- **Authentication**: Session-based auth
- **AI Integration**: Python Flask API

### AI Agent (Python)
- **NLP Libraries**: spaCy, NLTK
- **ML Framework**: scikit-learn
- **Models**: Custom trainable models
- **Safety**: Sandboxed code execution

## 📁 Project Structure

```
├── ai_agent/                 # Python AI system
│   ├── core/                # Core AI modules
│   │   ├── nlp_processor.py # Natural language processing
│   │   ├── code_generator.py # Code generation
│   │   ├── math_calculator.py # Mathematical calculations
│   │   └── conversation_manager.py # Chat management
│   ├── models/              # AI model implementations
│   │   ├── intent_recognizer.py # Intent recognition
│   │   ├── text_classifier.py # Text classification
│   │   └── code_completion.py # Code completion
│   ├── training/            # Model training system
│   │   ├── trainer.py       # Training orchestrator
│   │   └── data_preprocessor.py # Data preprocessing
│   ├── utils/               # Utility functions
│   │   ├── safe_executor.py # Safe code execution
│   │   └── model_manager.py # Model management
│   └── config/              # Configuration files
├── client/                  # React frontend
│   ├── src/
│   │   ├── components/      # UI components
│   │   ├── pages/          # Application pages
│   │   ├── hooks/          # Custom React hooks
│   │   └── lib/            # Utility libraries
├── server/                  # Express backend
│   ├── index.ts            # Main server file
│   ├── routes.ts           # API routes
│   ├── storage.ts          # Database interface
│   └── ai_routes.py        # AI-specific routes
├── shared/                  # Shared types and schemas
│   ├── schema.ts           # Database schema
│   └── ai_schema.ts        # AI-specific schemas
└── package.json            # Dependencies and scripts
```

## 🔧 Configuration

### AI Model Settings
Edit `ai_agent/config/settings.py`:
```python
MODEL_CACHE_SIZE = 5          # Models in memory
MAX_MEMORY_MB = 2048          # Max memory usage
TRAINING_TIMEOUT = 3600       # Training timeout
SAFE_EXECUTION_TIMEOUT = 30   # Code execution timeout
```

### Database Configuration
Set environment variables:
```bash
DATABASE_URL=postgresql://user:pass@localhost:5432/ai_agent
```

### Web Server Settings
Edit `server/index.ts`:
```typescript
const PORT = process.env.PORT || 5000;
const CORS_ORIGIN = process.env.CORS_ORIGIN || "http://localhost:5000";
```

## 🎮 Usage Examples

### Chat Interface
```
User: "Hello! Can you help me with coding?"
AI: "Hello! I'd be happy to help you with coding. What would you like to create?"

User: "Write a function to calculate fibonacci numbers"
AI: "I'll create a fibonacci function for you..."
```

### Code Generation
```
Input: "Create a function that sorts a list of numbers"
Output: 
def sort_numbers(numbers):
    return sorted(numbers)

# Usage example
numbers = [3, 1, 4, 1, 5, 9, 2, 6]
sorted_numbers = sort_numbers(numbers)
print(sorted_numbers)  # [1, 1, 2, 3, 4, 5, 6, 9]
```

### Mathematical Calculation
```
Input: "Solve: 2x + 3 = 11"
Output: 
Step 1: 2x + 3 = 11
Step 2: 2x = 11 - 3
Step 3: 2x = 8
Step 4: x = 8 ÷ 2
Step 5: x = 4
```

### Model Training
```json
{
  "model_type": "intent_recognizer",
  "data_source": {
    "intents": {
      "greeting": ["hello", "hi", "hey"],
      "goodbye": ["bye", "goodbye", "see you later"]
    }
  },
  "parameters": {
    "learning_rate": 0.01,
    "epochs": 10,
    "batch_size": 32
  }
}
```

## 🔒 Security Features

### Safe Code Execution
- Sandboxed environment with restricted module access
- Timeout protection for long-running code
- Memory limits to prevent resource abuse
- Whitelisted functions and imports only

### Data Protection
- Local data storage only (no external APIs)
- Session-based authentication
- Input validation on all endpoints
- No sensitive data exposure

## 🛠️ Development

### Available Scripts
```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run check        # TypeScript type checking
npm run db:push      # Push database schema
python ai_agent/setup.py      # Initialize AI agent
python ai_agent/download_models.py  # Download models
```

### Adding New Models
1. Create model class in `ai_agent/models/`
2. Add training logic in `ai_agent/training/`
3. Update model manager in `ai_agent/utils/`
4. Add UI components in `client/src/components/`

### API Endpoints
```
POST /api/ai/chat              # Chat with AI
POST /api/ai/code/execute      # Execute code
POST /api/ai/models/train      # Train models
GET  /api/ai/models/status     # Get model status
GET  /api/ai/conversation/:id  # Get conversation
```

## 📊 Performance

### System Requirements
- **Minimum**: 4GB RAM, 2 CPU cores
- **Recommended**: 8GB RAM, 4 CPU cores
- **Storage**: 2GB free space for models

### Optimization Tips
1. Adjust `MODEL_CACHE_SIZE` based on available RAM
2. Use model unloading for unused models
3. Enable database connection pooling
4. Monitor memory usage in web interface

## 🔍 Troubleshooting

### Common Issues

**Database Connection Failed**
```bash
# Check DATABASE_URL environment variable
echo $DATABASE_URL

# Reset database
npm run db:reset
```

**AI Models Not Loading**
```bash
# Reinstall models
python ai_agent/download_models.py

# Check model files
ls -la ai_agent/models/saved/
```

**Code Execution Errors**
```bash
# Check Python environment
python --version
pip list

# Verify whitelisted modules
python -c "import ai_agent.config.settings; print(settings.ALLOWED_MODULES)"
```

**Frontend Build Errors**
```bash
# Clear cache and reinstall
rm -rf node_modules package-lock.json
npm install
```

### Performance Issues
- Monitor memory usage in the web interface
- Check model cache size settings
- Verify database connection pooling
- Review system resource usage

## 📚 Documentation

- [Setup Guide](SETUP_GUIDE.md) - Detailed setup instructions
- [Installation Guide](INSTALLATION.md) - Quick installation steps
- [API Documentation](docs/API.md) - API reference
- [Model Training Guide](docs/TRAINING.md) - Training custom models

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new features
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Built with React, Express, and Python
- UI components from Radix UI and Tailwind CSS
- AI models powered by spaCy, NLTK, and scikit-learn
- Database management with Drizzle ORM

---

**Note**: This system is designed to run entirely locally without external dependencies, making it suitable for development environments or private deployments where data privacy is important.