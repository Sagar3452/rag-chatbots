# 🏥 MediBot — AI-Powered Medical Chatbot

An **End-to-End AI-Powered Medical Chatbot** built using **LLMs, Pinecone, and LangChain** to provide accurate health information, symptom analysis, and context-aware responses with efficient data retrieval and scalable deployment.

> ⚠️ **Disclaimer:** This chatbot is for informational purposes only and does not replace professional medical advice, diagnosis, or treatment. Always consult a qualified healthcare provider.

---

## ✨ Features

- 🩺 **Symptom Analysis** — understands and interprets user-described symptoms
- 💬 **Context-Aware Responses** — maintains conversation context for follow-up questions
- 📄 **Medical Document Q&A** — retrieves accurate answers from medical PDFs & literature
- 🔍 **Semantic Search** — Pinecone vector database for fast, accurate retrieval
- 🧠 **LLM-Powered** — GPT-based language model for natural, human-like responses
- 🔗 **LangChain Pipelines** — modular and extensible RAG chain architecture
- 🌐 **REST API** — FastAPI backend for scalable deployment

---

## 🏗️ Architecture

```
Medical PDFs / Documents
        │
        ▼
Text Extraction & Chunking (LangChain)
        │
        ▼
Embedding Generation (OpenAI Embeddings)
        │
        ▼
Vector Store (Pinecone)
        │
        ▼
User Query ──► Similarity Search ──► Context Retrieval
                                            │
                                            ▼
                                    LLM (OpenAI GPT)
                                            │
                                            ▼
                             Accurate Medical Response
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| LLM | OpenAI GPT (gpt-3.5-turbo / gpt-4) |
| Orchestration | LangChain |
| Vector Store | Pinecone |
| Backend API | FastAPI |
| Embeddings | OpenAI Embeddings |
| PDF Parsing | PyPDF2 / pdfplumber |
| Environment | Python 3.9+ |

---

## 🚀 Getting Started

### Prerequisites

- Python 3.9+
- An [OpenAI API key](https://platform.openai.com/api-keys)
- A [Pinecone API key](https://www.pinecone.io/)

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
PINECONE_API_KEY=your_pinecone_api_key_here
PINECONE_ENV=your_pinecone_environment
PINECONE_INDEX_NAME=medical-chatbot
```

### 5. Ingest medical documents into Pinecone

```bash
python store_index.py
```

### 6. Run the API server

```bash
uvicorn app:app --reload
```

The API will be available at `http://localhost:8000`.

---

## 📡 API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/upload` | Upload medical PDF documents |
| `POST` | `/chat` | Ask a health or symptom-related question |
| `GET` | `/history` | Retrieve conversation history |
| `GET` | `/docs` | Interactive Swagger UI documentation |

### Example: Ask a medical question

```bash
curl -X POST "http://localhost:8000/chat" \
  -H "Content-Type: application/json" \
  -d '{"question": "What are the symptoms of Type 2 diabetes?"}'
```

### Example Response

```json
{
  "answer": "Common symptoms of Type 2 diabetes include increased thirst, frequent urination, fatigue, blurred vision, and slow-healing wounds. It is recommended to consult a healthcare provider for proper diagnosis.",
  "sources": ["medical_handbook.pdf", "diabetes_guide.pdf"]
}
```

---

## 📁 Project Structure

```
rag-chatbots/
├── app.py                  # FastAPI app entry point
├── store_index.py          # Script to embed & upload docs to Pinecone
├── src/
│   ├── helper.py           # PDF loading & text extraction
│   └── prompt.py           # LLM prompt templates
├── research/
│   └── trials.ipynb        # Experimentation notebook
├── data/                   # Medical PDF documents
├── requirements.txt
├── .env.example
├── .gitignore
└── README.md
```

---

## 📦 Requirements

```
openai
langchain
langchain-openai
langchain-pinecone
pinecone-client
fastapi
uvicorn
pypdf2
python-dotenv
sentence-transformers
tiktoken
```

---

## 💡 How It Works

1. **Ingestion** — Medical PDFs are loaded, split into chunks, and embedded using OpenAI Embeddings
2. **Storage** — Embeddings are stored in Pinecone for fast vector similarity search
3. **Retrieval** — When a user asks a question, the most relevant chunks are retrieved from Pinecone
4. **Generation** — The retrieved context + user question is passed to GPT, which generates an accurate, context-aware response

---

## 🔮 Roadmap

- [ ] Add conversation memory for multi-turn dialogues
- [ ] Support multilingual medical queries
- [ ] Integrate a Streamlit / React frontend UI
- [ ] Add user authentication
- [ ] Docker + cloud deployment (AWS / GCP / Azure)
- [ ] Support DOCX and web-scraped medical sources

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
- [Pinecone](https://www.pinecone.io/) for scalable vector storage
- [OpenAI](https://openai.com/) for GPT and embedding models
- [FastAPI](https://fastapi.tiangolo.com/) for the backend framework
