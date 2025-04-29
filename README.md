
# TRUST ENGINE

A powerful Chrome extension and web app that detects whether a news article or a snippet is **real or fake** using an LSTM-based deep learning model.

## Overview

This project consists of:
- A **Chrome Extension** for real-time fake news detection on the web.
- A **Flask API** backend that serves the deep learning model.
- An **LSTM model** trained on text classification.
- Optional **OCR support** to process images containing text.

---

##  Project Structure

```
FAKE-NEWS-DETECTOR/
│
├── fake_news_extensions/      # Chrome extension files
│   ├── icon.png               # Extension icon
│   ├── manifest.json          # Chrome extension manifest (v3)
│   ├── popup.html             # Extension UI
│   ├── popup.js               # Client-side JS logic
│   └── style.css              # Styles for the popup
│
├── Model/                     # ML model and tokenizer
│   ├── lstm_model.keras       # Trained LSTM model
│   └── tokenizer.pkl          # Tokenizer for preprocessing
│
├── templates/
│   └── index.html             # Web interface (Flask-based)
│
├── app.py                     # Flask backend with REST API
├── README.md                  # Project documentation
```

---

##  Features

-  **Detect fake news** in real-time via Chrome extension or web form.
-  **Deep Learning (LSTM)** model for text classification.
-  **OCR support** to analyze news from images.
-  **URL extraction** for scraping news articles.
-  Easy integration via a local Flask server.

---

##  Model Details

- **Architecture**: LSTM
- **Input**: Tokenized and padded sequences of text.
- **Output**: Probability of being real or fake news.
- **Confidence**: Expressed as percentage in the UI.

---

##  How It Works

1. **Chrome Extension**:
   - User pastes or selects a news snippet.
   - Sends text to local Flask API (`/predict_json`).
   - Displays prediction and confidence.

2. **Flask API** (`app.py`):
   - Accepts POST requests with plain text, URLs, or image files.
   - Uses OCR for image input via Tesseract.
   - Parses article content from URLs using `newspaper3k`.
   - Returns prediction and confidence level.

---

##  Setup Instructions

###  Prerequisites
- Python 3.7+
- Google Chrome
- Tesseract OCR (for image-based detection)

###  Install Dependencies

```bash
pip install -r requirements.txt
```

> If `requirements.txt` is missing, install manually:
```bash
pip install flask tensorflow newspaper3k pillow pytesseract flask-cors
```

###  Tesseract OCR Setup (Windows Only)

- Install from: https://github.com/tesseract-ocr/tesseract
- Update paths in `app.py`:
```python
pytesseract.pytesseract.tesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe'
os.environ['TESSDATA_PREFIX'] = r'C:\Program Files\Tesseract-OCR\tessdata'
```

---

##  Running the Application

### 1. Start the Flask Server

```bash
python app.py
```

Flask will start at: `http://127.0.0.1:5000`

---

### 2. Load the Chrome Extension

1. Open `chrome://extensions`
2. Enable **Developer Mode**
3. Click **Load Unpacked**
4. Select the `fake_news_extensions` folder

---

##  API Endpoints

### `POST /predict`

- Form input: `article`, `url`, or `image`
- Returns: Rendered HTML result

### `POST /predict_json`

- JSON input: `{ "text": "your article here" }`
- Response:
```json
{
  "prediction": "Real News ✅",
  "confidence": 92.3
}
```

##  License

This project is licensed under the [MIT License](LICENSE).
