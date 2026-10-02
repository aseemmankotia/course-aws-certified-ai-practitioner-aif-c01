# Domain 3: Prompt Engineering & Inference Parameters Cheat Sheet

## Temperature Quick Reference
| Value | Behavior | Use Case | Exam Scenario |
|-------|----------|----------|---------------|
| 0 | Deterministic (same output every time) | Customer service, policy Q&A, legal docs | "Must provide consistent answers" |
| 0.3-0.5 | Slightly varied but mostly consistent | Technical documentation, formal writing | "Balanced accuracy and slight variation" |
| 0.7 | Default balanced (moderate creativity) | General content generation | Not specified in scenario |
| 0.8-1.0 | Highly creative and varied | Marketing, brainstorming, unique content | "Generate 50 UNIQUE descriptions" |

## Sampling Parameters
| Parameter | Range | What It Does | Exam Tip |
|-----------|-------|--------------|----------|
| **Top-p** | 0.0-1.0 | Consider tokens in top X% probability | 0.9 = diverse, 0.1 = focused |
| **Top-k** | 1-100+ | Consider only top N tokens | 20 = restricted vocab, 50+ = diverse |
| **Max tokens** | 256-4096 | Output length limit | 512 tokens ≈ 400 words |

**CRITICAL:** Cannot use Top-p AND Top-k simultaneously (they're alternatives)

## Prompting Techniques Comparison
| Technique | When to Use | Exam Keyword | Example |
|-----------|-------------|--------------|----------|
| **Zero-shot** | Task is common, no special format needed | "No examples provided" | "Translate: Hello" |
| **Few-shot** | Specialized domain, specific format/style, improve accuracy | "Domain-specific" or "technical terms" | "cat→chat, dog→chien, bird→?" |
| **Chain-of-thought** | Multi-step reasoning, need to verify logic | "Reasoning", "diagnosis", "math problems" | "Let's think step by step" |

## Common Exam Scenarios → Correct Configuration

### Scenario 1: Consistent Customer Service
- **Requirement:** Same answer every time, factual
- **Config:** Temperature: 0, Top-p: 0.1
- **Why:** Deterministic + restricted sampling = consistency

### Scenario 2: Creative Unique Content  
- **Requirement:** 50 different descriptions, engaging
- **Config:** Temperature: 0.8-1.0, Top-p: 0.9, Few-shot (if brand voice needed)
- **Why:** High temperature = variety, high Top-p = diverse vocabulary

### Scenario 3: Technical Translation
- **Requirement:** Specialized terms, accurate
- **Config:** Few-shot (2-3 examples), Temperature: 0.3
- **Why:** Examples teach terminology, low temperature for accuracy

### Scenario 4: Math/Logic Problems
- **Requirement:** Correct reasoning, show work
- **Config:** Chain-of-thought, Temperature: 0.7
- **Why:** Forces step-by-step logic, prevents reasoning errors

### Scenario 5: Legal/Formal Documents
- **Requirement:** Precise, reproducible, formal vocabulary
- **Config:** Temperature: 0, Top-k: 20, Max tokens: 256
- **Why:** Deterministic + restricted vocab + appropriate length

## Critical Exam Traps

### ❌ TRAP: "Add more examples to fix reasoning errors"
**WRONG:** Few-shot helps task understanding, not reasoning  
**CORRECT:** Use chain-of-thought for reasoning issues

### ❌ TRAP: "Max tokens: 280 for 280 characters"
**WRONG:** Tokens ≠ characters  
**CORRECT:** ~100 tokens for 280 chars (1 token ≈ 4 chars or 0.75 words)

### ❌ TRAP: "Temperature 0.7 for consistent outputs"
**WRONG:** 0.7 still introduces randomness  
**CORRECT:** Temperature MUST be 0 for identical outputs

### ❌ TRAP: "Use high temperature for better accuracy"
**WRONG:** High temperature = randomness, lower accuracy  
**CORRECT:** Low temperature (0-0.3) for accuracy, high (0.8-1.0) for creativity

## Decision Tree: Choosing Parameters

```
Need identical outputs every time?
├─ YES → Temperature: 0, Top-p: 0.1-0.3
└─ NO → Need creative/varied outputs?
    ├─ YES → Temperature: 0.8-1.0, Top-p: 0.9
    └─ NO → Temperature: 0.7 (default)

Task requires multi-step reasoning?
├─ YES → Chain-of-thought prompting
└─ NO → Specialized domain/format needed?
    ├─ YES → Few-shot (2-5 examples)
    └─ NO → Zero-shot

Need to restrict vocabulary (e.g., formal only)?
├─ YES → Top-k: 10-20
└─ NO → Top-p: 0.9 for diversity
```

## Memory Trick: "The Temperature Rule"
**0** = ❄️ Frozen (deterministic)  
**0.7** = 🌡️ Room temp (balanced/default)  
**1.0** = 🔥 Hot (maximum creativity)

Exam will give use case → you pick temperature
