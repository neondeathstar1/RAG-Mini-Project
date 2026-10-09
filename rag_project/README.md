# RAG Mini Project: Phishing Triage Runbook

This project builds a retrieval-augmented generation (RAG) system from scratch in Python for a fictional company's phishing triage runbook. Five short documents are split into overlapping chunks, embedded locally with all-MiniLM-L6-v2, and stored in ChromaDB using cosine distance. For each question, the system retrieves the closest chunks, drops matches above a distance threshold, and builds a prompt from what remains. If nothing passes the threshold, it refuses to answer. Eight test questions (six answerable, two not, including a ransomware near-miss) were used to run experiments on chunk size, number of chunks retrieved, and distance threshold. The key finding is that the distance threshold matters most: a value of 0.55 was the only tested setting that found all six answers and refused both unanswerable questions. Looser thresholds kept finding answers but stopped refusing.

## Files

- `rag_notebook.ipynb`: the full pipeline, experiments, and chart, with outputs saved
- `my_kb/`: the five runbook documents and `SOURCES.md`
- `goldset.json`: the eight test questions with evidence phrases
- `results.csv`: results of each configuration tested
- `figure.png`: chart of answers found and refusals held per configuration

## Run it

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install chromadb sentence-transformers pandas matplotlib jupyter nbformat python-dotenv
jupyter notebook
```

Open `rag_notebook.ipynb` and choose Kernel > Restart & Run All. No API key is needed. Without one, the generate step prints an offline answer built from the retrieved context.
