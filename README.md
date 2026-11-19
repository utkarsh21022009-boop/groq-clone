# NEXUS AI — Groq-Powered Ultra-Fast Inference Playground

![NEXUS AI Banner](https://img.shields.io/badge/NEXUS_AI-Groq_Inference_Playground-00f5d4?style=for-the-badge&logo=cpu&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-9d4edd?style=for-the-badge)
![TypeScript](https://img.shields.io/badge/TypeScript-5.7-3a86ff?style=for-the-badge&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-18-61dafb?style=for-the-badge&logo=react&logoColor=black)
![Tailwind](https://img.shields.io/badge/Tailwind_CSS-3.4-38bdf8?style=for-the-badge&logo=tailwind-css&logoColor=black)

**NEXUS AI** is a professional, high-performance artificial intelligence playground and inference workbench powered by the official **Groq API**. Built with a futuristic dark aesthetic, glassmorphism, glowing neon accents, and real-time Server-Sent Events (SSE) streaming, NEXUS AI provides an elite playground experience for developers, researchers, and creators.

---

## 🌟 Key Features

### 1. ⚡ Ultra-Fast Streaming Inference
- **Official Groq SDK** integration leveraging Groq LPUs for lightning-fast token generation.
- **Server-Sent Events (SSE)** delivering instant, character-by-character streaming.
- **Live Performance Metrics**: Real-time generation duration (`ms`) and throughput speed (`tokens/sec`).
- **Stop Generation**: Instant inference abort using `AbortController`.
- **Regenerate Responses**: One-click regeneration of assistant outputs.

### 2. 🧪 Dedicated Temperature Experiment Lab
- **Side-by-Side Temperature Benchmarking**: Run simultaneous inference requests across multiple temperature tiers (`0.0`, `0.3`, `0.7`, `1.0`, `1.5`, `2.0`) using the exact same prompt and model.
- **Empirical Entropy Comparison**: Visualize how sampling temperature affects probability distributions ($p_i \propto \exp(z_i / T)$).
- **Benchmark Presets**: Includes pre-configured prompts for hard sci-fi worldbuilding, recursive explanations, startup naming, and philosophical paradoxes.
- **Performance Diagnostics**: Independent latency and token speed measurement for each temperature card.

### 3. 🧠 Dynamic Model Selection
- **Auto-Discovery**: Fetches all available and active models directly from Groq's API (`/api/models`).
- **Model Metadata & Categorization**: Displays model identifiers, display names, context window sizes, parameter counts, and recommended tags (`openai/gpt-oss-120b`, `qwen/qwen3.8-27b`, `openai/gpt-oss-20b`, `allam-2-7b`, and more).
- **Zero-Code Model Switching**: Seamlessly change models in mid-chat without code modifications.

### 4. 🎛️ Advanced Parameter Controls
- **Temperature Slider** (0.0 – 2.0 with quick presets).
- **Top P (Nucleus Sampling)** (0.0 – 1.0).
- **Maximum Completion Tokens** (64 – 8192 tokens).
- **Frequency & Presence Penalties** (-2.0 – 2.0).
- **Custom System Instructions**: Editable prompt overrides with presets for Code Architect, Executive Analyst, Creative Scribe, and Standard Assistant.

### 5. 🎨 Magnificent Futuristic UI & Design
- **Animated Particle Constellation**: Interactive canvas background with subtle particle drift and mouse repulsion.
- **Glassmorphism**: Translucent panels with high-blur backdrops and glowing border accents.
- **Neon Accent Switcher**: Choose between *Cyber Cyan*, *Violet Nebula*, *Matrix Blue*, and *Synthwave Magenta*.
- **Collapsible Sidebar**: Desktop compact icon strip mode + full mobile drawer navigation.
- **Code Block Syntax Highlighting**: PrismJS integration supporting TypeScript, Python, Bash, SQL, Markdown, and JSON with one-click copy.
- **GitHub Flavored Markdown**: Native rendering for tables, blockquotes, lists, links, and inline code.

### 6. 🔒 Enterprise-Grade Security
- **Zero-Exposure Key Handling**: The `GROQ_API_KEY` is strictly confined to the server backend (`.env`). No API keys are ever transmitted to or exposed in the browser.
- **Masked Diagnostics**: Health checks display only masked keys (e.g. `gsk_0p...IJD7`).
- **Input Sanitization**: Numerical clamping and type validation on all incoming payload parameters.

### 7. 💾 Local Persistence & Data Management
- Full conversation history persistence in browser `localStorage`.
- Search conversations with live filtering.
- Grouping by date: Pinned, Today, Yesterday, Previous 7 Days, Older.
- Pin, rename, and delete individual conversations.
- **Export & Import**: Export chats as Markdown (`.md`) or JSON (`.json`) backups, with complete JSON restore support.

---

## 🏗️ Architecture

```
nexus-ai/
├── server/
│   └── index.ts            # Express backend with Groq SDK, SSE streaming, & static SPA server
├── src/
│   ├── components/
│   │   ├── ChatArea.tsx        # Message list, markdown rendering, & streaming bubbles
│   │   ├── ChatInput.tsx       # Auto-resizing textarea with keyboard shortcuts & send controls
│   │   ├── CodeBlock.tsx       # PrismJS syntax highlighting with copy button
│   │   ├── Navbar.tsx          # Top navigation, model selector, view toggle, & export
│   │   ├── ParametersPanel.tsx # Flyout parameter controls (Temp, Top P, Max Tokens, System Prompt)
│   │   ├── ParticleCanvas.tsx  # Interactive canvas particle constellation background
│   │   ├── SettingsModal.tsx   # Accent customization, defaults, API tester, & data import/export
│   │   ├── Sidebar.tsx         # Collapsible sidebar with search, history, & status indicator
│   │   └── TemperatureLab.tsx  # Dedicated multi-temperature side-by-side experiment workbench
│   ├── types/
│   │   └── index.ts            # TypeScript interfaces (Message, Conversation, Model, Settings)
│   ├── utils/
│   │   └── storage.ts          # LocalStorage persistence, defaults, and file export helpers
│   ├── App.tsx                 # Root application state orchestrator
│   ├── index.css               # Tailwind CSS imports & custom glowing styling
│   └── main.tsx                # React root mount
├── .env                        # Local environment variables (GROQ_API_KEY)
├── .env.example                # Template environment variables
├── .gitignore                  # Git exclusions (.env, node_modules, dist)
├── package.json                # Project dependencies & npm scripts
├── tailwind.config.js          # Custom theme colors, keyframe animations, & glowing effects
├── tsconfig.json               # TypeScript frontend configuration
└── vite.config.ts              # Vite bundler with API proxy to port 3001
```

---

## 🚀 Getting Started

### Prerequisites
- **Node.js** (v18.0.0 or higher recommended; developed and tested on v26)
- **npm** or **pnpm**
- A valid **Groq API Key** (from [Groq Console](https://console.groq.com/keys))

### Installation

1. **Clone or navigate into the project workspace:**
   ```bash
   cd "groq clone"
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Configure Environment Variables:**
   Create or edit the `.env` file in the root directory:
   ```bash
   cp .env.example .env
   ```
   Add your Groq API key:
   ```env
   GROQ_API_KEY=gsk_your_groq_api_key_here
   PORT=3001
   ```

---

## 💻 Running the Application

### Option A: Development Mode (with Hot Module Replacement)
Runs the Express backend server on port `3001` and Vite dev server on port `5173` concurrently:
```bash
npm run dev
```
Open **`http://localhost:5173`** in your browser.

### Option B: Production Mode (Unified Single-Port Deployment)
Builds the client application and serves both the API and the static assets from the Express server:
```bash
# 1. Build the frontend
npm run build

# 2. Start the production server
npm start
```
Open **`http://localhost:3001`** in your browser.

---

## 🧪 Verification & Testing

To test API connectivity and streaming outside the browser, you can run:

```bash
# Health check & latency test
curl http://localhost:3001/api/health

# List active models
curl http://localhost:3001/api/models

# Test real-time streaming SSE
curl -N -X POST http://localhost:3001/api/chat/stream \
  -H "Content-Type: application/json" \
  -d '{
    "messages": [{"role": "user", "content": "Explain quantum tunneling in 20 words."}],
    "model": "openai/gpt-oss-120b",
    "temperature": 0.7,
    "max_tokens": 100
  }'
```

---

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `⌘ + K` or `Ctrl + K` | Create a New Chat |
| `Enter` | Send Message |
| `Shift + Enter` | Insert Newline |
| `Escape` | Close Open Modals / Drawers |

---

## 📋 Implemented Features Checklist

- [x] **Original Branding**: NEXUS AI identity with futuristic dark cyberpunk styling.
- [x] **Official Groq SDK**: Direct server-side integration.
- [x] **Secure Proxy**: No API keys exposed to browser; key read from `GROQ_API_KEY`.
- [x] **Real-time SSE Streaming**: Immediate token display as generated.
- [x] **Model Discovery**: Dynamically queries `groq.models.list()`.
- [x] **Full Parameter Control**: Temperature, Top P, Max Tokens, Frequency & Presence Penalties, System Prompt.
- [x] **Dedicated Temperature Lab**: Side-by-side multi-temperature empirical benchmark workbench.
- [x] **Conversation Management**: Multiple chats, auto-titling, rename, delete, search, pin.
- [x] **Stop & Regenerate**: AbortController-powered live stop and message regeneration.
- [x] **Markdown & Code Highlighting**: PrismJS syntax highlighting with language tabs and copy button.
- [x] **Data Portability**: Export to Markdown (`.md`) and JSON (`.json`), plus JSON backup import.
- [x] **API Connectivity Diagnostics**: Live latency test and masked key status indicator.
- [x] **Responsive Mobile Layout**: Mobile hamburger drawer and collapsible desktop sidebar.

---

## ⚠️ Notes & Limitations
- **Model Terms**: Certain experimental community models on Groq (such as Canopy Labs models) require terms acceptance in the Groq Console before first use.
- **Audio Models**: Whisper models are specialized for audio transcription and are automatically filtered out from text chat selection.
# groq-clone
