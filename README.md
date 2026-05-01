# 🤖 MyPA — Hierarchical Multi-Agent Personal Assistant

> Send a task via Telegram. The system thinks, spawns agents, executes, and reports back.

---

## 🧠 What is This?

**MyPA** is a self-organizing, hierarchical Multi-Agent System (MAS) built in pure Python using Google ADK and the Gemini API.

You send a natural language instruction through Telegram — the system figures out everything else on its own: how many agents are needed, what tools they get, who talks to whom, and how to complete the task.

No hardcoded agent list. No fixed workflows. Fully dynamic.

---

## ⚙️ How It Works

```
You (Telegram)
     │
     ▼
┌─────────────────────────────┐
│   Layer 0 — Master Brain    │  ← Always-on. Listens 24/7.
│   Receives your instruction │
│   Spawns a Project Manager  │
└────────────┬────────────────┘
             │
             ▼
┌─────────────────────────────┐
│  Layer 1 — Project Manager  │  ← Spawned per task.
│  Analyzes the goal          │
│  Creates a Team Manifest    │
│  (agents, tools, chain)     │
│  Dissolves after completion │
└────────────┬────────────────┘
             │
     ┌───────┴────────┐
     ▼                ▼
┌─────────┐     ┌─────────┐
│ Worker  │     │ Worker  │  ← Layer 2. Spawned dynamically.
│ Agent A │     │ Agent B │    Each does one specific job.
└─────────┘     └─────────┘
```

### Agent Communication Protocol

Every message between agents follows this strict format:

| Field | Description |
|---|---|
| `sender_id` | Who sent the message |
| `receiver_id` | Who should receive it |
| `type` | `COMMAND` / `REPORT` / `REQUEST` |
| `payload` | The actual data or instruction |

---

## 📁 Project Structure

```
MultiAgentSystem/
├── main.py             ← Master Brain (Layer 0) — Telegram listener
├── core/
│   ├── agent.py        ← Base Agent class (blueprint for all agents)
│   ├── manager.py      ← Project Manager logic (Layer 1)
│   └── worker.py       ← Worker Agent logic (Layer 2)
├── tools/
│   ├── browser.py      ← Web research tool
│   └── file_ops.py     ← File read/write tool
└── config/
    └── settings.yaml   ← API keys & Telegram config
```

---

## 🚀 Tech Stack

- **Language:** Python 3.10+
- **AI Framework:** Google ADK (Agent Development Kit)
- **AI Model:** Gemini API (via Google AI Studio)
- **Interface:** Telegram Bot
- **Async:** `asyncio` for parallel agent execution

---

## ✨ Key Features

- **Dynamic Agent Spawning** — System decides on the fly how many agents are needed
- **Hierarchical Governance** — Master Brain → Project Manager → Workers
- **No Hardcoded Workflows** — Fully task-driven architecture
- **Self-Dissolving Teams** — Agents are created and destroyed per task (memory efficient)
- **Telegram Interface** — Give instructions from anywhere, anytime

---

## 🔮 Future Features (Planned)

- [ ] Voice interface — mini robot with mic + speaker
- [ ] Camera input for ambient data collection
- [ ] Self-fine-tuning using collected real-world data (Gemma 4)
- [ ] Web UI dashboard for monitoring active agents

---

## 🛠️ Setup (Coming Soon)

Full setup guide will be added as the project progresses.

---

## 📄 License

MIT License — free to use, modify, and distribute.

---

> Built from scratch. No paid frameworks. Just Python, Google ADK, and a big idea.
