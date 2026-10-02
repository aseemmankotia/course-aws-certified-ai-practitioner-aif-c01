## Chapter 5: Domain 3: Prompt Engineering Techniques & Inference Parameters — Practice Questions

**Q1.** A company is building a customer service chatbot that must provide consistent, factual responses to policy questions. The bot will retrieve the correct policy document, then use a foundation model to generate the response. Which inference parameter configuration is MOST appropriate?

A) Temperature: 0.9, Top-p: 0.95 to ensure creative and varied responses
B) Temperature: 0, Top-p: 0.1 to ensure deterministic and focused outputs
C) Temperature: 0.7, Top-k: 50 to balance creativity with consistency
D) Temperature: 1.0, Top-p: 1.0 to maximize response diversity

<details>
<summary>Answer</summary>

**Correct: B**

Customer service policy responses require deterministic, consistent outputs. Temperature: 0 ensures the same input produces the same output every time. Top-p: 0.1 restricts sampling to only the most probable tokens, eliminating creative variation. This configuration prioritizes accuracy and consistency over creativity.

**Why the others are wrong:**
- Temperature 0.9 and Top-p 0.95 create highly variable, creative outputs - exactly what you DON'T want for factual policy information where consistency is critical
- Temperature 0.7 is the default 'balanced' setting but still introduces randomness. For policy responses requiring exact consistency, this is too variable
- Temperature 1.0 with Top-p 1.0 maximizes randomness and creativity - the worst configuration for consistent factual responses

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A marketing team needs to generate 50 unique product descriptions for similar items. Each description should be creative and distinct. After generating 10 descriptions with Temperature: 0.3, they notice outputs are too similar. What should they do?

A) Increase Temperature to 0.8-1.0 and set Top-p to 0.9 for more diversity
B) Decrease Temperature to 0 and increase Max tokens to 1024
C) Keep Temperature at 0.3 but add more few-shot examples
D) Set Top-k to 10 to reduce token selection

<details>
<summary>Answer</summary>

**Correct: A**

Temperature 0.3 produces relatively deterministic outputs with low variation. For creative, unique content, increasing Temperature to 0.8-1.0 introduces more randomness. Top-p: 0.9 (nucleus sampling) allows diverse token selection from the top 90% probability mass, maximizing variety while maintaining coherence.

**Why the others are wrong:**
- Temperature 0 makes outputs even MORE deterministic and identical - opposite of what's needed. Max tokens affects length, not diversity
- Few-shot examples improve task understanding but don't increase output diversity. Temperature 0.3 is still too low for creative variation
- Top-k: 10 severely restricts token selection to only 10 options per step, reducing diversity - the opposite of what's needed

</details>

---

**Q3.** A developer is building a medical diagnosis assistant. The model must analyze patient symptoms and provide a diagnostic recommendation with clear reasoning. Which prompting technique is MOST appropriate?

A) Zero-shot with high temperature for creative diagnostic suggestions
B) Few-shot with 3-5 example diagnoses to guide the model
C) Chain-of-thought prompting to show step-by-step diagnostic reasoning
D) Simple instruction prompt with Temperature: 0 for consistency

<details>
<summary>Answer</summary>

**Correct: C**

Medical diagnosis requires transparent, step-by-step reasoning that can be validated by healthcare professionals. Chain-of-thought prompting (e.g., 'Let's think step by step: 1) Review symptoms, 2) Consider differential diagnoses, 3) Evaluate probability') forces the model to show its reasoning process, improving accuracy and allowing human verification of the logic.

**Why the others are wrong:**
- Zero-shot with high temperature introduces randomness in medical decisions - dangerous and unreliable. Medical diagnosis needs reasoning, not creativity
- Few-shot examples help but don't provide the transparent reasoning process needed to verify medical logic. You need to see HOW the model reached the conclusion
- Temperature 0 ensures consistency but doesn't provide reasoning steps. Medical professionals need to see the diagnostic logic, not just the final answer

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** You are testing a model's ability to translate technical documentation from English to Japanese. With no examples provided, the model produces adequate translations. Which prompting approach is being used, and what could improve accuracy?

A) Few-shot prompting; add Temperature: 1.0 for better translation variety
B) Zero-shot prompting; add 2-3 translation examples (few-shot) with technical terms
C) Chain-of-thought prompting; increase Max tokens to 2048
D) Zero-shot prompting; decrease Temperature to 0 for exact translations

<details>
<summary>Answer</summary>

**Correct: B**

The scenario describes zero-shot prompting (no examples provided). For technical documentation with specialized terminology, adding few-shot examples (2-3 sample translations showing how to handle technical terms) significantly improves accuracy by demonstrating the desired style and term handling.

**Why the others are wrong:**
- The current approach IS zero-shot (no examples), not few-shot. Temperature 1.0 adds randomness - wrong for translation accuracy where consistency matters
- Chain-of-thought is for reasoning tasks. Translation doesn't need step-by-step reasoning. Max tokens affects length, not accuracy
- Temperature 0 helps consistency but doesn't address the core issue - the model lacks context for technical term translation. Examples (few-shot) are needed

</details>

---

**Q5.** A financial analysis application must generate executive summaries that are exactly 150 words, use formal tone, and produce identical summaries for the same input data across multiple runs. Which configuration is correct?

A) Temperature: 0, Max tokens: 200, Top-p: 0.1, with zero-shot instruction
B) Temperature: 0.7, Max tokens: 150, Top-k: 50, with few-shot examples
C) Temperature: 0, Max tokens: 200, Top-p: 0.1, with chain-of-thought reasoning
D) Temperature: 0, Max tokens: 512, Top-p: 0.9, with few-shot examples

<details>
<summary>Answer</summary>

**Correct: A**

Temperature: 0 ensures deterministic, identical outputs for same input. Max tokens: 200 allows space for ~150 words (tokens ≈ 0.75 words). Top-p: 0.1 restricts to most probable tokens for consistency. Zero-shot works when the instruction is clear ('Write 150-word executive summary'), as foundation models understand this task without examples.

**Why the others are wrong:**
- Temperature 0.7 introduces randomness - outputs won't be identical across runs. Max tokens 150 is too restrictive (need buffer for exactly 150 words)
- Chain-of-thought is for reasoning tasks, not summarization. It adds unnecessary complexity and may reduce summary quality by focusing on reasoning steps instead of summary content
- Max tokens 512 is excessive for 150 words. Top-p 0.9 allows too much diversity - inconsistent with the requirement for identical outputs

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** An e-learning platform needs an AI tutor to solve math word problems. Initial attempts with simple instructions produce incorrect answers. Testing shows the model CAN do the math but makes logical errors in understanding the problem. What should you do FIRST?

A) Increase Temperature to 0.9 to encourage more creative problem-solving approaches
B) Add chain-of-thought prompting: 'Let's solve this step by step: 1) Identify what we know, 2) Identify what we need to find, 3) Choose the operation, 4) Calculate'
C) Provide 10 few-shot examples of solved math problems with answers
D) Decrease Temperature to 0 and increase Top-k to 100 for more calculation precision

<details>
<summary>Answer</summary>

**Correct: B**

The model can do calculations but makes logical/reasoning errors - perfect use case for chain-of-thought prompting. By instructing the model to show its reasoning ('step by step'), you force it to break down the problem logically, reducing reasoning errors. This technique specifically improves accuracy on multi-step reasoning tasks.

**Why the others are wrong:**
- Temperature controls randomness, not reasoning ability. Higher temperature adds variation but doesn't fix logical errors - it may make them worse by introducing randomness into an already flawed reasoning process
- Few-shot examples help demonstrate the task but 10 examples is excessive and won't fix reasoning errors as effectively as chain-of-thought. Few-shot works best with 2-5 examples, and doesn't force step-by-step reasoning
- Temperature and Top-k control output diversity, not logical reasoning. These parameters won't address the root cause (reasoning errors). The model already CAN calculate - it needs better reasoning structure

</details>

---

**Q7.** You're configuring a foundation model to generate social media posts. Requirements: posts must be engaging and varied (no two posts should be identical), stay under 280 characters, and maintain brand voice consistency. You have 5 example posts in the desired voice. Which configuration is BEST?

A) Few-shot (5 examples), Temperature: 0, Max tokens: 100
B) Few-shot (5 examples), Temperature: 0.8, Max tokens: 100, Top-p: 0.9
C) Zero-shot, Temperature: 1.0, Max tokens: 280, Top-k: 10
D) Chain-of-thought, Temperature: 0.7, Max tokens: 512

<details>
<summary>Answer</summary>

**Correct: B**

Few-shot with 5 examples teaches brand voice consistency. Temperature 0.8 provides creativity and variation (each post will be different). Max tokens 100 allows ~75 words (well under 280 characters). Top-p 0.9 enables diverse word choices while maintaining quality. This balances creativity with consistency.

**Why the others are wrong:**
- Temperature 0 produces deterministic outputs - all posts would be nearly identical, violating the 'varied' requirement. Need higher temperature for creative diversity
- Zero-shot loses brand voice consistency (no examples provided). Max tokens 280 is confusing (tokens ≠ characters; should be ~100 tokens for 280 chars). Top-k 10 severely limits vocabulary
- Chain-of-thought is for reasoning tasks, not creative writing. Max tokens 512 is excessive for 280 characters. Social media posts don't need step-by-step reasoning

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** A legal tech company is building a contract clause generator. The model must generate clauses that are legally precise and reproducible (same input = same clause). They also want to limit vocabulary to formal legal terms. Which parameter combination achieves this?

A) Temperature: 0, Top-k: 20, Max tokens: 256
B) Temperature: 0, Top-p: 0.3, Max tokens: 512
C) Temperature: 0.5, Top-p: 0.9, Max tokens: 256
D) Temperature: 0, Top-p: 0.95, Top-k: 50

<details>
<summary>Answer</summary>

**Correct: A**

Temperature: 0 ensures deterministic, reproducible outputs (same input = same clause). Top-k: 20 restricts vocabulary to only the 20 most probable tokens at each step, naturally limiting to formal, common legal terms and excluding casual language. Max tokens: 256 is appropriate for clause length (~200 words).

**Why the others are wrong:**
- Top-p: 0.3 restricts token selection but is less precise than Top-k for vocabulary control. Max tokens 512 is excessive for contract clauses. Top-p works better for diversity; Top-k is better for vocabulary restriction
- Temperature 0.5 introduces randomness - outputs won't be reproducible. Top-p 0.9 allows wide vocabulary diversity, opposite of the 'formal legal terms only' requirement
- Cannot use both Top-p and Top-k simultaneously (they're alternative sampling methods). Top-p 0.95 and Top-k 50 both allow too much diversity for the requirement of limited formal vocabulary

</details>

---

