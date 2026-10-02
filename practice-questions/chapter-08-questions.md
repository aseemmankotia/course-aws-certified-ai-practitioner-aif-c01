## Chapter 8: Domain 4: Responsible AI—Bias, Fairness & SageMaker Clarify — Practice Questions

**Q1.** A financial services company is building a loan approval model using SageMaker. During pre-training analysis, they discover that 92% of their historical loan data shows 'approved' outcomes. What is the PRIMARY risk this creates, and what should be done FIRST?

A) The model will have high accuracy but may over-predict 'approved' outcomes for underrepresented groups. Use SageMaker Clarify to generate a pre-training bias report before training.
B) The model will be biased toward rejecting loans. Balance the dataset by removing approved loans until it's 50/50.
C) This indicates data poisoning. Discard the dataset and collect new data with equal approved/rejected ratios.
D) The model will hallucinate loan amounts. Implement Bedrock Guardrails to filter outputs before deployment.

<details>
<summary>Answer</summary>

**Correct: A**

When majority class >80% (here 92%), the model risks over-predicting that class. This is PRE-TRAINING bias (biased training data). SageMaker Clarify's pre-training bias report detects class imbalance, demographic disparities, and label imbalance BEFORE training starts.

**Why the others are wrong:**
- Wrong direction—model over-predicts majority class (approved), not minority. 50/50 split isn't required; proper sampling techniques and bias detection are better.
- 92% approved loans is likely legitimate business data, not poisoning. Equal ratios aren't realistic for many domains. Exam tests recognizing imbalance ≠ attack.
- Bedrock Guardrails filters content (hate/PII/denied topics), not ML prediction bias. Hallucination is an LLM issue, not relevant to structured loan predictions.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** After deploying a resume screening model, HR discovers it recommends 40% fewer women candidates than men with equivalent qualifications. Which SageMaker Clarify feature should be used to investigate this POST-TRAINING bias?

A) Model explainability using SHAP values to identify which features contribute most to gender-based disparities in predictions
B) Pre-training bias report showing class imbalance in the training dataset
C) Model Monitor to detect data drift in incoming resume submissions
D) Feature importance using built-in XGBoost feature_importances_ attribute

<details>
<summary>Answer</summary>

**Correct: A**

POST-TRAINING bias = disparate predictions after deployment. SHAP (SHapley Additive exPlanations) values in SageMaker Clarify show which features drive individual predictions and can reveal if gender-correlated features (names, schools, word choices) cause disparate impact. This is model explainability.

**Why the others are wrong:**
- Pre-training bias report analyzes DATA before training, not deployed model predictions. The issue is discovered post-deployment = post-training investigation needed.
- Model Monitor detects distribution drift over time, not systematic bias between demographic groups. Exam differentiates monitoring vs bias detection.
- XGBoost feature_importances_ shows global importance but NOT individual prediction explanations or demographic disparities. SHAP provides local (per-prediction) and global explanability.

</details>

---

**Q3.** A healthcare startup is deploying a medical chatbot using Amazon Bedrock. They must prevent the model from disclosing patient SSNs, credit card numbers, and discussing experimental treatments not approved by their medical board. Which configuration BEST addresses both requirements?

A) Enable Bedrock Guardrails with PII redaction filters for SSN and credit cards, and configure denied topics for experimental treatments
B) Use SageMaker Clarify to detect bias in medical recommendations and generate SHAP explanations for each response
C) Implement prompt engineering to instruct the model to avoid PII and experimental topics, then use Model Monitor to track compliance
D) Create a Model Card documenting intended use, then use AWS Macie to scan outputs for sensitive data

<details>
<summary>Answer</summary>

**Correct: A**

Bedrock Guardrails has TWO key features tested heavily: (1) PII redaction—automatically filters/masks SSN, credit cards, names, addresses; (2) Denied topics—blocks specified topics from responses. This directly addresses both requirements in the question.

**Why the others are wrong:**
- SageMaker Clarify is for ML model bias/explainability, not LLM content filtering. SHAP doesn't prevent PII disclosure or topic blocking—wrong tool entirely.
- Prompt engineering alone is insufficient—models can ignore instructions. Model Monitor tracks model performance drift, not real-time content filtering. Exam expects knowledge that Guardrails is the proper preventive control.
- Model Cards document transparency but don't prevent harmful outputs. Macie scans S3 data at rest, not real-time LLM responses. Exam tests knowing the RIGHT service for each requirement.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** Your company is creating a Model Card for a fraud detection model. According to AWS responsible AI guidelines, which information is MANDATORY to include for transparency?

A) Model architecture hyperparameters, training code repository, and AWS account ID used for training
B) Model purpose, performance metrics, known limitations, and intended use cases with inappropriate use cases explicitly stated
C) SHAP values for the top 100 most important features and confusion matrix for all demographic groups
D) Legal disclaimer stating the model may hallucinate, list of all training data sources, and Bedrock Guardrails configuration

<details>
<summary>Answer</summary>

**Correct: B**

Model Cards require: (1) PURPOSE—what problem it solves, (2) METRICS—accuracy/precision/recall/fairness, (3) LIMITATIONS—known failure modes, (4) INTENDED USE—appropriate scenarios, (5) INAPPROPRIATE USE—explicit scenarios to avoid. This provides transparency for stakeholders. Exam tests these 5 elements.

**Why the others are wrong:**
- Model Cards focus on TRANSPARENCY for non-technical stakeholders, not technical implementation details. Hyperparameters and account IDs aren't user-facing transparency requirements. Training code is optional.
- SHAP values are technical explainability, not Model Card requirements. Confusion matrices may be included as metrics but aren't mandatory. Model Cards are about documentation, not detailed technical reports.
- Hallucination applies to LLMs, not fraud detection (classification model). Training data sources may be included but aren't mandatory. Bedrock Guardrails is for LLM content filtering, irrelevant to documenting an ML model.

</details>

---

**Q5.** A retail company's recommendation engine trained on 5 years of purchase data shows accuracy of 94% overall, but only 76% accuracy for customers under age 25. Which SageMaker Clarify metric would BEST quantify this post-training bias?

A) Disparate Impact (DI)—ratio of favorable outcome rates between demographic groups, where DI < 0.8 indicates bias
B) Class Imbalance (CI)—measures if training data has unequal representation of classes
C) SHAP summary plot—shows global feature importance across all predictions
D) Difference in Positive Proportions in Predicted Labels (DPPL)—compares prediction rates between groups

<details>
<summary>Answer</summary>

**Correct: A**

Disparate Impact = (favorable outcome rate for group A) / (favorable outcome rate for group B). If accuracy for <25 is 76% vs 94% overall, DI = 76/94 = 0.809. Threshold is DI < 0.8 indicates significant bias. This quantifies POST-TRAINING bias between demographic groups. Heavily tested metric.

**Why the others are wrong:**
- CI (Class Imbalance) is a PRE-TRAINING metric measuring training data imbalance (e.g., 90% approved loans). The question asks about POST-TRAINING performance disparities between age groups.
- SHAP summary shows which features matter, not demographic performance disparities. It doesn't quantify bias between groups—it explains predictions. Exam differentiates explainability vs bias metrics.
- DPPL measures difference in PREDICTION rates (what model predicts), not ACCURACY rates (correctness). The question specifies accuracy disparity. DPPL would be: if model predicts 'buy' for 60% of <25 but 80% of >25.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** A legal AI assistant built with Bedrock must filter all content containing violence, hate speech, and sexual content, while allowing discussion of legal cases involving these topics. How should Bedrock Guardrails be configured?

A) Enable content filters for violence, hate, and sexual content at MEDIUM threshold, then use denied topics to block non-legal discussions
B) Set content filters to HIGH threshold for violence/hate/sexual, which automatically allows legal context discussions
C) Use PII redaction to remove offensive content and configure custom regex patterns for legal terminology
D) Implement prompt engineering with system prompts defining allowed legal contexts, then enable all content filters at LOW threshold

<details>
<summary>Answer</summary>

**Correct: A**

Bedrock Guardrails content filters (violence/hate/sexual/insults/misconduct/prompt attacks) work with THRESHOLDS (none/low/medium/high). However, filters alone can't distinguish context. Denied topics can be configured to block specific non-legal uses while allowing legal case discussions. This combination provides both broad filtering and context-aware control.

**Why the others are wrong:**
- Content filter thresholds (LOW/MEDIUM/HIGH) control sensitivity, not contextual awareness. HIGH threshold blocks more but doesn't 'automatically allow legal context'—filters don't understand context without denied topics configuration.
- PII redaction removes SSN/credit cards/names/addresses, NOT offensive content. Custom regex is for PII patterns, not content filtering. Wrong feature for the requirement.
- Prompt engineering can help but is insufficient—models can ignore instructions. LOW threshold is most permissive (blocks least), which contradicts 'must filter all violence/hate/sexual'. Exam expects recognizing proper Guardrails features.

</details>

---

**Q7.** During a SageMaker model review, you discover that credit score has a SHAP value of +0.42 for loan approvals, but applicant's zip code has +0.38. The legal team flags zip code as potentially discriminatory. What should you do FIRST from a responsible AI perspective?

A) Remove zip code as a feature and retrain the model, then generate a new SageMaker Clarify post-training bias report comparing demographic outcomes
B) Keep zip code but document it in the Model Card as a known limitation with legal review pending
C) Use Bedrock Guardrails to filter any outputs mentioning zip code to end users
D) Lower the SHAP threshold to reduce zip code importance without removing the feature

<details>
<summary>Answer</summary>

**Correct: A**

Zip code can be a proxy for race (redlining history), making it legally problematic for lending despite being predictive. Responsible AI principle: remove potentially discriminatory features when identified. After retraining, use Clarify POST-TRAINING bias report to verify removal didn't create worse disparities. Exam tests knowing to retrain + reverify bias.

**Why the others are wrong:**
- Documenting known issues without mitigation isn't responsible AI—it's acknowledging but not addressing discrimination. Model Cards document AFTER mitigation, not as a substitute for action.
- Bedrock Guardrails filters LLM outputs (content/PII/topics), not ML model features. The issue is the model using zip code internally, not displaying it to users. Wrong service entirely.
- You can't 'lower SHAP threshold'—SHAP values are explanations of existing model behavior, not configurable parameters. This answer conflates explainability with feature engineering. Exam trap for students who don't understand SHAP.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** A generative AI application using Bedrock occasionally produces factually incorrect medical advice (hallucinations). The company is concerned about legal liability. Which combination of responsible AI practices BEST mitigates this risk?

A) Implement Bedrock Guardrails denied topics for medical advice, add human review for medical outputs, include disclaimers in the Model Card about limitations, and log all outputs for audit
B) Use SageMaker Clarify SHAP values to identify which prompt features cause hallucinations, then retrain with more medical data
C) Enable Bedrock content filters at HIGH threshold to block all medical misinformation, and use PII redaction to remove patient data
D) Create a detailed Model Card documenting hallucination rates, then rely on prompt engineering to instruct the model not to hallucinate

<details>
<summary>Answer</summary>

**Correct: A**

Layered responsible AI approach: (1) Denied topics = preventive control blocking medical advice generation, (2) Human review = human-in-the-loop for high-risk outputs, (3) Model Card transparency = documents limitations/inappropriate uses, (4) Audit logs = accountability. This combines technical + process + documentation controls. Exam tests multi-layer mitigation.

**Why the others are wrong:**
- SHAP is for ML models, not LLM hallucination analysis. Hallucination is an LLM generation issue, not a feature importance problem. More training data doesn't eliminate hallucination—architectural limitation of LLMs.
- Content filters block hate/violence/sexual content, NOT factual inaccuracy. PII redaction removes sensitive data, not incorrect medical advice. These features don't address hallucination risk.
- Model Card alone is transparency, not mitigation. Prompt engineering is insufficient—models frequently ignore instructions ('jailbreaking'). Exam expects knowing documentation alone isn't adequate risk mitigation.

</details>

---

