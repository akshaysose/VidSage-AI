# VidSage AI

VidSage AI is a Streamlit web application that summarizes content from YouTube videos and publicly accessible webpages. It uses LangChain document loaders to retrieve source content and the Groq-hosted Gemma model to produce a concise summary.

## Overview

The application provides a simple interface where users can:

1. Enter a Groq API key in the sidebar.
2. Paste a YouTube or webpage URL.
3. Submit the URL for validation and processing.
4. View the generated summary in the application.

The summarization prompt requests a summary of the loaded content in approximately 300 words.

## Features

- Streamlit-based user interface.
- YouTube transcript and metadata loading through `YoutubeLoader`.
- Webpage content loading through `UnstructuredURLLoader`.
- URL validation before processing.
- Groq API integration through LangChain's `ChatGroq` connector.
- Gemma model-based content summarization.
- Progress feedback while content is being loaded and summarized.
- Input validation and visible error reporting.

## Application Workflow

1. The user enters a Groq API key and source URL.
2. The application checks that both fields are provided.
3. The URL is validated with the `validators` package.
4. YouTube URLs are processed with `YoutubeLoader`.
5. Other valid URLs are processed with `UnstructuredURLLoader`.
6. The loaded documents are passed to a LangChain summarization chain.
7. The Groq Gemma model generates the summary.
8. The summary is displayed in the Streamlit interface.

## Technology Stack

- **Python** - Application runtime.
- **Streamlit** - Web interface and application execution.
- **LangChain** - Prompting, document loading, and summarization orchestration.
- **Groq** - LLM provider.
- **Gemma** - Language model used for summary generation.
- **YouTube Transcript API and PyTube** - YouTube content support.
- **Unstructured** - Webpage content extraction.
- **Validators** - URL validation.

## Project Structure

```text
VidSage AI/
├── app.py
├── requirements.txt
└── README.md
```

### `app.py`

Contains the complete Streamlit application, including:

- Page configuration and interface elements.
- Groq API key and URL inputs.
- URL validation.
- YouTube and webpage document loaders.
- LangChain prompt and summarization chain.
- Summary output and error handling.

### `requirements.txt`

Lists the Python packages used by the application and its LangChain, document-loading, model-integration, and data-processing components.

## Prerequisites

- Python 3.9 or newer.
- Internet access for package installation and source URL retrieval.
- A Groq API key.

## Installation

Open a terminal in the project directory and create a virtual environment:

```bash
python -m venv .venv
```

Activate the virtual environment.

### Windows PowerShell

```powershell
.venv\Scripts\Activate.ps1
```

### Windows Command Prompt

```bat
.venv\Scripts\activate
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

## Running the Application

Start the Streamlit server from the project directory:

```bash
streamlit run app.py
```

Streamlit will display a local URL in the terminal. Open that URL in a browser to use VidSage AI.

## Using the Application

1. Launch the application with `streamlit run app.py`.
2. Enter a valid Groq API key in the **Groq API Key** field in the sidebar.
3. Enter a YouTube URL or webpage URL in the URL field.
4. Select **Summarize the Content from YT or Website**.
5. Wait for the source to be loaded and summarized.
6. Read the generated summary displayed on the page.

## Model and Prompt

The application creates a `ChatGroq` client with the `Gemma-7b-It` model. The summarization prompt is configured to provide a summary of the loaded content in approximately 300 words.

## Input Handling

- Both the API key and URL are required.
- The URL must pass validation before loading begins.
- URLs containing `youtube.com` use the YouTube loader.
- Other valid URLs use the webpage loader.
- Processing errors are displayed in the Streamlit interface.

