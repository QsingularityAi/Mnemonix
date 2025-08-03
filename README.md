# Mnemonix - Your Personal Memory Extension

<div align="center">
  <img src="frontend/public/MnemonixLogo.png" alt="Mnemonix Logo" width="128" height="128">
  
  **I can remember anything for you**
  
  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
  [![Chrome Extension](https://img.shields.io/badge/Chrome-Extension-green.svg)](https://chrome.google.com/webstore)
  [![FastAPI](https://img.shields.io/badge/FastAPI-0.68+-blue.svg)](https://fastapi.tiangolo.com)
  [![React](https://img.shields.io/badge/React-19.0+-blue.svg)](https://reactjs.org)
</div>

## 🧠 What is Mnemonix?

Mnemonix is an intelligent browser extension that acts as your personal memory assistant. It helps you save, organize, and retrieve information from any webpage with the power of AI. Whether it's articles, quotes, notes, or bookmarks, Mnemonix remembers everything so you don't have to.

## ✨ Features

### 🔍 **Smart Search & Retrieval**
- AI-powered semantic search across all your saved content
- Quick search with `Alt+X` keyboard shortcut
- Context-aware results that understand what you're looking for

### 📚 **Content Management**
- **Bookmarks**: Save and organize web pages with automatic metadata extraction
- **Notes**: Create and manage personal notes with rich text support
- **Memories**: Store important information with AI-enhanced categorization
- **Quotes**: Capture and organize inspiring quotes from any webpage

### 🤖 **AI-Powered Intelligence**
- Automatic content summarization
- Smart categorization and tagging
- Contextual recommendations
- Natural language search queries

### ⚡ **Seamless Integration**
- Toggle sidebar with `Alt+M` on any webpage
- Non-intrusive overlay design
- Cross-website functionality
- Instant sync across devices

### 🔐 **Secure & Private**
- User authentication via Supabase
- Encrypted data storage
- Privacy-focused design
- Local processing where possible

## 🚀 Quick Start

### Prerequisites
- Chrome/Chromium browser
- Python 3.8+
- Node.js 16+

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/mnemonix.git
   cd mnemonix
   ```

2. **Set up environment variables**
   ```bash
   # Backend
   cp backend/.env.example backend/.env
   # Edit backend/.env with your API keys
   
   # Frontend
   cp frontend/.env.example frontend/.env
   # Default values work for local development
   ```

3. **Start the backend**
   ```bash
   cd backend
   python -m venv venv
   source venv/bin/activate  # Windows: venv\Scripts\activate
   pip install -r requirements.txt
   uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
   ```

4. **Build the extension**
   ```bash
   cd frontend
   npm install
   npm run build
   ```

5. **Load in Chrome**
   - Go to `chrome://extensions/`
   - Enable "Developer mode"
   - Click "Load unpacked"
   - Select the `frontend/dist/` folder

📖 **For detailed setup instructions, see [SETUP.md](SETUP.md)**

## 🎯 Usage

### Basic Operations

- **Open Mnemonix**: Press `Alt+M` on any webpage
- **Quick Search**: Press `Alt+X` for instant search
- **Save Content**: Select text and use the save options in the sidebar
- **Browse Saved Items**: Navigate through your bookmarks, notes, and memories

### Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Alt+M` | Toggle Mnemonix sidebar |
| `Alt+X` | Open quick search |

## 🏗️ Architecture

### Frontend (Chrome Extension)
- **React 19** with TypeScript
- **Tailwind CSS** for styling
- **Framer Motion** for animations
- **Vite** for building and bundling

### Backend (API Server)
- **FastAPI** with Python
- **MongoDB** for document storage
- **Pinecone** for vector search
- **Supabase** for authentication
- **Google Gemini AI** for content processing

### Key Components

```
mnemonix/
├── frontend/                 # Chrome extension
│   ├── src/                 # React application
│   ├── public/              # Extension files
│   │   ├── manifest.json    # Extension manifest
│   │   ├── content.js       # Content script
│   │   └── background.js    # Service worker
│   └── dist/                # Built extension
├── backend/                 # FastAPI server
│   ├── app/
│   │   ├── routers/         # API endpoints
│   │   ├── services/        # Business logic
│   │   ├── core/            # Configuration
│   │   └── utils/           # Utilities
│   └── requirements.txt
└── README.md
```

## 🔧 Development

### Making Changes

**Backend Development**:
```bash
cd backend
source venv/bin/activate
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

**Frontend Development**:
```bash
cd frontend
npm run dev          # For development server
npm run build        # Build extension
```

### API Documentation
When the backend is running, visit:
- **API Docs**: http://127.0.0.1:8000/docs
- **Health Check**: http://127.0.0.1:8000/health

## 🌐 Environment Variables

### Backend (.env)
```bash
# Authentication
SUPABASE_URL=your_supabase_url
SUPABASE_API_KEY=your_api_key
SUPABASE_ANON_KEY=your_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_service_role_key
SUPABASE_JWT_SECRET=your_jwt_secret

# Database
MONGODB_URI=your_mongodb_connection
MONGODB_DB=mnemonix_db

# AI Services
PINECONE_API_KEY=your_pinecone_key
PINECONE_INDEX=mnemonix-index
GEMINI_API_KEY=your_gemini_key
```

### Frontend (.env)
```bash
VITE_BACKEND_URL=http://127.0.0.1:8000
VITE_API_URL=http://127.0.0.1:8000
```

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details.

### Development Workflow

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Test thoroughly
5. Commit your changes (`git commit -m 'Add amazing feature'`)
6. Push to the branch (`git push origin feature/amazing-feature`)
7. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

- **Documentation**: Check [SETUP.md](SETUP.md) for detailed setup instructions
- **Issues**: Report bugs or request features via [GitHub Issues](https://github.com/yourusername/mnemonix/issues)
- **Discussions**: Join our [GitHub Discussions](https://github.com/yourusername/mnemonix/discussions)

## 🙏 Acknowledgments

- **FastAPI** for the excellent Python web framework
- **React** for the powerful frontend library
- **Supabase** for authentication and database services
- **Pinecone** for vector search capabilities
- **Google Gemini AI** for intelligent content processing
- **MongoDB** for flexible document storage

## 🔮 Roadmap

- [ ] Mobile app companion
- [ ] Advanced AI summarization
- [ ] Team collaboration features
- [ ] Integration with popular note-taking apps
- [ ] Offline mode support
- [ ] Advanced search filters
- [ ] Export/import functionality
- [ ] Browser sync across different browsers

---

<div align="center">
  <strong>Made with ❤️ for developers who never want to forget anything important</strong>
</div>