# Mnemonix Extension Setup Guide

## Prerequisites

- Python 3.8+
- Node.js 16+
- Chrome/Chromium browser for testing

## Environment Setup

### 1. Backend Environment Variables

Create a `.env` file in the `backend/` directory with the following variables:

```bash
# Copy the example file
cp backend/.env.example backend/.env
```

Then edit `backend/.env` with your actual values:

#### Required Services:

1. **Supabase** (Authentication & Database)
   - Sign up at https://supabase.com
   - Create a new project
   - Get your project URL and keys from Settings > API

2. **MongoDB** (Document Storage)
   - Use MongoDB Atlas (cloud) or local MongoDB
   - Get connection string from your MongoDB setup

3. **Pinecone** (Vector Database)
   - Sign up at https://pinecone.io
   - Create an index named "mnemonix-index"
   - Get your API key

4. **Google Gemini AI** (AI Processing)
   - Get API key from Google AI Studio

### 2. Frontend Environment Variables

Create a `.env` file in the `frontend/` directory:

```bash
# Copy the example file
cp frontend/.env.example frontend/.env
```

For local development, the default values should work:
```
VITE_BACKEND_URL=http://127.0.0.1:8000
VITE_API_URL=http://127.0.0.1:8000
```

## Installation & Running

### Backend Setup

1. Navigate to backend directory:
```bash
cd backend
```

2. Create virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Run the backend server:
```bash
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

The backend will be available at http://127.0.0.1:8000

### Frontend Setup

1. Navigate to frontend directory:
```bash
cd frontend
```

2. Install dependencies:
```bash
npm install
```

3. Build the extension:
```bash
npm run build
```

This will create a `dist/` folder with the built extension.

## Loading the Extension in Chrome

1. Open Chrome and go to `chrome://extensions/`

2. Enable "Developer mode" (toggle in top right)

3. Click "Load unpacked"

4. Select the `frontend/dist/` folder

5. The Mnemonix extension should now appear in your extensions list

## Testing the Extension

1. **Verify Extension Load**: Check that the extension appears in Chrome's extension toolbar

2. **Test Keyboard Shortcuts**:
   - `Alt+M` (Mac) - Toggle Mnemonix extension
   - `Alt+X` (Mac) - Quick search in Mnemonix

3. **Test Backend Connection**: 
   - Visit http://127.0.0.1:8000/health to verify backend is running
   - Check browser console for any connection errors

4. **Test on a Website**:
   - Navigate to any website
   - Press `Alt+M` to open the Mnemonix sidebar
   - Try saving content or searching

## Development Workflow

### Making Changes

**Backend Changes**:
- The FastAPI server runs with `--reload` so changes are automatically applied
- Check logs in the terminal where you ran `uvicorn`

**Frontend Changes**:
1. Make your changes in the `frontend/src/` directory
2. Rebuild: `npm run build`
3. Go to `chrome://extensions/`
4. Click the refresh button on the Mnemonix extension
5. Test your changes

### Debugging

**Backend Debugging**:
- Check terminal logs where uvicorn is running
- API documentation available at http://127.0.0.1:8000/docs

**Frontend Debugging**:
- Open Chrome DevTools (F12)
- Check Console tab for JavaScript errors
- Check Network tab for API call issues
- Use `chrome://extensions/` to see extension errors

## Common Issues

1. **Extension not loading**: Make sure you built the frontend (`npm run build`)

2. **API connection errors**: Verify backend is running on port 8000

3. **Environment variable errors**: Double-check your `.env` files have all required values

4. **Permission errors**: Make sure the extension has the necessary permissions in manifest.json

## Production Deployment

For production deployment, update the environment variables:

**Frontend `.env`**:
```
VITE_BACKEND_URL=https://your-production-backend.com
VITE_API_URL=https://your-production-backend.com
```

Then rebuild the extension with `npm run build`.