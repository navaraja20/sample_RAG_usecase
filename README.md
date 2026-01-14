# Custom PDF Chatbot using RAG

A Retrieval-Augmented Generation (RAG) implementation for querying custom PDF documents using LangChain and OpenAI.

## Overview

This project demonstrates how to build a conversational AI chatbot that can answer questions based on the content of your PDF documents. It uses vector embeddings and semantic search to retrieve relevant information and generate accurate responses.

## Features

- **PDF Document Processing**: Load and process PDF files
- **Text Chunking**: Split documents into manageable chunks with configurable overlap
- **Vector Embeddings**: Generate embeddings using OpenAI's embedding models
- **FAISS Vector Store**: Efficient similarity search using Facebook AI Similarity Search
- **Conversational Chain**: Maintains chat history for context-aware responses
- **Custom Prompts**: Configurable question rephrasing for better retrieval

## Requirements

```bash
pip install openai
pip install langchain
pip install langchain_community
pip install tiktoken
pip install faiss-cpu
pip install pypdf
```

## Setup

1. Clone this repository
2. Install the required dependencies
3. Set your OpenAI API key in the notebook:
   ```python
   OPENAI_API_KEY = "your-api-key-here"
   ```
4. Replace the PDF path with your document:
   ```python
   pdf_reader = PyPDFLoader("path/to/your/document.pdf")
   ```

## Usage

1. Open the `custom_pdf_chatbot.ipynb` notebook
2. Run the cells sequentially to:
   - Install dependencies
   - Configure OpenAI API
   - Load and process your PDF document
   - Create vector embeddings
   - Set up the conversational retrieval chain
3. Query your document using the chatbot:
   ```python
   query = "Your question here"
   result = qa({"question": query, "chat_history": chat_history})
   print(result["answer"])
   ```

## How It Works

1. **Document Loading**: PDFs are loaded using PyPDFLoader
2. **Text Splitting**: Documents are split into chunks (1000 chars with 200 char overlap)
3. **Embedding Creation**: Text chunks are converted to vector embeddings
4. **Vector Storage**: Embeddings are stored in FAISS for efficient retrieval
5. **Query Processing**: Questions are embedded and compared against the vector store
6. **Response Generation**: Relevant chunks are retrieved and sent to OpenAI LLM for answer generation

## Configuration

- **Chunk Size**: 1000 characters (adjustable in `RecursiveCharacterTextSplitter`)
- **Chunk Overlap**: 200 characters (for context preservation)
- **LLM**: OpenAI's GPT models (via LangChain)
- **Embeddings**: OpenAI embeddings

## Example Queries

The notebook includes sample queries demonstrating:
- Vendor experience evaluation
- Financial offer analysis
- General knowledge questions with document context

## License

This project is provided as-is for educational and demonstration purposes.