# AI ChatBot with Adaptive RAG over YouTube/PDF for DnD QA

This is what I developed for the final project of the AI Engineering Bootcamp at Ironhack, where we were tasked to create a chatbot that could answer questions about YouTube videos. The chatbot focused on Dungeons & Dragons character creation, can answer questions on the topic by extracting information from YouTube videos and PDF documents with detailed rules for the process.
This README outlines the installation steps, usage instructions, and key concepts.

## Table of Contents
- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [Repository Structure](#repository-structure)
- [Setup and Installation](#setup-and-installation)
- [Usage](#usage)
- [Environment Variables](#environment-variables)
- [Dependencies](#dependencies)
- [Acknowledgements](#acknowledgements)

---

## Project Overview

This chatbot offers a powerful tool for accessing and querying information from YouTube videos and relevant PDFs. It combines PDF processing with OCR techniques, NLP, RAG (retrieval-augmented generation), and a LangGraph architecture with agents and tools to answer user queries accurately, leveraging the LangChain framework and Pinecone as a vector store. This solution improves content accessibility, supports efficient knowledge retrieval, and can significantly enhance the user experience of creating a DnD character.

## Key Features

- **PDF Processing and Metadata Extraction:** Processes D&D Player Handbook PDF and stores relevant sections in a CSV format.
- **Multimodal QA:** Supports questions about both YouTube video content and document-based knowledge.
- **LangChain-Powered Workflow:** Utilizes LangChain agents and memory for enhanced contextual understanding.
- **Vector Store Integration with Pinecone:** Efficient document and video retrieval using embeddings.

## Repository Structure

- **PDF_Processing.py**: Processes PDF documents with various OCR techniques, extracts relevant content, and stores it in a CSV file for easy indexing in the vector store.
- **main_langgraph.py**: Main chatbot script, processing YouTube video transcripts and a CSV file (extracted from PDF) and integrating with the LangChain and Pinecone frameworks for the main QA functionality using LangGraph. It also includes the code for the deployment on Gradio.
- **combined_docs_final.csv**: CSV file containing extracted content from PDF, enabling efficient retrieval for user queries.

---

## Setup and Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Grimngor/Final-Project-Multimodal-chatbot-for-YT-video-QA.git

2. **Install Dependencies: Ensure you have Python 3.8 or later. Install the required libraries using**:
   ```bash
   pip install -r requirements.txt

3. **Set Up Environment Variables**:
**Set Up Environment Variables**: Create a .env file in the root directory to store your API keys (e.g., OpenAI, Pinecone) as detailed in the Environment Variables section below.

## Usage
### Running the Chatbot
To launch the chatbot with YouTube video QA capabilities, run the main script:
   ```bash
   python main_langgraph.py
   ```

This script will:
- Load and process YouTube video transcripts and the data from the PDF.
- Initialize the vector store and embed processed content.
- Use LangGraph agents to answer questions based on video content or related document information.

### PDF Processing
To process additional PDF files, use the PDF_Processing.py script. This script extracts relevant content, prepares it in a structured format, and stores it in combined_docs_final.csv for retrieval. Run it as follows:

```bash
python PDF_Processing.py
```
The extracted content can then be queried by the main chatbot to supplement responses with information from the processed PDF.

## Environment Variables
   ```env
   OPENAI_API_KEY=your_openai_api_key
   PINECONE_API_KEY=your_pinecone_api_key
   LANGCHAIN_API_KEY=your_langchain_api_key
   UNSTRUCTURED_API_KEY=your_unstructured_api_key (for PDF processing)
   ```
   These keys are necessary for accessing the OpenAI model, LangChain agents, and Pinecone vector store.

### Dependencies
The project uses several Python libraries, including but not limited to:

- yt-dlp: To download YouTube metadata.
- langchain, langgraph, and langchain-openai: For NLP and agent integration.
- pytesseract and fitz (PyMuPDF): For PDF processing and OCR.
- pinecone-client: For vector store management.
Install all dependencies via pip install -r requirements.txt.

### Acknowledgements
Special thanks to Ironhack for the AI Engineering Bootcamp framework, which inspired the business case and technical foundation of this project.
