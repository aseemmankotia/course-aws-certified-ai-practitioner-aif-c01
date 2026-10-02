## Chapter 7: Domain 3 (Continued): Fine-Tuning, Bedrock Agents & Model Evaluation — Practice Questions

**Q1.** A financial services company needs to adapt a foundation model to understand industry-specific terminology like 'prospectus', 'fiduciary duty', and 'amortization schedule'. They have 50GB of unlabeled financial documents but no labeled training data. Which approach should they use?

A) Fine-tuning with the unlabeled documents after manually labeling a subset
B) Continued pre-training on the unlabeled financial corpus
C) Prompt engineering with few-shot examples of financial terms
D) RAG using Bedrock Knowledge Bases with the financial documents

<details>
<summary>Answer</summary>

**Correct: B**

Continued pre-training adapts a model to a specific domain (financial) using large amounts of unlabeled text. This is the exact use case: domain adaptation without task-specific labels.

**Why the others are wrong:**
- Fine-tuning requires labeled data for a specific task (like sentiment or classification). They have no labels and don't need task-specific behavior—just domain understanding.
- Prompt engineering won't teach the model new terminology it hasn't seen. The model needs to learn these domain-specific terms through training.
- RAG retrieves documents at inference time but doesn't adapt the model's understanding of terminology. It's for knowledge lookup, not domain adaptation.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A healthcare company wants their Bedrock Agent to check patient eligibility by calling an external insurance API, then retrieve relevant medical guidelines from their document repository before responding. How should they implement this?

A) Create one action group that calls both the API and Knowledge Base sequentially
B) Create an action group for the API call and integrate a Knowledge Base for document retrieval
C) Use two separate Agents—one for API calls and one for Knowledge Base queries
D) Use Bedrock Guardrails to orchestrate the API call and document retrieval

<details>
<summary>Answer</summary>

**Correct: B**

Bedrock Agents use action groups (Lambda functions) to call external APIs and Knowledge Bases (RAG) to retrieve documents. These are two separate components that work together within a single Agent.

**Why the others are wrong:**
- Action groups are for API calls only (Lambda functions). Knowledge Bases are a separate integration for RAG—they don't go inside action groups.
- One Agent can handle both API calls (via action groups) and document retrieval (via Knowledge Bases). Multiple Agents add unnecessary complexity.
- Guardrails filter content (hate speech, PII). They don't orchestrate workflows or call APIs. That's the Agent's job.

</details>

---

**Q3.** A company fine-tuned Amazon Titan Text for extracting product names from customer reviews. They're evaluating the model's output against human-labeled reference extractions. Which metric is MOST appropriate?

A) BLEU score to measure n-gram overlap with reference extractions
B) ROUGE score to measure recall of product names in the extraction
C) BERTScore to measure semantic similarity of extracted product names
D) Perplexity to measure the model's confidence in its extractions

<details>
<summary>Answer</summary>

**Correct: B**

ROUGE measures recall (what percentage of reference n-grams were captured). For extraction tasks, you care most about recall—did the model capture all the product names that humans identified?

**Why the others are wrong:**
- BLEU measures precision (how many generated n-grams match reference). Extraction tasks prioritize recall over precision—missing items is worse than extra items.
- BERTScore measures semantic similarity using embeddings. Product name extraction needs exact match, not semantic similarity ("iPhone 15" ≠ "Apple smartphone").
- Perplexity measures how well a model predicts the next token. It's for language model evaluation, not extraction task quality.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A legal firm is deploying a Bedrock Agent to assist with contract review. They need to prevent the Agent from discussing ongoing litigation or competitor strategies, and must redact any Social Security Numbers in responses. What should they implement?

A) Action groups with Lambda functions to filter sensitive topics and PII
B) Bedrock Guardrails with denied topics for litigation/competitors and PII redaction enabled
C) Bedrock Knowledge Base filters to exclude sensitive documents from retrieval
D) Fine-tune the model with examples of appropriate responses to sensitive queries

<details>
<summary>Answer</summary>

**Correct: B**

Bedrock Guardrails provide content filters (denied topics) and PII redaction. This is exactly what Guardrails are designed for—preventing specific discussion topics and removing sensitive data.

**Why the others are wrong:**
- Action groups call external APIs. They're not designed for content filtering. You'd need custom code for every possible sensitive scenario—Guardrails are purpose-built for this.
- Knowledge Base filters control what documents are indexed/retrieved. They don't prevent the Agent from discussing topics or redact PII from generated responses.
- Fine-tuning teaches task-specific behavior but can't reliably enforce hard rules about never discussing topics or always redacting PII. Guardrails enforce these rules at inference time.

</details>

---

**Q5.** A machine translation system generates: "The cat sat on the mat." Reference translation: "The feline rested on the rug." The system outputs: "A cat was sitting on a mat." Which evaluation metric would rate this output HIGHEST?

A) BLEU score because it measures exact n-gram matches
B) ROUGE score because it measures recall of reference words
C) BERTScore because it captures semantic similarity despite word differences
D) All three metrics would rate this equally as the meaning is preserved

<details>
<summary>Answer</summary>

**Correct: C**

BERTScore uses embeddings to measure semantic similarity. "cat sitting mat" and "feline rested rug" have different words but similar meaning—BERTScore captures this. It's designed for paraphrase quality.

**Why the others are wrong:**
- BLEU measures exact n-gram overlap. "cat/feline", "sat/rested", "mat/rug" don't match. BLEU would score this LOW despite correct meaning.
- ROUGE measures recall of reference n-grams. Again, the words differ (cat≠feline), so ROUGE recall would be LOW.
- BLEU and ROUGE would score this poorly due to word mismatches. Only BERTScore accounts for semantic equivalence.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** A startup wants to build a customer service Agent that can query their product database (via API), search their help documentation (in Confluence), and escalate to human agents when needed. They have limited ML expertise. What AWS service BEST fits this requirement?

A) Fine-tune Amazon Titan Text on customer service conversations, then deploy with API integration
B) Use Bedrock Agents with action groups for database API and Knowledge Base connected to Confluence
C) Build a custom orchestration layer with Lambda functions calling Bedrock models and APIs
D) Use SageMaker to train a custom model on their help documentation and product data

<details>
<summary>Answer</summary>

**Correct: B**

Bedrock Agents handle exactly this: multi-step orchestration with API calls (action groups) and document retrieval (Knowledge Bases). Confluence is a supported data source. No ML expertise needed—managed service.

**Why the others are wrong:**
- Fine-tuning teaches task-specific behavior but doesn't handle orchestration (API calls + document search + escalation logic). You'd still need to build the orchestration layer.
- Custom Lambda orchestration works but requires significant development. Bedrock Agents provide this orchestration out-of-the-box with no code.
- SageMaker requires ML expertise to train and deploy models. The startup has limited expertise and doesn't need custom models—foundation models + orchestration solve this.

</details>

---

**Q7.** A company fine-tuned Claude on 10,000 labeled customer service chats to classify intent (billing, technical, account). Post-deployment, accuracy dropped from 92% to 78%. What is the MOST likely cause?

A) The model needs continued pre-training on customer service domain text
B) The production data distribution differs from the training data (data drift)
C) Fine-tuning dataset was too small—need 100,000+ examples minimum
D) Should have used prompt engineering instead of fine-tuning

<details>
<summary>Answer</summary>

**Correct: B**

Accuracy drop post-deployment indicates data drift—production inputs differ from training data. Common in production systems. The model was trained on historical data that doesn't match current patterns.

**Why the others are wrong:**
- Continued pre-training adapts to domain vocabulary. The model already understands customer service language (it worked at 92%). The issue is distribution shift, not vocabulary.
- 10,000 labeled examples is reasonable for fine-tuning classification. More data helps but wouldn't cause a 14-point accuracy drop—distribution mismatch is more likely.
- Fine-tuning was working (92% accuracy). Switching to prompt engineering wouldn't fix data drift and would likely perform worse than a fine-tuned model.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** A summarization model generates a 3-sentence summary of a 500-word article. The reference summary contains 8 key points, and the generated summary captures 5 of them but includes 1 hallucinated fact. Which metric will BEST reflect the model's recall of important information?

A) BLEU-4 score to measure 4-gram overlap accuracy
B) ROUGE-L score to measure longest common subsequence recall
C) BERTScore precision to identify the hallucinated fact
D) ROUGE-1 recall to measure unigram coverage of reference points

<details>
<summary>Answer</summary>

**Correct: D**

ROUGE-1 recall measures what percentage of reference unigrams appear in the summary. Since the question asks about 'recall of important information', ROUGE recall is the right metric (5 out of 8 points = 62.5% recall).

**Why the others are wrong:**
- BLEU measures precision (how much of the generated text matches reference). The question asks about recall (coverage of reference). BLEU is for translation, not summarization.
- ROUGE-L measures longest common subsequence, which captures sentence-level structure. ROUGE-1 recall is more direct for measuring coverage of key points.
- BERTScore precision measures hallucinations indirectly, but the question asks specifically about recall of reference information, not precision or hallucination detection.

</details>

---

