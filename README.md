# AI Coding Assistant

A full-stack AI-powered coding assistant that helps you understand, debug, and fix your entire codebase using OpenAI's GPT models and semantic search.

![AI Coding Assistant](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)
![Python](https://img.shields.io/badge/python-3.9+-blue.svg)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai)

## Features

- 🔍 **Semantic Code Search** - Index your entire codebase and search using natural language
- 💬 **One-Shot Queries** - Ask questions and get instant, context-aware answers
- 🤖 **Multi-Turn Chat** - Have ongoing debugging conversations with AI
- 📄 **Code Context Display** - See exactly which files and line ranges were used to generate answers
- 🎯 **Smart Chunking** - Automatically chunks code into 50-line segments for better context
- ⚡ **Fast Retrieval** - Uses OpenAI embeddings and cosine similarity for relevant code retrieval

## Tech Stack

**Backend:**
- FastAPI - Modern Python web framework
- OpenAI API - GPT-4o-mini for chat, text-embedding-3-small for embeddings
- NumPy & scikit-learn - Vector operations and similarity calculations
- Uvicorn - ASGI server

**Frontend:**
- Vanilla HTML/CSS/JavaScript
- Modern gradient design with responsive layout
- Real-time stats and session management

## Installation

### Prerequisites
- Python 3.9 or higher
- OpenAI API key ([Get one here](https://platform.openai.com/api-keys))

### Setup

1. **Clone the repository**
```bash
git clone https://github.com/YOUR_USERNAME/ai-coding-assistant.git
cd ai-coding-assistant
```

2. **Create a virtual environment**
```bash
python -m venv venv

# On Windows
venv\Scripts\activate

# On Mac/Linux
source venv/bin/activate
```

3. **Install dependencies**
```bash
pip install fastapi uvicorn numpy scikit-learn python-multipart openai
```

4. **Set your OpenAI API key**
```bash
# On Mac/Linux
export OPENAI_API_KEY="your-api-key-here"

# On Windows (Command Prompt)
set OPENAI_API_KEY=your-api-key-here

# On Windows (PowerShell)
$env:OPENAI_API_KEY="your-api-key-here"
```

5. **Run the server**
```bash
uvicorn main:app --host 0.0.0.0 --port 5000
```

6. **Open your browser**
```
http://localhost:5000
```

## Usage

### 1. Index Your Codebase

- Enter the path to your code (default is ".")
- Specify file extensions to index (e.g., .py, .js, .ts, .html, .css)
- Click "Index Codebase"

The system will:
- Scan all files matching your extensions
- Chunk them into 50-line segments
- Generate embeddings for semantic search
- Exclude common directories (node_modules, .git, __pycache__, etc.)

### 2. Ask One-Shot Questions

Perfect for quick questions about your code:
- "What does the login function do?"
- "How is authentication handled?"
- "Where is the database connection configured?"

The assistant will:
- Retrieve the most relevant code chunks
- Show you the exact files and line ranges
- Provide clear, actionable answers

### 3. Multi-Turn Debugging Chat

Great for complex debugging sessions:
- Paste error tracebacks
- Ask follow-up questions
- Get step-by-step fixes with exact code changes

Each session maintains conversation history for context-aware responses.

## API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/index` | POST | Index codebase files and generate embeddings |
| `/query` | POST | One-shot question answering with context |
| `/chat` | POST | Multi-turn conversational debugging |
| `/retrieve` | POST | Get relevant code chunks without AI response |
| `/stats` | GET | View indexing and session statistics |
| `/sessions/{id}/history` | GET | Retrieve chat history for a session |
| `/sessions/{id}` | DELETE | Clear a chat session |

## Project Structure

```
ai-coding-assistant/
├── main.py              # FastAPI backend server
├── static/
│   ├── index.html       # Frontend UI
│   ├── styles.css       # Styling
│   └── app.js           # Client-side logic
├── replit.md            # Project documentation
├── .gitignore           # Git ignore rules
└── README.md            # This file
```

## Configuration

The application uses the following defaults:
- **Server Port**: 5000
- **Chunk Size**: 50 lines per chunk
- **Embedding Model**: text-embedding-3-small
- **Chat Model**: GPT-4o-mini
- **Context Chunks**: 5 chunks per query (configurable)
- **Chat History**: Last 20 messages per session

## Security

- API keys are never logged or exposed in the frontend
- CORS is enabled for development (configure for production)
- Session data is stored in-memory (consider Redis for production)
- Embeddings are not persisted (consider database storage for production)

## Troubleshooting

**ImportError: cannot import name 'OpenAI'**
- You have an old version of the openai package
- Run: `pip install --upgrade openai`

**OpenAI API key not configured**
- Make sure your `OPENAI_API_KEY` environment variable is set
- The key must be set before starting the server

**No code chunks found**
- Make sure you've indexed your codebase first
- Check that the file extensions match your code files
- Verify the path is correct

## Contributing

Contributions are welcome! Feel free to:
- Report bugs
- Suggest new features
- Submit pull requests

## License

MIT License - feel free to use this project for personal or commercial purposes.

## Acknowledgments

- Built with [FastAPI](https://fastapi.tiangolo.com/)
- Powered by [OpenAI](https://openai.com/)
- Inspired by the need for better code understanding tools

---

**Made with ❤️ for developers who want to understand their code better**
