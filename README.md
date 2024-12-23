# Music Generation Web Application

This is a FastAPI-based web application that allows users to generate music based on user-provided lyrics using advanced machine learning models. The app utilizes Hugging Face's GPT-NEO model to generate lyrics and the Bark model (via Replicate) to create music based on those lyrics. The app provides a simple web interface to interact with.

## Features
- **Generate Lyrics:** Create lyrics using GPT-NEO from a user-defined prompt.
- **Generate Music:** Use the generated lyrics to produce music through the Bark model.
- **Web Interface:** An easy-to-use web interface to input prompts and view generated music.

## Setup

1. **Clone the repository:**
    ```bash
    git clone https://github.com/varun7778/Music-Generator.git
    cd Music-Generator
    ```

2. **Create and activate a virtual environment:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3. **Install required dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

4. **Set up environment variables:**
    - Create a `.env` file in the root directory of the project.
    - Define the necessary environment variables (for example, API keys or other secrets).

5. **Run the application:**
    ```bash
    uvicorn main:app --reload
    ```
    This will start the FastAPI server, and you can access the web app in your browser at `http://127.0.0.1:8000`.

## Project Structure

```
music-generation-webapp/
├── app/
│   ├── __init__.py
│   ├── main.py                # Main FastAPI application
│   ├── static/                 # Static files (e.g., images, CSS, JS)
│   └── templates/              # HTML templates for rendering
│       └── index.html          # The main page of the app
├── .env                        # Environment variables for API keys
├── requirements.txt            # Python dependencies
└── README.md                   # This file
```

## API Endpoints

### `GET /`
- **Description:** Renders the homepage (HTML form to input prompt and duration).
- **Response:** Renders `index.html` template.

### `POST /generate-music`
- **Description:** Accepts a prompt and duration as form data, generates lyrics using GPT-NEO, and generates music using Bark via Replicate.
- **Form Data:**
  - `prompt` (string): The input text to generate lyrics.
  - `duration` (integer): The duration of the music (not used directly in this implementation).
- **Response:** Returns a JSON response with a URL to the generated audio:
    ```json
    {
        "url": "https://generatedmusic.com/output.mp3"
    }
    ```
