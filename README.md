# 🧙‍♂️ **Deep Research** 🧠🚀  
*AI-powered deep-dive research engine — rewritten in pure Python*

[![CI](https://github.com/meltmagic-agency/deep-research/actions/workflows/ci.yml/badge.svg)](https://github.com/meltmagic-agency/deep-research/actions/workflows/ci.yml)
![PyPI](https://img.shields.io/pypi/v/deep-research?color=orange&label=PyPI)
![Python Versions](https://img.shields.io/pypi/pyversions/deep-research)
![License](https://img.shields.io/github/license/meltmagic-agency/deep-research)

> **Build like Stark. 🚀 Research like a 100-person team.**  

---

## ✨ Why You’ll Love It
| 💡 What It Does | 🔍 How It Works |
|-----------------|----------------|
| **1. Explodes a single question** into multiple high-quality SERP queries. | LLM (OpenAI _o3-mini_ or DeepSeek R1) 📜 ➜ JSON-validated queries |
| **2. Scours the web in parallel** | Firecrawl API ⚡ async + configurable concurrency |
| **3. Extracts smart learnings & next questions** | Token-aware prompt trimming 🪄 |
| **4. Loops recursively (breadth ↓, depth ↓)** | Unique learnings / URLs deduplicated |
| **5. Outputs either…** | • _a surgical one-liner answer_ ✂️<br>• _a multi-page Markdown report_ 📑 |

---

## 🚀 Quick Start

```bash
# 1 · Clone & enter
git clone https://github.com/meltmagic/deep-research.git
cd deep-research

# 2 · Add your keys
cp .env.example .env            # edit FIRECRAWL_KEY, OPENAI_KEY or FIREWORKS_KEY

# 3 · Install & run CLI
pip install -r requirements.txt
python -m deep_research         # interactive wizard 🧙
```

### 🐳 Docker One-Liner
```bash
docker compose up              # API 👉 http://localhost:8000/docs
```

---

## ⚙️ Configuration (.env)
| Key | 🚦 Required | 📝 Description |
|-----|------------|---------------|
| `FIRECRAWL_KEY` | ✅ | Web search + scrape |
| `OPENAI_KEY` | ✅* | LLM (o3-mini) |
| `FIREWORKS_KEY` | ✅* | DeepSeek R1 alternative |
| `CUSTOM_MODEL` + `OPENAI_ENDPOINT` | ✅* | Any OpenAI-compatible endpoint |
| `FIRECRAWL_CONCURRENCY` | ▫️ | Parallel calls (default 2) |
| `CONTEXT_SIZE` | ▫️ | Max tokens to send to LLM (default 128 000) |

\* Provide **one** of the three LLM options.

---

## 🖥️ CLI Demo
```
$ python -m deep_research
❓ What would you like to research?  Impact of autonomous trucks on jobs
📏 Breadth (2-10) [4]:
📐 Depth (1-5) [2]:
📄 Generate report or answer? (report/answer) [report]:
```
Outputs land in the **`reports/`** folder:  
`report.md` 📓 or `answer.md` 💬

---

## 🌐 REST API

| Verb | Endpoint | 🎯 Purpose |
|------|----------|-----------|
| **POST** | `/api/research` | Concise `answer` + metadata |
| **POST** | `/api/generate-report` | Full `reportMarkdown` |
| **GET**  | `/api/healthz` | Liveness ping |

Example 👇
```http
POST /api/research
Content-Type: application/json

{
  "query": "Why did the 2024 GPU shortage happen?",
  "breadth": 3,
  "depth": 2
}
```

---

## 🏗 Architecture Glimpse
```text
CLI / REST ↔️ Orchestrator 🔄
           ↙️                  ↘️
    Firecrawl 🌐          LLM 🎓
           ↘️                  ↙️
          Markdown Report 📑 / Exact Answer ⚡
```

---

## 🛣️ Roadmap
- 🔌 WebSocket progress stream  
- 🛡️ RAG verification to curb hallucinations  
- 🖼️ Streamlit front-end dashboard  
- 🔐 Optional API-key auth middleware  

[📬 Open an issue](https://github.com/meltmagic-agency/deep-research/issues) to suggest features!

---

## 🤝 Contributing
1. Fork → `git checkout -b magic-feature`  
2. `poetry install` or `pip install -r requirements-dev.txt`  
3. Lint `ruff`, type-check `mypy`, test `pytest -q`  
4. PR with emoji-rich description 😉

---

## 📝 License
**MIT** © 2025 MeltMagic Agency — Fork it, ship it, **make magic**. ✨
