# Taniya AI — AI Portfolio Assistant

Taniya AI is an AI-powered portfolio assistant built to answer questions about Taniya Negi's professional background, including her skills, projects, education, certifications, and experience.

The application uses a React frontend, FastAPI backend, and Groq LLM API to provide conversational responses based strictly on Taniya's professional profile.

## Features

- AI-powered portfolio assistant
- Conversational question answering
- Context-aware follow-up questions
- Profile-grounded responses
- Prevents unsupported information from being invented
- FastAPI REST backend
- Groq LLM integration
- Environment-based API key configuration
- CORS configuration for frontend-backend communication
- Pydantic request validation

## Tech Stack

### Frontend
- React
- JavaScript
- React Markdown
- Vite

### Backend
- Python
- FastAPI
- Uvicorn
- Pydantic

### AI / Generative AI
- Groq API
- Llama 3.3 70B Versatile
- Prompt Engineering
- LLM-based conversational AI

### Tools
- Git
- GitHub
- VS Code

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
React Chat Interface

## How It Works

1. The user enters a question in the React chat interface.
2. React sends the request to the FastAPI `/chat` endpoint.
3. FastAPI validates the request using Pydantic.
4. The backend provides Taniya's professional profile as the system context.
5. Conversation history is provided to the LLM to support follow-up questions.
6. Groq processes the request using the Llama 3.3 70B model.
7. The generated response is returned to the React frontend.
8. React displays the response in the chat interface.

## Profile-Grounded AI

Taniya AI is designed to answer questions using only information contained in the professional profile.

If information is not available, the assistant responds:

> "I don't have that information in Taniya's professional profile."

## Backend API

### Health Check

GET /

### Chat

POST /chat

## Project Structure

taniya-ai-backend/
├── main.py
├── requirements.txt
├── README.md
├── .gitignore
├── .env
└── .venv/

`.env` and `.venv/` are intentionally excluded from GitHub.

## Environment Variables

Create a `.env` file:

GROQ_API_KEY=your_groq_api_key

Never commit your `.env` file.

## Installation

Clone the repository:

git clone <YOUR_GITHUB_REPOSITORY_URL>

Navigate to the backend:

cd taniya-ai-backend

Create a virtual environment:

python -m venv .venv

Activate it:

source .venv/bin/activate

Install dependencies:

pip install -r requirements.txt

## Run the Backend

python -m uvicorn main:app --reload --port 8001

Backend:

http://127.0.0.1:8001

API documentation:

http://127.0.0.1:8001/docs

## Example Questions

- What are Taniya's technical skills?
- What projects has Taniya built?
- Which project uses Django?
- Tell me about EmailGuard AI.
- What technologies were used in the AI Resume Screener?
- What is Taniya's educational background?
- What certifications does Taniya have?

## Security

- API keys are stored in environment variables.
- `.env` is excluded through `.gitignore`.
- `.venv` is excluded from version control.
- API requests are validated using Pydantic.
- The Groq API key is never exposed to the React frontend.

## Future Improvements

- Deploy the FastAPI backend
- Deploy the React frontend
- Add automated testing
- Add structured logging
- Add rate limiting
- Improve API error handling
- Add persistent conversation sessions
- Add CI/CD using GitHub Actions

## Author

**Taniya Negi**

B.Tech — Computer Science & Engineering (AI & Data Science)

Interested in Artificial Intelligence, Machine Learning, Generative AI, and backend development.