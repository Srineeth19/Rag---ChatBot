# Rag---ChatBot

A Retrieval-Augmented Generation (RAG) chatbot that answers questions over your own
documents. Instead of relying only on what a language model memorized, it first retrieves
the most relevant passages from a vector database and passes them to the LLM as context,
which gives grounded, context-aware answers and reduces hallucinations.

## Features
- Document ingestion pipeline (load, clean, chunk)
- Embedding generation and storage in a FAISS vector index
- Semantic search to retrieve the most relevant chunks for each query
- LLM responses grounded in the retrieved context (via llama.cpp)
- Interactive chat interface built with Streamlit
- Containerized with Docker for reproducible setup

## How It Works
1. **Ingest:** documents are loaded and split into overlapping chunks.
2. **Embed:** each chunk is converted to a vector embedding and indexed in FAISS.
3. **Retrieve:** the user's question is embedded and the top-k similar chunks are fetched.
4. **Generate:** the question and retrieved chunks are combined into a prompt, and the LLM
   produces an answer based on that context.

## Tech Stack
Python, LangChain, FAISS, llama.cpp, Streamlit, Docker

## Project Structure

├── data/  

├── ingest.py        # chunking + embedding + index creation

├── app.py           # Streamlit chat UI

├── Dockerfile

├── requirements.txt

└── README.md


### Prerequisites
- Python 3.10+
- Docker (optional)
- A GGUF model file for llama.cpp

### Local Setup
git clone https://github.com/Srineeth19/Rag---ChatBot.git
cd Rag---ChatBot
pip install -r requirements.txt
python ingest.py
streamlit run app.py

### Docker
docker build -t rag-chatbot .
docker run -p 8501:8501 rag-chatbot

The app runs at http://localhost:8501.

## Usage
1. Add your documents to the `data/` folder.
2. Run the ingestion script to build the vector index.
3. Open the app and ask questions about your documents.

## Future Improvements
- Source citations alongside answers
- Support for more file types (PDF, DOCX, CSV)
- Conversation memory and query rewriting
- Evaluation of retrieval quality

## Author
**M Srineeth Reddy**: [GitHub](https://github.com/Srineeth19) | srineeth1915@gmail.com
