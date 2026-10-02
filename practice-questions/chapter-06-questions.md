## Chapter 6: Domain 3 (Continued): RAG Architecture & Vector Databases — Practice Questions

**Q1.** A financial services company needs to build a chatbot that answers questions about their constantly updated regulatory compliance documents. New regulations are published weekly, and the chatbot must provide accurate information within 24 hours of publication. The company wants to minimize operational overhead. Which solution BEST meets these requirements?

A) Fine-tune Amazon Titan Text on the compliance documents weekly and deploy the updated model
B) Implement RAG using OpenSearch Serverless vector engine with nightly document ingestion
C) Use Claude with a 200K context window and pass all documents in every prompt
D) Fine-tune Claude on the compliance documents and use prompt engineering for updates

<details>
<summary>Answer</summary>

**Correct: B**

RAG with OpenSearch Serverless is optimal for frequently changing data. Documents can be embedded and indexed nightly without retraining models. OpenSearch Serverless auto-scales and requires no cluster management ($0.24/OCU-hour). RAG retrieves only relevant docs per query, keeping prompts manageable.

**Why the others are wrong:**
- Fine-tuning weekly is operationally expensive, requires retraining time (hours/days), and model deployment overhead. Fine-tuning is for behavior changes, not dynamic data.
- Passing all documents in context is cost-prohibitive (massive token usage) and hits context limits. Even 200K tokens cannot hold weekly-updated regulatory documents at scale.
- Fine-tuning Claude doesn't solve the dynamic data problem—still need to retrain weekly. Prompt engineering alone cannot inject updated document knowledge without RAG.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A startup is building a customer support chatbot using RAG architecture. They have 500,000 product documentation vectors. They expect unpredictable traffic with long idle periods. Which vector database solution minimizes cost while meeting these requirements?

A) OpenSearch Serverless with k-NN plugin
B) Aurora PostgreSQL with pgvector extension on db.t3.medium
C) Self-managed FAISS on EC2 t3.large
D) OpenSearch provisioned cluster with 3 data nodes

<details>
<summary>Answer</summary>

**Correct: A**

OpenSearch Serverless auto-scales to zero during idle periods, charging only for active OCUs ($0.24/OCU-hour). With unpredictable traffic, this avoids paying for idle capacity. It handles 500K vectors easily and requires no cluster management.

**Why the others are wrong:**
- Aurora db.t3.medium costs $0.12/hour continuously (720 hours/month = $86.40) even during idle periods. No auto-scaling to zero. More cost-effective for steady workloads.
- Self-managed FAISS requires continuous EC2 instance costs, operational overhead for scaling, and manual index management. No auto-scaling. Higher operational burden.
- Provisioned OpenSearch cluster charges continuously for all 3 nodes regardless of traffic. No auto-scaling to zero. Better for predictable, sustained workloads.

</details>

---

**Q3.** An e-commerce company implements RAG for product recommendations. The workflow must: embed user query, search 2M product vectors, retrieve top 10 products, augment prompt with product details, and generate response. Average query response time must be under 2 seconds. Which vector database configuration BEST supports this?

A) Aurora pgvector with read replicas and query caching
B) OpenSearch Serverless with HNSW algorithm for approximate k-NN
C) FAISS with exact k-NN search on GPU instances
D) DynamoDB with vector embeddings stored as binary attributes

<details>
<summary>Answer</summary>

**Correct: B**

OpenSearch Serverless k-NN plugin uses HNSW (Hierarchical Navigable Small World) algorithm optimized for low-latency approximate nearest neighbor search on millions of vectors. Sub-second query times at scale. Auto-scales for traffic bursts.

**Why the others are wrong:**
- Aurora pgvector max limit is 1M vectors per table (exam tests this). 2M vectors requires partitioning. Also slower than purpose-built vector search engines for k-NN queries.
- Exact k-NN on 2M vectors is too slow for 2-second SLA. GPU instances are expensive and still require manual scaling. FAISS exact search doesn't meet latency requirements at scale.
- DynamoDB is not optimized for vector similarity search. No native k-NN support. Would require full table scan or custom indexing. Cannot meet 2-second latency for vector search.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A medical research team needs an AI assistant to answer questions about clinical trial data. The assistant must adopt a formal, cautious tone specific to medical research and avoid speculation. The knowledge base is stable (updated quarterly). Which approach is MOST appropriate?

A) Implement RAG with quarterly document re-indexing in OpenSearch
B) Fine-tune a foundation model on clinical trial reports with medical writing style examples
C) Use prompt engineering with RAG to inject relevant trial data and tone instructions
D) Fine-tune on clinical data and use RAG for retrieving specific trial details

<details>
<summary>Answer</summary>

**Correct: B**

Fine-tuning is optimal for changing model BEHAVIOR and STYLE. The requirement is formal, cautious tone—a behavior change. Data is static (quarterly updates), making fine-tuning practical. Exam key: behavior change = fine-tuning, dynamic data = RAG.

**Why the others are wrong:**
- RAG alone doesn't change model tone/behavior reliably. It injects facts but doesn't train the model to adopt specific writing styles. Over-engineering for static quarterly data.
- Prompt engineering for tone is less reliable than fine-tuning for consistent behavior. RAG adds complexity when data is static. Combination is unnecessary overhead.
- Combining both adds cost and complexity. Since data is static (quarterly), fine-tuning alone handles both knowledge and behavior. RAG benefit is minimal for infrequent updates.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** During RAG implementation, a developer embeds user queries using Amazon Titan Embeddings and searches OpenSearch Serverless. Retrieved documents are concatenated and added to the prompt. The model frequently generates responses unrelated to the retrieved documents. What is the MOST likely cause?

A) The embedding model dimension doesn't match the vector database index dimension
B) Top-k value is too high, introducing irrelevant documents into the prompt
C) The prompt template doesn't explicitly instruct the model to use the retrieved context
D) OpenSearch Serverless HNSW algorithm is returning approximate matches instead of exact matches

<details>
<summary>Answer</summary>

**Correct: C**

Common RAG failure: retrieved documents are in the prompt but the model doesn't know to use them. Prompt must explicitly say 'Answer based on the following documents:' or similar. Exam tests this RAG workflow gotcha.

**Why the others are wrong:**
- Dimension mismatch would cause search errors or no results, not irrelevant responses. This is caught during initial setup, not a runtime behavior issue.
- Too high top-k adds noise but model should still use relevant docs if instructed. This is secondary to missing prompt instructions. Typical top-k is 3-10, errors are obvious.
- HNSW approximate search is designed for this use case and provides high recall. Approximate vs exact is not the issue—the model is ignoring the context entirely due to prompt design.

</details>

---

**Q6.** A company is deciding between OpenSearch Serverless and Aurora pgvector for their RAG system. Requirements: 800K product vectors, average 50 queries/minute during business hours (8 hours/day), near-zero queries overnight. Estimated monthly costs must be compared. Which cost analysis is CORRECT?

A) OpenSearch Serverless: ~$350/month (scales to zero), Aurora pgvector: ~$90/month (continuous)
B) OpenSearch Serverless: ~$150/month (scales to zero), Aurora pgvector: ~$90/month (continuous)
C) OpenSearch Serverless: ~$600/month (minimum OCU), Aurora pgvector: ~$200/month (continuous)
D) OpenSearch Serverless: ~$90/month (scales to zero), Aurora pgvector: ~$350/month (continuous)

<details>
<summary>Answer</summary>

**Correct: B**

OpenSearch Serverless charges only for active OCUs. 8 hours/day × 30 days = 240 hours. At ~$0.24/OCU-hour with typical 2-3 OCUs for this workload = ~$150/month. Aurora db.t3.medium at $0.12/hour × 720 hours = ~$86.40/month continuous. Exam tests cost comparisons.

**Why the others are wrong:**
- $350 for OpenSearch is too high—overestimates OCU usage. $90 for Aurora is approximately correct but the comparison ratio is wrong.
- $600 for OpenSearch assumes continuous 3+ OCUs which contradicts the auto-scaling benefit. $200 for Aurora overprices db.t3.medium significantly.
- $90 for OpenSearch is too low—underestimates OCU-hours needed. $350 for Aurora is wrong instance pricing—db.t3.medium is $0.12/hour not $0.49/hour.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** A RAG system must process user queries through this workflow: 1) Embed query 2) Search vector DB 3) Retrieve top-k documents 4) Augment prompt 5) Generate response. The system uses Amazon Bedrock for generation. Where in this workflow does Amazon Bedrock get invoked?

A) Steps 1 and 5: embedding the query and generating the final response
B) Step 5 only: generating the response after prompt augmentation
C) Steps 1, 4, and 5: embedding, augmenting, and generating
D) Steps 2 and 5: searching vectors and generating the response

<details>
<summary>Answer</summary>

**Correct: B**

Amazon Bedrock foundation models are invoked at step 5 for generation. Embedding (step 1) uses Amazon Titan Embeddings or similar. Vector search (steps 2-3) uses OpenSearch/Aurora. Augmentation (step 4) is prompt construction. Generation (step 5) calls Bedrock API with augmented prompt.

**Why the others are wrong:**
- Embedding (step 1) typically uses dedicated embedding models (Titan Embeddings API), not the same Bedrock foundation model used for generation. These are separate services.
- Augmentation (step 4) is string concatenation/formatting, not a model call. Bedrock is not involved in prompt construction, only in consuming the final prompt.
- Vector search (step 2) is database query operation (OpenSearch, Aurora), not a Bedrock model invocation. Bedrock has no role in vector database operations.

</details>

---

**Q8.** A content moderation system needs to classify user-generated posts as safe/unsafe based on company policies. Policies evolve monthly based on new abuse patterns. The system must adapt quickly without extensive retraining. Posts contain dynamic references to current events. Which architecture is MOST appropriate?

A) RAG: embed policy documents, retrieve relevant policies per post, classify with foundation model
B) Fine-tune: monthly fine-tuning on labeled posts with updated policy examples
C) Prompt engineering: include full policy text in every classification prompt
D) Fine-tune for classification behavior, use RAG to inject current policy details

<details>
<summary>Answer</summary>

**Correct: D**

Hybrid approach is optimal: Fine-tuning trains the model's classification BEHAVIOR (safe/unsafe decision-making), while RAG injects monthly-updated POLICY DETAILS. Classification is a behavior (fine-tuning), policies are dynamic data (RAG). Exam tests when to combine approaches.

**Why the others are wrong:**
- RAG alone doesn't train classification behavior—model may not make consistent safe/unsafe decisions. Foundation models aren't pre-trained for company-specific content moderation logic.
- Monthly fine-tuning is operationally expensive and slow to adapt. Fine-tuning on abuse patterns is reactive. Doesn't handle dynamic current events in posts well.
- Passing full policy text every time is token-inefficient and costly at scale. Doesn't solve the classification behavior problem—model still needs to learn how to apply policies.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

