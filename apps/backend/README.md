# HireMind Backend ⚙️

The backend for **HireMind** is a high-performance Express & WebSocket server built with Bun, acting as the middleware between the candidate, Deepgram (for STT & TTS), Groq (for Llama-3.1), and PostgreSQL.

## 🚀 Key Modules

- **GitHub Scraper (`scrapers/github.ts`):** Fetches candidate's public repositories and formats details (description, name, stars, primary language, topics) to feed into the interviewer's system prompt.
- **WebSocket Handler (`ws.ts`):** Establishes a raw WebSocket server at `/ws/interview`. Manages bidirectional audio/transcript streams and links directly to Deepgram's live transcription API.
- **LLM Manager (`llm.ts`):** Handles conversation state utilizing a Redis-backed history cache. Connects to Groq to generate streaming conversational response chunks.
- **Text-to-Speech Engine (`tts.ts`):** Leverages Deepgram Aura voice generation to convert LLM sentences into playable MP3 buffers.
- **Evaluator (`result.ts`):** Grades the final transcript using a strict technical scorecard JSON schema.

## 📦 Tech Stack & Libraries

- **Runtime:** Bun
- **Server:** Express + WebSocket (`ws`)
- **Database:** PostgreSQL (with Prisma ORM)
- **Caching:** Redis (`redis` library)
- **APIs:** Groq SDK, Deepgram SDK, Axios

## ⚙️ Environment Variables

Create a `.env` file in this directory:

```ini
DATABASE_URL="postgresql://..." # PostgreSQL database connection string
REDIS_URL="redis://localhost:6379"
GROQ_API_KEY="gsk_..."
DEEPGRAM_API_KEY="..."
FRONTEND_URL="http://localhost:3000"
GITHUB_TOKEN="" # Optional: to prevent GitHub API rate limiting
```

## 🛠️ Scripts

Run these scripts using `bun` from the `apps/backend` directory:

- `bun run index.ts`: Start the API and WebSocket server.
- `bunx prisma migrate dev`: Perform migrations and update Prisma client.
- `bunx prisma studio`: View and edit PostgreSQL records in the browser.
