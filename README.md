# Tourist Assistant – RAG Chatbot  
Developed for the Izazov Hackathon (Red Black Tree)

## Overview
This project is a Serbian-language tourist assistant chatbot built during the Izazov Hackathon organized by Red Black Tree.  
The system uses a Retrieval-Augmented Generation (RAG) approach to answer user questions based on a custom dataset of travel arrangements.

The backend performs semantic search over a prepared corpus of travel-related text using FAISS and multilingual embeddings, then forwards relevant information to GPT-4o to generate a final response.

A Flask server exposes an API endpoint, and ngrok is used to make the service publicly available for the frontend.

---

## Features

### **RAG Pipeline**
- Embedding generation using the multilingual model  
  `paraphrase-multilingual-MiniLM-L12-v2`
- Fast semantic search with **FAISS**
- Prompt augmentation based on retrieved text chunks
- Answer generation with **OpenAI GPT-4o**

### **Flask Backend**
- `/query` endpoint for user requests  
- Chat history handling and context accumulation  
- Integration with ngrok for public access

### **Image Retrieval**
- Extracts Google search queries from generated responses
- Uses Google Custom Search API to obtain related images

### **Dataset Handling**
- Loads preprocessed text chunks from `text_corpus_chunks.jsonl`
- Loads FAISS vector index from `index.faiss`

---

## How It Works

### **1. Embedding and Retrieval**
The backend encodes the user query with MiniLM embeddings and performs similarity search using FAISS. The top-k most relevant text chunks are selected.

### **2. Prompt Construction**
Retrieved chunks are inserted into the prompt along with the latest user query and system instructions.

### **3. Response Generation**
GPT-4o receives the augmented prompt and returns the final answer in Serbian.

### **4. Image Extraction**
Any Google search links in the response are parsed to extract search terms. The backend then fetches image URLs using the Google Custom Search API.

---

## Technologies Used
- Python  
- Flask  
- FAISS  
- Sentence Transformers (MiniLM multilingual model)  
- OpenAI GPT-4o  
- Google Custom Search API  
- URLExtract  
- Requests  
- ngrok  


