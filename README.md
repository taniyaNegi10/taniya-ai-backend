
# Taniya AI — AI Portfolio Assistant Backend

Taniya AI is an AI-powered personal portfolio assistant designed to answer questions about Taniya Negi's professional background, including her education, skills, projects, certifications, and experience.

This repository contains the **FastAPI backend** that powers the AI assistant. It connects the React frontend to the Groq LLM API and provides profile-grounded conversational responses.

The backend is designed to answer only from Taniya's professional profile and avoid inventing unsupported information.

---

## Features

* AI-powered portfolio assistant backend
* Conversational question answering
* Context-aware follow-up questions
* Profile-grounded AI responses
* Prevents unsupported information from being invented
* FastAPI REST API
* Groq LLM integration
* Llama 3.3 70B Versatile
* Pydantic request validation
* CORS configuration for frontend-backend communication
* Environment-based API key configuration
* Secure separation of frontend and backend
* Interactive API documentation with Swagger UI

---

## Tech Stack

### Backend

* Python
* FastAPI
* Uvicorn
* Pydantic

### AI / Generative AI

* Groq API
* Llama 3.3 70B Versatile
* Prompt Engineering
* Large Language Models (LLMs)
* Conversational AI

### Frontend Integration

* React
* JavaScript
* Vite
* React Markdown

### Tools

* Git
* GitHub
* VS Code

---

## System Architecture

```text
                         User
                           |
                           v
                   React Frontend
                           |
                           | POST /chat
                           v
                   FastAPI Backend
                           |
                           | Profile + Conversation Context
                           v
                       Groq API
                           |
                           v
                  Llama 3.3 70B
                           |
                           v
                     AI Response
                           |
                           v
                   React Chat UI
```

---

## How It Works

1. The user enters a question in the React chat interface.
2. The React frontend sends the conversation to the FastAPI `/chat` endpoint.
3. FastAPI receives and validates the request using Pydantic.
4. The backend provides Taniya's professional profile as context for the AI.
5. Conversation history is included to support contextual follow-up questions.
6. The backend sends the request to the Groq API.
7. Groq processes the request using the Llama 3.3 70B Versatile model.
8. The generated response is returned by FastAPI.
9. The React frontend displays the AI response.

---

## Profile-Grounded AI

The assistant is designed to answer questions using only information available in Taniya's professional profile.

If the requested information is not available, the assistant should respond:

> "I don't have that information in Taniya's professional profile."

This helps reduce unsupported or fabricated information.

---

## Backend API

### Health Check

```http
GET /
```

Example response:

```json
{
  "message": "Taniya AI backend is running!"
}
```

### Chat

```http
POST /chat
```

Example request:

```json
{
  "messages": [
    {
      "role": "user",
      "content": "Which project uses Django?"
    }
  ]
}
```

Example response:

```json
{
  "response": "EmailGuard AI uses Django."
}
```

### API Documentation

When the backend is running, interactive Swagger documentation is available at:

```text
http://127.0.0.1:8001/docs
```

OpenAPI schema:

```text
http://127.0.0.1:8001/openapi.json
```

---

## Project Structure

```text
taniya-ai-backend/
│
├── main.py
├── requirements.txt
├── README.md
├── .gitignore
├── .env
└── .venv/
```

`.env` and `.venv/` are intentionally excluded from Git version control.

---

## Environment Variables

Create a `.env` file in the backend root directory:

```env
GROQ_API_KEY=your_groq_api_key
```

Never commit your `.env` file to GitHub.

---

## Installation

### 1. Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
```

### 2. Navigate to the Backend

```bash
cd taniya-ai-backend
```

### 3. Create a Virtual Environment

```bash
python -m venv .venv
```

### 4. Activate the Virtual Environment

macOS / Linux:

```bash
source .venv/bin/activate
```

Windows:

```bash
.venv\Scripts\activate
```

### 5. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Run the Backend

Start the FastAPI development server:

```bash
python -m uvicorn main:app --reload --port 8001
```

Backend:

```text
http://127.0.0.1:8001
```

Swagger API documentation:

```text
http://127.0.0.1:8001/docs
```

---

## Testing the Backend

You can test the health endpoint using:

```bash
curl http://127.0.0.1:8001/
```

Expected response:

```json
{
  "message": "Taniya AI backend is running!"
}
```

You can test the chat endpoint using:

```bash
curl -X POST http://127.0.0.1:8001/chat \
-H "Content-Type: application/json" \
-d '{"messages":[{"role":"user","content":"Which project uses Django?"}]}'
```

Expected response:

```json
{
  "response": "EmailGuard AI uses Django."
}
```

---

## Example Questions

The assistant can answer questions such as:

* What are Taniya's technical skills?
* What projects has Taniya built?
* Which project uses Django?
* Tell me about EmailGuard AI.
* What technologies were used in the AI Resume Screener?
* What is Taniya's educational background?
* What certifications does Taniya have?
* Tell me about Taniya's experience.

---

## Security

The backend follows several basic security practices:

* API keys are stored in environment variables.
* `.env` is excluded through `.gitignore`.
* `.venv` is excluded from version control.
* The Groq API key is never exposed to the React frontend.
* API requests are validated using Pydantic.
* CORS is configured for frontend-backend communication.

> Never upload your actual `GROQ_API_KEY` to GitHub.

---

## Frontend and Backend Repositories

The project is separated into two repositories:

### Frontend

**Taniya AI React Frontend**

Built using React and Vite.

### Backend

**Taniya AI Backend**

Built using FastAPI and integrated with the Groq API.

This separation keeps the frontend and backend independently maintainable and deployable.

---

## Future Improvements

* Deploy the FastAPI backend
* Deploy the React frontend
* Add automated testing
* Add structured logging
* Add rate limiting
* Improve API error handling
* Add persistent conversation sessions
* Add authentication if required
* Add CI/CD using GitHub Actions
* Improve production monitoring

---

## Author

**Taniya Negi**

B.Tech — Computer Science & Engineering (AI & Data Science)

Interested in Artificial Intelligence, Machine Learning, Generative AI, and backend development.
