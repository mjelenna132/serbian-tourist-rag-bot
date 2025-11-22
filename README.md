README
Overview
This project was developed for the Red Black Tree Hackathon.
The goal was to build a Serbian-language tourist assistant that can answer user questions about travel arrangements, destinations, activities, prices, and available dates. The system uses Retrieval-Augmented Generation (RAG) to combine a local knowledge base with a large language model.
The architecture consists of:
An embedding model for semantic text search
A FAISS vector index for fast similarity lookup
A tourism knowledge base stored as text chunks
An OpenAI GPT-4o model for generating natural-language answers
A small Flask server with ngrok tunneling for mobile/web access
Optional Google Custom Search for fetching related destination images
Key Features
Multilingual embeddings using the paraphrase-multilingual-MiniLM-L12-v2 model
Fast semantic search over the travel dataset using FAISS
Retrieval of the top-K relevant text chunks for each user query
Conversation handling with context memory
Generation of final answers using GPT-4o with inserted retrieved knowledge
Extraction of URLs from responses and fetching of images via Google’s Custom Search API
Flask API endpoint for external clients (/query)
Project Structure
Embeddings & Retrieval
Loads a pretrained transformer embedding model (MiniLM) from Hugging Face
Generates embeddings for user queries
Searches the FAISS index to find relevant travel information
Ranks and selects chunks based on embedding similarity scores
Only relevant chunks are forwarded to GPT-4o as context
GPT-4o Integration
GPT-4o receives:
Chat history
Retrieved knowledge snippets
User query
Produces the final answer in Serbian
Backend Server
Flask HTTP server exposing /query endpoint
Accepts JSON requests from frontend/mobile
Uses ngrok to expose a public HTTPS URL
Optionally fetches destination images using Google Custom Search API
File Loading
The system loads:
index.faiss — vector index built from preprocessed travel text
text_corpus_chunks.jsonl — aligned text chunks used for retrieval
Both files must be stored in Google Drive or local storage and are loaded at startup.
How It Works (Pipeline)
User sends a message
The message is encoded into an embedding
FAISS returns the closest text chunks
The backend prepares a combined prompt containing:
System instructions
Retrieved chunks
Current user message
GPT-4o generates the answer
The backend extracts any URLs
Google Custom Search provides image links
Final response returned to the client
Technologies Used
Python
Flask
FAISS
Hugging Face Sentence Transformers
OpenAI GPT-4o
ngrok
Google Custom Search API
If you'd like, I can also write:
A Serbian version of the README
A longer, more formal version for GitHub
A version tailored for your CV or portfolio
