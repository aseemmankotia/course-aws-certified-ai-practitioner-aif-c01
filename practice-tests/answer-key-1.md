# Answer Key — Practice Test 1

**Q1. Correct: B**

Supervised learning with classification is correct because the company has labeled training data (X-rays marked as fractured/non-fractured) and needs to predict categorical outcomes (fracture detected: yes/no). Classification algorithms learn from labeled examples to categorize new inputs.

---

**Q2. Correct: C**

Unsupervised learning with clustering is correct because there are no predefined labels or categories. Clustering algorithms like K-means discover natural groupings in unlabeled data based on similarity patterns in purchasing behavior.

---

**Q3. Correct: A**

This correctly describes the hierarchical relationship: AI is the broadest concept (any system exhibiting intelligent behavior), ML is a subset of AI (systems that learn from data), and deep learning is a subset of ML (using multi-layered neural networks for representation learning).

---

**Q4. Correct: B**

Overfitting is correct because high training accuracy (98%) combined with significantly lower validation/test accuracy (75%) indicates the model learned training data too specifically, including noise and peculiarities, rather than generalizable fraud patterns.

---

**Q5. Correct: B**

Regression is correct because the target variable is a continuous numerical value (hours of remaining life). Regression algorithms predict quantities on a continuous scale rather than discrete categories.

---

**Q6. Correct: C**

Reinforcement learning is correct because the system learns through interaction (trial and error) and receives rewards (positive feedback for sales) or penalties (negative feedback for ignored suggestions). The agent learns a policy to maximize cumulative rewards over time.

---

**Q7. Correct: B**

The validation set is used during model development to tune hyperparameters (learning rate, number of layers, regularization strength, etc.) and make model selection decisions. It provides feedback to prevent overfitting without contaminating the test set, which must remain unseen until final evaluation.

---

**Q8. Correct: B**

Fine-tuning a pre-trained foundation model is most cost-effective because it leverages knowledge learned from massive datasets during pre-training. With only 500 examples, fine-tuning can adapt the model to industry-specific documents efficiently, while training from scratch would require significantly more data and compute resources.

---

**Q9. Correct: A**

The fundamental distinction is that generative models learn the joint probability distribution P(X,Y) to generate new data instances (text, images, code, etc.), while discriminative models learn the conditional probability P(Y|X) to classify or make predictions about existing inputs.

---

**Q10. Correct: B**

LLMs excel at natural language understanding, context comprehension, and generating human-readable text. Fine-tuning on medical domain data enables the model to handle specialized terminology while maintaining conversational capabilities. This matches all requirements: NLP understanding, medical terminology handling, and explanation generation.

---

**Q11. Correct: B**

Recall (sensitivity/true positive rate) measures the proportion of actual fraud cases correctly identified. With only 45% recall, the model misses 55% of fraud cases, which is critical for fraud detection where catching fraudulent transactions is paramount. High accuracy likely results from correctly identifying the large number of legitimate transactions (class imbalance).

---

**Q12. Correct: B**

The validation set should be separate from training data to prevent overfitting during hyperparameter tuning. The test set must remain completely untouched until final evaluation to provide an unbiased estimate of real-world performance. Standard practice is train/validation/test splits (e.g., 70/15/15 or 80/10/10 of original data).

---

**Q13. Correct: C**

Hybrid systems combine collaborative filtering (user-item interactions) with content-based filtering (product features/attributes). This addresses the cold-start problem: for new users, content-based methods can recommend items similar to what they've shown interest in, while collaborative filtering leverages patterns from similar users as more data accumulates.

---

**Q14. Correct: B**

This is a supervised binary classification problem: predict whether equipment will fail (yes/no) within a specific time window (24-48 hours). Historical labeled data exists (sensor readings + failure records). Classification models can output probability scores for failure risk, enabling actionable maintenance decisions with confidence thresholds.

---

**Q15. Correct: A**

The model has learned patterns specific to high-resolution professional photos (overfitting to training distribution) but fails to generalize to different image qualities and conditions. This is overfitting caused by training data not representing the diversity of real-world data. The 30-point accuracy gap between training and test indicates the model memorized training-specific features rather than learning robust, generalizable patterns.

---

**Q16. Correct: B**

Amazon Bedrock provides access to foundation models (like Claude, Titan, etc.) that excel at conversational understanding, context retention, and generating explanations. It requires no ML expertise, supports multi-turn conversations natively, and can handle ambiguous natural language inputs. Foundation models are pre-trained on vast datasets and can perform complex reasoning tasks without custom training.

---

**Q17. Correct: C**

Recall (also called Sensitivity or True Positive Rate) measures the proportion of actual positive cases (customers who will churn) that are correctly identified. The formula is TP/(TP+FN). Since the business wants to minimize false negatives (missing customers who will actually churn), maximizing recall is the correct focus. High recall ensures most at-risk customers are identified, even if some false positives occur.

---

**Q18. Correct: C**

For categorical data with significant missing values (30%), the best practice is to use mode imputation (most frequent value) or domain-specific imputation, and importantly, create a separate binary indicator feature to flag which records had missing values. This preserves the information that data was missing (which may be predictive) and maintains the dataset size. The missing pattern itself could be meaningful (e.g., users who don't provide age may have different behavior).

---

**Q19. Correct: C**

Variational autoencoders (VAEs) with differential privacy are specifically designed for generating synthetic data that preserves statistical properties while providing mathematical privacy guarantees. Differential privacy adds noise during training to prevent memorization of individual records, making it the best choice for sensitive healthcare data.

---

**Q20. Correct: C**

Task-specific fine-tuning or optimization is the most common reason a smaller model outperforms a larger general-purpose model. A 70B model fine-tuned on summarization tasks will typically outperform a larger general-purpose model that hasn't been optimized for that specific task. This demonstrates that model size alone doesn't determine performance.

---

**Q21. Correct: C**

Temperature controls the randomness of predictions by scaling the logits before applying softmax. Lower temperatures (e.g., 0.1) make the model more deterministic and focused on high-probability tokens. Higher temperatures (e.g., 1.0 or above) increase randomness and creativity by flattening the probability distribution. Temperature 0 = deterministic, always picks highest probability token.

---

**Q22. Correct: C**

Hallucination is when generative AI models produce outputs that are fluent and coherent but factually incorrect or not grounded in training data. This is a well-known limitation of LLMs where they generate plausible-sounding but false information, especially about specific facts, numbers, or specifications.

---

**Q23. Correct: B**

Model quantization (reducing precision from FP32 to INT8/INT4) and optimized inference infrastructure are essential for meeting high-throughput, low-latency requirements. Quantization reduces model size and speeds up inference while maintaining acceptable quality. Combined with optimization techniques like batching, caching, and specialized hardware, this enables the required 10,000 req/min at <100ms.

---

**Q24. Correct: B**

Discriminative models learn P(Y|X) - the probability of a label given input - essentially learning decision boundaries between classes. Generative models learn P(X) or P(X|Y) - the distribution of the data itself - allowing them to generate new samples. Example: A discriminative model classifies if an image is a cat; a generative model creates new cat images.

---

**Q25. Correct: B**

Context window size determines how much text the model can process at once. A 50-page earnings call transcript could be 50,000-100,000 tokens. Models with smaller context windows (e.g., 4K tokens) would require chunking the document, potentially missing connections between sections. Models with large context windows (32K, 100K, or 200K tokens) can process the entire document at once, critical for accurate metric extraction.

---

**Q26. Correct: B**

Self-attention allows each token in a sequence to attend to all other tokens, computing attention weights that determine how much each token should influence the representation of every other token. This enables the model to capture long-range dependencies and contextual relationships. For example, in 'The cat sat on the mat because it was soft', self-attention helps 'it' attend to 'mat' rather than 'cat'.

---

**Q27. Correct: B**

Top-k sampling limits the model to choosing from only the k most probable next tokens at each step. Top-k=10 means only the 10 highest probability tokens are candidates, leading to more predictable outputs. Top-k=50 includes more lower-probability options, increasing diversity but risking less coherent outputs. Top-k=1 is equivalent to greedy decoding (always pick the most probable token).

---

**Q28. Correct: B**

Diffusion models (like DALL-E 2, Stable Diffusion, Midjourney) have become the state-of-the-art for image generation because they produce higher quality, more detailed, and more realistic images than VAEs. VAEs tend to produce blurrier images due to their reconstruction objective and the way they learn latent representations. For marketing materials requiring high-quality product images, diffusion models are superior.

---

**Q29. Correct: C**

Retrieval-Augmented Generation (RAG) retrieves relevant current information from an external knowledge base and includes it in the prompt, allowing the model to generate responses based on up-to-date information. This solves the training cutoff problem without retraining, is cost-effective, and can be updated in real-time as new products launch. RAG combines retrieval with generation for grounded, current responses.

---

**Q30. Correct: B**

LLMs are specifically designed for text generation tasks and can be fine-tuned on domain-specific financial data to produce accurate, contextually relevant investment analysis and recommendations. Fine-tuning allows the model to learn financial terminology, regulatory requirements, and industry-specific patterns.

---

**Q31. Correct: D**

Temperature is a sampling parameter that controls randomness in token selection. Lower temperature (closer to 0) makes outputs more deterministic and focused, selecting tokens with highest probability. Higher temperature increases randomness and creativity, allowing lower-probability tokens to be selected. This directly affects output diversity and creativity.

---

**Q32. Correct: C**

Cosine similarity measures the cosine of the angle between two vectors, focusing on directional similarity rather than magnitude. This is the standard metric for comparing embeddings because it captures semantic similarity effectively and is robust to vector magnitude differences. Values range from -1 to 1, with 1 indicating identical direction (high similarity).

---

**Q33. Correct: B**

Hallucination is when generative models produce outputs that are fluent and confident-sounding but factually incorrect or nonsensical. LLMs are trained to predict plausible next tokens based on patterns, not to verify factual accuracy. They can generate false information when they lack knowledge or misapply learned patterns, especially problematic in high-stakes domains like healthcare.

---

**Q34. Correct: B**

In RAG, the retrieval component searches external knowledge bases (vector databases, document stores, APIs) to find relevant information based on the input query. This retrieved context is then provided to the LLM along with the prompt, grounding the generation in actual source documents. This reduces hallucinations and provides up-to-date information beyond the model's training data.

---

**Q35. Correct: A**

GANs use an adversarial training approach with two networks: a generator that creates images and a discriminator that tries to distinguish real from fake images. This adversarial game improves both networks. Diffusion models work differently by learning to reverse a noise-adding process, starting with pure noise and iteratively denoising to create images. This is a fundamental architectural distinction affecting training dynamics and output characteristics.

---

**Q36. Correct: C**

VAEs are specifically designed to learn latent representations of data and generate novel samples by sampling from the learned distribution. They excel at generating variations that maintain the statistical properties of training data while creating new combinations, making them ideal for generating novel but biologically plausible protein sequences.

---

**Q37. Correct: A**

Parameters (weights and biases) are learned during training through backpropagation and remain fixed during inference. Hyperparameters control the generation behavior - temperature, top-p, top-k can all be adjusted at inference time to control randomness, creativity, and determinism of outputs without changing the model itself.

---

**Q38. Correct: A**

GANs are specifically designed for synthetic data generation. When trained on anonymized data, they learn the underlying distribution and correlations without memorizing individual records. The generator creates entirely new synthetic samples that maintain statistical properties while providing strong privacy guarantees by not directly copying real data points.

---

**Q39. Correct: A**

The attention mechanism computes attention scores that determine how much each input token should influence the generation of each output token. This allows the model to dynamically focus on relevant parts of the input sequence, capturing long-range dependencies and contextual relationships critical for coherent generation.

---

**Q40. Correct: C**

Foundation models are pattern-based predictors that generate statistically probable sequences based on training patterns. They don't have explicit knowledge bases or fact-checking mechanisms. When generating citations or specific claims, they predict text that 'looks like' a valid reference based on patterns seen during training, which can result in plausible-sounding but fabricated information.

---

**Q41. Correct: B**

Amazon Textract is specifically designed for document analysis and OCR with specialized features for forms (key-value pairs) and handwriting recognition. The Queries feature allows extraction of specific fields, and it maintains 95%+ accuracy for handwritten content.

---

**Q42. Correct: B**

RAG with Bedrock Knowledge Bases is designed for this exact scenario: grounding foundation model responses in proprietary documents without fine-tuning. It automatically handles document ingestion, vectorization, retrieval, and source citation.

---

**Q43. Correct: A**

Amazon Comprehend custom classification is purpose-built for this use case and most cost-effective at scale. At 50,000 tickets/day, the per-unit pricing model is significantly cheaper than calling foundation models for each ticket.

---

**Q44. Correct: A**

This combination handles both requirements: Textract extracts text from scanned PDFs, Comprehend DetectPII identifies PII with high accuracy across multiple types, and Lambda performs the actual redaction. This is the standard AWS pattern for PII redaction at scale.

---

**Q45. Correct: A**

Claude Haiku is optimized for speed and cost-efficiency while maintaining quality for summarization tasks. At 500 articles/day with 2,000 words each, Haiku provides the best balance of speed (sub-second response), cost (lowest per-token pricing), and quality for summarization.

---

**Q46. Correct: D**

Amazon Comprehend Targeted Sentiment is specifically designed for entity-level sentiment analysis. It detects sentiment associated with specific entities (product features). Combined with custom entity recognition for product-specific features, this provides the exact capability needed.

---

**Q47. Correct: C**

Comprehend Medical with ontology linking provides standardized medical entity extraction (medications, conditions, dosages) linked to RxNorm and ICD-10-CM codes. This ensures accuracy, consistency, and auditability through standardized medical codes, which is critical for pharmaceutical analysis.

---

**Q48. Correct: B**

OpenSearch with k-NN (vector search) using Titan Embeddings provides semantic search at scale for 2M products. Titan Embeddings convert products/queries to vectors capturing semantic meaning, k-NN finds similar vectors, and OpenSearch supports real-time indexing for new products.

---

**Q49. Correct: A**

Bedrock with guardrails allows setting content filters, denied topics, and word filters to enforce regulatory language requirements. Prompt templates ensure consistent structure. This combination enables compliant generative report creation at scale.

---

**Q50. Correct: A**

Textract handles forms, tables, and handwriting extraction from PDFs and images. Comprehend analyzes extracted text for routing (sentiment, key phrases). EventBridge provides event-driven routing. This combination is purpose-built for document processing automation and meets the 2-minute SLA.

---

**Q51. Correct: A**

Comprehend supports 15+ languages natively, provides sentiment analysis and topic modeling (for trending topics), and batch mode is most cost-effective for 10M posts with a 6-hour SLA. Language auto-detection handles mixed-language inputs efficiently.

---

**Q52. Correct: B**

Claude with RAG provides the multi-file context understanding needed for code review. RAG retrieves relevant code files, and Claude's large context window (100K+ tokens) handles complex analysis, bug detection, and explanations. This architecture supports the conversational aspect for junior developers.

---

**Q53. Correct: D**

Textract with Queries specifically extracts required fields from varying document types. Amazon A2I (Augmented AI) enables human review for low-confidence results, ensuring the 98%+ accuracy requirement. This combination provides automated extraction with human-in-the-loop validation.

---

**Q54. Correct: C**

Amazon Bedrock with foundation models like Claude is designed for complex document understanding tasks that require semantic comprehension, context preservation across long documents, and structured information extraction. Foundation models excel at understanding nuanced financial language, extracting multiple entity types, and performing sentiment analysis simultaneously with proper prompt engineering.

---

**Q55. Correct: A**

RAG with Amazon Bedrock provides the best solution by grounding responses in approved, curated documents stored in a knowledge base. This approach significantly reduces hallucinations, ensures responses come from authorized sources, and allows the organization to control exactly what information the chatbot can access. RAG retrieves relevant context before generating responses, keeping answers within defined boundaries.

---

**Q56. Correct: C**

Multilingual foundation models available through Amazon Bedrock (like Claude or Titan) are inherently trained on multiple languages and can perform complex tasks like feature extraction, aspect-based sentiment analysis, and competitor mention detection across languages in a single model with appropriate prompt engineering. This eliminates the need for translation or multiple models while maintaining context and nuance.

---

**Q57. Correct: A**

Claude Haiku through Amazon Bedrock is the most cost-effective model for high-volume document processing tasks while still providing strong performance for structured extraction and summarization with proper prompting. Since lawyers review all output, perfect accuracy isn't required, making Haiku's balance of cost and capability ideal. Few-shot prompting helps ensure consistent output formatting for legal clauses.

---

**Q58. Correct: B**

Amazon Bedrock Knowledge Bases with embeddings provides semantic search capabilities for natural language questions, automatically chunks and indexes documents from S3, integrates with foundation models for conversational responses, and importantly provides source citations showing which document sections were used to generate answers. This ensures workers can verify information and meets the accuracy requirement with traceability.

---

**Q59. Correct: A**

Amazon Bedrock batch inference provides up to 50% cost savings compared to on-demand for large volume processing, making it ideal for 100,000 daily descriptions. Claude Haiku is cost-effective for generation tasks, and the 50-page style guide fits within context windows when embedded in the system prompt, eliminating RAG overhead. Batch processing tolerates the asynchronous nature of this workload.

---

**Q60. Correct: A**

Prompt Flows in Amazon Bedrock enables orchestration of multi-step workflows combining data retrieval, content generation with Claude (excellent at maintaining formatting and following complex instructions), and output formatting. This approach handles the scale (50k daily), maintains consistency through structured prompts, and doesn't require model fine-tuning.

---

**Q61. Correct: B**

Foundation models in Bedrock (like Claude or Titan) excel at structured information extraction when prompted with JSON schema and few-shot examples. This approach provides high accuracy for the specific task, returns data in the required structured format, and can be implemented immediately without training. Modern FMs handle medical terminology effectively with proper prompting.

---

**Q62. Correct: B**

Modern foundation models (Claude, GPT-4, etc.) are natively multilingual and can generate content directly in target languages while maintaining brand voice and adapting to regional preferences in a single API call. This eliminates separate translation steps, reduces token usage (no double processing), and produces more natural, contextually appropriate content than translate-then-refine approaches.

---

**Q63. Correct: B**

Models like Anthropic Claude 3 (200K token context) can process both the full contract (20-50 pages) and template in a single prompt, enabling direct comparison, identification of deviations, explanations, and suggestions. This approach is most straightforward, maintains full context for accurate analysis, and provides comprehensive results without complex orchestration.

---

**Q64. Correct: B**

Agents for Amazon Bedrock is purpose-built for this use case: Knowledge Bases provide RAG with automatic source citation, action groups enable Salesforce integration through API calls, and function calling supports escalation logic. This fully managed solution handles orchestration, conversation flow, and multi-step tasks without custom code for agent orchestration.

---

**Q65. Correct: B**

A single API call with structured output (JSON) requesting all three platform versions minimizes costs by processing input once, reduces latency (one call vs three), and still produces platform-optimized content. Foundation models excel at multi-constraint generation in a single prompt. At 50 articles/day with 3 posts each, this saves 100 API calls daily compared to separate requests.

---

**Q66. Correct: B**

This approach combines effective prompt engineering (clear format instructions and few-shot examples to guide the model) with a programmatic validation layer that ensures reliability. The deterministic parsing verifies all required sections are present, addressing the consistency and completeness requirements. This is a best practice for production applications requiring structured outputs—use the foundation model's capabilities through prompting while adding deterministic checks for critical requirements. This balances model flexibility with application reliability without requiring expensive fine-tuning.

---

**Q67. Correct: B**

Collecting additional representative training data and validating performance across all demographic segments directly addresses the fairness issue at its root cause. This ensures the AI system performs equitably across all patient populations before deployment, which is a core principle of responsible AI - particularly fairness and inclusiveness.

---

**Q68. Correct: A**

Implementing fairness metrics allows you to quantitatively measure bias, and adjusting the algorithm to reduce stereotyping while maintaining relevance addresses the root cause. This approach balances fairness with system effectiveness, which is a key responsible AI practice.

---

**Q69. Correct: B**

Human review loops in high-stakes systems serve primarily to ensure accountability and provide human oversight for decisions with significant consequences. This is a fundamental principle of responsible AI - maintaining human agency and oversight, especially for decisions affecting lives, rights, or safety (e.g., healthcare, criminal justice, employment).

---

**Q70. Correct: B**

A tiered response system balances security needs with customer impact, implements proportional automated actions based on confidence levels, and maintains human oversight for ambiguous cases. This approach embodies responsible AI principles: accountability (human review for medium-risk), safety (blocking high-confidence fraud), and minimizing harm (not auto-blocking uncertain cases). With 1M daily transactions, 2% false positive = 20,000 legitimate customers blocked daily.

---

**Q71. Correct: B**

Transparency in responsible AI means providing appropriate, contextual information about AI system operation, limitations, and use - tailored to the audience (users, regulators, technical teams may need different levels of detail). It's about meaningful disclosure that enables understanding and informed decisions, not necessarily complete technical exposure.

---

**Q72. Correct: A**

This multi-layered approach addresses multiple responsible AI principles: safety (content filtering), transparency (disclaimers about limitations), accountability (feedback mechanisms and human escalation), and continuous improvement. It acknowledges that no single technical solution fully prevents hallucinations or offensive content in generative AI, requiring multiple complementary safeguards.

---

**Q73. Correct: A**

This solution meets all HIPAA requirements: customer-managed KMS keys provide control over encryption for data at rest, VPC endpoints ensure private connectivity without internet exposure (encryption in transit via TLS), and CloudTrail provides comprehensive API audit logs required for HIPAA compliance. This is the most complete solution with minimal operational overhead.

---

**Q74. Correct: C**

RAG with Amazon Kendra provides direct traceability to source documents, allowing the company to show exactly which data influenced each recommendation. Provenance tracking links outputs to specific knowledge base articles, and Bedrock Agents with detailed logging captures the reasoning chain. This combination directly addresses explainability and traceability requirements for regulatory compliance.

---

**Q75. Correct: B**

Amazon Bedrock Guardrails is specifically designed to filter sensitive information including PII from prompts and model responses in real-time. It can detect and redact or block content containing PII types like names, addresses, credit card numbers, and SSNs before they reach the foundation model.

---

**Q76. Correct: C**

This solution ensures data residency by deploying Bedrock only in EU regions for EU customers, VPC endpoints prevent internet exposure, DynamoDB with disabled backups prevents data replication outside the region, API Gateway resource policies enforce regional boundaries, and Step Functions provides reliable orchestration for data deletion requests required for GDPR right to be forgotten.

---

**Q77. Correct: B**

Amazon Bedrock model invocation logging to S3 captures full request/response data including prompts and outputs. S3 Object Lock in compliance mode with 7-year retention ensures logs cannot be deleted or modified (tamper-proof). KMS encryption protects data at rest. S3 versioning adds protection. Athena enables SQL-based log analysis for auditing.

---

**Q78. Correct: B**

Amazon Bedrock Guardrails is the native, purpose-built feature for applying real-time content filters to foundation model inputs and outputs. It can detect and block profanity, hate speech, and harmful content with pre-built filters and denied topics configuration, with minimal latency impact as it's integrated directly into the Bedrock inference path.

---

