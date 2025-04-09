# 🌍 Universal Translator + Culture Guide

A smart travel and communication companion that enables seamless connection across languages and cultures. This AI-powered tool instantly translates text, speech, and signs while offering real-time cultural context to help users navigate new environments with confidence.

---

## ✨ What It Does

- 🎤 **Real-Time Voice Translation** — Translate speech in conversations as you speak.
- 📷 **Sign & Text Capture** — Use your phone camera to read and translate signs instantly with AR overlays.
- 🧠 **Cultural Tips Engine** — Get localized insights like etiquette, greetings, and slang decoding.
- 🧾 **Offline Translation Mode** — Translate common phrases and signs without internet.
- 🔄 **Multi-language Support** — Supports 100+ languages, with dialect distinctions.

---

## 💡 Why It Works

- Breaks down communication barriers for travelers, immigrants, and expats
- Educates users about cultural norms to avoid misunderstandings
- Enhances user confidence and safety while exploring new places
- Combines AI and AR into a compact, user-friendly app

---

## 🧪 Tech Stack

| Feature | Technology |
|--------|-------------|
| Translation | NLP Models (Transformer-based: T5, MarianMT, etc.) |
| Voice Input | Speech-to-Text (Whisper, Google STT) |
| Voice Output | Text-to-Speech (Google TTS, Amazon Polly) |
| Sign Capture | ARKit / ARCore + OCR (Tesseract, EasyOCR) |
| Cultural Guide | Knowledge Graph + NLP + Crowd-Sourced Data |
| Platform | Flutter (Cross-platform UI), Python (Backend APIs) |

---

## 🏗️ Technical Design

### 1. System Architecture

```
+------------------------+           +---------------------------+
|      Mobile App        |           |     Backend API (FastAPI) |
| (Flutter: iOS & Android)| ←──────→ |  Translation & Culture API|
+------------------------+           +---------------------------+
          |                                      |
          |     REST API (HTTPS, JWT-secured)   |
          |                                      ↓
     +-------------------+        +-----------------------------+
     | Speech-to-Text    |        | Cultural Knowledge Service  |
     | (Whisper API)     |        | (slang, etiquette DB, etc.)|
     +-------------------+        +-----------------------------+
          ↓
+----------------------+   +----------------+   +--------------------+
| NLP Translation      |   | OCR Engine      |   | Text-to-Speech     |
| (HuggingFace models) |   | (Tesseract/Easy)|   | (Google TTS/Polly) |
+----------------------+   +----------------+   +--------------------+
```

### 2. Module Breakdown

#### 🔄 Translation Engine
- **Text Translation**: Uses HuggingFace transformers (T5, MarianMT) for dynamic text-to-text translation.
- **Voice Translation**:
  - Converts audio to text (STT)
  - Translates the text using NLP models
  - Converts the result back to audio (TTS)
- **Sign Translation**: 
  - Captures image via camera
  - Detects text via OCR
  - Translates and displays overlay via AR

#### 🧠 Culture & Slang Intelligence
- Uses a hybrid knowledge graph and rule-based NLP system
- Matches location/region + language to a curated tip database
- Slang decoding based on crowdsourced dictionary and NLP context extraction
- Culture tips include etiquette, customs, hand gestures, dos/don’ts

#### 🎥 AR Translation
- Uses ARKit/ARCore to anchor translated text as 3D overlay in the user's view
- Tracks bounding boxes on detected signs to maintain accuracy
- Works offline with cached phrase packs

#### 📡 Backend Services
- **FastAPI REST Layer**: Handles routing, validation, and device authentication
- **Rate Limiting & Quotas**: Managed per IP/device/token to avoid abuse
- **Async Processing**: Background workers (Celery/Redis) for STT/TTS/translation queue
- **Logs/Monitoring**: Integrated with Prometheus/Grafana for observability

---

## 🚀 Getting Started (Backend)

### Prerequisites
- Python 3.9+
- FastAPI
- Tesseract OCR
- Transformers (HuggingFace)
- Google/AWS API keys

### Setup
```bash
# Clone the repository
$ git clone https://github.com/your-org/universal-translator.git
$ cd universal-translator/backend

# Install dependencies
$ pip install -r requirements.txt

# Run the API server
$ uvicorn main:app --reload
```

### API Base URL
```
http://localhost:8000/
```

---

## 🧠 Key API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/translate/text` | POST | Translate a text snippet to target language |
| `/translate/voice` | POST | Upload voice and return translated audio |
| `/translate/image` | POST | Submit image with text and receive AR overlay |
| `/culture/tips` | GET | Get cultural tips for region/language |
| `/culture/slang` | GET | Get definitions of local slang |

---

## 📱 Mobile App Features (Flutter)

- Voice input with real-time display and translation
- AR-based sign detection and overlays
- Culture guide panel with context-based recommendations
- Travel phrasebook
- Favorites and offline mode support

---

## 🔐 Security Considerations

- Minimal personally identifiable data retained
- Encrypted transmissions (HTTPS, TLS)
- API usage quotas and abuse detection
- JWT-secured API endpoints
- GDPR & CCPA compliant data handling

---

## 🛣️ Roadmap

- [ ] Community-sourced cultural tips & slang moderation
- [ ] Full offline translation packs
- [ ] Real-time conversation mode with subtitles
- [ ] AR sign translation overlay on live camera feed
- [ ] Gesture and emoji interpretation

---

## 🧾 License

MIT License — see [LICENSE](LICENSE) for full details.

---

## 📬 Contact

- GitHub: https://github.com/teambits009
- Email: brandonopere6@gmail.com/brandon@techopssapex.com

