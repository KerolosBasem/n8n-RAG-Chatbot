n8n RAG Chatbot

An end-to-end Retrieval-Augmented Generation (RAG) chatbot built with n8n, Google Gemini, Cohere, and a vector store. The project allows users to upload or update documents in Google Drive and then interact with an AI chatbot that answers questions based on the information contained in those documents.

🚀 Project Overview

The workflow is divided into two main parts:

1. Document Ingestion

The ingestion workflow automatically monitors a specific Google Drive folder for updated files. When a file is updated, n8n downloads the document, extracts its content, splits the text into smaller chunks, generates vector embeddings using Google Gemini Embeddings, and stores the resulting documents in an in-memory vector store.

Document metadata such as the uploader's name and creation date is also preserved, making the retrieved information more traceable.

2. RAG Chat

The chat workflow provides an interactive interface where users can ask questions about the ingested documents. An n8n AI Agent receives the user's question and searches the vector store for relevant context.

The retrieval process uses Google Gemini embeddings and Cohere reranking to improve the relevance of the retrieved information. The top relevant results are provided to the AI Agent, which uses Google Gemini as the language model to generate the final response.

🧠 RAG Approach

The chatbot follows a context-first approach. Its system prompt instructs the AI to:

Answer using the retrieved context.
Avoid unsupported assumptions or hallucinations.
Clearly state when the required information is not available.
Preserve numerical accuracy.
Handle conflicting information carefully.
Provide source information when available.

This makes the chatbot more reliable for document-based question answering.

🔄 Workflow
Google Drive
     ↓
File Updated
     ↓
Download Document
     ↓
Extract Text
     ↓
Split into Chunks
     ↓
Generate Gemini Embeddings
     ↓
Vector Store
     ↓
      ┌───────────────────┐
      │   User Question   │
      └─────────┬─────────┘
                ↓
           AI Agent
                ↓
       Vector Store Search
                ↓
         Cohere Reranker
                ↓
       Relevant Context
                ↓
       Google Gemini LLM
                ↓
          Final Answer
🛠️ Technologies
n8n – Workflow automation and orchestration
Google Drive – Document source
Google Gemini – Embeddings and chat model
Cohere – Retrieval reranking
Vector Store – Semantic document retrieval
RAG – Grounded question answering
AI Agent – Reasoning and response generation
✨ Key Features
Automated document ingestion from Google Drive
PDF text extraction
Recursive text chunking with overlap
Semantic search using vector embeddings
Cohere-based reranking
Context-grounded AI responses
Conversation memory
Source-aware responses
Protection against hallucinated information
Fully orchestrated through n8n
📌 Purpose

This project demonstrates how RAG can be implemented as an automated n8n workflow, connecting document ingestion, vector search, reranking, memory, and an LLM into a practical conversational AI system.

It can serve as a foundation for building internal knowledge assistants, document Q&A systems, company knowledge bases, support bots, and AI-powered document search applications.
