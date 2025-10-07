# AI Companion App

<div align="center">

![AI Companion](https://img.shields.io/badge/AI-Companion-blue)
![Next.js](https://img.shields.io/badge/Next.js-13-black)
![TypeScript](https://img.shields.io/badge/TypeScript-5.1-blue)
![LangChain](https://img.shields.io/badge/LangChain-0.0.92-green)

**Build conversational AI companions with personality, memory, and context-aware responses**

[Features](#-features) • [Demo](#live-demo) • [Quick Start](#-quick-start) • [Architecture](#system-overview)

</div>

---

## 📖 Overview

AI Companion App is a production-ready, full-stack template for building customizable AI chatbots with persistent memory and dynamic personalities. Each companion maintains conversational context through vector similarity search and chat history, enabling more natural and engaging interactions.

### What Makes This Different?

- **🎭 Unique Personalities** - Define characters with custom backstories, behaviors, and conversational styles
- **🧠 Contextual Memory** - Vector database integration enables semantic recall of relevant information
- **💬 Multi-Model Support** - Switch between OpenAI GPT, Llama2, Vicuna, or custom LLM providers
- **📱 Multi-Channel** - Chat via web interface or SMS (Twilio integration)
- **🔒 Enterprise Auth** - Secure authentication with Clerk
- **⚡ Real-time Streaming** - Instant response streaming for better UX

---

## ✨ Features

### Core Capabilities

| Feature | Description |
|---------|-------------|
| **Character System** | Define unlimited AI companions with text-based configuration files |
| **Vector Memory** | Semantic search through Pinecone or Supabase pgvector |
| **Chat History** | Persistent conversation storage via Upstash Redis |
| **Streaming Responses** | Real-time token streaming using Vercel AI SDK |
| **Rate Limiting** | Built-in protection against abuse (10 req/10s) |
| **Multi-modal Output** | Support for text, images, audio, and video responses |
| **SMS Integration** | Text your AI companion via Twilio (optional) |
| **Export Functionality** | Export chat history to Character.AI format |

### Supported LLM Providers

- ✅ **OpenAI** (GPT-3.5-turbo-16k, GPT-4)
- ✅ **Replicate** (Llama2-13b, Vicuna-13b)
- ✅ **Steamship** (Custom agents)
- 🔧 **Extensible** - Easy to add new providers

---

## Live Demo
```bash
# Try it yourself
npm run dev
# Navigate to http://localhost:3000
```

## 🚀 Quick Start
### Prerequisites

Node.js 18.x or higher
```bash
npm or yarn
```
API keys for services you plan to use (see Environment Setup)

### Installation
### Clone the repository
```bash
git clone https://github.com/yourusername/ai-companion-app.git
cd ai-companion-app
```

### Install dependencies
```bash
npm install
```
### Copy environment template
```bash
cp .env.local.example .env.local
```
### Configure your environment variables (see below)
### Environment Setup
Create a .env.local file with the following variables:
### Vector Database (choose one)
```bash
VECTOR_DB= 'pinecone'  or 'supabase'
```
### Authentication (Clerk)
```bash
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_****
CLERK_SECRET_KEY=sk_****
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL=/
NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL=/
```
### LLM Providers
```bash
OPENAI_API_KEY=sk-****
REPLICATE_API_TOKEN=r8_****
```

### Vector Database (Pinecone)
```bash
PINECONE_API_KEY=****
PINECONE_ENVIRONMENT=us-****
PINECONE_INDEX=****
```
### OR Vector Database (Supabase)
```bash
SUPABASE_URL=https://****
SUPABASE_PRIVATE_KEY=****
```
### Chat History (Upstash Redis)
```bash
UPSTASH_REDIS_REST_URL=https://****
UPSTASH_REDIS_REST_TOKEN=****
```

### Optional: SMS Support (Twilio)
```bash
TWILIO_ACCOUNT_SID=AC****
TWILIO_AUTH_TOKEN=****
```

### Optional: Steamship Agents
```bash
STEAMSHIP_API_KEY=****
```

## Generate Vector Embeddings
Before running the app, generate embeddings for your character backstories:
### For Pinecone
```bash
npm run generate-embeddings-pinecone
```

### For Supabase
```bash
npm run generate-embeddings-supabase
```

## Run Development Server
```bash
npm run dev
```

## 🏗️ Architecture
### System Overview
<img width="419" height="286" alt="image" src="https://github.com/user-attachments/assets/c6f9a51a-11e5-4d6a-84df-4ac06e4e0278" />


## Data Flow

1. User sends message → Authenticated via Clerk
2. Rate limiting check → Upstash Redis
3. Retrieve chat history → Last 30 messages from Redis
4. Vector similarity search → Relevant backstory chunks from Pinecone/Supabase
5. Construct prompt → Combine personality + history + context
6. LLM inference → Stream response from chosen provider
7. Store message → Save to Redis for future context

## Key Components
```bash
src/
├── app/
│   ├── api/
│   │   ├── chatgpt/route.ts       # OpenAI integration
│   │   ├── llama2-13b/route.ts    # Replicate Llama2
│   │   ├── vicuna13b/route.ts     # Replicate Vicuna
│   │   ├── steamship/route.ts     # Steamship agents
│   │   └── text/route.ts          # Twilio SMS handler
│   ├── utils/
│   │   ├── memory.ts              # Vector DB & Redis manager
│   │   ├── config.ts              # Configuration loader
│   │   └── rateLimit.ts           # Rate limiting logic
│   └── page.tsx                   # Landing page
├── components/
│   ├── Examples.tsx               # Character gallery
│   ├── QAModal.tsx                # Chat interface
│   ├── ChatBlock.tsx              # Multimodal message rendering
│   └── Navbar.tsx                 # Navigation bar
└── companions/
    ├── companions.json            # Character configurations
    ├── Alex.txt                   # Character definition files
    ├── Evelyn.txt
    └── ...
```



