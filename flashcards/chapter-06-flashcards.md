## Chapter 6: Domain 3 (Continued): RAG Architecture & Vector Databases — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | RAG vs Fine-tuning decision rule for the exam? | Dynamic data or frequently changing knowledge → RAG. Change model behavior, style, or tone → Fine-tuning. Exam keyword: 'frequently updated' = RAG, 'adopt specific style' = fine-tune. |
| 2 | OpenSearch Serverless pricing for vector search? | $0.24 per OCU-hour. Auto-scales to zero when idle. Exam tip: Best for unpredictable/bursty traffic. Compare against Aurora pgvector continuous costs. |
| 3 | Aurora pgvector maximum vectors per table? | 1 million vectors per table. Exam tests this limit. Above 1M requires table partitioning. Pricing: db.t3.medium at $0.12/hour continuous (no auto-scaling). |
| 4 | 5 steps of RAG workflow in order? | 1) Embed user query 2) Search vector DB 3) Retrieve top-k documents 4) Augment prompt with docs 5) Generate response. Exam tests: where does Bedrock get invoked? Answer: step 5 only. |
| 5 | OpenSearch Serverless k-NN algorithm for fast vector search? | HNSW (Hierarchical Navigable Small World). Approximate k-NN optimized for low latency on millions of vectors. Sub-second query times. Exam: HNSW = fast approximate, not exact search. |
| 6 | When does RAG make sense vs passing all docs in context? | Use RAG when: docs exceed context window, cost of tokens is high, or only subset is relevant per query. Exam trap: 'use 200K context' sounds good but costs far more than RAG retrieval. |
| 7 | Aurora pgvector vs OpenSearch Serverless: steady workload, 24/7 queries? | Aurora pgvector is more cost-effective: $0.12/hour = ~$86/month continuous. OpenSearch Serverless ~$170+/month if always active. Exam: steady load = provisioned cheaper, bursty = serverless cheaper. |
| 8 | Common RAG prompt engineering mistake causing model to ignore retrieved docs? | Not explicitly instructing model to use the context. Must say: 'Answer based on the following documents:' or 'Use only the provided context'. Exam tests this RAG workflow gotcha. |
| 9 | Vector database options on AWS for RAG? | 1) OpenSearch Serverless (k-NN plugin, serverless), 2) Aurora pgvector (RDS PostgreSQL extension), 3) FAISS self-managed on EC2. Exam: know pricing and scaling differences. |
| 10 | What does 'augment prompt' mean in RAG workflow step 4? | Concatenate retrieved documents with user query into final prompt. Format: 'Context: [docs]\n\nQuestion: [query]\n\nAnswer:'. This is prompt construction, not a model API call. |
| 11 | Fine-tuning use case: medical assistant with formal tone and quarterly-updated clinical data? | Fine-tuning is optimal. Reason: formal tone = behavior change (fine-tuning strength). Quarterly updates = static enough for fine-tuning. Exam: 'adopt tone' = fine-tune, 'weekly updates' = RAG. |
| 12 | Typical top-k value for RAG document retrieval? | 3-10 documents. Too low (k=1) misses context. Too high (k=50) adds noise and token costs. Exam: if question mentions 'irrelevant responses', consider k is too high or prompt doesn't use context. |
