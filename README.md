
# 🎌 Anime Recommender System

A smart anime recommendation system that understands what you're looking for and suggests the perfect shows to watch next. Built with LangChain, Groq LLM, and ChromaDB.

## What It Does

Tell it what kind of anime you're in the mood for (like "light-hearted anime with school settings"), and it'll recommend three shows with detailed explanations of why each one fits your vibe.

## Tech Stack

- **LangChain** - For building the RAG pipeline
- **Groq (Llama 3.1)** - Fast LLM inference
- **ChromaDB** - Vector database for semantic search
- **HuggingFace Embeddings** - Text embeddings (all-MiniLM-L6-v2)
- **Streamlit** - Simple web interface
- **Docker + Kubernetes** - Containerization and deployment

## Project Structure

```
├── app/                    # Streamlit application
├── src/                    # Core recommendation logic
│   ├── data_loader.py     # Data preprocessing
│   ├── vector_store.py    # ChromaDB integration
│   ├── recommender.py     # LLM recommendation engine
│   └── prompt_template.py # Prompt engineering
├── pipeline/              # Pipeline orchestration
├── config/                # Configuration management
├── utils/                 # Logging and error handling
└── Dockerfile             # Container setup
```

## Getting Started

### Prerequisites

- Python 3.10+
- Groq API key (get it from [console.groq.com](https://console.groq.com))

### Installation

1. Clone the repository
```bash
git clone <your-repo-url>
cd anime-recommender
```

2. Install dependencies
```bash
pip install -e .
```

3. Set up your environment variables
```bash
# Create a .env file
echo "GROQ_API_KEY=your_api_key_here" > .env
```

4. Build the vector store (one-time setup)
```bash
python pipeline/build_pipeline.py
```

5. Run the app
```bash
streamlit run app/app.py
```

The app will be available at `http://localhost:8501`

## Docker Deployment

Build and run with Docker:
```bash
docker build -t anime-recommender .
docker run -p 8501:8501 --env-file .env anime-recommender
```

## Kubernetes Deployment

Deploy to a K8s cluster:
```bash
# Create secrets
kubectl create secret generic llmops-secrets --from-env-file=.env

# Deploy
kubectl apply -f llmops-k8s.yaml
```

## How It Works

1. **Data Processing**: Anime data is loaded and combined into searchable text chunks
2. **Vector Store**: Text is embedded and stored in ChromaDB for semantic search
3. **Retrieval**: User queries are matched against the vector store
4. **Generation**: Groq's LLM generates personalized recommendations with context

## Example Queries

- "Action anime with overpowered main character"
- "Romance anime that will make me cry"
- "Comedy anime for beginners"
- "Dark psychological thriller anime"

## Future Improvements

- [ ] Add user ratings and collaborative filtering
- [ ] Implement feedback loop for better recommendations
- [ ] Support for anime list import (MyAnimeList, AniList)
- [ ] Multi-language support

## Author

**Sanjay**

---

Built with ❤️ for anime lovers everywhere
