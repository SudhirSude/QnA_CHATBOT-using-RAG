# QnA_CHATBOT-using-RAG
Project Description: RAG (Retrieval-Augmented Generation) Pipeline for Document Querying
This Jupyter notebook outlines the implementation of a Retrieval-Augmented Generation (RAG) pipeline, which combines document retrieval with a large language model (LLM) to answer user queries based on provided context. The pipeline is built using the LangChain framework, along with other libraries like Hugging Face Embeddings, Chroma Vector Store, and Ollama LLM. Below is a detailed breakdown of the project:

1. Data Ingestion
The project begins by loading data from multiple sources:

Text Files: A text file (speech.txt) is loaded using TextLoader from LangChain.

Web Pages: HTML content from a specific webpage is loaded using WebBaseLoader. The loader is configured to extract only specific HTML elements (e.g., post titles, content, and headers) using BeautifulSoup.

PDF Documents: A PDF file (attention.pdf) is loaded using PyPDFLoader.

These documents are then processed and prepared for further analysis.

2. Text Splitting
To handle large documents, the project uses a RecursiveCharacterTextSplitter to divide the text into smaller, manageable chunks. The splitter is configured with:

Chunk Size: 1000 characters per chunk.

Chunk Overlap: 200 characters to ensure context is preserved across chunks.

This step is crucial for efficient processing and retrieval of relevant information.

3. Vector Embedding and Vector Store
The project leverages Hugging Face Embeddings to convert text chunks into high-dimensional vector representations. Specifically, the all-MiniLM-L6-v2 model is used for generating embeddings. These embeddings are then stored in a Chroma Vector Store, which allows for efficient similarity searches.

4. Similarity Search
The vector store enables semantic search functionality. Users can query the vector store with natural language questions, and the system retrieves the most relevant document chunks based on vector similarity. For example:

Query: "Who are the authors of attention is all you need?"

Query: "What is encoder and decoder stack?"

The system retrieves and displays the most relevant content from the stored documents.

5. Retriever and Chain with LangChain
The project integrates a retriever and a document chain to create a seamless query-response pipeline:

Retriever: The retriever fetches relevant documents from the vector store based on the user's query.

Document Chain: A ChatPromptTemplate is used to structure the input for the LLM. The template instructs the model to answer questions based only on the provided context and to think step-by-step before generating a detailed response.

LLM Integration: The project uses Ollama LLM with the llama3.2 model to generate responses.

The retrieval chain combines the retriever and document chain, enabling the system to:

Retrieve relevant documents for a given query.

Pass the documents and query to the LLM.

Generate a detailed, context-aware response.

6. Example Query and Response
The notebook demonstrates the pipeline's functionality with an example query:

Query: "Scaled Dot-Product Attention"

Response: The system provides a step-by-step explanation of the concept, including its mathematical formulation and practical implementation.

Key Features
Multi-Source Data Ingestion: Supports text files, web pages, and PDFs.

Efficient Text Processing: Splits large documents into smaller chunks for better handling.

Semantic Search: Uses vector embeddings and a vector store for accurate document retrieval.

LLM Integration: Combines retrieval with a large language model for context-aware responses.

Modular Design: Built using LangChain's modular components, making it easy to extend or modify.

Technologies Used
LangChain: Framework for building LLM-powered applications.

Hugging Face Embeddings: For generating text embeddings.

Chroma Vector Store: For storing and querying vector embeddings.

Ollama LLM: For generating responses using the llama3.2 model.

BeautifulSoup: For parsing and extracting HTML content.

Potential Applications
Question-Answering Systems: Automatically answer user queries based on a knowledge base.

Document Summarization: Extract key information from large documents.

Research Assistance: Help researchers find relevant information from a collection of papers or articles.
