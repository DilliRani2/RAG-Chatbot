# 🤖 RAG Chatbot

An AI-powered **Retrieval-Augmented Generation (RAG) Chatbot** that answers questions using information retrieved from uploaded text documents. Built with Python, LangChain, ChromaDB, Hugging Face embeddings, Groq LLM, and Gradio.

## ✨ Features

- 📄 **Document Upload:** Upload `.txt` documents using Google Colab or the web interface.
- ✂️ **Text Chunking:** Split documents into smaller chunks using `RecursiveCharacterTextSplitter`.
- 🧠 **Semantic Search:** Generate embeddings with `sentence-transformers/all-MiniLM-L6-v2`.
- 🗄️ **Vector Database:** Store document embeddings in ChromaDB.
- 💬 **Question Answering:** Ask questions and receive answers based on retrieved document context.
- ⚡ **Groq LLM Integration:** Generate responses using `openai/gpt-oss-120b` through Groq.
- 🔍 **Retriever Comparison:** Compare answers using different retrieval settings, including `k=1` and `k=3`.
- 📝 **Custom Prompt Instructions:** Modify the system prompt and experiment with response behavior.
- 📚 **Context Preview:** Inspect the document chunks retrieved for a question.
- 🎨 **Interactive Web Interface:** Use a Gradio interface with document chat, example questions, and title customization.

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Google Colab | Development and execution environment |
| LangChain | RAG pipeline and prompt orchestration |
| ChromaDB | Vector storage and similarity search |
| Hugging Face Embeddings | Document and query vector representations |
| Groq | Large language model inference |
| Gradio | Interactive chatbot web interface |

## 🏗️ How It Works

1. **Load a document:** Upload a text file and extract its contents.
2. **Split the text:** Divide the document into chunks of 300 characters with 50 characters of overlap.
3. **Create embeddings:** Convert the text chunks into vector representations.
4. **Store vectors:** Save the embeddings in a ChromaDB collection.
5. **Retrieve context:** Search for relevant chunks based on the user's question.
6. **Generate an answer:** Send the retrieved context and question to the Groq-hosted LLM.
7. **Display the response:** Present the answer through the notebook or Gradio interface.

## 🚀 Getting Started

### Option 1: Run in Google Colab

1. Open the notebook `Rag_project_.ipynb` in Google Colab.
2. Run the dependency installation cell.
3. Add your `GROQ_API_KEY` to Google Colab Secrets.
4. Upload a `.txt` document when prompted.
5. Run the cells in order to create the embeddings, vector database, and RAG chain.
6. Test the chatbot with your own questions.
7. Run the Gradio application cell to launch the interactive interface.

### Option 2: Install Dependencies Locally

Install the required packages:

```bash
pip install -U langchain langchain-core langchain-groq langchain-community langchain-chroma langchain-huggingface langchain-text-splitters chromadb sentence-transformers gradio
```

Configure your Groq API key using an environment variable:

**Windows PowerShell**

```powershell
$env:GROQ_API_KEY="your_groq_api_key"
```

**Linux/macOS**

```bash
export GROQ_API_KEY="your_groq_api_key"
```

Create a Python application that initializes the language model and embeddings, then runs the RAG pipeline and Gradio interface.

Get your API key from the [Groq Console](https://console.groq.com/).

## ⚙️ Configuration

### Text Chunking

```python
text_splitter = RecursiveCharacterTextSplitter(
    chunk_size=300,
    chunk_overlap=50
)
```

### Embedding Model

```python
embeddings = HuggingFaceEmbeddings(
    model_name="sentence-transformers/all-MiniLM-L6-v2"
)
```

### Vector Database

```python
vectorstore = Chroma.from_documents(
    documents=chunks,
    embedding=embeddings,
    collection_name="rag_documents"
)
```

### Language Model

```python
llm = ChatGroq(
    model="openai/gpt-oss-120b",
    api_key=GROQ_API_KEY,
    temperature=0
)
```

Ensure the model is available to your Groq account before running the notebook.

## 🧪 Experiments

The project includes experiments for exploring the RAG pipeline:

**1. Upload a different document**

Test the chatbot with another `.txt` document and evaluate whether it answers questions using the new content.

**2. Compare retrieval settings**

Compare `k=1` with `k=3` to observe how the number of retrieved chunks affects the answer.

**3. Ask sample questions**

Try questions about the document's main topic, key points, important concepts, examples, and summary.

**4. Modify prompt instructions**

Change the prompt to test how instructions affect the generated responses.

**5. Customize the interface**

Modify the webpage title and configure example questions.

## 📁 Project Structure

```text
rag-chatbot/
├── Rag_project_.ipynb
└── README.md
```

The notebook contains the installation steps, document-processing pipeline, embedding setup, vector database, RAG chain, sample query, and Gradio interface.

## 🔐 Security

- Store API keys in Colab Secrets or environment variables.
- Never commit API keys or credentials to GitHub.
- Avoid uploading confidential documents to a publicly accessible application.
- Review access controls before deploying the chatbot publicly.

## ⚠️ Limitations

- The current document-processing workflow focuses on `.txt` files.
- Answers depend on document quality, retrieval relevance, and the language model.
- The model may produce inaccurate answers, so important information should be verified against the source document.
- Retrieving more chunks does not always improve answer quality.
- The Gradio interface requires the notebook's language model and embedding variables to be initialized before it runs.

## 🔮 Future Enhancements

- Support PDF and DOCX documents.
- Display source citations alongside answers.
- Support multiple documents in a single session.
- Add persistent chat history.
- Improve retrieval with reranking and configurable chunk sizes.
- Deploy the chatbot with authentication and secure storage.

## 👩‍💻 Author

**Dilli Rani**

- GitHub: [DilliRani2](https://github.com/DilliRani2)
