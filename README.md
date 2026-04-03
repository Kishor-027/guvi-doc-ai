# GUVI Document Analysis API

## Overview
A full-stack document analysis platform built with FastAPI and modern web technologies. Upload PDF, DOCX, or image files to get AI-powered summaries, entity extraction, and sentiment analysis instantly.

## Features
- 📄 **Multi-format Support**: PDF, DOCX, PNG, JPG, JPEG
- 🤖 **AI Summarization**: Powered by Google Gemini
- 🔍 **Entity Extraction**: Names, dates, organizations, amounts
- 😊 **Sentiment Analysis**: Positive, Neutral, Negative classification
- 📸 **OCR**: Tesseract-based optical character recognition for images
- 🔐 **API Key Authentication**: Secure endpoints
- 🎨 **Modern UI**: Interactive web interface with real-time processing

## Tech Stack
### Backend
- Python 3.9+
- FastAPI 0.135.3
- PyMuPDF (PDF extraction)
- docx2txt (DOCX extraction)
- pytesseract (OCR)
- Google Gen AI SDK (Gemini)

### Frontend
- HTML5 + CSS3 + JavaScript
- Tailwind CSS
- Material Design Icons

## Local Setup

### Prerequisites
- Python 3.9 or higher
- Tesseract OCR installed
- Git

### Installation

1. **Clone repository**
```bash
git clone https://github.com/your-username/guvi-doc-ai.git
cd guvi-doc-ai
```

2. **Create virtual environment**
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\Activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Install Tesseract** (for OCR)
   - **Windows**: Download from https://github.com/UB-Mannheim/tesseract/wiki
   - **macOS**: `brew install tesseract`
   - **Linux**: `sudo apt-get install tesseract-ocr`

5. **Setup environment variables**
```bash
cp .env.example .env
# Edit .env and add:
# API_KEY=test123
# GEMINI_API_KEY=your_gemini_api_key_here
```

Get a Gemini API key from: https://ai.google.dev/

6. **Run server**
```bash
uvicorn main:app --reload
```

Visit: http://localhost:8000

## API Documentation

### Endpoint: `/api/document-analyze`

**Method**: POST

**Headers**:
```json
{
  "Content-Type": "application/json",
  "x-api-key": "test123"
}
```

**Request Body**:
```json
{
  "fileName": "sample.pdf",
  "fileType": "pdf",
  "fileBase64": "BASE64_ENCODED_FILE"
}
```

**File Types**: `pdf`, `docx`, `image`

**Response** (Success):
```json
{
  "status": "success",
  "fileName": "sample.pdf",
  "summary": "Document summary text...",
  "entities": {
    "names": ["John Doe"],
    "dates": ["2026-04-03"],
    "organizations": ["GUVI Inc"],
    "amounts": ["₹10,000"]
  },
  "sentiment": "Neutral"
}
```

## Deployment to Render

### Steps
1. Push code to GitHub (with `.env` NOT committed)
2. Connect GitHub repo to Render
3. Create new Web Service
4. Set build command: `pip install -r requirements.txt`
5. Set start command: `uvicorn main:app --host 0.0.0.0 --port $PORT`
6. Add environment variables in Render dashboard:
   - `API_KEY=test123`
   - `GEMINI_API_KEY=your_key`
7. Deploy

## Project Structure
```
.
├── main.py                 # FastAPI application
├── templates/
│   └── index.html         # Frontend SPA
├── requirements.txt        # Python dependencies
├── .env.example           # Environment template
└── README.md
```

## File Limits
- Maximum file size: **50 MB**
- Supported image formats: PNG, JPG, JPEG
- Supported document formats: PDF, DOCX

## Security Notes
- API key validated on every request
- Base64 file encoding prevents binary upload issues
- No file storage - all processing in-memory
- File size validation on both client and server
- Input sanitization for entity extraction

## Troubleshooting

**OCR not working?**
- Windows: Ensure Tesseract is installed in `C:\Program Files\Tesseract-OCR\`
- Verify path in main.py line 20

**Gemini API returns error?**
- Check API key is valid and has quota remaining
- Verify GEMINI_API_KEY is set in environment
- Check internet connection

**Frontend not loading?**
- Ensure `templates/index.html` exists
- Clear browser cache (Ctrl+Shift+R)
- Check FastAPI is running on correct port

## Performance
- Average processing time: 5-10 seconds
- Includes: text extraction, regex analysis, AI processing
- Concurrent requests supported via FastAPI async handling

## Built For
GUVI Hackathon 2026

## License
MIT