<div align="center">

# 🎬 AI Video Agent

**Turn any video into a searchable, translated, summarized knowledge base — automatically.**

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Streamlit](https://img.shields.io/badge/UI-Streamlit-FF4B4B?logo=streamlit&logoColor=white)](https://streamlit.io/)
[![LangChain](https://img.shields.io/badge/Orchestration-LangChain-1C3C3C)](https://www.langchain.com/)
[![Whisper](https://img.shields.io/badge/Transcription-OpenAI%20Whisper-412991)](https://github.com/openai/whisper)
[![ChromaDB](https://img.shields.io/badge/Vector%20Store-ChromaDB-FF6F00)](https://www.trychroma.com/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

</div>

---

## 📖 Overview

**AI Video Agent** takes a video — a YouTube link or a local file — and turns it into something you can actually *talk to*. It downloads the audio, transcribes it locally with Whisper, translates non-English speech into English, indexes the content into a vector store, and lets you ask questions or generate summaries through a Mistral-powered RAG pipeline — all from a clean Streamlit interface, with one-click PDF export when you're done.

No manual transcript-wrangling. No copy-pasting into ChatGPT. Drop in a link, get back answers.

## ✨ Features

- 🎥 **Video/audio ingestion** — pull audio straight from a YouTube URL or load a local file
- 🗣️ **Local speech-to-text** — fully offline transcription via OpenAI Whisper, no audio leaves your machine for this step
- 🌐 **Hindi → English translation** — automatically translates non-English transcripts before downstream processing
- 🧠 **RAG-powered Q&A** — chunk, embed, and store transcripts in ChromaDB, then query them through a Mistral LLM via LangChain
- 💬 **Conversational interface** — ask follow-up questions about the video content, not just a one-shot summary
- 📄 **Export to PDF** — turn summaries or transcripts into a shareable document
- ⚡ **Streamlit UI** — simple, no-setup web interface to drive the whole pipeline

## 🛠️ How It Works

```
 YouTube URL / local file
          │
          ▼
   yt-dlp + ffmpeg            (audio extraction)
          │
          ▼
   OpenAI Whisper             (local transcription)
          │
          ▼
   deep-translator            (Hindi → English, if needed)
          │
          ▼
   sentence-transformers      (chunk + embed transcript)
          │
          ▼
   ChromaDB                   (vector storage)
          │
          ▼
   LangChain + Mistral        (RAG retrieval + generation)
          │
          ▼
   Streamlit UI                (chat / summary / export)
```

## 🧰 Tech Stack

| Layer | Tools |
|---|---|
| Audio/video acquisition | `yt-dlp`, `pydub`, `ffmpeg-python` |
| Speech-to-text | `openai-whisper`, `torch`, `torchaudio` |
| Translation | `deep-translator` |
| LLM orchestration | `langchain`, `langchain-core`, `langchain-community`, `langchain-mistralai`, `mistralai` |
| RAG / vector store | `chromadb`, `sentence-transformers`, `langchain-huggingface`, `huggingface-hub`, `tiktoken` |
| UI | `streamlit`, `streamlit-extras`, `watchdog` |
| Export | `reportlab`, `fpdf2` |

## 🚀 Getting Started

### Prerequisites

- Python **3.10+**
- [FFmpeg](https://ffmpeg.org/download.html) installed and available on your system `PATH` (required by `pydub` / `ffmpeg-python`)
- A [Mistral AI API key](https://console.mistral.ai/)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/faizankd1/AI_Video_Agent.git
cd AI_Video_Agent

# 2. Create and activate a virtual environment
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt
```

### Configuration

Create a `.env` file in the project root:

```env
MISTRAL_API_KEY=your_mistral_api_key_here
```

### Run the app

```bash
streamlit run app.py
```

> Replace `app.py` above with your actual entry-point filename if it's different.

Then open the local URL Streamlit prints in your terminal, drop in a video link, and start asking questions.

## 📂 Project Structure

```
AI_Video_Agent/
├── app.py                 # Streamlit entry point
├── requirements.txt
├── .env                    # API keys (not committed)
└── ...                     # pipeline modules, utils, etc.
```

> This is a placeholder — swap in your real folder layout, or send it over and I'll fill this section in precisely.

## 🗺️ Roadmap

- [ ] Support additional source languages beyond Hindi
- [ ] Batch processing for multiple videos
- [ ] Export to Markdown / DOCX in addition to PDF
- [ ] Speaker diarization

## 🤝 Contributing

Contributions, issues, and feature requests are welcome. Feel free to open an issue or submit a pull request.

## 📄 License

This project is licensed under the [MIT License](LICENSE) — update this if you're using a different license.

---

<div align="center">
Built with 🐍 Python, 🦜 LangChain, and ☕
</div>