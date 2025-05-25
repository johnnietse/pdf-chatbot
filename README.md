# PDF Chatbot with Flask and Langchain

A chatbot that interacts with users via text and answers questions based on the content of a specific PDF document. Built with Flask, Langchain, and OpenAI's GPT-3.5-turbo.

## Why Build a Chatbot to Analyze PDF Documents Using LLM?
In organizations, thousands of pages of PDFs (manuals, reports, contracts) hold critical knowledge. Manually reading them is time-consuming and error-prone.
This project solves that: Create an AI assistant that digests PDFs in seconds and answers questions like a human expert about what it had read, while processing sensitive PDFs locally (no cloud uploads) to ensure data privacy. This is especially critical scenarios where you need to keep thousands of pages of information confidential for snensitive materials like internal manuals, proprietary reports, legal contracts, or medical records, while also requiring an AI-powered personal assistant chatbot to summarize the reading for you in seconds.

![Screenshot (1181)](https://github.com/user-attachments/assets/d9a56ba3-254d-4bbd-b1f6-7c97a3b33611)
![Screenshot (1182)](https://github.com/user-attachments/assets/049ecb09-833e-46b1-bfe9-fcd8f127a505)

## Features

- **PDF Processing**: Upload and process PDF documents for conversational retrieval.
- **AI-Powered Responses**: Utilizes OpenAI's GPT-3.5-turbo for intelligent responses.
- **Interactive UI**: Ready-to-use frontend with HTML, CSS, and JavaScript.
- **Light/Dark Mode**: Toggle between light and dark themes.
- **Easy Deployment**: Docker support for consistent deployment across environments.

## Table of Contents

1. [Build a Chatbot for your Data](#build-a-chatbot-for-your-data)
2. [Setting Up and Understanding the User Interface](#setting-up-and-understanding-the-user-interface)
3. [Using the Chatbot](#using-the-chatbot)
4. [Troubleshooting](#troubleshooting)
5. [Docker Deployment (Optional)](#docker-deployment-optional)
6. [Frontend Overview](#frontend-overview)
7. [Understanding The Worker: Document Processing and Conversation Management](#understanding-the-worker-document-processing-and-conversation-management)
8. [Understanding The Server](#understanding-the-server)
9. [Conclusions](#conclusions)

---

## Build a Chatbot for your Data

### Introduction
Create a chatbot for your PDF files using Flask (web framework) and Langchain (for Large Language Models). The chatbot comprehends and answers questions about document content.

**Demo:** (https://chatbot-for-own-data.xs6r134s1i6.us-east.codeengine.appdomain.cloud/)


### Key Technologies
- **Flask**: Lightweight Python web framework for backend development.
- **Langchain**: Framework for AI-driven language applications (text retrieval, summarization, etc.).
- **Chatbots**: Human-like conversation software for diverse domains (customer service, education, etc.).

### Tech Stack
- HTML
- CSS
- JavaScript
- Python

### Learning Objectives
- Understand Langchain and AI applications.
- Set up a development environment with Python Flask.
- Implement PDF upload functionality.
- Integrate with OpenAI's GPT-3 model.
- (Optional) Deploy to a web server.

### Prerequisites
Basic knowledge of HTML/CSS, JavaScript, and Python is helpful but not required.

---

## Setting Up and Understanding the User Interface

### Initial Setup
1. Download the ZIP File from the repository and extract it
   - Locate the downloaded ZIP file (e.g., my_project.zip).
   - Right-click → Extract All (Windows) or double-click (Mac/Linux).
   - Save the extracted folder to a preferred location (e.g., Documents/ or Downloads/).


2. Open a Terminal
   - Navigate to the extracted folder:

```bash
cd path/to/extracted_folder
```

Note: (Replace path/to/extracted_folder with your actual path.)

3. Create a virtual environment:
   ```bash
   pip3 install virtualenv
   virtualenv my_env
   ```
   - For Windows:
     ```bash
     my_env\Scripts\activate
     ```
     
   - For Mac/Linux:
     ```bash
     source my_env/bin/activate
     ```
      
4. Install dependencies:

```bash
pip install Flask Flask_Cors langchain==0.0.299 openai==0.28 pdf2image chromadb==0.4.15 pypdf tiktoken
```

5. Since the project includes a requirements.txt, use "pip install -r requirements.txt" in addition to running the above command.
   
6. Add your OpenAI API key
- Get a key from OpenAI.
- In `worker.py`, add your actual key into the quotations -> `api_key = " "`.

7. Running the Application:
### Local Execution
```bash
python3 server.py
```
Access the app at `http://127.0.0.1:8080`. Visit it to use the chatbot.

## Using the Chatbot
1. Upload a PDF via the web interface.
2. Ask questions about the document content.
3. Reset the chat anytime to start over.

## Troubleshooting
- **"API key not found"**: Ensure your OpenAI key is set in `worker.py`.
- **PDF upload fails**: Check if the file is valid (e.g., not corrupted).
- **Slow responses**: Reduce `chunk_size` in `CharacterTextSplitter`.
- **Port 8080 busy**: To fix it,	Run `lsof -i :8080` (Mac/Linux) or `netstat -ano findstr :8080` (Windows) to free the port.
- ***Port conflicts**: Change the port in server.py (e.g., port=8000).
- **Missing modules**: Reinstall dependencies with `pip install -r requirements.txt`.

## Docker Deployment (Optional)

1. Build the image:

```bash
docker build -t build_chatbot_for_your_data .
```

2. Run the container:

```bash
docker run -p 8080:8080 build_chatbot_for_your_data
```

## Frontend Overview
- HTML/CSS/JavaScript: Ready-to-use interface with Bootstrap, Font Awesome, and jQuery.
- Key Files:
   - `index.html`: Layout and structure.
   - `style.css`: Visual styling and animations.
   - `script.js`: Interactivity (messaging, theme toggling, etc.).


## Understanding The Worker: Document Processing and Conversation Management

### Key Functions
1. **Language Model Initialization**:
- Uses OpenAI's GPT-3.5-turbo.
- Requires an API key (set in environment variables).

2. **PDF Processing**:
- Loads PDFs with `PyPDFLoader`.
- Splits documents into chunks with `CharacterTextSplitter`.
- Creates a vector store (`Chroma`) for retrieval.

3. **Prompt Handling**:
- Processes user messages with `ConversationalRetrievalChain`.
- Maintains chat history for context.


## Understanding The Server
### Flask Backend
- Routes:
   - `/`: Serves the frontend (`index.html`).
   - `/process-document`: Handles PDF uploads.
   - `/process-message`: Processes user queries.

### CORS Policy
Configured to allow requests from any domain ('`*`').

## Conclusions
You’ve built a chatbot capable of:
- **Retrieval-Augmented Search and Generation**: Leveraging document content for answers & Combine LLMs with document data.
- **Langchain Integration**: Using embeddings and vector stores & Processing documents with embeddings and vector stores.
- **Full-Stack Development**: Combining Flask, JavaScript, and AI models & Using Flask to build a backend for handling requests.


---

# Project Attribution
This chatbot was developed as part of a guided project tutorial provided by the IBM Cognitive Class AI platform. The project demonstrates the integration of Flask, LangChain, and Large Language Models (LLMs) to build an AI-powered assistant capable of analyzing and answering questions about PDF documents.
