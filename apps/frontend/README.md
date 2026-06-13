# HireMind Frontend 🎨

The frontend for **HireMind** is a React single-page application (SPA) optimized for low-latency audio processing and real-time user interaction. It guides the candidate through starting the interview, visualizing active speech status, and viewing the final evaluation report.

## 🚀 Key Features & Components

- **GitHub Kickstart Form (`Form.tsx`):** Ingestion interface to kickstart the interview via GitHub profile submission.
- **Live Interview Dashboard (`Interview.tsx`):** Handshakes WebSocket connection with the backend, records microphone input via `MediaRecorder`, and orchestrates raw binary audio playback.
- **Visualizing Speech (`VoiceOrb.tsx`):** A fluid visualizer showing the speaking status of both the Interviewer and the Candidate in real time (using `AudioContext` and web audio analyzers).
- **Result Report (`Result.tsx`):** Polls the backend for technical evaluation, rendering the custom score (out of 10), technical feedback, and interactive message transcript.

## 📦 Tech Stack & Libraries

- **Framework:** React 19
- **Routing:** React Router v7
- **Styles:** TailwindCSS v4
- **Icons:** Lucide React
- **Notifications:** Sonner
- **Audio Engine:** HTML5 Web Audio API (`AudioContext`, `MediaStream`, `AnalyserNode`, `AudioBufferSourceNode`)

## ⚙️ Environment Variables

Create a `.env` file in this directory:

```ini
BACKEND_URL="http://localhost:3001"
```

## 🛠️ Scripts

Run these scripts using `bun` from the `apps/frontend` directory:

- `bun dev`: Starts the local dev server with Hot Module Replacement (HMR).
- `bun run build`: Builds the static entrypoint HTML files to `/dist`.
- `bun start`: Serves the production bundle.
