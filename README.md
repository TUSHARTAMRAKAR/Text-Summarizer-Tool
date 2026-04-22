<div align="center">

<br/>

# ◈ SummarAI
## AI-Powered Text Summarization Tool

<p align="center">
  <em>Paste any article. Get a sharp, accurate summary in seconds.</em><br/>
  <em>Powered by state-of-the-art NLP — completely free, runs locally.</em>
</p>

<br/>

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Flask](https://img.shields.io/badge/Flask-3.0-000000?style=for-the-badge&logo=flask&logoColor=white)](https://flask.palletsprojects.com)
[![HuggingFace](https://img.shields.io/badge/HuggingFace-Transformers-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black)](https://huggingface.co)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.2-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)](https://pytorch.org)
[![License](https://img.shields.io/badge/License-MIT-22C55E?style=for-the-badge)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Active-22C55E?style=for-the-badge)]()

<br/>

### 🌐 [Live Demo →](https://your-app.onrender.com) &nbsp;&nbsp;|&nbsp;&nbsp; 📖 [API Docs](docs/API.md) &nbsp;&nbsp;|&nbsp;&nbsp; 🐛 [Report a Bug](https://github.com/TUSHARTAMRAKAR/Text-Summarizer-Tool/issues)

<br/>

</div>

---

## 📌 Table of Contents

- [About the Project](#-about-the-project)
- [Features](#-features)
- [Live Demo](#-live-demo)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [API Reference](#-api-reference)
- [How It Works](#-how-it-works)
- [Running Tests](#-running-tests)
- [Roadmap](#-roadmap)
- [Contributing](#-contributing)
- [License](#-license)
- [Author](#-author)

---

## 📖 About the Project

**SummarAI** is a full-stack web application that uses Natural Language Processing (NLP) to automatically summarize long-form text — articles, research papers, blog posts, news — into concise, readable summaries.

The project implements **two distinct summarization approaches**:

- **Abstractive** — uses the `facebook/bart-large-cnn` transformer model (fine-tuned on 300,000+ CNN/DailyMail articles) to *understand* the text and write a fresh summary in its own words, just like a human would.
- **Extractive** — uses a custom-built TF-IDF scoring algorithm to identify and return the most statistically important sentences from the original text.

This was built as a beginner-to-intermediate learning project to understand NLP pipelines, REST API design, and full-stack web development — from model inference all the way to a production-ready interface.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🧠 **Abstractive Summarization** | `facebook/bart-large-cnn` rewrites text in its own words — natural, human-sounding output |
| ✂️ **Extractive Summarization** | Custom TF-IDF engine selects the most important original sentences |
| 📏 **3 Summary Lengths** | Short, Medium, Long — control exactly how detailed the output is |
| 📊 **Live Statistics** | Compression ratio, word counts, and method used — shown after every summary |
| 📋 **One-Click Copy** | Copy the generated summary to clipboard instantly |
| 🎯 **Built-in Sample Article** | Demo article included — works immediately with no setup |
| 🌐 **Clean REST API** | JSON API with 3 endpoints — can be integrated into any app |
| 💯 **100% Free & Local** | No paid APIs, no subscriptions, no data sent to the cloud |

---

## 🌐 Live Demo

> 🚀 The app is deployed and accessible here:

**[https://summari-84uc.onrender.com](https://summari-84uc.onrender.com)**

> ⚠️ Note: The app runs on Render's free tier — it may take 30–60 seconds to wake up on first visit.

---

## 🛠️ Tech Stack

| Layer | Technology | Why |
|---|---|---|
| **Frontend** | HTML5, CSS3, Vanilla JavaScript | Lightweight, no framework overhead |
| **Backend** | Python 3.10, Flask 3.0 | Simple, fast REST API server |
| **AI Model** | HuggingFace Transformers + BART | State-of-the-art abstractive summarization |
| **NLP Algorithm** | Custom TF-IDF (no libraries) | Fast extractive summarization, zero dependencies |
| **Deployment** | Render | Free cloud hosting for Python apps |
| **Testing** | pytest | Unit + integration test coverage |

---

## 🗂️ Project Structure

```
Text-Summarizer-Tool/
│
├── 📂 backend/
│   ├── app.py              # Flask app — all API routes and server config
│   └── summarizer.py       # Core NLP engine (BART abstractive + TF-IDF extractive)
│
├── 📂 frontend/
│   ├── templates/
│   │   └── index.html      # Main UI — single page app
│   └── static/
│       ├── css/
│       │   └── style.css   # Dark editorial theme, fully responsive
│       └── js/
│           └── main.js     # UI logic, API calls, state management
│
├── 📂 tests/
│   └── test_summarizer.py  # 15 unit + integration tests (pytest)
│
├── 📂 docs/
│   └── API.md              # Full API endpoint reference
│
├── requirements.txt        # All Python dependencies with pinned versions
├── .gitignore              # Excludes venv, cache, model files from Git
├── LICENSE                 # MIT License
└── README.md               # This file
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.10 or higher — [Download](https://python.org/downloads)
- pip (bundled with Python)
- ~2GB free disk space (for the BART model cache)
- Git — [Download](https://git-scm.com)

---

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/TUSHARTAMRAKAR/Text-Summarizer-Tool.git
cd Text-Summarizer-Tool
```

**2. Create a virtual environment**

```bash
python -m venv venv
```

**3. Activate the virtual environment**

```bash
# Windows
venv\Scripts\activate

# macOS / Linux
source venv/bin/activate
```

You'll see `(venv)` at the start of your terminal prompt. ✅

**4. Install dependencies**

```bash
pip install -r requirements.txt
```

> ⚠️ The first run will download the `facebook/bart-large-cnn` model (~1.6GB).  
> This only happens once — it's cached locally afterwards.

**5. Start the server**

```bash
cd backend
python app.py
```

**6. Open in browser**

```
http://localhost:5000
```

The app is running. 🎉

---

## 🔌 API Reference

Full documentation → [`docs/API.md`](docs/API.md)

Base URL: `http://localhost:5000`

---

### `POST /api/summarize`

Summarize a piece of text.

**Request body:**

```json
{
  "text": "Paste your article text here...",
  "length": "medium",
  "method": "abstractive"
}
```

| Parameter | Type | Options | Default |
|---|---|---|---|
| `text` | `string` | 50 – 50,000 characters | required |
| `length` | `string` | `short` · `medium` · `long` | `medium` |
| `method` | `string` | `abstractive` · `extractive` | `abstractive` |

**Success response `200`:**

```json
{
  "success": true,
  "summary": "Artificial intelligence is reshaping industries worldwide...",
  "original_word_count": 500,
  "summary_word_count": 82,
  "compression_ratio": "84%",
  "method_used": "abstractive"
}
```

**Error response `400`:**

```json
{
  "success": false,
  "error": "Text is too short. Please provide at least 50 characters."
}
```

---

### `GET /api/health`

Returns server and model status.

```json
{
  "status": "healthy",
  "model_loaded": true,
  "version": "1.0.0"
}
```

---

### `GET /api/sample`

Returns a built-in demo article for testing.

---

## 🧠 How It Works

### Abstractive Summarization (BART Transformer)

```
Your Text
    ↓
BART Encoder  →  Reads and builds deep understanding of the text
    ↓
BART Decoder  →  Generates a brand new summary, word by word
    ↓
Fresh Summary (written in the model's own words)
```

BART (Bidirectional and Auto-Regressive Transformer) was fine-tuned by Facebook AI on the CNN/DailyMail dataset — 300,000+ news articles with human-written summaries. It learns to compress information the same way a journalist would.

---

### Extractive Summarization (TF-IDF)

```
Your Text
    ↓
Split into individual sentences
    ↓
Score each sentence using TF-IDF weights
(words rare in the document but frequent in the sentence = more important)
    ↓
Rank sentences by score
    ↓
Return top N sentences in original order
```

**TF-IDF** = Term Frequency × Inverse Document Frequency. It mathematically identifies which words — and therefore which sentences — carry the most unique information in the document. No AI model needed, works fully offline, instant results.

---

## 🧪 Running Tests

```bash
# From project root with venv active
python -m pytest tests/ -v
```

Expected output:

```
tests/test_summarizer.py::TestExtractive::test_extractive_returns_dict     PASSED
tests/test_summarizer.py::TestExtractive::test_extractive_success_flag     PASSED
tests/test_summarizer.py::TestExtractive::test_extractive_has_summary      PASSED
tests/test_summarizer.py::TestExtractive::test_extractive_method_label     PASSED
tests/test_summarizer.py::TestExtractive::test_extractive_word_counts      PASSED
tests/test_summarizer.py::TestExtractive::test_extractive_short_length     PASSED
tests/test_summarizer.py::TestWordCounting::test_compression_ratio         PASSED
tests/test_summarizer.py::TestEdgeCases::test_handles_multiline_text       PASSED
tests/test_summarizer.py::TestEdgeCases::test_all_length_options           PASSED
tests/test_summarizer.py::TestAPIEndpoints::test_health_endpoint           PASSED
tests/test_summarizer.py::TestAPIEndpoints::test_summarize_endpoint_valid  PASSED
...

15 passed in 3.42s ✅
```

---

## 🗺️ Roadmap

- [x] Abstractive summarization (BART model)
- [x] Extractive summarization (TF-IDF)
- [x] 3 summary length options
- [x] REST API with JSON responses
- [x] Beautiful responsive web UI
- [x] Unit + integration test coverage
- [x] Deployed to Render
- [ ] PDF file upload and summarization
- [ ] Summarize from a URL (paste a link, get a summary)
- [ ] Export summary as .txt / .pdf
- [ ] Multi-language support
- [ ] Summary history (save and revisit past summaries)
- [ ] Browser extension

---

## 🤝 Contributing

Contributions are welcome and appreciated!

1. Fork the repository
2. Create your feature branch
```bash
git checkout -b feature/your-feature-name
```
3. Commit your changes using [Conventional Commits](https://www.conventionalcommits.org/)
```bash
git commit -m "feat: add PDF upload support"
```
4. Push to your branch
```bash
git push origin feature/your-feature-name
```
5. Open a Pull Request and describe what you changed and why

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

You're free to use, copy, modify, and distribute this project, as long as the original license is included.

---

<div align="center">

<br/>

## 👤 Author

### Tushar Tamrakar

[![GitHub](https://img.shields.io/badge/GitHub-TUSHARTAMRAKAR-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/TUSHARTAMRAKAR)

<br/>

*Built from scratch as a learning project — NLP, Flask, full-stack development, and Git workflow.*

<br/>

---

**⭐ Found this useful? Give it a star — it helps others discover the project!**

---

<sub>Made with ❤️ by Tushar Tamrakar</sub>

<br/>

</div>
