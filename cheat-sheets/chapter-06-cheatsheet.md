# Chapter 6: RAG Architecture & Vector Databases - Exam Cheat Sheet

## RAG vs Fine-Tuning Decision Matrix
| Scenario | Use RAG | Use Fine-Tuning |
|----------|---------|----------------|
| Data changes frequently (daily/weekly) | ✅ | ❌ |
| Need to change model tone/style | ❌ | ✅ |
| Large document corpus (GB+) | ✅ | ❌ |
| Change model behavior/reasoning | ❌ | ✅ |
| Static domain knowledge (quarterly updates) | ❌ | ✅ |
| Quick updates required (no retrain time) | ✅ | ❌ |
| **Exam keyword**: 'frequently updated' | ✅ | ❌ |
| **Exam keyword**: 'adopt formal tone' | ❌ | ✅ |

## Vector Database Service Comparison
| Feature | OpenSearch Serverless | Aurora pgvector | FAISS (self-managed) |
|---------|----------------------|-----------------|----------------------|
| **Pricing** | $0.24/OCU-hour | $0.12/hour (db.t3.medium) | EC2 costs (varies) |
| **Scaling** | Auto-scales to zero | Manual scaling | Manual |
| **Vector limit** | Millions+ | 1M per table (exam!) | No limit |
| **Latency** | Sub-second (HNSW) | ~100ms (smaller datasets) | Varies |
| **Management** | Serverless (none) | RDS managed | Full self-management |
| **Best for** | Bursty/unpredictable traffic | Steady 24/7 workload | Full control needed |
| **Monthly cost (idle 16h/day)** | ~$150 | ~$86 (continuous) | $50+ (continuous) |

## RAG Workflow (5 Steps - Exam Tests Order)
1. **Embed query**: User query → embedding model (Titan Embeddings) → vector
2. **Search vector DB**: Query vector → k-NN search → similarity scores
3. **Retrieve top-k**: Return k most similar documents (typical k=3-10)
4. **Augment prompt**: Concatenate docs + query → "Context: [docs]\n\nQuestion: [query]"
5. **Generate response**: Augmented prompt → Bedrock API → final answer

**Exam trap**: Where does Bedrock get called? **Step 5 only** (generation).

## Key Numbers & Limits (Heavily Tested)
- **Aurora pgvector**: Max 1M vectors per table
- **OpenSearch Serverless**: $0.24/OCU-hour, auto-scales
- **Aurora db.t3.medium**: $0.12/hour = $86.40/month continuous
- **Typical top-k**: 3-10 documents (balance relevance vs noise)
- **HNSW algorithm**: Approximate k-NN, sub-second latency at scale

## Common Exam Scenarios

### Scenario: 'Frequently changing data'
- **Answer**: RAG with nightly/weekly re-indexing
- **Wrong answer trap**: Fine-tuning (too slow to retrain)

### Scenario: 'Model must adopt formal/medical/legal tone'
- **Answer**: Fine-tuning on style examples
- **Wrong answer trap**: RAG alone (doesn't change behavior)

### Scenario: 'Unpredictable traffic, long idle periods'
- **Answer**: OpenSearch Serverless (scales to zero)
- **Wrong answer trap**: Aurora pgvector (continuous costs)

### Scenario: '2M vectors, need sub-2-second response'
- **Answer**: OpenSearch Serverless with HNSW
- **Wrong answer trap**: Aurora pgvector (1M limit per table)

### Scenario: 'Model ignores retrieved documents'
- **Answer**: Prompt doesn't explicitly instruct to use context
- **Wrong answer trap**: Blaming approximate search or top-k value

## Cost Optimization Rules
- **Bursty traffic** → OpenSearch Serverless (pay for active hours only)
- **Steady 24/7** → Aurora pgvector (continuous cheaper than serverless)
- **High token costs** → RAG (retrieve relevant docs vs full context window)
- **Frequent updates** → RAG (avoid fine-tuning costs)

## Prompt Engineering for RAG (Exam Gotcha)
**Wrong**: Just concatenate documents
**Correct**: Explicit instruction
```
Context: [retrieved documents]

Question: [user query]

Answer based ONLY on the context above:
```

## Hybrid Architecture (When to Combine)
- **Fine-tune + RAG**: Change behavior (fine-tune) + inject dynamic data (RAG)
- **Example**: Content moderation with evolving policies
  - Fine-tune: Classification behavior (safe/unsafe logic)
  - RAG: Monthly-updated policy details

## Exam Red Flags
- "Use 200K context for all docs" → Wrong, use RAG instead
- "Fine-tune weekly on new data" → Wrong, use RAG instead
- "RAG will change model tone" → Wrong, use fine-tuning
- "Aurora pgvector for 5M vectors" → Wrong, exceeds 1M limit
- "Exact k-NN for 2-second SLA" → Wrong, use approximate (HNSW)
