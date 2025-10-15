Code Review Assistant

This project is a simple web application that uses the OpenAI API to provide automated code reviews. You can upload a source code file, and the application will return suggestions for improving readability, modularity, and identifying potential bugs.

Features

Automated Code Review: Leverages the OpenAI GPT model to analyze your code.

Simple Web Interface: An easy-to-use HTML form for uploading files.

FastAPI Backend: A robust and fast Python web framework.

Tech Stack

Backend: Python 3.10+, FastAPI

AI Model: OpenAI GPT (via openai Python library)

Server: Uvicorn

Prerequisites

Python 3.10 or higher

An active OpenAI API key

Setup and Installation

Clone the repository:

git clone https://github.com/krishnasairayavaram/code-review-assistant.git
cd code-review-assistant


Create and activate a virtual environment (recommended):

# Windows
python -m venv venv
venv\Scripts\activate

# macOS/Linux
python3 -m venv venv
source venv/bin/activate


Install the required dependencies:

pip install -r requirements.txt


Set up your environment variables:

Create a .env file in the root of the project and add your OpenAI API key:

OPENAI_API_KEY="your_openai_api_key_here"


The application loads this key from the environment variables.

How to Run the Application

Run the FastAPI app using Uvicorn:

uvicorn main:app --reload


The --reload flag enables hot-reloading, automatically restarting the server when you make changes to the code.

Access the application at http://127.0.0.1:8000.

How to Use

Open your web browser and navigate to http://127.0.0.1:8000.

Use the upload form to select a source code file from your local machine.

Click the Get Review button.

The application will send the file to the OpenAI API and display the review suggestions on the page.

Example Request

URL: http://127.0.0.1:8000/review

Method: POST

Body: multipart/form-data with a single file field named file

Example Response
{
  "review": "The code is generally well-structured. However, consider breaking down the `process_data` function into smaller, more manageable pieces to improve modularity. Also, handle division by zero in the calculator function to prevent runtime errors."
}

Project Structure
.
├── .env              # Environment variables (contains OPENAI_API_KEY)
├── main.py           # FastAPI application logic
├── requirements.txt  # Project dependencies
├── templates/
│   └── index.html    # HTML form for file uploads
└── README.md         # This file

Notes

Never commit .env with your API key to GitHub. Use .gitignore to prevent this.

You can provide a .env.example file with a placeholder key for collaborators.
