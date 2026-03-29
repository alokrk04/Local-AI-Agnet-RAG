🍕 Local Pizza Restaurant AI Agent (RAG)
A fully local, private, and free-to-run AI agent built with Python, LangChain, and Ollama. This agent uses Retrieval-Augmented Generation (RAG) to act as an expert on a pizza restaurant, answering user questions based on a local dataset of customer reviews stored in a ChromaDB vector database.

🌟 Features
100% Local & Free: No data leaves your machine. No OpenAI or Anthropic API keys required.

RAG Powered: Context-aware responses built directly from the realistic_restaurant_reviews.csv dataset.

Automated Vector Database: Automatically parses the CSV, generates embeddings, and builds a local ChromaDB vector store on the first run.

Latest Open-Source Models: Utilizes Ollama to run llama3.2 for generation and mxbai-embed-large for highly accurate vector embeddings.

🏗️ Technical Stack
Framework: LangChain

LLM: Ollama (llama3.2)

Embeddings: Ollama (mxbai-embed-large)

Vector Database: ChromaDB

Data Handling: Pandas

🚀 Getting Started
1. Prerequisites
You will need to have Ollama installed on your machine to run the local models.

Once Ollama is installed, open your terminal and pull the required models:

Bash
# Pull the LLM for text generation
ollama pull llama3.2

# Pull the embedding model for vector search
ollama pull mxbai-embed-large
2. Installation
Clone this repository (or download the files) and set up your Python environment:

Bash
# (Optional but recommended) Create a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate

# Install the required dependencies
pip install -r requirements.txt
3. Usage
You don't need to run a separate ingestion script! The database initializes itself. Just run the main application:

Bash
python main.py
What happens next?

First Run: The script (vector.py) will automatically detect if the ChromaDB database exists. If not, it will read realistic_restaurant_reviews.csv, chunk the data, generate embeddings using mxbai-embed-large, and save them to a local ./chrome_langchain_db folder.

Chat Loop: The agent will boot up and prompt you to ask questions. You can ask things like:

"What do customers say about the gluten-free options?"

"Are there any complaints about the delivery time?"

"What is the best pizza on the menu?"

Type q at any time to exit the chat.

📂 Project Structure
Plaintext
├── chrome_langchain_db/               # Auto-generated local ChromaDB directory
├── realistic_restaurant_reviews.csv   # Source dataset containing pizza reviews
├── requirements.txt                   # Python dependencies
├── vector.py                          # Database initialization and retriever setup
├── main.py                            # Main agent logic and interactive chat loop
└── README.md                          # Project documentation
🛠️ How It Works
Data Ingestion: vector.py uses Pandas to read the restaurant reviews. It concatenates the Title and Review text, and stores the Rating and Date as searchable metadata.

Vectorization: These documents are embedded using mxbai-embed-large and stored locally via Chroma.

Retrieval: When you ask a question in main.py, the retriever fetches the top 5 most relevant reviews based on your query.

Generation: LangChain formats these retrieved reviews into a prompt template and feeds them to llama3.2, which synthesizes a helpful, expert answer.
