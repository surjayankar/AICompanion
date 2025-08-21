# AI Companion App  

The **AI Companion App** is a full-stack template for building customizable AI companions that you can chat with directly in the browser.  

Each companion has its own **personality, backstory, and memory**, allowing for more natural and engaging conversations. The system uses a **vector database** for contextual recall, enabling companions to reference details from previous interactions or their defined backstory.  

---

## ✨ Key Features  

- **Multiple AI Companions** – define as many unique characters as you want  
- **Custom Personalities** – control behavior, tone, and backstory through simple text files  
- **Conversational Memory** – stores chat history for richer, more contextual dialogue  
- **Vector Database Integration** – powered by Supabase pgvector for semantic search  
- **Choice of LLMs** – fast and reliable responses from OpenAI or more dynamic interactions with Replicate’s Vicuna  
- **Authentication & User Management** – secured with Clerk  
- **Modern Web Stack** – Next.js frontend with LangChain.js for orchestration  

---

## 🛠️ Tech Stack  

- **Frontend & App Logic** → Next.js  
- **Authentication** → Clerk  
- **Vector Database** → Supabase (pgvector)  
- **Conversation History** → Upstash (Redis)  
- **LLM Orchestration** → LangChain.js  
- **Models Supported** → OpenAI GPT, Replicate (Vicuna13b)  

---

## 📖 How It Works  

1. **Character Definition** – Each companion has a description, seed conversation, and backstory stored in the project.  
2. **Embeddings** – Character data is embedded and stored in Supabase pgvector.  
3. **Conversation Flow** – LangChain retrieves relevant memory and backstory, then builds prompts for the chosen LLM.  
4. **Chat Interface** – A clean Next.js interface lets users talk to companions in real time.  

---

## 🚀 Use Cases  

- AI friends & social chatbots  
- Storytelling and creative writing partners  
- Coaching or educational companions  
- Entertainment and roleplay  
- Experimentation for developers learning about LLM apps  

---

## ⚠️ Limitations  

- Only the most recent chat is displayed in the UI (conversation history is stored but not fully visualized)  
- Vicuna responses can be slow due to cold start times  
- Error handling is minimal (timeouts may fail silently)  
- Conversation history in Upstash must be cleared manually  

---

 
