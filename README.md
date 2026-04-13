# Advanced LLM Systems
Structured QLoRA & Enterprise RAG
## Overview
This project implements advanced LLM system techniques including:
- **Structured JSON extraction** via QLoRA fine-tuning
- **Advanced RAG architectures** (Parent-Document Retrieval, HyDE)
- **Prompt injection defense** via sandboxing
## Requirements
```toml
dependencies = [
    "accelerate>=1.11.0",
    "bitsandbytes>=0.48.1",
    "datasets<4.0",
    "faiss-cpu>=1.12.0",
    "ipykernel>=7.2.0",
    "numpy>=2.4.2",
    "peft>=0.17.1",
    "pypdf>=6.1.1",
    "sentence-transformers>=5.1.1",
    "torch>=2.10.0",
    "transformers>=4.57.0",
]
```
Install with uv and set up your Hugging Face API token (requires access to Llama 3.2 models).
## Project Structure
### Part 1: Structured QLoRA
Fine-tunes Qwen3.5-0.8B-Base to extract structured JSON from clinical text:
- 4-bit NF4 quantization with double quantization
- LoRA with 0.3-0.6% trainable parameters
- Training on NCBI Disease dataset
- Validates JSON output parsing
### Part 2: Advanced RAG
**Task 2.1: Parent-Document Retrieval**
- Downloads "Attention Is All You Need" paper
- Creates parent chunks (1000 chars) and child chunks (200 chars)
- Embeds child chunks in FAISS, retrieves parent chunks
**Task 2.2: HyDE**
- Generates hypothetical academic answer using LLM
- Embeds hallucinated answer for better retrieval
**Task 2.3: Prompt Injection Defense**
- Tests defense against malicious injected commands
- Uses XML sandboxing to isolate untrusted context
## Running
Open `llm_system.ipynb` in Jupyter and run cells sequentially.
