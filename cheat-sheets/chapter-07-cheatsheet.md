# Domain 3 (Cont.): Fine-Tuning, Agents & Evaluation - Quick Reference

## Fine-Tuning vs Continued Pre-Training

| Aspect | Fine-Tuning | Continued Pre-Training |
|--------|-------------|------------------------|
| **Data Type** | Labeled (task-specific) | Unlabeled (domain text) |
| **Use Case** | Adapt to specific task (classification, NER, sentiment) | Adapt to domain vocabulary (medical, legal, financial) |
| **Data Size** | 500-10K examples typical | 50GB+ text corpus |
| **When to Use** | Have labels, need task behavior | Have domain corpus, need terminology understanding |
| **Exam Frequency** | Heavily tested | Rarely tested (edge case) |

**Exam Trap:** If scenario has unlabeled data + domain adaptation → continued pre-training. If labeled data + task → fine-tuning.

---

## Bedrock Agents Architecture

### Components

| Component | Purpose | Example |
|-----------|---------|----------|
| **Action Groups** | Call external APIs via Lambda | Check inventory, process payment, query database |
| **Knowledge Bases** | RAG document retrieval | Search help docs, retrieve policies, find product specs |
| **Guardrails** | Content filtering + PII redaction | Block hate speech, redact SSN, deny specific topics |
| **Orchestration** | Multi-step workflow | Agent decides: call API → retrieve docs → generate response |

### Knowledge Base Data Sources
- Amazon S3
- Confluence  
- SharePoint
- Salesforce
- Web crawlers

**Exam Trap:** Action groups ≠ Knowledge Bases. Action groups = API calls. Knowledge Bases = document retrieval.

---

## Bedrock Guardrails

| Filter Type | Purpose | Exam Note |
|-------------|---------|------------|
| **Content Filters** | Block hate, violence, sexual content, insults | Applied at inference time |
| **PII Redaction** | Remove SSN, credit cards, emails, addresses | Works on input and output |
| **Denied Topics** | Prevent discussing specific subjects | Define topics Agent can't discuss |
| **Word Filters** | Block custom word lists | Custom profanity or competitor names |

**Exam Trap:** Guardrails enforce rules at inference time. Fine-tuning can't reliably enforce "never discuss X."

---

## Model Evaluation Metrics

### BLEU Score
- **Range:** 0-1 (higher = better)
- **Measures:** N-gram overlap with reference (precision)
- **Best For:** Machine translation
- **Exam Note:** Exact word matches required. "cat" ≠ "feline" → low score

### ROUGE Score  
- **Range:** 0-1 (higher = better)
- **Measures:** Recall of reference n-grams
- **Types:** ROUGE-1 (unigrams), ROUGE-2 (bigrams), ROUGE-L (longest sequence)
- **Best For:** Summarization quality
- **Exam Note:** Focus on recall (coverage of key points)

### BERTScore
- **Range:** 0-1 (higher = better)  
- **Measures:** Semantic similarity using embeddings
- **Best For:** Paraphrase detection, semantic equivalence
- **Exam Note:** Handles synonyms. "cat sat" vs "feline rested" → high score

### Quick Decision Tree
```
Translation task? → BLEU
Summarization task? → ROUGE  
Paraphrase/semantic similarity? → BERTScore
Extraction task? → ROUGE (focus on recall)
```

**Exam Trap:** Students use BLEU for summarization (wrong—use ROUGE for recall).

---

## Common Exam Scenarios

### Scenario: API + Document Search
**Question:** Agent needs to call API and search documents.  
**Answer:** Action group (Lambda for API) + Knowledge Base (RAG for docs)

### Scenario: Unlabeled Domain Text  
**Question:** 50GB unlabeled medical text, need domain understanding.  
**Answer:** Continued pre-training (NOT fine-tuning—no labels)

### Scenario: Block Sensitive Topics
**Question:** Prevent Agent from discussing litigation.  
**Answer:** Bedrock Guardrails with denied topics (NOT action groups)

### Scenario: Different Words, Same Meaning
**Question:** Evaluate "cat" vs "feline" equivalence.  
**Answer:** BERTScore (NOT BLEU—needs exact matches)

### Scenario: Summarization Quality
**Question:** Check if summary captured all key points.  
**Answer:** ROUGE recall (NOT BLEU—that's for translation)

---

## Numbers to Memorize

- **Fine-tuning:** 500-10K examples typical (no hard minimum)
- **Continued pre-training:** 50GB+ text corpus  
- **BLEU range:** 0-1 (0.4+ considered good for translation)
- **ROUGE range:** 0-1 (0.3-0.5 typical for summaries)
- **BERTScore range:** 0-1 (0.8+ considered high similarity)

---

## Domain 3 Exam Weight: 28%

**Most Tested Topics:**
1. Fine-tuning vs continued pre-training decision  
2. Bedrock Agents: action groups + Knowledge Bases
3. BLEU vs ROUGE vs BERTScore use cases
