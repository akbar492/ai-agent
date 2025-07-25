# Quick Installation Guide

## Prerequisites Check
Before starting, ensure you have:
- Node.js 20+ installed
- Python 3.11+ installed  
- At least 4GB RAM available

## One-Command Setup

### Option 1: Automated Setup (Recommended)
```bash
# Clone and setup everything
git clone <repository-url> && cd ai-generative-agent && npm run setup
```

### Option 2: Manual Setup
```bash
# 1. Install dependencies
npm install

# 2. Setup database (will use Neon Database)
npm run db:setup

# 3. Initialize AI models
npm run ai:init

# 4. Start application
npm run dev
```

## Verify Installation

1. Open http://localhost:5000
2. Try the chat interface - type "Hello"
3. Test code generation - ask "Create a function to add two numbers"
4. Check model status in the "Model Training" tab

## Common Issues

**Port 5000 already in use?**
```bash
export PORT=3000 && npm run dev
```

**Database connection failed?**
```bash
npm run db:reset
```

**AI models not loading?**
```bash
npm run ai:download-models
```

## Next Steps

Once installed:
1. Read the full [Setup Guide](SETUP_GUIDE.md) for detailed configuration
2. Try the example tutorials in the web interface
3. Train your first custom model with sample data

## Support

If you encounter issues:
1. Check the application logs in the terminal
2. Review the troubleshooting section in [Setup Guide](SETUP_GUIDE.md)
3. Ensure all prerequisites are met

The system is designed to work locally without external dependencies once installed.