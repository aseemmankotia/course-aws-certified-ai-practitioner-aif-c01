# Domain 4: Responsible AI Cheat Sheet

## Bias Detection (SageMaker Clarify)

| Bias Type | When Detected | What It Measures | Key Metrics |
|-----------|---------------|------------------|-------------|
| **Pre-training** | Before model training | Training data imbalance | Class Imbalance (CI), demographic representation |
| **Post-training** | After deployment | Prediction disparities | Disparate Impact (DI), accuracy differences |

### Critical Thresholds
- **Class Imbalance**: Majority class >80% = high risk of over-prediction
- **Disparate Impact**: DI < 0.8 = significant bias between groups
  - Formula: `DI = (favorable rate group A) / (favorable rate group B)`
  - Example: 76% accuracy / 94% accuracy = 0.809 DI

### SHAP (Model Explainability)
- **Purpose**: Explains individual prediction feature contributions
- **Output**: SHAP value per feature (positive = increases prediction, negative = decreases)
- **Use Case**: Identify bias-causing features (e.g., zip code correlation with protected classes)
- **Exam Note**: SHAP = explainability tool, NOT bias metric itself

---

## Bedrock Guardrails

### 1. Content Filters
| Filter Type | Thresholds | Use Case |
|-------------|------------|----------|
| Hate speech | NONE/LOW/MEDIUM/HIGH | Block discriminatory content |
| Violence | NONE/LOW/MEDIUM/HIGH | Filter violent descriptions |
| Sexual content | NONE/LOW/MEDIUM/HIGH | Age-appropriate filtering |
| Insults | NONE/LOW/MEDIUM/HIGH | Professional communication |
| Misconduct | NONE/LOW/MEDIUM/HIGH | Illegal activity discussion |
| Prompt attacks | NONE/LOW/MEDIUM/HIGH | Jailbreak prevention |

**Threshold Meanings**:
- LOW = blocks only egregious (most permissive)
- MEDIUM = balanced default
- HIGH = strict filtering (blocks more)

### 2. PII Redaction
Automatically filters/masks:
- Social Security Numbers (SSN)
- Credit card numbers
- Names, addresses
- Phone numbers, email addresses
- Bank account numbers
- Driver's license numbers

**Exam Trap**: PII redaction ≠ content filtering. Use content filters for hate/violence.

### 3. Denied Topics
- Block specific discussion topics (custom configuration)
- Example: Experimental medical treatments, financial advice, political opinions
- Use with content filters for context-aware control

---

## Model Cards (Transparency)

### 5 Mandatory Elements
1. **Model Purpose**: Problem it solves
2. **Performance Metrics**: Accuracy, precision, recall, fairness metrics
3. **Known Limitations**: Failure modes, accuracy gaps
4. **Intended Use Cases**: Appropriate scenarios
5. **Inappropriate Use Cases**: Explicitly state misuse scenarios

**Exam Note**: Model Cards = user-facing transparency, not technical implementation details.

---

## Service Selection Guide

| Requirement | Service | Feature |
|-------------|---------|----------|
| Detect training data imbalance | SageMaker Clarify | Pre-training bias report |
| Analyze deployed model disparities | SageMaker Clarify | Post-training bias report (DI, DPPL) |
| Explain individual predictions | SageMaker Clarify | SHAP values |
| Block hate/violence in LLM | Bedrock Guardrails | Content filters |
| Remove SSN/credit cards from LLM | Bedrock Guardrails | PII redaction |
| Prevent specific topic discussions | Bedrock Guardrails | Denied topics |
| Document model transparency | Model Cards | Purpose/metrics/limitations |

---

## Common Exam Scenarios

### Scenario 1: Dataset Imbalance
**Problem**: 92% of loan data shows 'approved'
**Risk**: Model over-predicts 'approved' for all groups
**Solution**: SageMaker Clarify pre-training bias report → identify imbalance → apply sampling techniques

### Scenario 2: Demographic Performance Gap
**Problem**: 94% accuracy overall, 76% for age <25
**Calculation**: DI = 76/94 = 0.809 (borderline bias)
**Solution**: Post-training bias report → investigate with SHAP → remove discriminatory features → retrain

### Scenario 3: LLM Content Risks
**Problem**: Chatbot must block PII and medical advice
**Solution**: Bedrock Guardrails PII redaction + denied topics for medical advice + human review loop

### Scenario 4: Feature Discrimination
**Problem**: Zip code SHAP value = +0.38 (high impact), legally problematic
**Solution**: Remove feature → retrain → verify with new post-training bias report

---

## Legal Risk Mitigation

| Risk Type | Mitigation Strategy | Tools |
|-----------|---------------------|-------|
| Hallucination (false info) | Denied topics + human review + disclaimers | Guardrails + Model Card |
| Discrimination | Bias detection + remove proxy features + audit | Clarify + retraining |
| IP infringement | Training data licensing + attribution | Documentation |
| PII exposure | Redaction + access controls + logging | Guardrails PII redaction |

**Exam Principle**: Layered approach = technical controls + process controls + transparency documentation

---

## Key Exam Differentiators

- **Pre-training vs Post-training**: DATA analysis vs MODEL analysis
- **SHAP vs DI**: Explainability (feature contributions) vs Bias metric (outcome ratios)
- **Clarify vs Guardrails**: ML bias detection vs LLM content filtering
- **DPPL vs DI**: Prediction rates vs Favorable outcome rates
- **Content filters vs PII**: Offensive content vs Sensitive data
- **Model Card vs Technical docs**: User transparency vs Implementation details
