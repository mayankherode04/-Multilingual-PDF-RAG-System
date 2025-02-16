# Multilingual-PDF-RAG-System

## Overview
The **Multilingual-PDF-RAG-System** is an advanced **Retrieval-Augmented Generation (RAG)** pipeline designed to extract, process, and query text from multilingual PDF documents. This system leverages **OCR (Optical Character Recognition), embeddings-based retrieval, and an LLM-powered query engine** to provide structured, detailed responses based on document content.

## Features
- **Multilingual OCR Support**: Extracts text from PDFs in English, Hindi, Bengali, and Simplified Chinese.
- **Text Chunking & Embedding**: Uses **RecursiveCharacterTextSplitter** to split text into meaningful chunks and encodes them with **SentenceTransformers**.
- **FAISS Vector Indexing**: Efficient similarity search for retrieving relevant document sections.
- **LLM-Powered Querying**: Utilizes **Ollama**'s `llama3` model for generating comprehensive answers.
- **Batch PDF Processing**: Supports handling multiple PDFs efficiently.

## Dependencies
Ensure you have the following installed:
```bash
pip install fitz pytesseract pillow ollama faiss-cpu sentence-transformers langchain numpy
```

## How It Works
1. **Extract Text from PDFs**
   - Extracts direct text if available.
   - Uses **Tesseract OCR** for image-based text extraction.
2. **Chunk & Embed Text**
   - Splits text using **RecursiveCharacterTextSplitter**.
   - Generates vector embeddings using **Sentence-Transformers**.
3. **Index & Search**
   - Stores embeddings in a **FAISS index**.
   - Finds the most relevant chunks for a given query.
4. **Generate Responses**
   - Feeds retrieved context into **Llama3** to generate structured, detailed answers.

## Code Structure
```
Multilingual-PDF-RAG-System/
│── main.py                  # Main script
│── requirements.txt         # Required dependencies
│── README.md                # Project Documentation
└── data/                    # Folder for storing PDFs
```

## Usage
### 1. Place Your PDFs
Store the PDFs in the `data/` directory.

### 2. Run the System
```bash
python main.py
```

### 3. Example Queries
After extracting and indexing text, you can query the system with:
```python
queries = [
    "Provide a comprehensive summary of the document including key themes, character development, and symbolic elements.",
    "Analyze the main character's journey and its philosophical implications.",
    "Explain the document's central message and its relevance to contemporary readers.",
]
for q in queries:
    print(f"\nQuestion: {q}")
    print(f"Answer: {qa_system.get_answer(q)}\n")
    print("―" * 60)
```

## Future Enhancements
- **Add support for more languages**.
- **Enhance query performance using hybrid search**.
- **Optimize OCR processing for scanned PDFs**.
- **Integrate with web-based UI for easier querying**.






