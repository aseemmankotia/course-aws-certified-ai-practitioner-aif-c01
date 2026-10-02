# Domain 2: Generative AI Fundamentals - Exam Cheat Sheet

## Token vs Embedding vs Vector
| Concept | Definition | Example | Exam Trap |
|---------|-----------|---------|----------|
| **Token** | Smallest unit of text (word, subword, char) | 'Hello world' = 2 tokens | Don't confuse with characters - 'AI' might be 1 token |
| **Embedding** | Numerical vector representing a token | 1536 dimensions for GPT-3.5 | Each token gets its own embedding - not shared |
| **Vector** | Generic array of numbers | [0.23, -0.45, 0.67, ...] | Embedding is a specific type of vector |

## Foundation Model Characteristics
✅ **Must Have:**
- Pre-trained on billions of tokens (massive data)
- Billions of parameters (GPT-3: 175B, GPT-4: >1T estimated)
- Zero-shot capable (perform tasks without task-specific training)
- General-purpose (not domain-specific)

❌ **Common Mistake:** Fine-tuned models are NOT foundation models (they're specialized)

## Transformer Architecture

### Self-Attention Complexity
```
Sequence Length → Attention Pairs → Memory/Compute
100 tokens      → 10,000 pairs   → Baseline
200 tokens      → 40,000 pairs   → 4x
1,000 tokens    → 1,000,000      → 100x
Complexity: O(n²)
```

### Why Transformers Beat RNNs
| Aspect | RNN | Transformer | Exam Answer |
|--------|-----|-------------|-------------|
| **Processing** | Sequential (token by token) | Parallel (all tokens at once) | ✅ Parallelization = faster |
| **Complexity** | O(n) | O(n²) | Despite higher complexity, parallelization wins |
| **Long-range** | Weak (vanishing gradients) | Strong (direct connections) | ✅ Self-attention connects distant tokens |
| **Training Speed** | Slow (can't parallelize) | Fast (GPU-friendly) | ✅ Primary reason for adoption |

## GenAI Lifecycle Stages

### 1. Pre-training (Foundation Model Creation)
- **Data:** Billions of tokens from internet, books, code
- **Compute:** Thousands of GPUs, weeks/months
- **Cost:** Millions of dollars
- **Output:** Foundation model with zero-shot capability
- **Exam Tip:** Most expensive stage - not repeated for each use case

### 2. Fine-tuning (Specialization)
- **Data:** 10K-1M task-specific examples
- **Compute:** Few GPUs, hours/days
- **Cost:** Thousands of dollars
- **Output:** Specialized model for specific domain/task
- **Exam Tip:** Requires much less data/compute than pre-training

### 3. Alignment (RLHF)
- **Purpose:** Safety, reduce harmful outputs, human preferences
- **Method:** Reinforcement Learning from Human Feedback
- **When:** After fine-tuning, before deployment
- **Exam Tip:** RLHF is for safety/alignment, NOT task accuracy

### 4. Deployment
- **Methods:** API, self-hosted, edge deployment
- **Considerations:** Latency, cost, privacy

## Key Numbers to Memorize

| Metric | Value | Context |
|--------|-------|----------|
| GPT-3.5 embedding dims | 1536 | Each token → 1536-dim vector |
| GPT-4 context window | 128K tokens | vs GPT-3.5: 4K-16K tokens |
| Attention complexity | O(n²) | Doubling length = 4x compute/memory |
| Foundation model params | Billions (B) | GPT-3: 175B, GPT-4: >1T |
| Fine-tuning data | 10K-1M examples | vs pre-training: billions |

## Common Exam Traps

### Trap 1: Token Counting
❌ Wrong: 'Hello world!' = 11 characters = 11 tokens
✅ Right: Typically 3 tokens ['Hello', ' world', '!']

### Trap 2: Memory Scaling
❌ Wrong: 2x tokens = 2x memory (linear)
✅ Right: 2x tokens = 4x memory (quadratic for attention)

### Trap 3: Foundation vs Fine-tuned
❌ Wrong: Fine-tuned model is a type of foundation model
✅ Right: Foundation model is pre-trained general model; fine-tuned is specialized from foundation

### Trap 4: RLHF Purpose
❌ Wrong: RLHF improves task accuracy
✅ Right: RLHF improves safety/alignment (reducing harmful outputs)

### Trap 5: Transformer Advantage
❌ Wrong: Transformers are faster because they have O(n) complexity
✅ Right: Transformers are faster due to parallelization despite O(n²) complexity

## Quick Decision Matrix

**When to use Foundation Model (zero-shot):**
- Limited task-specific data (<1K examples)
- General use case (not highly specialized)
- Need quick deployment
- Budget constraints (no fine-tuning cost)

**When to Fine-tune:**
- Have 10K+ labeled examples
- Specialized domain (medical, legal, financial)
- Need higher accuracy on specific tasks
- Can afford compute for training

**When to use RLHF:**
- Safety-critical applications
- Customer-facing chatbots
- Need to reduce harmful/biased outputs
- Want model to follow human preferences
