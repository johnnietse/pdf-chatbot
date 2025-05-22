# PDF Chatbot with Flask and Langchain

![Screenshot (1181)](https://github.com/user-attachments/assets/d9a56ba3-254d-4bbd-b1f6-7c97a3b33611)
![Screenshot (1182)](https://github.com/user-attachments/assets/049ecb09-833e-46b1-bfe9-fcd8f127a505)

A chatbot that interacts with users via text and answers questions based on the content of a specific PDF document. Built with Flask, Langchain, and OpenAI's GPT-3.5-turbo.

## Features

- **PDF Processing**: Upload and process PDF documents for conversational retrieval.
- **AI-Powered Responses**: Utilizes OpenAI's GPT-3.5-turbo for intelligent responses.
- **Interactive UI**: Ready-to-use frontend with HTML, CSS, and JavaScript.
- **Light/Dark Mode**: Toggle between light and dark themes.
- **Easy Deployment**: Docker support for consistent deployment across environments.

## Table of Contents

1. [Build a Chatbot for your Data](#build-a-chatbot-for-your-data)
2. [Setting Up and Understanding the User Interface](#setting-up-and-understanding-the-user-interface)
3. [Understanding The Worker: Document Processing and Conversation Management](#understanding-the-worker-document-processing-and-conversation-management)
4. [Understanding The Server](#understanding-the-server)
5. [(Optional) Advanced Exercises](#optional-advanced-exercises)
6. [Running the Application](#running-the-application)
7. [Conclusion](#conclusion)

---

## Build a Chatbot for your Data

**Estimated time needed:** 60 minutes

### Introduction
Create a chatbot for your PDF files using Flask (web framework) and Langchain (for Large Language Models). The chatbot comprehends and answers questions about document content.

**Demo:** [Try The Demo App](#)

### Key Technologies
- **Flask**: Lightweight Python web framework for backend development.
- **Langchain**: Framework for AI-driven language applications (text retrieval, summarization, etc.).
- **Chatbots**: Human-like conversation software for diverse domains (customer service, education, etc.).

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
   i. Locate the downloaded ZIP file (e.g., my_project.zip).
   ii. Right-click → Extract All (Windows) or double-click (Mac/Linux).
   iii. Save the extracted folder to a preferred location (e.g., Documents/ or Downloads/).


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
   -  For Windows:
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


## Frontend Overview
- HTML/CSS/JavaScript: Ready-to-use interface with Bootstrap, Font Awesome, and jQuery.
- Key Files:
   - `index.html`: Layout and structure.
   - `style.css`: Visual styling and animations.
   - `script.js`: Interactivity (messaging, theme toggling, etc.).


## Understanding The Worker: Document Processing and Conversation Management

### Key Functions
1. Language Model Initialization:
- Uses OpenAI's GPT-3.5-turbo.
- Requires an API key (set in environment variables).

2. PDF Processing:
- Loads PDFs with PyPDFLoader.
- Splits documents into chunks with CharacterTextSplitter.
- Creates a vector store (Chroma) for retrieval.

3. Prompt Handling:
- Processes user messages with ConversationalRetrievalChain.
- Maintains chat history for context.


## Understanding The Server
### Flask Backend
- Routes:
   - /: Serves the frontend (index.html).
   - /process-document: Handles PDF uploads.
   - /process-message: Processes user queries.

### CORS Policy
Configured to allow requests from any domain ('*').


