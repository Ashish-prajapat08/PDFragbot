
# 📚 Modular RAG PDF Chatbot

A modular **Retrieval-Augmented Generation (RAG)** chatbot that lets you upload PDFs and interact with an AI assistant. The assistant answers queries based on your documents using a **FastAPI backend**, **Streamlit frontend**, **ChromaDB vector store**, and **Groq’s LLaMA3 model**.

---

## 🏗 Project Structure

```
PDFragbot/
├── client/         # Streamlit Frontend
│   ├── components/
│   │   ├── chatUI.py
│   │   ├── history_download.py
│   │   └── upload.py
│   ├── utils/
│   │   └── api.py
│   ├── app.py
│   └── config.py
├── server/         # FastAPI Backend
│   ├── modules/
│   │   ├── load_vectorstore.py
│   │   ├── llm.py
│   │   ├── pdf_handler.py
│   │   └── query_handlers.py
│   ├── logger.py
│   ├── main.py
│   ├── uploaded_pdfs/   # auto-created after run
│   └── chroma_store/    # auto-created after run
└── README.md
```

---

## ✨ Features

* 📂 Upload and parse PDFs
* 🧩 Chunk documents + generate embeddings (HuggingFace)
* 🗄 Store embeddings in **ChromaDB**
* 🤖 Query docs with **Groq LLaMA3**
* ⚡ Microservice design → **FastAPI backend + Streamlit frontend**

---

## 🔎 How RAG Works

**Retrieval-Augmented Generation (RAG)** = LLM + External Knowledge.

1. Documents are chunked and embedded → stored in a vector database (ChromaDB).
2. At query time, relevant chunks are retrieved.
3. LLaMA3 combines the query + retrieved context → generates accurate, context-aware answers.

---

## 🚀 Getting Started

### 1. Clone Repository

```bash
git clone https://github.com/Ashish-prajapat08/PDFragbot.git
cd ragbot2.0
```

### 2. Setup Backend (FastAPI)

```bash
cd server
python -m venv venv
source venv/bin/activate    # Windows: venv\Scripts\activate
pip install -r requirements.txt

# Add your Groq API Key
echo "GROQ_API_KEY=your_api_key_here" > .env

# Run FastAPI server
uvicorn main:app --reload
```

### 3. Setup Frontend (Streamlit)

```bash
cd ../client
pip install -r requirements.txt
streamlit run app.py
```

---

## 🌐 API Endpoints

* `POST /upload_pdfs/` → Upload PDFs & build vectorstore
* `POST /ask/` → Query PDFs & get AI response

👉 Test via **Postman** or directly from the Streamlit client.

---

## 🛠 Roadmap

* [ ] Add authentication
* [ ] Dockerize frontend & backend
* [ ] Support more file formats (DOCX, TXT, etc.)

---

⚡ With this modular design, you can easily extend the chatbot with new features, models, or storage backends.

