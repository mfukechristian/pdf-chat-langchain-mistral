# PDF Chat with RAG (Retrieval-Augmented Generation)

This is a simple chatbot that lets you **upload a PDF and ask questions about it**. It uses **Mistral AI + LangChain** to read your PDF, store the content in memory, and answer your questions using RAG (Retrieval-Augmented Generation).

---

## Features

- Upload any PDF file
- Text is split and embedded using **MistralAI embeddings**
- Store embeded chunks in memory (vector store)
- Ask questions, get context-aware answers

---

## Setup Instructions

### 1. Create a Virtual Environment (optional but recommended)

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 2. Install Dependencies

Install the necessary packages:

```bash
pip install langchain
pip install langchain_mistralai
pip install python-dotenv
pip install langchain_community
pip install pypdf
pip install gradio
```

### 3. Add Your Mistral API Key

Create a `.env` file in your project folder and add:

```
MISTRAL_API_KEY=your_mistral_api_key_here
```

Then, load it in your code:

```python
from dotenv import load_dotenv
import os

load_dotenv()
api_key = os.getenv("MISTRAL_API_KEY")
```

Make sure `api_key` is available before running the chatbot.

---

## 🧠 How It Works (Behind the Scenes)

1. You upload a PDF.
2. The PDF is **read and split** into smaller text chunks.
3. Each chunk is **embedded** using `MistralAIEmbeddings`.
4. These embeddings are stored in an **in-memory vector store**.
5. When you ask a question:

   - The app retrieves relevant chunks from memory.
   - It passes them into a prompt with your question.
   - Mistral generates a response based on that context.

---

## ▶️ Running the App

Run the Python file. A Gradio interface will launch in your browser where you can:

1. Upload a PDF
2. Click "Embed PDF"
3. Ask questions in natural language

---

## ✅ Example Use Cases

- Understand research papers
- Ask questions about contracts
- Summarize long PDFs
