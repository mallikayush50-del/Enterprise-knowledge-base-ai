<<<<<<< HEAD
# Enterprise Knowledge Base AI

An AI-powered **Retrieval-Augmented Generation (RAG)** application built with Python, Streamlit, LangChain, OpenAI, and Chroma. It allows users to upload company documents and ask questions based on their content.

The application retrieves relevant document passages and uses an OpenAI language model to generate answers grounded in the retrieved information.

## Features

- **Document Upload:** Upload multiple PDF, DOCX, and TXT files.
- **Document Processing:** Extract text and preserve source metadata, including PDF page numbers.
- **Text Chunking:** Split documents into smaller chunks for efficient retrieval.
- **Semantic Search:** Use OpenAI embeddings to find relevant document passages.
- **Vector Database:** Store and search document embeddings using Chroma.
- **AI-Powered Answers:** Generate answers using the retrieved document context.
- **Source Information:** Display source filenames, PDF page numbers, and retrieved text passages.
- **Knowledge Base Management:** Build and clear the knowledge base through the Streamlit interface.
- **Error Handling:** Display errors encountered during document processing and knowledge base creation.
- **Context-Grounded Responses:** Instruct the language model not to invent company policies or facts unsupported by the retrieved documents.

## Tech Stack

| Technology | Purpose |
|---|---|
| Python | Application logic |
| Streamlit | Web interface |
| LangChain | Document processing, retrieval, and prompt management |
| OpenAI API | Text embeddings and answer generation |
| Chroma | Vector database and similarity search |
| PyPDF | PDF document loading |
| Docx2txt | DOCX document loading |
| python-dotenv | Loading environment variables |

## Project Structure

```text
enterprise-knowledge-base-ai/
├── app.py
├── requirements.txt
├── .env
├── .gitignore
└── README.md
```

- `app.py` — Contains the document-processing pipeline, vector database, retrieval logic, answer generation, and Streamlit interface.
- `requirements.txt` — Lists the Python packages required by the application.
- `.env` — Stores the OpenAI API key locally.
- `.gitignore` — Specifies files and directories Git should ignore.
- `README.md` — Provides project documentation and setup instructions.

## Prerequisites

Before running the application, install:

- Python
- An OpenAI API key with access to the configured embedding and chat models
- Git, if cloning the project from a repository

## Installation and Setup

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd enterprise-knowledge-base-ai
```

Replace `<your-repository-url>` with your actual repository URL.

### 2. Create a virtual environment

```bash
python -m venv .venv
```

### 3. Activate the virtual environment

**Windows PowerShell:**

```powershell
.venv\Scripts\Activate.ps1
```

**macOS/Linux:**

```bash
source .venv/bin/activate
```

### 4. Install dependencies

```bash
python -m pip install -r requirements.txt
```

The dependencies should include the packages used by the application:

```text
streamlit
python-dotenv
langchain-community
langchain-core
langchain-openai
langchain-text-splitters
langchain-chroma
pypdf
docx2txt
```

### 5. Configure your OpenAI API key

Create a `.env` file in the project root directory, alongside `app.py`.

Add the following line:

```text
OPENAI_API_KEY=your_actual_api_key
```

Replace `your_actual_api_key` with your own OpenAI API key.

Keep your API key private and never commit your `.env` file to Git.

### 6. Run the application

```bash
python -m streamlit run app.py
```

Open the local URL shown in your terminal. The default is usually:

```text
http://localhost:8501
```

## How to Use

1. Start the Streamlit application.
2. Upload one or more PDF, DOCX, or TXT documents.
3. Click **Build Knowledge Base**.
4. Wait for the documents to be processed and indexed.
5. Enter a question in the question input field.
6. Click **Get Answer**.
7. Read the generated answer and inspect the displayed sources to review the supporting passages.
8. Click **Clear Knowledge Base** when you want to remove the current knowledge base from the application session.

## How It Works

The application follows a Retrieval-Augmented Generation workflow.

1. **Upload:** Users select supported company documents.
2. **Extract:** LangChain document loaders extract the document text.
3. **Chunk:** `RecursiveCharacterTextSplitter` divides the text into chunks of 1,000 characters, with a 200-character overlap.
4. **Embed:** The OpenAI `text-embedding-3-small` model converts text into vector embeddings.
5. **Store:** Chroma stores the chunks and embeddings for similarity search.
6. **Retrieve:** The application retrieves the four most relevant chunks by default for each question.
7. **Generate:** The `gpt-4.1-mini` model uses the retrieved context to generate an answer.
8. **Display:** Streamlit presents the answer and the retrieved source passages.

## Configuration

The application uses the following settings in `app.py`:

| Setting | Value | Description |
|---|---|---|
| `EMBEDDING_MODEL` | `text-embedding-3-small` | Model used to create embeddings |
| `LLM_MODEL` | `gpt-4.1-mini` | Model used to generate answers |
| `CHUNK_SIZE` | `1000` | Maximum chunk size configured for text splitting |
| `CHUNK_OVERLAP` | `200` | Overlap between adjacent text chunks |
| `TOP_K` | `4` | Number of document chunks retrieved per question |
| `SUPPORTED_EXTENSIONS` | `.pdf`, `.docx`, `.txt` | Supported file extensions |

You can adjust these settings in `app.py` to experiment with different chunk sizes, overlap amounts, and retrieval counts.

## Security Considerations

- Never commit API keys or confidential company documents to version control.
- Add `.env` and `.venv/` to `.gitignore`.
- Upload only documents you are authorized to process using the configured services.
- Treat AI-generated answers as potentially incomplete or inaccurate.
- Verify important company policies against authoritative documents.

## Limitations

- Answer quality depends on the content and quality of the uploaded documents and retrieved passages.
- The model may not answer correctly if the relevant information is missing or not retrieved.
- API calls may incur costs depending on your OpenAI usage.
- Chroma is created using `Chroma.from_documents()` without a persistent storage directory, so the knowledge base is not configured to survive application restarts.
- Clearing the knowledge base removes it from the current Streamlit session; it does not delete the original files from the user's computer.
- The current implementation does not provide user authentication or role-based document access.

## Future Improvements

- Persistent vector storage.
- Conversation history.
- Improved relevance filtering and retrieval evaluation.
- Document management and deletion controls.
- User authentication and access control.
- Support for additional document formats.
- Cloud deployment.

## License

Add a license file if you intend to distribute this project publicly. Otherwise, specify your preferred usage terms.

---

**Built with Python, Streamlit, LangChain, OpenAI, and Chroma.**
=======
# Enterprise-knowledge-base-ai
>>>>>>> 0efb4fb4407df267a7201b4ef8723ac93d676960
