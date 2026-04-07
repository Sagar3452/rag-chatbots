# 🤖 RAG Chatbots — Chat with Your PDFs

A **Retrieval-Augmented Generation (RAG)** chatbot that lets you upload PDF documents and have intelligent conversations with their content. Powered by OpenAI GPT, LangChain, and a vector database for fast semantic search.

---

## ✨ Features

- 📄 **Upload PDFs** — supports single or multiple PDF documents
- 🔍 **Semantic Search** — chunks and embeds documents for accurate retrieval
- 🧠 **GPT-Powered Answers** — uses OpenAI to generate context-aware responses
- ⚡ **Fast Retrieval** — vector database (FAISS/Chroma) for efficient similarity search
- 🔗 **LangChain Pipelines** — modular, extensible RAG chain architecture
- 🌐 **REST API** — FastAPI backend for easy integration

---

## 🏗️ Architecture

```
PDF Upload
    │
    ▼
Text Extraction & Chunking (LangChain)
    │
    ▼
Embedding Generation (OpenAI Embeddings)
    │
    ▼
Vector Store (FAISS / Chroma)
    │
    ▼
User Query ──► Similarity Search ──► Context Retrieval
                                            │
                                            ▼
                                    GPT (OpenAI LLM)
                                            │
                                            ▼
                                      Final Answer
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| LLM | OpenAI GPT (gpt-3.5-turbo / gpt-4) |
| Orchestration | LangChain |
| Vector Store | FAISS / Chroma |
| Backend API | FastAPI |
| Embeddings | OpenAI Embeddings |
| PDF Parsing | PyPDF2 / pdfplumber |

---

## 🚀 Getting Started

### Prerequisites

- Python 3.9+
- An [OpenAI API key](https://platform.openai.com/api-keys)

### 1. Clone the repository

```bash
git clone https://github.com/Sagar3452/rag-chatbots.git
cd rag-chatbots
```

### 2. Create a virtual environment

```bash
python -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Set up environment variables

Create a `.env` file in the root directory:

```env
OPENAI_API_KEY=your_openai_api_key_here
```

### 5. Run the API server

```bash
uvicorn main:app --reload
```

The API will be available at `http://localhost:8000`.

---

## 📡 API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/upload` | Upload a PDF document |
| `POST` | `/chat` | Ask a question about uploaded docs |
| `GET` | `/docs` | Interactive API documentation (Swagger UI) |

### Example: Ask a question

```bash
curl -X POST "http://localhost:8000/chat" \
  -H "Content-Type: application/json" \
  -d '{"question": "What is the main topic of the document?"}'
```

---

## 📁 Project Structure

```
rag-chatbots/
├── main.py                 # FastAPI app entry point
├── rag/
│   ├── loader.py           # PDF loading & text extraction
│   ├── chunker.py          # Text splitting logic
│   ├── embedder.py         # Embedding generation
│   ├── retriever.py        # Vector store & similarity search
│   └── chain.py            # LangChain RAG pipeline
├── requirements.txt
├── .env.example
└── README.md
```

---

## 📦 Requirements

```
openai
langchain
langchain-openai
faiss-cpu
chromadb
fastapi
uvicorn
pypdf2
python-dotenv
```

---

## 🔮 Roadmap

- [ ] Multi-document support with source attribution
- [ ] Conversation memory / chat history
- [ ] Support for DOCX, TXT, and web URLs
- [ ] Streamlit / Gradio frontend UI
- [ ] Docker deployment

---

## 🤝 Contributing

Contributions are welcome! Feel free to open issues or submit pull requests.

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/my-feature`)
3. Commit your changes (`git commit -m 'Add my feature'`)
4. Push to the branch (`git push origin feature/my-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- [LangChain](https://www.langchain.com/) for the RAG pipeline framework
- [OpenAI](https://openai.com/) for GPT and embedding models
- [FastAPI](https://fastapi.tiangolo.com/) for the backend framework
