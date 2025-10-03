# YouTube Synthesizer

YouTube Synthesizer is a Streamlit-based web application that transforms any YouTube video into key educational assets: concise notes, important topics, and a chatbot for video-based Q&A, with support for podcasts. Just provide a YouTube link and the video language—YouTube Synthesizer does the rest!

## Features

- **Transcript Extraction**: Fetches full transcripts from YouTube videos in a chosen language.
- **Translation**: Automatically translates transcripts to English if the original video is in another language.
- **Important Topics Extraction**: Identifies and summarizes the five most important topics discussed in the video.
- **Notes Generation**: Produces detailed notes based on the video transcript for easy review and study.
- **Video Chatbot**: Allows users to interact with the video content via a chatbot using Retrieval-Augmented Generation (RAG) on the transcript.
- **Podcast Generation**: (Optional/Planned) The app is designed to support audio podcast creation from transcripts.
- **Intuitive UI**: Built with Streamlit, offering a sidebar for inputs and a main area displaying results.

## How It Works

1. **Input**: Paste a YouTube video URL and specify the language code.
2. **Choose Task**: Select "Notes For You" to get important topics and detailed notes, or "Chat with Video" to enable the chatbot.
3. **Processing**:
    - The app extracts and translates (if needed) the video transcript.
    - For notes: Extracts key topics and generates comprehensive notes.
    - For chat: Segments transcript, creates a vector store, and allows natural-language Q&A on video content.
4. **Output**: View the extracted topics and notes or chat interactively with the video content.

## Tech Stack

- **Language**: Python (100%)
- **Framework**: Streamlit (for the web interface)
- **AI/LLM**: Google Gemini (via `langchain-google-genai` and `ChatGoogleGenerativeAI`)
- **Embeddings & RAG**: LangChain, Chroma vector store
- **YouTube Transcript Extraction**: `youtube-transcript-api`
- **Environment Management**: `python-dotenv`
- **Other Dependencies**: `gtts`, `sentence-transformers`, `rapidocr-onnxruntime`, `pysqlite3-binary`, and more.

See [`requirements.txt`](https://github.com/imswatisinha/YouTube_Synthesizer/blob/d7de0eaa69faecdcb1202c65777bab6de0d92d8c/requirements.txt) for a full list.

## Live Link
https://youtubesynthesizer-wfstkfj2cd787cajyetcf5.streamlit.app/

## Main Files

- [`app.py`](https://github.com/imswatisinha/YouTube_Synthesizer/blob/d7de0eaa69faecdcb1202c65777bab6de0d92d8c/app.py): Streamlit app logic and UI.
- [`supporting_functions.py`](https://github.com/imswatisinha/YouTube_Synthesizer/blob/d7de0eaa69faecdcb1202c65777bab6de0d92d8c/supporting_functions.py): Core functions for video processing, LLM interactions, and RAG.
- [`requirements.txt`](https://github.com/imswatisinha/YouTube_Synthesizer/blob/d7de0eaa69faecdcb1202c65777bab6de0d92d8c/requirements.txt): All dependencies.

## Usage

1. Clone the repository:
    ```bash
    git clone https://github.com/imswatisinha/YouTube_Synthesizer.git
    cd YouTube_Synthesizer
    ```
2. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```
3. Run the app:
    ```bash
    streamlit run app.py
    ```
4. Open your browser to the provided local address and start synthesizing YouTube videos!

## License

MIT License. See [LICENSE](LICENSE) for details.

---

> This README was generated based on the available code and may not include all features. For the latest updates, visit the [GitHub repository](https://github.com/imswatisinha/YouTube_Synthesizer).
