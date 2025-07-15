Medical Chatbot using LangChain, FAISS & LLMs
This project is an intelligent medical chatbot that can understand and answer user queries by referring to domain-specific medical documents such as textbooks, research papers, and clinical guidelines. It is built using LangChain, FAISS, and powerful open-source Large Language Models (LLMs) from Hugging Face or Groq.

🔍 Purpose
The goal of this chatbot is to enable accurate, grounded, and fast information retrieval from medical literature. Instead of relying on internet-based responses or hallucinated answers from a generic AI model, this system only uses the knowledge encoded in your local documents — making it ideal for use in:

Medical education

Hospital knowledge bases

AI-driven clinical assistants

Offline/secure medical environments

⚙️ How It Works
🗂 1. Document Ingestion
Medical PDFs are loaded from a /data folder using PyPDFLoader via LangChain's DirectoryLoader. These documents are parsed and prepared for processing.

✂️ 2. Text Chunking
Long PDF texts are broken down into smaller, overlapping chunks using LangChain’s RecursiveCharacterTextSplitter. This ensures that context is preserved for better semantic understanding by the LLM.

🧠 3. Embedding Generation
Each text chunk is converted into a vector (embedding) using HuggingFace’s sentence-transformers/all-MiniLM-L6-v2. This allows the system to represent meaning numerically and perform semantic search.

💽 4. Vector Store with FAISS
The generated embeddings are stored in a FAISS vector database, enabling fast and efficient similarity-based retrieval of the most relevant text chunks.

❓ 5. Query Processing
When a user enters a medical question, the chatbot:

Searches the FAISS vector store to find the top-k most relevant chunks.

Injects them into a prompt using a custom template.

Sends this prompt to a language model (LLM) to generate a factual, concise answer.

🤖 6. Language Models (LLMs)
Supports two backends:

HuggingFace Inference API (e.g. Mistral-7B-Instruct)

Groq API (e.g. LLaMA3 or Mixtral for lightning-fast inference)

🧪 Features
✅ RAG pipeline (Retrieval-Augmented Generation)

✅ Support for offline document-based QA

✅ Context-aware answers with optional source tracing

✅ Modular and easy to extend

✅ Fast retrieval via FAISS

✅ HuggingFace and Groq support

✅ Web UI using Streamlit (if enabled)

💡 Example Use Case
User: What is the standard treatment for early-stage breast cancer?
Bot: (Based on extracted PDF context)
“The standard treatment typically involves a combination of surgery (lumpectomy or mastectomy), radiation therapy, and adjuvant systemic therapy such as hormone therapy or chemotherapy…”

