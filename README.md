# 🚀 GUVI Document Analysis API

## 📌 Overview

A full-stack AI-powered document analysis platform built using FastAPI and modern web technologies.
The system allows users to upload **PDF, DOCX, and image files** and instantly receive:

* 📄 Summaries
* 🔍 Entity extraction
* 😊 Sentiment analysis

The application combines traditional text extraction techniques with **Google Gemini AI** for intelligent document understanding.

---

## ✨ Features

* 📄 **Multi-format Support**
  Supports PDF, DOCX, PNG, JPG, JPEG

* 🤖 **AI Summarization**
  Generates concise summaries using Gemini AI

* 🔍 **Entity Extraction**
  Extracts names, dates, organizations, and monetary values

* 😊 **Sentiment Analysis**
  Classifies content as Positive, Neutral, or Negative

* 📸 **OCR Support**
  Tesseract-based extraction for images

* 🔐 **API Key Authentication**
  Secures API endpoints

* 🎨 **Modern UI**
  Clean landing page with real-time processing

---

## 🧠 Architecture Overview

The system follows a modular processing pipeline:

1. **Input Layer**

   * Receives base64 encoded file via API

2. **Processing Layer**

   * PDF → PyMuPDF
   * DOCX → docx2txt
   * Image → Tesseract OCR

3. **AI Layer**

   * Google Gemini API used for:

     * Summarization
     * Sentiment analysis
     * Entity refinement

4. **Output Layer**

   * Returns structured JSON response:

     * summary
     * entities
     * sentiment

---

## 🛠 Tech Stack

### Backend

* Python 3.9+
* FastAPI
* PyMuPDF
* docx2txt
* pytesseract
* Google GenAI SDK (Gemini)

### Frontend

* HTML5, CSS3, JavaScript
* Tailwind CSS
* Material Icons

### Deployment

* Docker
* Render

---

## ⚙️ Local Setup

### 🔧 Prerequisites

* Python 3.9+
* Tesseract OCR installed
* Git

---

### 📥 Installation

```bash
git clone https://github.com/Kishor-027/guvi-doc-ai.git
cd guvi-doc-ai
```

```bash
python -m venv venv
venv\Scripts\activate   # Windows
```

```bash
pip install -r requirements.txt
```

---

### 🧾 Install Tesseract

* Windows: https://github.com/UB-Mannheim/tesseract/wiki
* macOS:

```bash
brew install tesseract
```

* Linux:

```bash
sudo apt-get install tesseract-ocr
```

---

### 🔐 Environment Variables

```bash
cp .env.example .env
```

Edit `.env`:

```env
API_KEY=test123
GEMINI_API_KEY=your_api_key_here
```

---

### ▶️ Run Server

```bash
uvicorn main:app --reload
```

Visit:

```
http://localhost:8000
```

---

## 📡 API Documentation

### Endpoint

```
POST /api/document-analyze
```

### Headers

```json
{
  "Content-Type": "application/json",
  "x-api-key": "test123"
}
```

---

### 📤 Request Body

```json
{
  "fileName": "sample.pdf",
  "fileType": "pdf",
  "fileBase64": "BASE64_STRING"
}
```

Supported file types:

* pdf
* docx
* image

---

### 📥 Response

```json
{
  "status": "success",
  "fileName": "sample.pdf",
  "summary": "Document summary...",
  "entities": {
    "names": ["Ravi Kumar"],
    "dates": ["10 March 2026"],
    "organizations": ["ABC Pvt Ltd"],
    "amounts": ["₹10,000"]
  },
  "sentiment": "Neutral"
}
```

---

## 🌐 Live Demo

* 🔗 App URL: https://guvi-doc-ai-1.onrender.com
* 🔗 API Endpoint: https://guvi-doc-ai-1.onrender.com/api/document-analyze

---

## 🚀 Deployment (Render - Docker)

This project uses Docker to support OCR dependencies.

### Steps:

1. Push code to GitHub
2. Create new Web Service in Render
3. Select **Environment: Docker**
4. Set Dockerfile path:

```
Dockerfile
```

5. Add environment variables:

```
API_KEY=test123
GEMINI_API_KEY=your_key
```

6. Deploy

---

## 📂 Project Structure

```
.
├── main.py
├── templates/
│   └── index.html
├── Dockerfile
├── requirements.txt
├── .env.example
├── .gitignore
└── README.md
```

---

## 🔐 Security Notes

* API key validation on every request
* No file storage (in-memory processing)
* Base64 encoding prevents file corruption
* Input validation implemented

---

## ⚠️ Known Limitations

* OCR accuracy depends on image quality
* Large files may take longer to process
* Entity extraction may vary by document structure
* Processing is synchronous (no queue system)

---

## ⚡ Performance

* Average processing time: **5–10 seconds**
* Supports concurrent requests via FastAPI

---

## 🤖 AI Tools Used

* ChatGPT — development guidance, debugging, architecture design, documentation
* Google Gemini API — summarization, sentiment analysis, entity extraction
* Stitch AI — landing page UI design
* VS Code AI tools — integration and refinement

---

## 🏁 Built For

**GUVI Hackathon 2026**
