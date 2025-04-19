# 🧠 Fake News Detector with Real-Time Cross Verification 🌐

## Overview

This project is an AI-powered browser-integrated tool to **detect and verify fake news** in real-time. Users can input news articles directly via text, image (screenshot), or PDF upload. It uses a deep learning-based LSTM model for classification and performs **live cross-verification** using web search APIs and semantic similarity scoring.

⚙️ Built with:
- **Python, Flask** – Backend API
- **TensorFlow / Keras (LSTM)** – Fake News Detection Model
- **Tesseract OCR** – Image and PDF text extraction
- **Sentence Transformers** – Semantic similarity
- **SerpAPI** – Real-time web search for cross-referencing
- **JavaScript, HTML, CSS** – Chrome/Edge/Firefox browser extension UI

---

## 🔍 Features

- ✅ Classifies news as: **Fake**, **Possibly Fake**, **Possibly Real**, or **Real**
- 📷 Supports **Image/PDF** uploads using OCR for text extraction
- 🔎 **Real-time cross-verification** against credible online sources
- 🧠 Uses **semantic similarity** to verify article claims
- 🌐 Available as a browser extension for **Chrome**, **Edge**, and **Firefox**
- 🔐 Fully local and secure – no external storage or logging

---

## 🧰 Installation & Setup

### Backend Setup (Flask + Model)


# Example path (Windows)
pytesseract.pytesseract.tesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe'
os.environ['TESSDATA_PREFIX'] = r'C:\Program Files\Tesseract-OCR\tessdata'
Then run the backend:


python app.py
Model & Tokenizer
Place the following files in the root folder:
lstm_model.keras
tokenizer.pkl

🧪 Running the Extension
Open your browser (Chrome/Edge/Firefox)

Go to chrome://extensions/ or about:debugging#/runtime/this-firefox

Enable Developer Mode

Click Load Unpacked and select the extension/ folder

Use the popup to paste or upload a news article

📦 Project Structure
bash
Copy
Edit
fake-news-detector/
│
├── app.py                     # Flask backend API
├── lstm_model.keras           # Trained LSTM model
├── tokenizer.pkl              # Tokenizer object
├── templates/
│   └── index.html             # Web interface
├── extension/
│   ├── popup.html             # Browser extension UI
│   ├── popup.js               # JS for extension logic
│   ├── manifest.json          # Extension config
│   └── style.css              # Styling for extension
├── utils/
│   └── cross_verify.py        # Sentence Transformer + SerpAPI
├── requirements.txt           # Python dependencies
└── README.md                  # This file


🎯 Future Enhancements
BERT-based fine-tuned model for better accuracy
Fake news detection for multilingual content
Feedback system to improve model performance over time
Offline mode with cached verification sources

🤝 Contributors
Aathithiyaa – AI Developer 
Jeeva - Full Stack Engineer



📜 License
This project is licensed under the MIT License.

⚠️ This is a research-based tool and still under active development. Always verify news from trusted sources.
