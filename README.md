# Remedy-Relay
Remedy Relay is a web-based medical assistant chatbot application designed to provide concise and reliable answers to medical queries. It leverages advanced language models and vector search to retrieve and generate responses based on uploaded medical documents.

## Features

- Interactive chatbot interface for medical question answering
- Uses Gemini (Google Generative AI) for response generation
- Vector search powered by Pinecone for efficient document retrieval
- PDF document ingestion and chunking for context-aware answers
- Modern, responsive web UI built with Flask and Bootstrap

## Prerequisites

- Python 3.10 or higher
- pip (Python package manager)
- Pinecone account and API key
- Google Generative AI (Gemini) API key

## Installation

1. **Clone the Repository**

	```bash
	git clone https://github.com/Vidhi-bhutia/Remedy-Relay.git
	cd Remedy-Relay
	```

2. **Set Up the Python Environment**

	It is recommended to use a virtual environment:

	```bash
	python -m venv venv
	source venv/bin/activate  # On Windows: venv\Scripts\activate
	```

3. **Install Dependencies**

	Install all required Python packages:

	```bash
	pip install -r requirements.txt
	```

4. **Configure Environment Variables**

	Create a `.env` file in the project root directory and add your API keys:

	```env
	PINECONE_API_KEY=your-pinecone-api-key
	GOOGLE_API_KEY=your-gemini-api-key
	```

	Replace `your-pinecone-api-key` and `your-gemini-api-key` with your actual credentials.

5. **Prepare Data**

	Place your medical PDF documents in the `data/` directory. The application will automatically ingest and process these files.

## Usage

1. **Start the Application**

	Run the Flask app:

	```bash
	python app.py
	```

	The application will be available at `http://localhost:8080/` by default.

2. **Interact with the Chatbot**

	- Open your browser and navigate to `http://localhost:8080/`.
	- Type your medical question in the chat interface and receive concise, context-aware answers.

## Project Structure

```
Remedy-Relay/
│
├── app.py                  # Main Flask application
├── requirements.txt        # Python dependencies
├── setup.py                # (Optional) Setup script
├── template.sh             # (Optional) Shell script template
├── .env                    # Environment variables (not committed)
│
├── data/                   # Directory for PDF documents
│   └── book.pdf            # Example PDF
│
├── src/                    # Source code
│   ├── __init__.py
│   ├── helper.py           # Embedding and utility functions
│   └── prompt.py           # Prompt templates
│
├── research/               # Notebooks and experiments
│   └── trials.ipynb
│
├── templates/              # HTML templates
│   └── chat.html           # Chatbot UI
│
└── remedy_relay.egg-info/  # Package metadata (auto-generated)
```

## How It Works

1. **Document Ingestion**: PDF files in the `data/` directory are loaded and split into manageable text chunks.
2. **Embedding Generation**: Each chunk is embedded using a sentence transformer model.
3. **Vector Indexing**: Embeddings are stored in Pinecone for fast similarity search.
4. **Retrieval-Augmented Generation**: When a user asks a question, relevant document chunks are retrieved and passed to the Gemini model to generate a concise answer.

## Customization

- To use a different language model, update the model name in `app.py` where `ChatGoogleGenerativeAI` is initialized.
- To adjust the number of retrieved document chunks, modify the `search_kwargs` parameter in the retriever setup.

## Troubleshooting

- Ensure your API keys are correct and active.
- If you encounter model errors, verify the model name and your access permissions for Gemini.
- For dependency issues, ensure all packages in `requirements.txt` are installed.

## License

This project is provided for educational and research purposes. Please consult the repository owner for licensing details if you intend to use it commercially.

## Acknowledgements

- [LangChain](https://github.com/langchain-ai/langchain)
- [Pinecone](https://www.pinecone.io/)
- [Google Generative AI (Gemini)](https://ai.google.dev/)
- [Flask](https://flask.palletsprojects.com/)