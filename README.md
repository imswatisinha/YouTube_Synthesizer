# 🎬 VidSynth AI - YouTube Content Synthesizer

VidSynth AI is an intelligent YouTube video analyzer that transforms video content into actionable insights. It extracts transcripts from YouTube videos, generates comprehensive notes, identifies key topics, and provides an interactive chatbot interface to query video content using advanced AI technologies.

## ✨ Features

### 🎯 Core Capabilities
- **Transcript Extraction**: Automatically fetches transcripts from YouTube videos in multiple languages
- **Multi-language Support**: Processes videos in various languages (English, Hindi, Spanish, French, etc.) with automatic translation to English
- **Important Topics Extraction**: Identifies and summarizes the 5 most important topics discussed in the video
- **Smart Note Generation**: Creates well-structured, concise notes with bullet points and key takeaways
- **Interactive Chat**: Ask questions about the video content using an intelligent RAG (Retrieval-Augmented Generation) chatbot
- **Vector Store Search**: Uses semantic search to find relevant content within video transcripts

### 🎨 User Interface
- Clean and intuitive Streamlit-based web interface
- Sidebar for easy input configuration
- Real-time processing status updates
- Interactive chat interface with conversation history

## 🛠️ Tech Stack

### **Frontend Framework**
- **Streamlit**: Web application framework for creating the interactive UI

### **AI & Machine Learning**
- **Google Generative AI (Gemini)**: 
  - Model: `gemini-2.5-flash-lite`
  - Used for transcript translation, topic extraction, and note generation
- **LangChain**: Framework for building LLM-powered applications
  - `langchain-google-genai`: Google Generative AI integration
  - `langchain-core`: Core LangChain components for prompt templates
  - `langchain-text-splitters`: Text chunking for efficient processing
  - `langchain-chroma`: Vector store integration
  - `langchain_community`: Community-contributed components
  - `langchain_experimental`: Experimental features

### **Vector Database & Embeddings**
- **Chroma**: Vector database for storing and retrieving document embeddings
- **Google Generative AI Embeddings**: Model `embedding-001` for creating semantic embeddings
- **Sentence Transformers**: Library for sentence and text embeddings

### **YouTube Integration**
- **youtube-transcript-api**: Fetches transcripts from YouTube videos (version 1.2.2)

### **Utilities & Dependencies**
- **python-dotenv**: Environment variable management for API keys
- **pysqlite3-binary**: SQLite database support (required for Chroma on certain platforms)
- **requests**: HTTP library for making API calls
- **gtts**: Google Text-to-Speech (for potential audio features)
- **pypdf**: PDF processing capabilities
- **rapidocr-onnxruntime**: OCR support using ONNX Runtime
- **langchainhub**: LangChain prompt hub integration

### **Programming Language**
- **Python 3.x**: Core programming language

## 📋 Prerequisites

Before running the application, ensure you have:
- Python 3.8 or higher installed
- Google Generative AI API key (Gemini API access)
- Internet connection for API calls and YouTube access

## 🚀 Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/imswatisinha/YouTube_Synthesizer.git
   cd YouTube_Synthesizer
   ```

2. **Install required dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables**
   
   Create a `.env` file in the root directory and add your Google Generative AI API key:
   ```
   GOOGLE_API_KEY=your_google_api_key_here
   ```

   To obtain a Google Generative AI API key:
   - Visit [Google AI Studio](https://makersuite.google.com/app/apikey)
   - Sign in with your Google account
   - Create a new API key

## 💻 Usage

1. **Start the application**
   ```bash
   streamlit run app.py
   ```

2. **Access the web interface**
   - The application will open in your default browser
   - If not, navigate to `http://localhost:8501`

3. **Use the application**

   **For Note Generation:**
   - Paste a YouTube video URL in the sidebar
   - Enter the video language code (e.g., `en` for English, `hi` for Hindi, `es` for Spanish)
   - Select "Notes For You" option
   - Click "✨ Start Processing"
   - View the important topics and generated notes

   **For Interactive Chat:**
   - Paste a YouTube video URL in the sidebar
   - Enter the video language code
   - Select "Chat with Video" option
   - Click "✨ Start Processing"
   - Wait for the video to be processed and vectorized
   - Start asking questions about the video content in the chat interface

## 🔧 How It Works

### Architecture Overview

1. **Transcript Extraction**
   - Extracts video ID from YouTube URL using regex
   - Fetches transcript using YouTube Transcript API
   - Supports multiple language codes

2. **Language Processing**
   - Detects non-English transcripts
   - Translates content to English using Google Gemini AI
   - Preserves context, tone, and meaning

3. **Content Analysis** (Notes Mode)
   - Identifies 5 key topics using AI prompts
   - Generates structured notes with bullet points
   - Organizes content into clear sections

4. **RAG-based Chat** (Chat Mode)
   - Splits transcript into chunks (10,000 chars with 1,000 char overlap)
   - Creates embeddings using Google's embedding model
   - Stores embeddings in Chroma vector database
   - Performs similarity search for user queries
   - Generates contextual responses using retrieved information

## 📁 Project Structure

```
YouTube_Synthesizer/
│
├── app.py                      # Main Streamlit application
├── supporting_functions.py     # Core functionality and helper functions
├── requirements.txt            # Project dependencies
├── .env                        # Environment variables (create this)
└── README.md                   # Project documentation
```

## 🔑 Key Functions

### `supporting_functions.py`
- `extract_video_id(url)`: Extracts YouTube video ID from URL
- `get_transcript(video_id, language)`: Fetches transcript from YouTube
- `translate_transcript(transcript)`: Translates non-English content to English
- `get_important_topics(transcript)`: Extracts 5 key topics from transcript
- `generate_notes(transcript)`: Creates structured notes
- `create_chunks(transcript)`: Splits text into processable chunks
- `create_vector_store(docs)`: Creates vector embeddings and stores in Chroma
- `rag_answer(question, vectorstore)`: Retrieves relevant context and generates answers

## ⚠️ Important Notes

- The application requires a valid Google Generative AI API key
- Processing time varies based on video length and transcript size
- Translation may take additional time for non-English videos
- Large videos may require more processing time for vector store creation
- Internet connection is required for all operations

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the issues page or submit a pull request.

## 📝 License

This project is open source and available for educational and personal use.

## 👥 Author

**Swati Sinha**
- GitHub: [@imswatisinha](https://github.com/imswatisinha)

## 🙏 Acknowledgments

- Google Generative AI for powerful language models
- LangChain for the excellent AI framework
- Streamlit for the intuitive UI framework
- YouTube Transcript API for transcript extraction capabilities

---

**Note**: Make sure to keep your API keys secure and never commit them to version control. Always use environment variables for sensitive information.