# Serbian Tourist RAG Bot

Tourist Assistant — RAG Chatbot
Izazov Hackathon 2024 (Red Black Tree)
This project is an AI-powered tourist assistant developed during the Izazov Hackathon organized by Red Black Tree. It uses a Retrieval-Augmented Generation (RAG) pipeline to provide accurate travel recommendations based on a custom dataset of travel arrangements.
The system uses multilingual embeddings (supports Serbian), FAISS vector search, OpenAI GPT-4o, and Google Custom Search for fetching related images.
Features
Retrieval-Augmented Generation (RAG) with FAISS and GPT-4o
Multilingual embedding model (paraphrase-multilingual-MiniLM-L12-v2)
Semantic search over travel arrangement dataset
Flask backend with a /query endpoint
Google Custom Search API for image retrieval
Ngrok tunneling for public access
URL extraction for dynamic image queries
How It Works
1. Data Loading
The backend loads:
index.faiss (FAISS index containing all embeddings)
text_corpus_chunks.jsonl (list of dataset text chunks)
2. Semantic Retrieval (R in RAG)
The user query is encoded into an embedding.
FAISS returns the top-k most similar dataset entries.
3. Prompt Augmentation (A in RAG)
Retrieved dataset chunks are inserted into the prompt along with the user’s question.
4. Answer Generation (G in RAG)
GPT-4o receives the augmented prompt and generates the final answer.
5. Image Extraction
The backend extracts search queries from the model's output and uses Google Custom Search to fetch related images.
Technologies Used
Python (Flask)
SentenceTransformers (MiniLM multilingual model)
FAISS for vector similarity search
OpenAI GPT-4o
Google Custom Search API
Ngrok
URLExtract and Requests
