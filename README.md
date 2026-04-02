# GUVI Document Analysis API

## Description
A FastAPI-based document analysis system for PDF, DOCX, and image files. It supports OCR for images, AI-powered summarization, entity extraction, and sentiment analysis.

## Features
- PDF text extraction
- DOCX text extraction
- Image OCR using Tesseract
- AI-powered summarization using Gemini
- Entity extraction: names, dates, organizations, amounts
- Sentiment analysis
- API key authentication

## Tech Stack
- Python
- FastAPI
- PyMuPDF
- docx2txt
- pytesseract
- Pillow
- Google GenAI SDK

## Setup Instructions
1. Clone the repository
2. Create virtual environment
3. Install dependencies
4. Add environment variables in `.env`
5. Run the server

## Run
```bash
uvicorn main:app --reload