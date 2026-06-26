# Pipecat Quickstart

## Overview
This repository contains a voice AI bot built with Pipecat. The project was created locally by **monamukil**.

## Tech Stack
- **Python 3.11+**
- **uv** - fast Python package manager
- **Pipecat AI** (`pipecat-ai` and its plugins: kokoro, moonshine, ollama, silero, webrtc)
- **FastAPI** for the WebSocket API
- **Docker** for containerization
- **OpenAI / Ollama** for LLM backend
- **Moonshine** for speech‑to‑text
- **Kokoro** for text‑to‑speech

## Local Installation
1. Install Python 3.11+ and ensure it is on your `PATH`.
2. Install `uv` (if not already):
   ```sh
   pip install uv
   ```
3. Install the project dependencies:
   ```sh
   uv sync --locked
   ```
4. Set required environment variables (e.g., API keys) in a `.env` file or export them:
   ```sh
   export DEEPGRAM_API_KEY=your_key   # if using Deepgram
   # add any other needed variables
   ```
5. Run the bot:
   ```sh
   python server/local_bot.py
   ```

## Docker Setup
To build and run the entire project inside a Docker container:

```sh
# Navigate to the server directory
cd d:/Personal_Projects/joey/pipecat-quickstart/server

# Build the Docker image
docker build -t pipecat-quickstart .

# Run the container (exposes port 8000)
docker run -p 8000:8000 --rm pipecat-quickstart
```

The container will start the bot using `local_bot.py`. Pass any required environment variables with `-e`, e.g.:

```sh
docker run -p 8000:8000 -e DEEPGRAM_API_KEY=your_key --rm pipecat-quickstart
```

## Accessing the Web UI
The bot exposes a FastAPI WebSocket endpoint. After the container is running, open your browser and navigate to:

```
http://localhost:8000
```

(If you have a custom front‑end, point it to the same address and port.)

## License
This project is licensed under the **Apache License 2.0**.
See the full license text: https://www.apache.org/licenses/LICENSE-2.0
