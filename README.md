# RAG Document Q&A (Free, Open-Source)

A question-answering system that retrieves relevant passages from a set of documents and generates grounded answers, using only free open-source models.

## Problem
Language models often make up answers. Retrieval-augmented generation (RAG) reduces this by giving the model relevant source text and instructing it to answer only from that text.

## Approach
1. **Embedding:** documents are converted to vectors with `all-MiniLM-L6-v2` (Sentence Transformers).
2. **Retrieval:** the top-k documents are found using cosine similarity.
3. **Generation:** `Qwen2.5-1.5B-Instruct` writes an answer using only the retrieved context, and says "I don't know" if the answer is not there.

## Results
- Relevant questions (e.g. "How can I stop my model from overfitting?") return answers grounded in the retrieved documents.
- Out-of-scope questions (e.g. "What is the capital of France?") correctly return "I don't know."

## How to run
Click the "Open in Colab" badge in the notebook, set the runtime to T4 GPU, and run all cells. No API key or payment required.

## Limitations and future work
- Small 1.5B model sometimes adds irrelevant detail to its explanations.
- Knowledge base is currently 5 sample sentences; next step is loading real lecture notes (PDF/text).
- Add a quantitative evaluation set of questions with expected answers.
