# Answer Key — Practice Test 2

**Q1. Correct: B**

With only 3% positive cases, a model that always predicts 'no readmission' achieves 97% accuracy while being completely useless. Class imbalance is the core issue. The business complaint ('fails to identify at-risk patients') confirms low recall on the minority class. Solutions include resampling techniques (SMOTE), adjusting class weights in the loss function, or optimizing for F1-score/AUC-ROC instead of accuracy.

---

**Q2. Correct: C**

PCA provides feature loadings (coefficients) for each principal component, showing exactly how much each original feature contributes to each new dimension. This interpretability is critical for the business requirement to understand 'which original features most influence each reduced dimension.' PCA components are linear combinations, making them mathematically traceable back to original features.

---

**Q3. Correct: D**

Logistic regression provides inherent interpretability through coefficients that directly show how each feature influences the log-odds of approval. For regulatory compliance, you can state: 'A 1-unit increase in credit score increases approval probability by X%.' The model is deterministic, auditable, and the explanations are part of the model itself (not post-hoc approximations). This level of transparency is critical for regulated industries.

---

**Q4. Correct: C**

The key diagnostic clue is that training/validation performance are nearly identical (no overfitting), and test set performance is good (93-94%), but deployment performance dramatically drops to 78%. This indicates the test set was drawn from the same distribution as training data, but real-world deployment data (different scanner) has a different distribution. This is classic distribution/domain shift - the model learned features specific to one scanner type that don't transfer to another.

---

**Q5. Correct: A**

ALS with mini-batch gradient descent is specifically designed for sparse matrix factorization at scale. It only processes observed (non-zero) entries, making it computationally feasible. ALS alternates between fixing user factors and solving for item factors (and vice versa), which is more efficient than full SVD. This is the standard approach for large-scale recommender systems (used by Spotify, Netflix).

---

**Q6. Correct: D**

Time-series data often exhibits non-stationarity - patterns change over time due to seasonality shifts, trend changes, or external factors. The test set (records 12,001-14,000) may have been from a specific historical period that doesn't represent current deployment conditions. The key clue is 'after deployment' performance drops, suggesting the most recent data (post-14,000) has different characteristics than the historical test set. Proper evaluation should use the most recent data as the test set.

---

**Q7. Correct: A**

Adam optimizer combines adaptive learning rates (addresses the slow progress issue) with momentum (addresses oscillation). Learning rate scheduling (e.g., reduce on plateau, cosine annealing) allows starting with higher rates for fast initial progress, then decreasing for stable convergence. This addresses both problems: wild oscillation at lr=0.1 and slow progress at lr=0.001. Adam's per-parameter adaptive rates are particularly effective when different parameters need different learning rates.

---

**Q8. Correct: B**

Macro-averaged F1 computes F1 for each class independently, then averages them equally. This ensures the minority class (Negative, 10%) has equal weight to majority classes in the optimization objective. If Negative class has 0% recall (model never predicts it), macro F1 will be low even if Positive/Neutral have high F1. This forces the model to perform well on ALL classes, which is what the business needs ('identifying negative sentiment').

---

**Q9. Correct: B**

For autonomous vehicles, inference speed is PRIMARY because detection latency directly impacts safety. At 30 FPS, you have 33ms per frame. Real-world deployment involves additional overhead (preprocessing, postprocessing, network delays, system load). Model A at 8 FPS (125ms) is too slow even with optimization - you'd need 4-5x speedup, which is unrealistic. Model B at 45 FPS provides safety margin for variable conditions (complex scenes, multiple objects). The 4% mAP difference (92% vs 88%) is acceptable given the critical need for real-time performance.

---

**Q10. Correct: B**

Explainability is mandated for regulatory compliance in healthcare (physicians need to understand AI reasoning), and robustness directly addresses the observed issue of implausible recommendations on edge cases. These two characteristics are non-negotiable for the described scenario.

---

**Q11. Correct: B**

0.5% fraud rate is severe class imbalance. SMOTE (Synthetic Minority Over-sampling Technique) or weighted loss functions specifically address imbalanced datasets. Optimizing for precision-recall (not just accuracy) aligns with the business requirement of high recall while controlling false positives.

---

**Q12. Correct: B**

Gradient boosted trees (like XGBoost) provide excellent performance on tabular financial data while offering inherent interpretability through feature importance scores. They handle non-linear relationships well and scale to 50K daily predictions. Feature importance is built-in, not post-hoc, meeting regulatory audit requirements.

---

**Q13. Correct: B**

Transfer learning is the gold standard for limited labeled data in computer vision. Pre-trained models (ImageNet or medical image models) have learned generic visual features (edges, textures, shapes). Fine-tuning adapts these features to rare diseases with just 500 examples per class, typically achieving much higher accuracy than training from scratch.

---

**Q14. Correct: A**

This is textbook concept drift. The model learned 2023 user preferences, but user behavior evolves (new products, seasonal trends, changing tastes). Input feature distribution shifts confirm this. The 'staleness' and 40% CTR drop indicate the model's learned relationships no longer reflect current reality. Concept drift requires retraining on recent data.

---

**Q15. Correct: B**

Slice-based evaluation (testing on specific subpopulations) is the correct approach for identifying model weaknesses on critical subgroups. Creating a sarcasm test set measures performance on exactly the failure mode the business cares about. 92% overall accuracy masks poor sarcasm performance — slice evaluation reveals hidden failures.

---

**Q16. Correct: B**

Unsupervised learning is specifically designed for discovering patterns and natural groupings in unlabeled data. Clustering algorithms like k-means or hierarchical clustering can identify which symptoms co-occur without requiring predefined disease categories. This matches the requirement of having unlabeled data and wanting to discover natural groupings.

---

**Q17. Correct: C**

Recall (sensitivity/true positive rate) measures the proportion of actual fraud cases correctly identified, which directly addresses the business requirement of catching 85% of fraud. The 45% detection rate is a recall problem. With 98% accuracy but only 45% recall, the model is biased toward the majority class (legitimate transactions at 98%). Class imbalance techniques like adjusted class weights, threshold tuning, or cost-sensitive learning can improve recall even if precision decreases (more false alarms).

---

**Q18. Correct: B**

Transfer learning's core advantage is that the pre-trained model has already learned generalizable low-level features (edges, textures, shapes) and mid-level features from millions of ImageNet images. These features transfer well to new visual tasks. Fine-tuning requires fewer domain-specific images and significantly less computational resources than training from scratch, while often achieving better performance. This is especially valuable with only 5,000 labeled images, which would be insufficient for training a deep CNN from scratch.

---

**Q19. Correct: B**

RAG grounds the model's responses in verified external data sources, directly addressing hallucination by retrieving factual information before generation. Lower temperature (0.2) reduces randomness and creative fabrication, making outputs more deterministic and factual. This combination is the industry standard approach for accuracy-critical applications.

---

**Q20. Correct: A**

At 500K daily items with predictable patterns, fine-tuning a smaller open-source model (like Llama or Mistral) and self-hosting eliminates per-token API costs. Fine-tuning on brand examples maintains voice consistency. The high volume makes the upfront fine-tuning investment worthwhile, and ongoing costs become compute-only, drastically reducing the $12K/month API spend.

---

**Q21. Correct: B**

Constitutional AI allows defining explicit rules that the model must follow, such as 'never infer demographic information not explicitly stated.' This directly addresses the specific bias behavior of making unsupported assumptions. The technique uses the model itself to critique and revise outputs against defined principles, making it effective for this exact use case.

---

**Q22. Correct: C**

This two-stage approach (fast Model A for initial retrieval, slower Model B for re-ranking only 100 results) balances accuracy and latency. Model A handles the 10K queries/hour volume quickly, then Model B's superior accuracy improves only the most promising results. Re-ranking 100 items is fast even with Model B. This hybrid approach is standard for production semantic search under latency constraints.

---

**Q23. Correct: B**

The company deploying the AI application is responsible for its outputs, regardless of user prompts. Courts have held service providers liable for copyright infringement in generated content. Implementing content filtering, plagiarism detection, and citations is the appropriate mitigation. Companies like GitHub Copilot have added duplication detection for this reason.

---

**Q24. Correct: B**

PII tokenization (detecting PII via NER, replacing with tokens like [NAME_1], [ACCOUNT_1], processing the sanitized text, then substituting real values back) prevents PII from being sent to external model APIs or logged. This is the privacy-preserving approach recommended by NIST and used by companies like AWS Comprehend for PII protection. The model never sees actual PII.

---

**Q25. Correct: A**

Few-shot prompting provides concrete examples of the desired behavior (tone, completeness, structure), which is far more effective than abstract instructions. 3-5 examples establish a pattern the model can follow consistently. This is empirically the most effective technique for style and format consistency in production systems.

---

**Q26. Correct: B**

Foundation models trained on multilingual data can occasionally generate in other languages, especially if prompts contain words that appear in multiple languages or trigger multilingual patterns. Explicit output language constraints plus post-generation language detection are the standard mitigation. This is a known behavior of multilingual models.

---

**Q27. Correct: D**

Map-reduce leverages Model X (cheap) for parallel chunk processing, then Model Y for combining summaries. At 15K-25K words (~20K-33K tokens), docs exceed Model X but mostly fit Model Y. This hybrid approach minimizes expensive Model Z usage while maintaining quality through proper combination. Parallelization also improves throughput for 50K reports/month.

---

**Q28. Correct: A**

Language models can memorize and regurgitate sensitive data from training corpora, including API keys, passwords, and private information. This is a documented risk (e.g., extracting training data papers). Secret scanning tools (like GitHub's secret detection) should check outputs before delivery. This is critical for preventing credential leakage.

---

**Q29. Correct: A**

Rule-based post-processing provides deterministic, auditable control over outputs. By scanning for diagnosis language, medical predictions, and treatment recommendations, non-compliant outputs can be blocked with 100% certainty. For regulatory compliance, deterministic controls are superior to probabilistic approaches (RLHF, prompting). This is the only option that guarantees constraint adherence.

---

**Q30. Correct: B**

Temperature = 0.0 produces deterministic, repeatable outputs by always selecting the most probable next token. This is essential for regulatory compliance where identical inputs must produce identical outputs for audit trails.

---

**Q31. Correct: C**

This is hallucination, where the model generates plausible-sounding but false information. RAG grounds responses in verified source documents, significantly reducing hallucinations by retrieving actual medical literature before generation.

---

**Q32. Correct: B**

Output filtering catches content that bypasses input checks (like obfuscated requests), while guardrails provide policy-based validation. This defense-in-depth approach protects against prompt injection and ensures generated content complies with safety policies regardless of how the input was crafted.

---

**Q33. Correct: A**

Larger models exhibit emergent capabilities and better generalization to out-of-distribution examples. While both models scored similarly on the test set, Model A's scale enables it to handle the greater diversity and complexity of real-world production data that differs from the test distribution.

---

**Q34. Correct: B**

RAG dynamically retrieves the most relevant examples for each specific query, providing better context than static few-shot examples. It's cost-effective because it doesn't require expensive fine-tuning or larger models, and retrieves only relevant contracts rather than stuffing the context window with potentially irrelevant examples.

---

**Q35. Correct: D**

During autoregressive generation, models must generate one token at a time and cannot parallelize across the sequence being generated (though they can parallelize across batch and attention heads). Training processes entire sequences in parallel. This sequential token generation is why inference can be more computationally intensive per-token despite training processing entire batches.

---

**Q36. Correct: B**

Low temperature (0.2) reduces randomness and ensures deterministic outputs. Structured output formatting with JSON schema validation enforces the required format programmatically. Few-shot prompting with compliant examples teaches the model the exact pattern needed. This combination addresses both the consistency requirement and format compliance.

---

**Q37. Correct: C**

Multilingual training with cross-lingual transfer is essential for handling 15 languages and code-switching. Models trained this way learn shared representations across languages and can handle mid-conversation language switches. This directly addresses the core requirements of multilingual understanding and generation with code-switching capability.

---

**Q38. Correct: B**

Hallucination is a fundamental characteristic of generative models that predict likely token sequences based on training patterns. For less common topics with sparse training data, models generate plausible-sounding content by combining patterns from related contexts, producing confident but incorrect outputs. This is inherent to how these models work, not a fixable bug.

---

**Q39. Correct: C**

When correct documents are retrieved but the answer contradicts them, the problem is in the generation phase. The foundation model must be properly instructed and architected to prioritize retrieved context over its parametric knowledge. This requires explicit grounding mechanisms, appropriate prompting, and potentially fine-tuning to follow retrieved evidence faithfully.

---

**Q40. Correct: B**

Systematic performance degradation on specific demographic groups indicates training data bias. The model learned patterns predominantly from majority-group data and lacks exposure to diverse linguistic expressions. This is a fundamental bias issue requiring diverse training data, not a tuning or prompting fix. It reflects real-world fairness concerns in AI deployment.

---

**Q41. Correct: C**

Amazon Textract handles OCR, layout analysis, tables, and forms excellently but cannot be fine-tuned for custom business fields. Fine-tuning a Bedrock FM on the structured text output from Textract allows the model to learn company-specific field patterns and extraction logic while leveraging Textract's proven OCR capabilities. This two-stage approach is the standard architecture for custom document understanding at scale.

---

**Q42. Correct: B**

Fine-tuning with differential privacy is the state-of-the-art approach for generating synthetic data that maintains statistical properties while providing mathematical privacy guarantees. The fine-tuned model learns the underlying distributions and correlations in the data, and differential privacy ensures individual patient records cannot be reconstructed. This is the only option that provides both provable privacy and high-fidelity statistical distributions.

---

**Q43. Correct: C**

Amazon Personalize provides real-time recommendations optimized for sub-200ms latency and exposes the reasoning metadata (user-item interactions, item features used). Rule-based explanation templates using this metadata are fast, cost-effective, accurate, and satisfy the trust requirement without adding significant latency. This is a proven pattern for explainable recommendations at scale.

---

**Q44. Correct: C**

Amazon Comprehend DetectPiiEntities has proven high accuracy for standard PII, and custom entity recognition can be trained specifically for legal entities with labeled data. The multi-pass approach (standard PII first, then custom entities) with human review of low-confidence predictions is the architecture most likely to exceed 99.9% accuracy. This combines purpose-built tools with domain customization and human oversight.

---

**Q45. Correct: A**

Amazon Lookout for Equipment is purpose-built for predictive maintenance on sensor time-series data and excels at this specific task. RAG with Bedrock allows the system to generate natural language explanations grounded in the actual repair manuals and documentation, providing citations. This separation of concerns (specialized service for prediction, FM for explanation) is architecturally sound and leverages each service's strengths.

---

**Q46. Correct: A**

Amazon Lex handles conversation management, slot filling, and intent recognition very efficiently and cost-effectively for high-volume scenarios. Using Bedrock only for final response generation (when needed) minimizes expensive FM inference calls. This architecture leverages Lex's optimized conversation engine for the heavy lifting and uses the FM strategically, significantly reducing costs compared to using Bedrock for every turn.

---

**Q47. Correct: C**

Drug-drug interaction discovery requires explicit relationship mapping and multi-hop reasoning (Drug X → Protein Y ← Drug Z implies potential interaction). Knowledge graphs in Neptune excel at storing and querying these explicit relationships. Amazon Comprehend Medical extracts medical entities, and Bedrock can reason over the structured graph to identify novel interaction patterns. This architecture separates structured knowledge representation from reasoning, which is crucial for reliable scientific inference.

---

**Q48. Correct: A**

This architecture uses purpose-built services (Rekognition for video analysis, Transcribe for speech, Textract for text) that are optimized, cost-effective, and accurate for their specific tasks. Amazon Bedrock acts as the synthesis layer, taking structured outputs and generating natural language descriptions. This separation of concerns is efficient, scalable, and cost-effective for processing 20,000 videos in 6 months.

---

**Q49. Correct: D**

Dynamic pricing is fundamentally a predictive modeling problem best solved with ML models that can learn complex, non-linear relationships from historical data. SageMaker Clarify provides SHAP values showing which features (demand, competitors, inventory, season) contributed to each pricing decision. Amazon Bedrock then converts these technical explanations into business-friendly natural language. This architecture separates pricing optimization (ML model) from explanation generation (FM), leveraging each service's strengths.

---

**Q50. Correct: C**

Fraud detection on structured financial data (income, credit score) is best handled by purpose-built ML models like gradient boosting, which excel at this task. Unstructured data (essays, documents) benefits from NLP analysis with Comprehend and Bedrock. The ensemble approach combines the strengths of both - statistical ML for structured data and FMs for unstructured understanding. SageMaker Clarify provides the explanation layer. This is a proven architecture for multi-modal fraud detection.

---

**Q51. Correct: B**

This multi-stage approach maximizes accuracy: Textract for OCR, Comprehend Medical for medical entity recognition (FDA-approved, high accuracy), structured templates for standardized clinical metrics extraction (ensuring consistency), and Bedrock for narrative generation from validated structured data with citations. The citations to page numbers allow easy verification. This architecture provides the highest accuracy-to-manual-review ratio for regulatory-sensitive content.

---

**Q52. Correct: A**

Amazon Personalize is purpose-built for personalized recommendations at massive scale and handles behavior-based recommendations efficiently. Batch processing explanations overnight with Bedrock (rather than real-time) dramatically reduces costs for 500,000 users while still providing timely explanations. Students don't need instant explanation generation - they need the recommendations to be available when they log in. This architecture optimizes for scale and cost.

---

**Q53. Correct: B**

A strict RAG architecture where the FM can ONLY work with retrieved content (and is architecturally prevented from generating beyond retrieved evidence) provides the strongest safeguards. Amazon Kendra's verified medical knowledge base becomes the source of truth, and Bedrock synthesizes and explains only what's retrieved. This is the only architecture that structurally prevents hallucinated medical claims, which is critical for liability in healthcare.

---

**Q54. Correct: B**

Fine-tuning Amazon Titan Text on domain-specific anonymized data creates a model that learns the statistical distributions, patterns, and relationships within transaction data. This enables controlled generation with parameters for segments and constraints while ensuring the model never saw PII during training. Structured prompts allow precise control over conditional generation requirements.

---

**Q55. Correct: A**

Amazon Bedrock Knowledge Bases with OpenSearch Serverless provides sub-3-second retrieval at scale with built-in citation support. Cohere Embed specializes in semantic search accuracy for domain-specific content. Claude 3 Sonnet balances response quality with speed. Custom metadata filtering enables distinguishing document types and authority levels. The RetrieveAndGenerate workflow provides attribution to source documents automatically.

---

**Q56. Correct: A**

Claude 3.5 Haiku provides the lowest per-token cost in the Claude family while maintaining quality for structured generation tasks. Prompt caching dramatically reduces costs for repeated brand guidelines and templates across 50K products. Parallel inference for languages with batching keeps latency acceptable. At ~$0.25 per 1M input tokens and $1.25 per 1M output tokens with caching, this approach stays well under $0.02/product even for multilingual generation. Amazon Translate handles compliance statements cost-effectively.

---

**Q57. Correct: A**

Amazon Comprehend Medical is purpose-built for clinical text with pre-trained models achieving >95% accuracy on medical entities, ICD-10 mapping, and medication extraction. It's HIPAA-eligible and optimized for high-throughput medical document processing (easily handles 10K/hour). HealthLake provides native FHIR formatting for healthcare interoperability. This is the only purpose-built, validated solution for clinical extraction that meets regulatory requirements.

---

**Q58. Correct: A**

Claude 3.5 Sonnet handles multi-task analysis in single API calls with structured outputs, reducing orchestration complexity. It achieves >92% accuracy on classification tasks with proper prompt engineering and supports 200K+ token context for full conversation analysis. Step Functions provides reliable orchestration with parallel processing for the 30-minute SLA. Batch processing via S3 and Step Functions is cost-effective for 500K monthly conversations. QuickSight integrates natively for QA reporting.

---

**Q59. Correct: A**

Claude 3.5 Haiku provides optimal cost-performance for text generation tasks at ~$0.001 per 1K tokens. Prompt caching reduces costs by 90% for repeated brand guidelines across 500K descriptions (10K videos × 50 segments). At ~$0.25 input + $1.25 output per 1M tokens with caching, total cost is well under $0.50/video. Amazon Bedrock model evaluation provides built-in quality assessment. CloudWatch Evidently offers native A/B testing integration. This architecture is purpose-built for high-volume, cost-optimized content generation.

---

**Q60. Correct: A**

Multi-step prompting with Claude provides the required explainability through chain-of-thought reasoning and intermediate outputs that can be audited. This approach handles complex multi-task requirements (extraction, analysis, comparison, generation) while maintaining traceability for each step, which is critical for financial regulatory compliance. Storing intermediate outputs creates the audit trail needed.

---

**Q61. Correct: A**

This approach correctly sequences operations: PHI removal must happen first before any LLM processing to ensure compliance. Amazon Comprehend Medical is purpose-built for HIPAA-compliant PHI detection. Using Claude with language-specific prompts that include reading level and terminology constraints provides better control than generic translation. The validation step for terminology consistency is essential for medical accuracy across languages.

---

**Q62. Correct: A**

Guardrails for Amazon Bedrock provides native, efficient filtering at inference time with denied topics and customizable patterns. The combination of proactive filtering (Guardrails) and validation against product specs addresses both competitor mentions and unsubstantiated claims systematically. This multi-layer approach (prevent generation + verify accuracy) is most reliable for production use.

---

**Q63. Correct: A**

Hierarchical chunking with metadata preservation addresses the root cause—loss of structural context and cross-reference information during chunking. Multi-hop retrieval intelligently fetches referenced sections when detected, ensuring the LLM has complete context for interconnected clauses. This approach maintains the efficiency of RAG while solving the cross-reference problem.

---

**Q64. Correct: A**

The two-stage approach with explicit instructions and post-generation validation addresses LLM hallucination systematically. Constraining the model to only cite provided sources reduces hallucination, while verification ensures accuracy by checking: (1) citation exists in retrieved set, and (2) the specific claim actually appears in that paper. This catches both fabricated citations and incorrect attributions.

---

**Q65. Correct: C**

This approach optimizes cost by using purpose-built services (Rekognition for visual, Comprehend for text toxicity) which are significantly cheaper and faster than LLMs for straightforward detection. Only flagged content goes to the expensive LLM for nuanced context evaluation. This hybrid approach meets the 10-minute SLA (purpose-built services are faster) while minimizing LLM API costs, which would be substantial at 10,000 videos/day if every video used Bedrock for all tasks.

---

**Q66. Correct: A**

Claude 3.5 Sonnet provides the optimal balance of capabilities: 200K token context window handles even the longest transcripts (50K tokens) in a single call eliminating chunking complexity, native JSON mode ensures structured output without parsing issues, prompt caching dramatically reduces latency and cost for repeated system instructions (financial analysis framework) and company-specific context that remains constant across calls, and superior reasoning capabilities accurately extract nuanced financial metrics and sentiment. Real-time performance is achieved through caching without infrastructure overhead.

---

**Q67. Correct: B**

AWS responsible AI guidelines prioritize fairness as a core pillar. When disparate impact is detected (23% difference in approval rates for similar profiles), active mitigation is required. Demographic parity constraints during retraining directly address the fairness gap. A slight accuracy trade-off is acceptable when it prevents discriminatory outcomes. This approach is proactive and addresses root cause rather than symptoms.

---

**Q68. Correct: A**

This is a multi-select question requiring two answers: A and C. RAG with verified medical sources directly addresses hallucination by grounding responses in factual data (veracity pillar). Human-in-the-loop is critical for high-stakes healthcare decisions (safety and governance pillars). Together they provide technical mitigation (RAG) and procedural safeguard (human verification). For the exam format limitation, A is the primary technical control.

---

**Q69. Correct: D**

This scenario describes a classic filter bubble and feedback loop problem, which falls under robustness and safety. The model creates a self-reinforcing system that reduces diversity and long-term platform health. Exploration strategies (like epsilon-greedy or Thompson sampling) intentionally inject diversity to prevent feedback loops. This addresses the root technical cause. While monitoring (option C) is important, the question asks for the violated principle AND what should have been implemented as a solution—exploration is the preventive technical control.

---

**Q70. Correct: B**

Transparency requires providing meaningful information about AI decisions, especially when they affect individuals differently. SageMaker Clarify provides post-hoc explanations using SHAP values or other techniques, which allow explaining complex models without sacrificing performance. For regulated industries, maintaining explanation logs creates an audit trail. This balances business needs (complex models for better pricing) with responsible AI requirements (explainable decisions).

---

**Q71. Correct: B**

This approach addresses immediate harm (excessive false positives causing account restrictions) while maintaining platform safety. Prioritizing human review for affected populations provides a near-term mitigation while model improvements are developed. Cultural context training addresses the root cause (misunderstanding of cultural norms). This balances safety, fairness, and practicality. It doesn't lower safety standards but adds human judgment where the AI is demonstrably less reliable.

---

**Q72. Correct: A**

For an AI system used by expert scientists (not direct patient care), transparency through comprehensive documentation is most critical. Model cards that explicitly document known biases, limitations, and appropriate use cases empower researchers to interpret results correctly and compensate for known limitations. Scientists can then make informed decisions about which predictions to pursue and which require additional validation. This enables responsible use without unnecessarily restricting potentially valuable research directions.

---

**Q73. Correct: B**

Customer managed KMS keys provide full control over encryption, support automatic rotation (configurable at 90 days or annually), and integrate with CloudTrail for detailed audit logging of all key usage. This meets all requirements: encryption at rest and in transit, customer control, automatic rotation at the specified interval, and comprehensive audit trails for compliance.

---

**Q74. Correct: A**

Options A and D together provide the complete solution. SageMaker Model Monitor with DataCaptureConfig automatically captures prediction requests/responses, monitors for drift against baselines, and scales across multiple models/accounts efficiently. CloudTrail data events capture the actual API calls with full request/response payloads, enabling complete traceability, and Athena provides efficient querying for audit purposes.

---

**Q75. Correct: C**

This solution implements defense in depth: S3 Access Points provide fine-grained S3 access control, Kendra ACLs ensure document-level authorization during retrieval, Bedrock Agents with action groups can programmatically validate permissions before document retrieval (preventing unauthorized context), and WAF rules add protection against prompt injection attempts. This creates multiple security layers that work together to prevent both access control bypasses and prompt injection.

---

**Q76. Correct: B**

This solution addresses all requirements: EU region processing (GDPR data residency), S3 Glacier vault lock ensures 7-year retention of original recordings cannot be altered (regulatory compliance), separate storage for deletable transcripts, DynamoDB provides efficient mapping for deletion requests, Macie automatically detects PII for proper tagging, and Step Functions orchestrates the complex workflow of deleting transcripts while preserving locked recordings. The architecture separates immutable compliance data from deletable personal data.

---

**Q77. Correct: D**

This solution provides comprehensive controls: KMS encryption protects at rest, IAM permission boundaries prevent privilege escalation and block exports at the principal level, SCPs provide organization-wide preventive controls that can't be overridden, aws:PrincipalOrgID prevents accidental cross-org sharing, session names in IAM roles provide non-repudiation by tying actions to specific employees, CloudTrail log file integrity validation ensures audit logs can't be tampered with, and separate security account for logs prevents deletion. This creates multiple layers of preventive and detective controls.

---

**Q78. Correct: A**

Amazon A2I is purpose-built for this exact use case—human review of ML predictions with built-in workflow management. It natively supports confidence threshold configuration, integrates with Textract and Comprehend, provides worker authentication through Cognito, automatically captures complete audit trails (who reviewed, when, what decision, input/output data), and integrates with CloudTrail for API-level governance. DynamoDB provides queryable audit history, and S3 versioning ensures document lineage. This is the AWS-native, fully managed solution designed specifically for ML governance with human-in-the-loop.

---

