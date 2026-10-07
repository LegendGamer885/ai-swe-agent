# 🤖 Antigravity AI Software Engineering Agent (HNX26PSI09)

> **Autonomous AI Software Engineering Agent with a modern AI Web Interface & CLI that reads codebases, localizes bugs without block pointers, applies surgical minimal unified diffs (never full rewrites), validates fixes against automated test suites, prevents regressions with auto-rollback, and explains "What was wrong" & "Why it was wrong".**

Built for the **HNX26PSI09: AI Software Engineering Agent** Hackathon challenge.

---

## 🌟 Hackathon Evaluation Alignment

| Evaluation Criteria | Score / Requirement | How This Agent Solves It |
|---|---|---|
| **Hidden & Visible Acceptance Tests** | 30 Points | Pre-patch and post-patch automated test execution (`pytest`, `unittest`, `npm test`, `go test`). The agent only accepts changes that pass tests. |
| **Did You Break Anything Working?** | 0 Regressions | Automatic rollback mechanism: if post-patch tests fail or regress, backed-up files are immediately restored. |
| **Understand Codebase & Right Parts** | Autonomous Localization | Scans repository, indexes source files, ranks relevance using BM25/keyword scoring + Gemini context understanding without requiring user line pointers. |
| **Is Code Clean and Minimal?** | Surgical Diff Rule | Strict prompt enforcement & AST diffing produces minimal unified diffs (e.g. 2 lines modified), **never rewriting whole files**. |
| **Can You Explain the Bug?** | "What & Why" Diagnostics | Structured diagnostic cards explain: **1. What was wrong**, **2. Why it was wrong**, and **3. How it was resolved**. |
| **What to Build First** | Benchmark Guarantee | Includes a pre-packaged public demo repository with documented bugs and automated tests for 1-click live verification. |
| **Web & AI Interface** | Clean Model Look | Modern dark/light AI-model UI inspired by Cursor, Claude, and ChatGPT with syntax-highlighted diff viewers and live status steppers. |
| **File Upload Debugging** | File & Codebase Input | Users can upload single or multi-file scripts or paste snippets with error logs for instant surgical repairs. |

---

## 🏗️ Architecture

```
ai-swe-agent/
├── agent/
│   ├── benchmark_sample.py    ← Pre-built documented bug & pytest test suite
│   ├── bug_fixer.py           ← Generates minimal unified diff via Gemini / LLM
│   ├── code_understander.py   ← Semantic indexer & relevance ranker
│   ├── file_debugger.py       ← Uploaded file debugger with What/Why explanations
│   ├── llm_client.py          ← Multi-LLM adapter (Gemini, Grok, OpenAI, Heuristic)
│   ├── patch_applier.py       ← Safe unified diff applier with auto-rollback
│   ├── repo_reader.py         ← Clones GitHub repos or reads local paths
│   ├── reporter.py            ← Colored terminal reports & comparison tables
│   └── test_runner.py         ← Pytest, npm, and Go test executor & parser
├── web/
│   ├── server.py              ← FastAPI backend REST & Static file server
│   └── static/
│       ├── index.html         ← Modern AI SPA interface
│       ├── css/style.css      ← Modern typography, animations & diff syntax colors
│       └── js/
│           ├── app.js         ← Controller, tabs, file upload & API integration
│           └── diff_viewer.js ← Color-coded unified diff renderer
├── prompts/
│   ├── understand.txt         ← Codebase root cause analysis prompt
│   ├── fix.txt                ← Strict surgical unified diff prompt
│   └── explain.txt            ← Code explanation prompt
├── tests/                     ← 61 automated unit and integration tests (100% pass)
├── GITHUB_PUSH_GUIDE.md       ← Complete step-by-step GitHub push instructions
├── requirements.txt           ← Project dependencies
├── cli.py                     ← CLI interface (`fix`, `serve`, `explain`, `test`)
└── .env                       ← Configured with Gemini API key
```

---

## ⚡ Quick Start

### 1. Prerequisites
- Python 3.9+ (Tested on Python 3.14 on Windows)
- Git

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Configure API Key
Gemini is configured as the default provider in `.env`:
```env
GEMINI_API_KEY=your_gemini_api_key
DEFAULT_PROVIDER=gemini
GEMINI_MODEL=gemini-3.8-flash
```

---

## 🌐 Launching the Web Interface

Start the FastAPI web server:
```bash
python cli.py serve
```
Or with Uvicorn:
```bash
python -m uvicorn web.server:app --host 127.0.0.1 --port 8000
```

Open your browser at **`http://127.0.0.1:8000`** to access:
1. **GitHub Repo Fixer**: Enter any public GitHub repository URL or click **Load Sample**.
2. **File Upload Debugger**: Drag & drop any code file (`.py`, `.js`, `.ts`, etc.) to get a minimal diff fix and What/Why explanation.
3. **1-Click Benchmark**: Run the live Hackathon "What to build first" benchmark test case.
4. **Settings Modal**: Switch LLM models or customize API keys on the fly.
5. **GitHub Push Guide**: Interactive commands to push your project to GitHub.

---

## 💻 CLI Usage

### 1. Fix a Bug in a GitHub Repo or Local Project
```bash
python cli.py fix --repo https://github.com/owner/repo --issue "Fix off-by-one in pagination"
```

### 2. Run the Benchmark Demo
```bash
python cli.py fix --repo demo --issue "Fix pagination calculation"
```

### 3. Run Pre/Post Test Suites on any Repo
```bash
python cli.py test --repo ./my-project
```

### 4. Explain Codebase Mechanics
```bash
python cli.py explain --repo ./my-project --query "How does authentication middleware work?"
```

---

## 🧪 Automated Test Suite

Run all 61 automated tests:
```bash
python -m pytest tests/ -v
```

All 61 tests pass:
- Unit tests for pure-Python patch application & rollback
- Test runner framework detection
- File upload debugging with syntax repair & AST inspection
- Multi-provider LLM Client logic
- Full end-to-end benchmark test execution (fails before, passes after)
- FastAPI REST endpoints

---

## 🚀 How to Push to GitHub

For detailed step-by-step instructions with credentials and remote setup, see **[GITHUB_PUSH_GUIDE.md](GITHUB_PUSH_GUIDE.md)**.

Quick push commands:
```powershell
git add .
git commit -m "feat: complete HNX26PSI09 AI SWE Agent with Web UI & minimal diff engine"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/ai-swe-agent.git
git push -u origin main
```
