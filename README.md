# NYSgpt Rerankers on Amazon SageMaker

Usage notebook and sample data for three NYSgpt cross-encoder rerankers on AWS Marketplace:

| Model | Domain | Result |
|---|---|---|
| NYSgpt Scientific Reranker | Scientific papers | 93% top-1 accuracy vs 68% for OpenAI embeddings ([card](https://huggingface.co/NYSgpt/44b-reranker)) |
| NYSgpt Scientific Reranker Mini | Scientific papers, 22.7M params | 87% top-1 accuracy vs 68% for OpenAI embeddings ([card](https://huggingface.co/NYSgpt/44b-reranker-mini)) |
| NYSgpt Biomedical Reranker | bioRxiv / medRxiv | Beats the NLM's MedCPT cross-encoder on its own candidate pool, R@10 0.544 vs 0.525 ([card](https://huggingface.co/NYSgpt/biomed-reranker)) |

## Input
`application/json`: `{"query": "text", "documents": ["text", ...], "top_k": 10}` or `{"pairs": [["query", "document"], ...]}`

## Output
`application/json`: `{"scores": [...], "ranking": [{"index": i, "score": s}, ...]}` — higher is more relevant.

## Contents
- `reranker-usage.ipynb` — subscribe, deploy a real-time endpoint, rerank, run batch transform, clean up.
- `data/sample-input.json`, `data/sample-output.json`

Support: Brendan@nysgpt.com
