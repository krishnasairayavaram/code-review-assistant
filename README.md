# Code Review Assistant

This project is a simple web application that uses the Google Generative AI (Gemini) API to provide automated code reviews. You can upload a source code file, and the application will return suggestions for improving readability, modularity, and identifying potential bugs.

## Features

- **Automated Code Review**: Leverages the Gemini 1.5 Flash model to analyze your code.
- **Simple Web Interface**: An easy-to-use HTML form for uploading files.
- **FastAPI Backend**: A robust and fast Python web framework.

## Tech Stack

- **Backend**: Python 3.10+, FastAPI
- **AI Model**: Google Gemini 1.5 Flash
- **Server**: Uvicorn

## Prerequisites

- Python 3.10 or higher
- An active Google AI Studio API key.

## Setup and Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/code-review-assistant.git
    cd code-review-assistant
    ```

2.  **Create and activate a virtual environment (recommended):**
    ```bash
    # For Windows
    python -m venv venv
    venv\Scripts\activate

    # For macOS/Linux
    python3 -m venv venv
    source venv/bin/activate
    ```

3.  **Install the required dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Set up your environment variables:**

    Create a `.env` file in the root of the project and add your Google AI Studio API key:
    ```
    GOOGLE_API_KEY="your_google_api_key_here"
    ```
    The application loads this key from the environment variables.

## How to Run the Application

Once you have completed the setup, you can run the application using Uvicorn:

```bash
uvicorn main:app --reload
```

The `--reload` flag enables hot-reloading, which automatically restarts the server when you make changes to the code.

The application will be available at `http://127.0.0.1:8000`.

## How to Use

1.  Open your web browser and navigate to `http://127.0.0.1:8000`.
2.  You will see an upload form. Click "Choose File" to select a source code file from your local machine.
3.  Click the "Get Review" button.
4.  The application will send the file to the Gemini API and display the review suggestions on the same page.

### Example Request

-   **URL**: `http://127.0.0.1:8000/review`
-   **Method**: `POST`
-   **Body**: `multipart/form-data` with a single file field named `file`.

### Example Response

The API will return a JSON object with the code review:

```json
{
  "review": "The code is generally well-structured. However, consider breaking down the `process_data` function into smaller, more manageable pieces to improve modularity. Also, there is a potential for a null pointer exception on line 42 if the `user` object is not properly initialized."
}
```

## Project Structure

```
.
├── .env          # Environment variables (contains GOOGLE_API_KEY)
├── main.py       # FastAPI application logic
├── requirements.txt # Project dependencies
├── templates/
│   └── index.html  # HTML form for file uploads
└── README.md     # This file
