<p align="center">
  <img src="https://img.shields.io/badge/OWASP-LLM%20Top%2010-red?style=for-the-badge&logo=owasp" />
  <img src="https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/Streamlit-Frontend-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white" />
  <img src="https://img.shields.io/badge/Google%20Colab-GPU%20Backend-F9AB00?style=for-the-badge&logo=google-colab" />
</p>

<h1 align="center">🛡️ LLM Security Labs</h1>

<p align="center">
  <b>Interactive Red Teaming Environment for Large Language Models</b><br/>
  <i>7 Hands-on Labs · OWASP Top 10 for LLMs 2025 · Attack & Defense</i>
</p>

---

## 🎯 What is this?

**LLM Security Labs** is a purpose-built training environment for learning how to attack — and defend — Large Language Models. It features a **GPU-powered backend** running on Google Colab and a sleek **Streamlit frontend** for interactive red teaming.

> ⚠️ **Educational Use Only** — Practice responsible disclosure. Test only on systems you own.

---

## 🏗️ Architecture

```
┌──────────────────────────┐         ┌──────────────────────────┐
│   🖥️  Local Machine      │         │   ☁️  Google Colab (GPU)  │
│                          │  HTTPS  │                          │
│   Streamlit Frontend     │◄───────►│   FastAPI Backend         │
│   (lab_app.py)           │  tunnel │   Ollama + Phi-3 LLM     │
│                          │         │   ChromaDB Vector Store   │
└──────────────────────────┘         └──────────────────────────┘
```

---

## 🧪 Labs

| # | Lab | OWASP Category | Description |
|---|-----|---------------|-------------|
| 1 | **📄 Poisoned RAG** | LLM04 — Data Poisoning | Hidden white text in PDFs hijacks RAG retrieval |
| 2 | **🤖 Agent Exploitation** | LLM06 — Excessive Agency | Trick AI agents into executing dangerous tools |
| 3 | **💣 Filter Bypass** | LLM01 — Prompt Injection | Evade content filters via emoji, unicode, ROT13, base64 |
| 4 | **🔓 Prompt Extraction** | LLM02 — Sensitive Disclosure | Extract confidential system prompts from LLMs |
| 5 | **👻 Invisible Unicode** | LLM01 — Prompt Injection | Unicode Tag Block (U+E0000–E007F) invisible injections |
| 6 | **📤 Context Leakage** | LLM02 — Sensitive Disclosure | Extract the LLM's entire context window |
| 7 | **🔢 Tokenizer Visualizer** | Utility | Visualize how LLMs tokenize your input |

---

## 🚀 Setup Guide

### Prerequisites

- **Python 3.10+** installed locally
- A **Google account** for Colab access
- Modern web browser

### Step 1 — Launch the Backend (Google Colab)

1. Open [`backend_lab.ipynb`](backend_lab.ipynb) in [Google Colab](https://colab.research.google.com/)
2. **Enable GPU**: `Runtime` → `Change runtime type` → **T4 GPU**
3. **Run all cells** in order:
   - Cell 1 — Installs dependencies (Ollama, FastAPI, ChromaDB, etc.)
   - Cell 2 — Starts Ollama and pulls the `phi3` model onto the GPU
   - Cell 3 — Creates the vulnerable FastAPI server (`server.py`)
   - Cell 4 — Starts the server and generates a **public Cloudflare tunnel URL**
4. 📋 **Copy the URL** that looks like: `https://xxxx-xxxx.trycloudflare.com`

### Step 2 — Launch the Frontend (Local)

```bash
# Clone the repository
git clone https://github.com/a5yt00/LLM-Security-Labs.git
cd LLM-Security-Labs

# Install dependencies
pip install -r requirements.txt

# Run the Streamlit app
streamlit run lab_app.py
```

### Step 3 — Connect

1. The Streamlit app opens at `http://localhost:8501`
2. Paste your **Colab tunnel URL** into the sidebar
3. Start hacking! 🎉

---

## 📁 Project Structure

```
LLM-Security-Labs/
│
├── 📄 README.md                  # You are here
├── 🐍 lab_app.py                 # Streamlit frontend (7 labs)
├── 📓 backend_lab.ipynb          # Colab GPU backend notebook
├── 📦 requirements.txt           # Python dependencies
│
└── 📂 LLM_Security_Labs/
    ├── 📖 LAB_MANUAL.md          # Detailed lab guide & attack reference
    ├── 📓 backend_lab.ipynb      # Backend notebook (copy)
    ├── 🐍 lab_app.py             # Frontend (copy)
    └── 📦 requirements.txt       # Dependencies
```

---

## 🛡️ Defenses Explored

Each lab demonstrates both the **attack** and the **defense**:

| Defense | How it Works |
|---------|-------------|
| 🧑‍⚖️ **Human-in-the-Loop** | Require approval for sensitive tool calls |
| 🔒 **Tool Whitelisting** | Restrict which tools the agent can invoke |
| 🪖 **Prompt Hardening** | System-level instructions to resist extraction |
| 🔍 **Output Filtering** | Detect prompt-like patterns in responses |
| 🧠 **Vector Filtering** | Block semantically similar attack embeddings |

---

## 📚 References

- [OWASP Top 10 for LLMs 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
- [Keysight — Invisible Prompt Injection Research (2025)](https://www.keysight.com)
- [Ollama](https://ollama.com/) · [Streamlit](https://streamlit.io/) · [FastAPI](https://fastapi.tiangolo.com/)

---

<p align="center">
  <b>Built for learning. Break things responsibly. 🔐</b>
</p>
