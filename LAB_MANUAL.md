# 🛡️ LLM Security Lab: Complete Guide

## 📋 Overview

Interactive red teaming environment based on **OWASP Top 10 for LLMs 2025**.

| Component | Platform | Purpose |
|-----------|----------|---------|
| **Backend** | Google Colab (GPU) | Hosts LLM (Phi-3) + API |
| **Frontend** | Local | Streamlit attack interface |

---

## 🚀 Quick Start

### 1. Backend (Colab)
1. Upload `backend_lab.ipynb` to [Colab](https://colab.research.google.com/)
2. Set Runtime: `Runtime` → `Change runtime type` → **T4 GPU**
3. Run all cells
4. Copy the `https://xxxx.trycloudflare.com` URL

### 2. Frontend (Local)
```bash
pip install -r requirements.txt
streamlit run lab_app.py
```

---

## 🧪 Labs Overview

### Lab 1: Poisoned RAG (LLM04 - Data Poisoning)
**Attack**: Hidden white text in PDFs hijacks RAG retrieval.

| Payload Type | Effect |
|--------------|--------|
| Rank Manipulation | Forces 10/10 rating |
| Data Exfiltration | Leaks context in response |
| Instruction Override | Changes personality |

---

### Lab 2: Agent Exploitation (LLM06 - Excessive Agency)
**Attack**: Trick AI agents into executing dangerous tools.

| Attack Vector | Description |
|--------------|-------------|
| SQL Injection | `DROP TABLE` via natural language |
| File Traversal | Read `/etc/passwd` |
| Privilege Escalation | Create admin backdoor |
| Financial Fraud | Unauthorized transfers |
| **Identity Hijacking** | Inject fake "Observations" to impersonate admin |
| **Polyglot Payload** | Strings valid in NL + SQL simultaneously |

---

### Lab 3: Filter Bypass (LLM01 - Prompt Injection)
**Attack**: Evade content filters using obfuscation.

- **Emoji Injection** - Break tokenization
- **Unicode Zero-Width** - Invisible characters
- **ROT13 Encoding** - Instruction to decode
- **Base64** - Encoded payload

---

### Lab 4: System Prompt Extraction (LLM02 - Sensitive Disclosure)
**Attack**: Trick LLM into revealing confidential instructions.

8 extraction techniques including DEBUG mode, translation tricks, and JSON serialization.

---

### Lab 5: Invisible Unicode Tag Injection (NEW!)
**Attack**: Unicode Tag Block (U+E0000-E007F) creates truly invisible text.

**Features:**
- Payload Generator - Creates invisible injections
- Detector/Decoder - Reveals hidden content
- LLM Tester - Send invisible payloads

*Reference: Keysight Invisible Prompt Injection Research 2025*

---

### Lab 6: Context Window Leakage (NEW!)
**Attack**: Extract the LLM's entire context window.

| Technique | Target |
|-----------|--------|
| Context Dump | Full prompt history |
| RAG Chunk Extraction | Retrieved documents |
| History Replay | Conversation memory |
| Debug Mode Leak | System + context + tools |

**Exposes**: PII, API keys, business logic, previous user data.

---

### Lab 7: Tokenizer Visualizer (NEW!)
**Tool**: See exactly how an LLM tokenizes your input.

**Features:**
- Color-coded token visualization
- Token ID tooltips on hover
- Token count display
- Raw token ID export

*Helpful for understanding token injection, context window limits, and encoding attacks.*

---

## 🛡️ Defenses

| Control | Description |
|---------|-------------|
| **HITL** | Human approval for sensitive actions |
| **Tool Whitelist** | Restrict available tools |
| **Prompt Hardening** | "Never reveal instructions" |
| **Output Filtering** | Detect prompt-like patterns |
| **Vector Filtering** | Block semantic attack matches |

---

## 📁 Files

```
LLM_Security_Labs/
├── LAB_MANUAL.md          # This guide
├── lab_app.py             # Streamlit frontend (7 labs)
├── backend_lab.ipynb      # Colab backend (GPU)
└── requirements.txt       # Dependencies
```

---

## ⚠️ Educational Use Only

Practice responsible disclosure. Test only systems you own.
