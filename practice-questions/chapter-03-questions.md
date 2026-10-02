## Chapter 3: Domain 2: Generative AI Fundamentals & Transformer Architecture — Practice Questions

**Q1.** A company is building a chatbot that needs to process user queries. The architecture team is debating whether to use tokens or embeddings as the primary representation for text processing. Which statement BEST describes the relationship between tokens and embeddings in transformer-based models?

A) Tokens are the output of the model while embeddings are the input; tokens represent semantic meaning while embeddings are just raw text
B) Embeddings are created from tokens; each token is converted to a numerical vector (embedding) that the model can process mathematically
C) Tokens and embeddings are interchangeable terms; both refer to the same concept of converting text to numbers
D) Embeddings are stored in a database while tokens are processed in real-time; embeddings are permanent while tokens are temporary

<details>
<summary>Answer</summary>

**Correct: B**

This is the exact relationship: tokenization happens first (splitting text into smallest units), then each token is mapped to a high-dimensional numerical vector (embedding) that captures semantic meaning. For example, 'Hello world' becomes 2 tokens, which become 2 embeddings of 1536 dimensions each in GPT-3.5.

**Why the others are wrong:**
- Backwards - tokens are the INPUT (text split into units), embeddings are the numerical representation used for processing, not the output
- Tokens and embeddings are distinct concepts with specific technical definitions - not interchangeable. Tokens are discrete units, embeddings are continuous vectors
- Neither is about storage vs. real-time processing - both are transformations that happen during text processing. Embeddings aren't 'permanent' in databases by default

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** An AI startup needs to deploy a language model for a specialized medical diagnosis task with only 50,000 labeled medical records. They have limited computational resources (4 GPUs, 2 weeks timeline). Which approach BEST meets their requirements?

A) Pre-train a new foundation model from scratch on medical literature, then deploy directly without fine-tuning
B) Use an existing foundation model and fine-tune it on their 50,000 medical records to specialize it for diagnosis
C) Create a specialized model by training only on their 50,000 records from random initialization
D) Use a foundation model in zero-shot mode without any fine-tuning since foundation models are pre-trained on massive data

<details>
<summary>Answer</summary>

**Correct: B**

Fine-tuning an existing foundation model is the correct approach: it leverages billions of parameters already pre-trained on massive data, then adapts them to the specific medical task with limited data (50k records) and resources. This is the standard GenAI lifecycle: pre-training (already done) → fine-tuning (their task) → deployment.

**Why the others are wrong:**
- Pre-training from scratch requires billions of tokens, hundreds of GPUs, and months of training - impossible with 4 GPUs and 2 weeks. Foundation models take massive resources to create
- Training from random initialization with only 50k samples will result in poor performance - not enough data. Models need either massive data (billions of tokens) or transfer learning from pre-trained weights
- Zero-shot might work for general tasks but medical diagnosis requires specialized knowledge. Fine-tuning is necessary to adapt the model to medical terminology and diagnostic patterns

</details>

---

**Q3.** A data scientist is comparing RNN and Transformer architectures for a document summarization task with 10,000-token documents. Training time is critical. Which statement BEST explains why Transformers would be preferred over RNNs for this use case?

A) Transformers process all tokens in parallel using self-attention, enabling faster training, while RNNs must process tokens sequentially making them slow for long sequences
B) Transformers use less memory than RNNs because they don't store hidden states, making them better for long documents
C) RNNs have O(n²) complexity while Transformers have O(n) complexity, making RNNs too slow for 10,000 tokens
D) Transformers don't suffer from the vanishing gradient problem while RNNs do, making Transformers more accurate

<details>
<summary>Answer</summary>

**Correct: A**

This is the key advantage: Transformers compute attention between all token pairs in parallel (parallelization), while RNNs must process token 1, then token 2, then token 3 sequentially. For 10,000 tokens, parallel processing dramatically reduces training time. This parallelization is why transformers replaced RNNs despite the O(n²) attention complexity.

**Why the others are wrong:**
- Backwards - Transformers actually use MORE memory due to storing attention matrices (O(n²) space). Self-attention requires computing relationships between all token pairs
- Completely backwards - self-attention in Transformers is O(n²) complexity, RNNs are O(n). Transformers are still faster due to parallelization despite higher complexity
- While RNNs do have vanishing gradients for very long sequences, the primary reason for choosing Transformers in this scenario is training speed through parallelization, not gradient flow

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** During model development, a team notices their transformer model's training time scales poorly as document length increases. They measure: 100 tokens = 2 seconds, 200 tokens = 8 seconds, 400 tokens = 32 seconds. What is causing this scaling pattern?

A) Linear scaling (O(n)) due to sequential token processing in the encoder layers
B) Quadratic scaling (O(n²)) due to self-attention computing relationships between all token pairs
C) Exponential scaling (O(2ⁿ)) due to the decoder generating tokens one at a time
D) Logarithmic scaling (O(log n)) due to the hierarchical structure of attention heads

<details>
<summary>Answer</summary>

**Correct: B**

The pattern (100→2s, 200→8s [4x], 400→32s [4x]) shows quadratic scaling: doubling tokens quadruples time. This is because self-attention computes attention scores between ALL pairs of tokens. For n tokens, there are n² pairs to compute (100 tokens = 10,000 pairs, 200 tokens = 40,000 pairs).

**Why the others are wrong:**
- Linear scaling would show 100→2s, 200→4s, 400→8s (time doubles when tokens double). Transformers process in parallel but attention computation is quadratic
- Exponential would show 100→2s, 200→~4s, 400→~16s. The observed pattern (4x increase per doubling) is quadratic, not exponential
- Transformers don't have hierarchical attention by default, and the pattern clearly shows quadratic not logarithmic scaling

</details>

---

**Q5.** A company wants to deploy a generative AI model for customer service. They have three options: (A) foundation model with zero-shot prompting, (B) fine-tuned model on 100K customer service transcripts, (C) RLHF-aligned model trained with human feedback. The priority is reducing harmful or inappropriate responses. Which option BEST addresses this requirement?

A) Option A (zero-shot) because foundation models are pre-trained on clean, filtered data and won't generate harmful content
B) Option B (fine-tuned) because fine-tuning on company data automatically removes harmful patterns from the model
C) Option C (RLHF-aligned) because alignment with human feedback specifically trains the model to avoid harmful outputs and follow human preferences
D) All three options are equivalent for safety because harmful content filtering happens at the API layer, not during training

<details>
<summary>Answer</summary>

**Correct: C**

RLHF (Reinforcement Learning from Human Feedback) is specifically designed for alignment - training models to be helpful, harmless, and honest. This is the final stage in the GenAI lifecycle: pre-training → fine-tuning → alignment (RLHF) → deployment. RLHF uses human feedback to reward safe behaviors and penalize harmful outputs.

**Why the others are wrong:**
- Foundation models can still generate harmful content despite being pre-trained on large datasets. Pre-training focuses on prediction accuracy, not safety alignment
- Fine-tuning adapts the model to a specific domain (customer service) but doesn't inherently make it safer. It could even amplify harmful patterns if they exist in the training data
- While API-level filtering exists, it's a band-aid solution. RLHF trains the model itself to avoid generating harmful content at the source, which is more robust

</details>

---

**Q6.** An engineer is debugging a tokenization issue. The input string 'Hello world!' produces 3 tokens: ['Hello', ' world', '!']. But the input 'Helloworld!' produces 2 tokens: ['Hello', 'world!']. The model uses 1536-dimensional embeddings. How many total embedding dimensions will be processed for BOTH inputs combined?

A) 1536 dimensions (embeddings are shared across tokens)
B) 3072 dimensions (2 unique words × 1536)
C) 4608 dimensions (3 tokens in first input × 1536)
D) 7680 dimensions (5 total tokens across both inputs × 1536)

<details>
<summary>Answer</summary>

**Correct: D**

Each token gets its own embedding vector. First input = 3 tokens = 3 × 1536 = 4608 dimensions. Second input = 2 tokens = 2 × 1536 = 3072 dimensions. Total = 4608 + 3072 = 7680 dimensions. Each token is processed independently as a 1536-dimensional vector.

**Why the others are wrong:**
- Embeddings aren't shared - each token position gets its own 1536-dimensional vector even if the word is the same
- This counts unique words, but tokenization creates 5 total tokens (3 + 2), and each token gets embedded separately regardless of uniqueness
- This only counts the first input (3 tokens × 1536 = 4608) but ignores the second input's 2 tokens

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** A research team is evaluating whether to use a foundation model or train a specialized model from scratch for a legal document analysis task. They have 500GB of legal documents and a budget for 100 GPU-hours. Which factor is the PRIMARY advantage of using a foundation model for this scenario?

A) Foundation models are smaller in size (fewer parameters) making them faster to deploy than specialized models
B) Foundation models are zero-shot capable, meaning they can perform tasks without task-specific training, saving time and compute
C) Foundation models are always more accurate than specialized models because they're trained on more diverse data
D) Foundation models don't require fine-tuning and can be used directly in production without any adaptation

<details>
<summary>Answer</summary>

**Correct: B**

Zero-shot capability is the defining advantage: foundation models can perform new tasks without task-specific training because they learned general language understanding during pre-training on massive data. With limited compute (100 GPU-hours), zero-shot or few-shot learning is feasible, while training from scratch would require thousands of GPU-hours.

**Why the others are wrong:**
- Foundation models are actually LARGER (billions of parameters) than specialized models. Size is a disadvantage, not advantage. They're deployed despite size because of their capabilities
- Not always - specialized models trained on domain-specific data can outperform foundation models. Foundation models excel at general tasks and transfer learning, not guaranteed accuracy on specialized domains
- Foundation models typically benefit from fine-tuning for specialized tasks. While they CAN be used zero-shot, fine-tuning on legal documents would improve performance for legal analysis

</details>

---

**Q8.** A machine learning engineer notices that in a transformer's self-attention layer, increasing sequence length from 512 to 1024 tokens causes memory usage to increase from 2GB to 8GB. Management asks why this happens and if there's a trade-off. What is the MOST accurate explanation?

A) Memory increases linearly with sequence length because each token requires its own embedding; the trade-off is longer sequences need more storage for embeddings
B) Memory increases quadratically because self-attention creates an n×n attention matrix for n tokens; the trade-off is that parallelization (which enables faster training) requires storing all token pair relationships
C) Memory increases exponentially because the decoder must generate all possible output sequences; the trade-off is generation quality versus memory usage
D) Memory increases due to the encoder-decoder architecture requiring separate storage for both; the trade-off is bidirectional context versus memory usage

<details>
<summary>Answer</summary>

**Correct: B**

Doubling tokens (512→1024, 2x) quadruples memory (2GB→8GB, 4x) = quadratic O(n²). Self-attention computes attention scores between ALL token pairs, creating an n×n matrix (512² = 262k pairs vs 1024² = 1M pairs). The trade-off: this quadratic memory/compute cost is accepted because parallelization (processing all tokens simultaneously) dramatically speeds up training versus sequential RNNs.

**Why the others are wrong:**
- Linear scaling would show 2GB→4GB when doubling sequence length. Embeddings do scale linearly but attention matrices (which dominate memory for long sequences) scale quadratically
- Decoder generation is sequential but doesn't cause exponential memory scaling. The attention matrix is the dominant memory consumer and it's quadratic
- Encoder-decoder architecture doesn't cause quadratic scaling - the self-attention mechanism itself does. Even encoder-only models (like BERT) have quadratic memory usage

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

