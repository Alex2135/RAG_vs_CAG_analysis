# RAG vs CAG with Llama 3.1 8B Model

This repository demonstrates and compares two powerful approaches for knowledge injection in large language models:

* **Retrieval-Augmented Generation (RAG)**
* **Cache-Augmented Generation (CAG)**

The experiments use the quantized Llama 3.1 8B Instruct model and analyze their effectiveness and efficiency for Ukrainian pop culture question-answering.

---

## Requirements

* Python 3.10
* Poetry (for environment and dependency management)
* Up to 16GB VRAM (GPU highly recommended for Llama 3.1 8B Instruct)
* [Hugging Face account](https://huggingface.co/join) with accepted request for the `meta-llama/Llama-3.1-8B-Instruct` model

---

## Installation

1. **Clone this repository**

   ```bash
   git clone <YOUR_REPO_URL>
   cd <YOUR_REPO_DIRECTORY>
   ```

2. **Set up the Poetry virtual environment**

   ```bash
   poetry config virtualenvs.in-project true
   poetry env use python3.10
   source .venv/bin/activate
   poetry install
   ```

3. **Request access to the Llama 3.1 8B Instruct model**

   * Visit: [https://huggingface.co/meta-llama/Llama-3.1-8B-Instruct](https://huggingface.co/meta-llama/Llama-3.1-8B-Instruct)
   * Click “Access request” and wait for approval

4. **Log in to Hugging Face from the notebook**

   * Insert your HF token when prompted (from [https://huggingface.co/settings/tokens](https://huggingface.co/settings/tokens))

---

## Running the Experiment

**Notebook script:**
`RAG vs CAG with Llama3.1 8b model.py`

To execute the notebook as a script:

```bash
python "RAG vs CAG with Llama3.1 8b model.py"
```

Or open in Jupyter Lab (recommended for step-by-step analysis):

```bash
poetry run jupyter lab
```

---

## What the Code Does

* **Loads a quantized Llama 3.1 8B model and tokenizer**
* **Prepares pop culture context** (biography of Stepan Giga) for experiments
* **Implements three knowledge-injection strategies**:

  1. **Direct context-injection:** Entire biography as prompt
  2. **RAG:** FAISS+MiniLM-based retrieval of relevant context chunks for each question
  3. **CAG:** One-time KV-caching of knowledge, enabling efficient follow-up questions
* **Compares number of input tokens required by each method**
* **Visualizes results** (absolute & relative token usage) using matplotlib

---

## Results & Interpretation

The experiment demonstrates the trade-offs between classic context-stuffing, RAG, and CAG for token efficiency and suitability to large LLMs like Llama-3.

---

## Citation & License

* [Original CAG implementation](https://github.com/hhhuang/CAG)
* [Meta Llama 3.1 8B Instruct](https://huggingface.co/meta-llama/Llama-3.1-8B-Instruct)

---