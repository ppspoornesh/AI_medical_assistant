
# GenAI Engineer Hiring Task – Medical AI Assistant

All **compulsory** parts (1‑4) are fully implemented.

### Features Delivered
| Requirement | Implementation |
|-------------|----------------|
| **RAG + memory** | LangChain + FAISS + `ConversationBufferMemory` |
| **Report generation** | LLM function‑calling → exact extraction → `ReportLab` PDF |
| **Agentic flow** | 6 specialized agents + LangGraph orchestrator |
| **API** | FastAPI (`/docs` endpoint) |
| **Frontend** | Streamlit (upload, chat, download PDF) |
| **Multi‑format docs** | PDF, DOCX, XLSX, images (PyPDF2, python‑docx, openpyxl, OCR) |

### Architecture Diagram
`docs/architecture.png`

### Tech Stack
| Component | Technology |
|-----------|------------|
| Backend | **FastAPI**, Uvicorn |
| Frontend | **Streamlit** |
| LLM | **Ollama** (`llama3:8b` + `nomic‑embed‑text`) |
| RAG | **LangChain**, **FAISS**, **LangGraph** |
| Document parsing | **PyPDF2**, **python‑docx**, **openpyxl**, **pytesseract** |
| PDF generation | **ReportLab** |
| Environment | Python 3.11, `requirements.txt` |

---

## How to Run Locally

```bash
# 1. Clone / unzip the project
unzip Medical-AI-Assistant.zip   # or git clone ...

# 2. Create a virtual environment
python -m venv .venv
.\.venv\Scripts\activate   # Windows
# source .venv/bin/activate   # macOS/Linux

# 3. Install dependencies
pip install -r requirements.txt

# 4. Start Ollama (required for LLM)
#   - Install Ollama from https://ollama.com
#   - Run in a separate terminal:
ollama serve
ollama pull llama3:8b
ollama pull nomic-embed-text

# 5. Launch the app (two processes)
#   Terminal 1 – FastAPI
uvicorn app.main:app --host 0.0.0.0 --port 8000

#   Terminal 2 – Streamlit UI
streamlit run frontend/streamlit_app.py --server.port 8501