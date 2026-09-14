# Miku — Personal AI Operating Layer

Local-first personal AI assistant for the desktop. Miku combines secure access, conversational intelligence, tool-augmented actions, and a real-time operator HUD in one runtime.

**Status:** Ongoing development — core runtime, security gate, tool routers, and HUD are integrated; features are being hardened iteratively.

---

## What Miku does

- **Conversational AI** — Gemini-backed dialogue with intent routing, long-term memory, and bilingual (Hindi / English) replies  
- **Secure session** — Face authentication with PIN fallback before privileged use  
- **Operator HUD** — Futuristic web UI: boot → security → main dashboard (FastAPI + WebSocket)  
- **Tools** — Scientific calculator engines, live weather, web search, system metrics (CPU / RAM / disk)  
- **Desktop control** — Open/close apps and common system actions via text or voice-driven commands  
- **Voice** — TTS replies aligned with on-screen responses  

---

## Architecture (high level)

```text
Browser HUD (HTML/CSS/JS)
        │  HTTP + WebSocket
        ▼
FastAPI app (app.py)
        │
        ├── MikuBridge          → chat, memory, personality, TTS
        ├── Security            → face auth / PIN session
        ├── Tool / Intent routers → calculator, search, commands
        ├── Search engine       → weather, general lookup
        └── Desktop / system control
