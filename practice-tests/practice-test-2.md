# Practice Test 2: AWS AI Practitioner (AIF-C01): First-Attempt Certification

- **Questions:** 78
- **Time limit:** 90 minutes
- **Passing score:** 70%%

> Answers are in `answer-key-2.md`. Track results in `score-tracker.md`.

---

**Q1.** A healthcare startup is building a system to predict patient readmission risk. They have 500,000 patient records with 45 features each, but only 3% of patients were readmitted. Initial model testing shows 97% accuracy, but the business team reports the model fails to identify most at-risk patients. What is the PRIMARY issue and appropriate solution?

A) The model has high variance due to too many features. Apply L1 regularization to reduce feature count and retrain.
B) The dataset exhibits class imbalance causing the model to optimize for the majority class. Use techniques like SMOTE, class weights, or focus on precision-recall metrics instead of accuracy.
C) The 97% accuracy indicates overfitting to the training data. Increase the train-test split ratio from 80-20 to 60-40.
D) The model architecture is too simple for 45 features. Switch from logistic regression to a deep neural network with at least 5 hidden layers.

---

**Q2.** An e-commerce company wants to reduce the dimensionality of their product catalog dataset containing 200 features (price, ratings, category embeddings, user interaction counts) down to 20 features for clustering analysis. They need to interpret which original features most influence each reduced dimension for business insights. Which technique should they use?

A) t-SNE (t-Distributed Stochastic Neighbor Embedding) because it preserves local structure and is ideal for visualization
B) Autoencoder neural networks because they can learn non-linear feature combinations with high compression ratios
C) PCA (Principal Component Analysis) because it produces interpretable linear combinations with loadings that show feature contributions to each component
D) Random projection because it maintains pairwise distances while being computationally efficient for high-dimensional data

---

**Q3.** A financial institution is developing a loan approval model. Regulatory requirements mandate that the institution must be able to explain each individual loan decision to customers and auditors, including which specific factors led to approval or denial. The dataset has 50,000 applications with 80 features including credit score, income, debt ratios, and employment history. Which modeling approach BEST satisfies this requirement?

A) Gradient Boosting Machine (XGBoost) with SHAP values to provide post-hoc feature importance explanations for each prediction
B) Decision Tree with max_depth=10 to create an inherently interpretable model structure that can be visualized
C) Deep Neural Network with attention mechanisms to highlight which features the model focuses on
D) Logistic Regression with L2 regularization to produce interpretable coefficients showing feature impact

---

**Q4.** A data scientist is training a CNN for medical image classification. During training, they observe: Training loss: 0.15, Validation loss: 0.14, Test accuracy: 94%, Validation accuracy: 93%. However, when deployed to a hospital using images from a different scanner model, accuracy drops to 78%. What is the MOST likely root cause?

A) The model is overfitting to the training data due to insufficient regularization, causing poor generalization to new data
B) The model suffers from high bias and needs a more complex architecture with additional convolutional layers
C) The model exhibits distribution shift (domain shift) where training data doesn't represent the deployment environment's data distribution
D) The batch size during training was too large, causing the model to converge to sharp minima that don't generalize well

---

**Q5.** A recommendation system uses collaborative filtering to suggest products. The user-item interaction matrix is 1,000,000 users × 500,000 items, but only 0.01% of entries are non-zero (extremely sparse). Matrix factorization via SVD is computationally prohibitive. Which approach is MOST appropriate for this scale and sparsity?

A) Use mini-batch gradient descent with Alternating Least Squares (ALS) to iteratively factorize the matrix, processing only observed interactions
B) Apply k-means clustering on users and items separately, then use cluster centroids to reduce dimensionality before applying SVD
C) Convert the sparse matrix to dense format and use distributed SVD across multiple GPU nodes
D) Use item-based collaborative filtering with cosine similarity, computing similarities only for item pairs with at least 100 common users

---

**Q6.** A time-series forecasting model predicts hourly energy consumption. The data scientist splits data as: records 1-10,000 for training, records 10,001-12,000 for validation, records 12,001-14,000 for testing. After deployment, forecast accuracy is significantly worse than test metrics. What is the MOST critical flaw in the evaluation approach?

A) The test set is too small (2,000 records) compared to training set (10,000 records), leading to unreliable test metrics
B) Time-series data should use k-fold cross-validation instead of a single train-validation-test split to get robust performance estimates
C) The model may have data leakage from future timestamps into past predictions during training, which wouldn't occur in real-time deployment
D) The validation and test sets don't account for distribution shift over time; recent data patterns may differ from historical patterns the model learned

---

**Q7.** A model training job uses stochastic gradient descent (SGD) with learning_rate=0.1, batch_size=32. Training loss oscillates wildly and never converges after 100 epochs. Reducing learning_rate to 0.001 makes training extremely slow with minimal progress after 100 epochs. Which combination of changes is MOST likely to achieve both stable and efficient convergence?

A) Use Adam optimizer with learning_rate=0.001 and implement learning rate scheduling to adaptively adjust the rate during training
B) Increase batch_size to 512 and keep learning_rate=0.1 to smooth out gradient estimates and reduce oscillation
C) Switch to momentum-based SGD with momentum=0.9 and learning_rate=0.01, and implement gradient clipping to prevent exploding gradients
D) Use learning_rate=0.01 with exponential decay, and implement early stopping to halt training when validation loss stops improving

---

**Q8.** A natural language processing model achieves 99% accuracy on a sentiment classification task with three classes: Positive (45%), Neutral (45%), and Negative (10%). The confusion matrix shows the model predicts Positive for 95% of all samples. Business users report the model is 'useless' for identifying negative sentiment. What is the BEST metric to optimize during model retraining?

A) Weighted F1-score with class weights inversely proportional to class frequency
B) Macro-averaged F1-score treating all classes equally regardless of frequency
C) Area Under ROC Curve (AUC-ROC) using one-vs-rest approach for multi-class classification
D) Cohen's Kappa coefficient to account for agreement by chance in imbalanced datasets

---

**Q9.** A computer vision team is selecting between two object detection models for autonomous vehicles. Model A: 92% mAP, 8 FPS inference speed, 250MB model size. Model B: 88% mAP, 45 FPS inference speed, 50MB model size. The deployment hardware can process maximum 30 FPS. Which factor should be the PRIMARY decision criterion and which model should be chosen?

A) Model accuracy (mAP) is primary for safety-critical applications; choose Model A despite slower speed since it exceeds the 30 FPS requirement when optimized
B) Inference speed is primary to ensure real-time detection; choose Model B as it provides 45 FPS headroom for processing overhead and edge cases
C) Model size is primary for edge deployment constraints; choose Model B as 50MB allows for faster loading and updates
D) The accuracy-speed tradeoff should be balanced using a composite metric; calculate (mAP × FPS) to get scores of 736 (Model A) and 3,960 (Model B), choose Model B

---

**Q10.** A healthcare startup is building a diagnostic assistant that must explain its reasoning to physicians for regulatory compliance. The model needs to process patient symptoms (text), lab results (numerical data), and medical images simultaneously. During testing, the team notices the model sometimes generates medically implausible recommendations when certain symptom combinations appear. Which combination of AI characteristics is MOST critical to address for this use case?

A) High accuracy and low latency to ensure fast diagnosis delivery
B) Explainability and robustness to handle edge cases and provide transparent reasoning
C) Scalability and cost-efficiency to support multiple concurrent users
D) Data efficiency and transfer learning to minimize training data requirements

---

**Q11.** An ML engineer is comparing supervised learning approaches for a fraud detection system. The dataset contains 1 million transactions with only 0.5% labeled as fraudulent. The business requires detecting 95% of fraud cases (high recall) while minimizing false positives that anger legitimate customers. Which challenge type and mitigation strategy combination is MOST appropriate?

A) Overfitting problem — apply L1/L2 regularization and cross-validation
B) Class imbalance problem — use SMOTE oversampling or weighted loss functions with precision-recall optimization
C) Underfitting problem — increase model complexity and add more features
D) Concept drift problem — implement online learning with sliding time windows

---

**Q12.** A financial services company needs to predict customer loan default risk. Regulators require the ability to audit individual predictions and understand which factors (income, credit history, employment) contributed to each decision. The model will process 50,000 applications daily. Which model selection provides the BEST balance of interpretability and performance for this regulated environment?

A) Deep neural network with SHAP values for post-hoc explanations
B) Gradient boosted trees (XGBoost) with feature importance analysis
C) Linear regression with regularization and coefficient analysis
D) Random forest with permutation feature importance

---

**Q13.** A research team is training a computer vision model to classify rare diseases from medical scans. They have 500 labeled examples per disease class and 50,000 general medical images without labels. Training from scratch achieves only 60% accuracy. Which learning paradigm would MOST effectively improve performance given the limited labeled data?

A) Unsupervised learning using k-means clustering on the 50,000 unlabeled images
B) Transfer learning using a model pre-trained on ImageNet, then fine-tuning on the 500 labeled examples per class
C) Semi-supervised learning combining the labeled and unlabeled data with pseudo-labeling
D) Reinforcement learning with reward signals based on classification accuracy

---

**Q14.** An ML pipeline for real-time product recommendations experiences significant performance degradation after 6 months in production. The model was trained on 2023 data, and monitoring shows input feature distributions have shifted substantially from training distributions. The business reports recommendations feel 'stale' and click-through rates dropped 40%. Which type of model performance issue is occurring, and what is the PRIMARY root cause?

A) Model decay due to concept drift — the relationship between features and user preferences has changed over time
B) Data quality degradation due to upstream ETL pipeline failures corrupting input features
C) Overfitting to training data causing poor generalization to new user behaviors
D) Infrastructure bottleneck causing increased latency and timeout errors in the recommendation service

---

**Q15.** A startup is building a sentiment analysis model for customer reviews. They have 10,000 reviews labeled as positive/negative by their team. During evaluation, the model achieves 92% accuracy but consistently misclassifies sarcastic reviews (e.g., 'Oh great, another broken product' labeled as positive). The business considers sarcasm detection critical. What is the MOST appropriate evaluation strategy to identify and measure this specific model weakness?

A) Calculate precision and recall separately for positive and negative classes to identify class-specific performance issues
B) Create a dedicated test set of sarcastic reviews and measure accuracy on this slice separately from overall accuracy
C) Increase the training dataset size to 50,000 reviews to give the model more sarcasm examples
D) Use cross-validation with 10 folds to get more reliable accuracy estimates across different data splits

---

**Q16.** A healthcare research team is analyzing patient symptom descriptions to identify potential disease patterns. They have 50,000 unlabeled text records and want the AI system to discover natural groupings of symptoms without predefined categories. The team needs to understand which symptoms frequently co-occur. Which ML approach is MOST appropriate for this requirement?

A) Supervised learning with a pre-labeled dataset of known diseases to train a classification model
B) Unsupervised learning using clustering algorithms to identify natural groupings in the symptom data
C) Reinforcement learning with reward signals based on diagnostic accuracy
D) Semi-supervised learning with 5% labeled data and 95% unlabeled data

---

**Q17.** A financial services company is deploying an AI model to detect fraudulent transactions. During testing, they discover the model has 98% accuracy overall, but only catches 45% of actual fraud cases (which represent 2% of all transactions). The business requires catching at least 85% of fraud cases, even if it means more false alarms. Which metric should the team prioritize optimizing, and what is the MOST likely underlying issue?

A) Optimize precision; the model has high class imbalance and needs synthetic minority oversampling (SMOTE)
B) Optimize F1-score; the model needs balanced precision and recall through adjusted decision thresholds
C) Optimize recall; the model suffers from class imbalance and needs techniques like adjusted class weights or threshold tuning
D) Optimize accuracy; the model needs more training data from the majority class

---

**Q18.** An agricultural company is building a computer vision system to identify plant diseases from leaf images. They plan to use transfer learning with a foundation model pre-trained on ImageNet. The model will be fine-tuned on 5,000 labeled images of diseased and healthy plants across 20 disease types. Which statement BEST describes the primary advantage of transfer learning in this scenario compared to training from scratch?

A) Transfer learning eliminates the need for labeled training data by using zero-shot learning capabilities
B) Transfer learning leverages low-level feature representations learned from millions of images, requiring less domain-specific training data and compute resources
C) Transfer learning provides better interpretability by maintaining the original model architecture without modifications
D) Transfer learning automatically handles class imbalance by adjusting weights based on the pre-training dataset distribution

---

**Q19.** A financial services company is building a chatbot that must provide accurate regulatory compliance information. During testing, the model occasionally generates plausible-sounding but factually incorrect regulatory citations. The team has already implemented prompt engineering with specific instructions to only cite verified sources. Which combination of techniques would BEST address this hallucination issue while maintaining response quality?

A) Increase the temperature parameter to 0.9 and implement a secondary LLM to verify all citations
B) Implement Retrieval Augmented Generation (RAG) with a verified regulatory database and reduce temperature to 0.2
C) Fine-tune the model on a dataset of regulatory documents and increase the max_tokens parameter
D) Use a larger foundation model with more parameters and implement chain-of-thought prompting

---

**Q20.** A media company needs to generate unique product descriptions for 500,000 items daily. Current costs using a foundation model API are $12,000/month. The descriptions follow predictable patterns but must maintain brand voice and avoid repetition. Which approach would MOST cost-effectively meet these requirements?

A) Switch to a smaller open-source model, fine-tune it on brand examples, and host on company infrastructure
B) Implement aggressive prompt caching and reduce temperature to minimize token usage
C) Use batch processing APIs with lower priority pricing and implement response caching for similar products
D) Create template-based generation with rule-based systems and only use the LLM for creative variations

---

**Q21.** An AI system generates medical appointment summaries from doctor-patient conversations. During auditing, the team discovers the model occasionally includes demographic assumptions not present in the conversation (e.g., assuming a patient's occupation based on their name). Which technique specifically addresses this bias manifestation?

A) Implement differential privacy techniques to anonymize training data
B) Use Constitutional AI with explicit rules prohibiting unsupported inferences about protected characteristics
C) Increase model diversity by using ensemble methods with multiple foundation models
D) Apply reinforcement learning from human feedback (RLHF) with general preference data

---

**Q22.** A research team is evaluating embeddings for a semantic search system across legal documents. They compare two models: Model A (384 dimensions, trained on general web data) and Model B (1024 dimensions, trained on legal corpus). Model A shows 72% retrieval accuracy while Model B shows 89% accuracy, but Model B's inference time is 4x slower. The system must handle 10,000 queries/hour with sub-200ms latency. What is the BEST optimization strategy?

A) Use Model B with dimensionality reduction via PCA to 384 dimensions after embedding generation
B) Implement Model B with approximate nearest neighbor search (ANN) using HNSW indexing
C) Use Model A with query expansion techniques and re-ranking using Model B on top-100 results
D) Fine-tune Model A on legal documents to improve accuracy while maintaining speed

---

**Q23.** A company's generative AI application produces training materials. A user inputs: 'Create a Python tutorial using examples from the book Clean Code.' The model generates content that closely paraphrases passages from the copyrighted book. Which statement BEST describes the liability and mitigation approach?

A) The company is not liable because the user explicitly requested copyrighted content in their prompt
B) The company is potentially liable for copyright infringement and should implement output filtering against known copyrighted works
C) This is fair use because the content is being used for educational purposes in training materials
D) The foundation model provider is liable since their training data caused the copyright issue

---

**Q24.** A generative AI system for customer service must handle sensitive PII (personally identifiable information). The architecture team is debating data handling strategies. The system receives customer queries containing names, addresses, and account numbers, then generates personalized responses. Which approach BEST balances functionality and privacy?

A) Encrypt all PII before sending to the model API and decrypt the responses
B) Use named entity recognition (NER) to detect and replace PII with tokens before model processing, then substitute back in responses
C) Fine-tune a model on customer data so it understands context, then deploy it in a private VPC
D) Implement access controls and audit logging for all queries containing PII

---

**Q25.** A prompt engineer is optimizing a customer email response system. Current prompt: 'Write a response to this customer email: {email_text}' produces responses that are sometimes too formal and sometimes miss key customer concerns. Which prompt engineering technique would MOST effectively improve consistency and relevance?

A) Few-shot prompting with 3-5 examples of email/response pairs demonstrating desired tone and completeness
B) Add 'Be professional and address all customer concerns' to the instruction
C) Implement chain-of-thought by adding 'Think step-by-step about what the customer needs'
D) Increase temperature to 0.8 to generate more varied responses and select the best one

---

**Q26.** An e-commerce company uses a foundation model to generate product descriptions. They notice the model occasionally outputs descriptions in languages other than English, despite English-only prompts and product data. Which phenomenon BEST explains this behavior and how should it be addressed?

A) This is mode collapse; address by using a different random seed for each generation
B) This is multilingual bleed from training data; address by adding explicit 'Respond only in English' instruction and setting a language detection filter
C) This is overfitting to non-English product data; address by fine-tuning on English-only examples
D) This is a prompt injection attack; address by sanitizing input product data

---

**Q27.** A data science team is selecting a foundation model for a document summarization pipeline that processes 50,000 financial reports monthly. Each report is 15,000-25,000 words. They're comparing models with different context windows: Model X (4K tokens), Model Y (16K tokens), Model Z (128K tokens). Model Z costs 8x more per token than Model X. What is the MOST cost-effective approach while maintaining quality?

A) Use Model X with recursive summarization: chunk document, summarize each chunk, then summarize the summaries
B) Use Model Y for all documents and truncate reports to fit the 16K context window
C) Use Model Z only when document exceeds Model Y's context window, otherwise use Model Y
D) Use Model X with map-reduce approach: summarize chunks in parallel, then use Model Y to combine

---

**Q28.** A generative AI system for code generation is being evaluated for production deployment. During testing with the prompt 'Write a function to validate credit card numbers,' the model outputs code that includes a valid-looking API key in a comment: '# API Key: sk_live_4xKJh... (example only)'. The key format matches a real payment processor's key structure. What is the PRIMARY risk and appropriate mitigation?

A) Memorization of training data; implement output scanning to detect and remove potential secrets before returning to users
B) Prompt injection vulnerability; sanitize user prompts to prevent requests for sensitive data
C) Model hallucination creating realistic but fake credentials; add disclaimer that code examples may be fictional
D) Copyright violation if the code was from a private repository; implement license checking on outputs

---

**Q29.** A healthcare startup is building a symptom checker using a foundation model. During compliance review, legal requires that the system never directly diagnoses conditions, always recommends professional consultation, and avoids generating clinical predictions. The team has tried prompt engineering but the model occasionally violates these constraints. Which additional technique provides the STRONGEST guarantee of compliance?

A) Implement rule-based post-processing that detects and blocks outputs containing diagnosis keywords or medical predictions
B) Use reinforcement learning from human feedback (RLHF) with medical professionals rating outputs for compliance
C) Switch to a medical-specific foundation model that was trained on clinical guidelines
D) Add a confidence threshold where low-confidence responses trigger a fallback 'please consult a doctor' message

---

**Q30.** A financial services company is developing a generative AI application that must produce deterministic outputs for regulatory compliance audits. The same prompt about a customer's account status must generate identical responses across multiple runs. Which temperature setting should be configured?

A) Temperature = 0.7 to balance creativity with consistency
B) Temperature = 0.0 to ensure deterministic outputs
C) Temperature = 1.0 to maximize response diversity
D) Temperature = 0.5 with top_p = 0.9 for controlled randomness

---

**Q31.** A healthcare research team is using a foundation model to analyze medical literature. They notice that when asking about a rare disease treatment, the model sometimes fabricates citations to non-existent medical journals. What is this phenomenon called, and what is the BEST mitigation strategy?

A) Overfitting; increase the training dataset size with more medical journals
B) Bias amplification; implement fairness constraints in the model architecture
C) Hallucination; implement Retrieval Augmented Generation (RAG) with verified medical databases
D) Mode collapse; adjust the learning rate and retrain the foundation model

---

**Q32.** An e-commerce company wants to generate product descriptions using a foundation model. They need to prevent the model from generating descriptions for prohibited items (weapons, hazardous materials) even if users attempt prompt injection attacks. Which combination of safeguards provides the MOST comprehensive protection?

A) Input filtering only, to block prohibited keywords before they reach the model
B) Output filtering combined with guardrails that validate generated content against safety policies
C) Fine-tuning the model on only approved product categories to eliminate knowledge of prohibited items
D) Prompt engineering with system instructions stating the model must refuse prohibited requests

---

**Q33.** A machine learning team is comparing foundation models for a text summarization task. Model A has 70 billion parameters and Model B has 7 billion parameters. Both models achieve similar ROUGE scores on their test dataset. When deployed to production with real-world documents, Model A consistently outperforms Model B. What is the MOST likely explanation?

A) Model A has better generalization capabilities due to emergent properties from scale, handling diverse real-world inputs beyond the test set distribution
B) Model B is overfitting to the test dataset while Model A has better regularization
C) The ROUGE metric is calculated incorrectly and doesn't reflect Model A's superior performance
D) Model A has a higher learning rate during training, resulting in better convergence

---

**Q34.** A legal firm is implementing a generative AI system to draft contract clauses. They use few-shot prompting with 5 example contracts in the prompt. The system works well for standard agreements but fails for complex multi-party contracts. They have a library of 10,000 contracts. What is the MOST cost-effective approach to improve performance on complex contracts?

A) Fine-tune a foundation model on all 10,000 contracts to specialize it for legal drafting
B) Implement RAG to retrieve the 5 most relevant contracts dynamically based on the specific request context
C) Increase few-shot examples to 50 contracts in every prompt to provide more context
D) Switch to a larger foundation model with a 128K token context window to fit more examples

---

**Q35.** A research team is evaluating different foundation model architectures. They observe that transformer-based models require significantly more computational resources during inference compared to training on a per-token basis. What is the PRIMARY reason for this computational characteristic?

A) The self-attention mechanism has O(n²) complexity where n is the sequence length, making longer sequences computationally expensive
B) Inference requires forward passes through all transformer layers while training can use gradient checkpointing to reduce memory
C) Models must load all parameters from storage into memory for each inference request, causing I/O bottlenecks
D) Inference processes one token at a time sequentially, preventing the parallelization benefits available during training

---

**Q36.** A financial services company is developing a generative AI application that must produce consistent risk assessment reports. The reports need to follow a strict format with specific sections and numerical ranges. During testing, the model occasionally generates creative but non-compliant outputs. Which combination of techniques would MOST effectively ensure output consistency while maintaining quality?

A) Increase temperature to 0.9 and use multiple sampling iterations to select the best output
B) Set temperature to 0.2, implement structured output formatting with JSON schema validation, and use few-shot prompting with compliant examples
C) Use maximum token limits and apply post-processing filters to remove non-compliant text
D) Enable top-k sampling with k=50 and increase the frequency penalty parameter

---

**Q37.** A machine learning team is evaluating foundation models for a multilingual customer service chatbot. The application requires understanding context across conversation turns, handling code-switching between languages mid-conversation, and generating responses in 15 different languages. Which model characteristic is MOST critical for this use case?

A) Large context window size of at least 32K tokens
B) High parameter count exceeding 100 billion parameters
C) Training on multilingual datasets with strong cross-lingual transfer capabilities
D) Support for fine-tuning with custom instruction datasets

---

**Q38.** An AI research team observes that their generative model produces high-quality outputs for common scenarios but generates plausible-sounding but factually incorrect information for less common topics. When questioned about obscure historical events, the model confidently provides detailed but inaccurate dates and facts. What fundamental limitation of current generative AI models does this demonstrate?

A) Insufficient model capacity requiring scaling to larger parameter counts
B) Hallucination due to the model's probabilistic nature and training data distribution imbalance
C) Improper prompt engineering lacking explicit instructions for accuracy
D) Outdated training data requiring model retraining on recent information

---

**Q39.** A healthcare AI application uses retrieval-augmented generation (RAG) to answer medical questions by combining a foundation model with a vector database of medical literature. During evaluation, the system sometimes returns correct retrieved documents but the generated answer contradicts the retrieved information. Which component of the RAG architecture is MOST likely responsible for this issue?

A) The embedding model producing semantically inaccurate vector representations
B) The vector database similarity search returning insufficient context
C) The generation model not properly grounding its output in the retrieved context
D) The chunking strategy creating fragments that lose important medical context

---

**Q40.** A company is implementing a content moderation system using a generative AI model to classify user-generated posts into safe/unsafe categories and explain the reasoning. During testing, the model achieves 94% accuracy but shows significantly lower performance (76% accuracy) on posts containing regional slang and cultural references from underrepresented communities. What does this performance disparity MOST likely indicate?

A) The model requires additional fine-tuning with a larger learning rate to improve overall performance
B) Training data bias with insufficient representation of diverse linguistic and cultural patterns
C) The confidence threshold for unsafe classification needs adjustment to reduce false negatives
D) Prompt engineering needs optimization to include more explicit examples of slang terminology

---

**Q41.** A financial services company is building a document processing system that must extract structured data from handwritten loan applications, typed forms, and scanned contracts. The system needs to handle tables, checkboxes, signatures, and custom fields unique to their business. They require 99.5% accuracy on their custom fields and need to process 50,000 documents daily. Which approach BEST meets these requirements?

A) Use Amazon Textract with custom queries for standard fields and Amazon Bedrock with Claude for complex handwritten sections, combining results in a post-processing Lambda function
B) Fine-tune Amazon Textract using their labeled dataset of 10,000 documents, then use Textract Queries API for all custom field extraction
C) Use Amazon Textract for layout analysis and text extraction, then fine-tune an Amazon Bedrock foundation model on their 10,000 labeled documents to extract custom fields from the Textract output
D) Deploy a custom computer vision model on SageMaker trained on their documents, using Amazon Bedrock only for quality validation of extracted data

---

**Q42.** A healthcare research organization needs to generate synthetic patient records for ML model training while maintaining statistical properties of real data distributions (age, diagnosis correlations, treatment outcomes). The synthetic data must pass statistical tests for distribution matching but contain zero actual patient information. They have 500,000 real patient records. Which solution provides the MOST appropriate balance of privacy and data utility?

A) Use Amazon Bedrock to generate synthetic records by providing the foundation model with statistical summaries and distributions from real data, without exposing individual patient records
B) Fine-tune an Amazon Bedrock model on the 500,000 real patient records with differential privacy enabled, then generate synthetic records from the fine-tuned model
C) Use Amazon Comprehend Medical to extract entities from real records, randomize the entities, then use Amazon Bedrock to generate coherent records from the randomized entities
D) Export anonymized patient records to Amazon S3, use Amazon Bedrock to paraphrase and modify each record individually, ensuring no record matches the original

---

**Q43.** An e-commerce company wants to implement a product recommendation system that explains why each product is recommended to increase customer trust. The system must process user browsing history, purchase history, and current session behavior in real-time (under 200ms latency). Which architecture BEST satisfies these requirements?

A) Use Amazon Personalize for real-time recommendations, then send the top 10 results to Amazon Bedrock to generate natural language explanations for each recommendation
B) Fine-tune a small language model on product descriptions and user behavior patterns, deploy it on SageMaker with a real-time endpoint that generates both recommendations and explanations simultaneously
C) Use Amazon Personalize for recommendations and create rule-based explanation templates that reference the metadata used in the recommendation algorithm (e.g., 'customers who bought X also bought Y')
D) Implement a RAG architecture where user behavior is stored in a vector database, use Amazon Bedrock to retrieve similar user patterns and generate both recommendations and explanations based on retrieved patterns

---

**Q44.** A legal firm needs to redact personally identifiable information (PII) from 100,000 legal documents in 15 languages before sharing them with external auditors. The documents contain standard PII (names, addresses) as well as legal-specific entities like case numbers, client IDs, and attorney-client privileged communications. Redaction accuracy must exceed 99.9% as missed PII creates legal liability. Which solution provides the HIGHEST accuracy?

A) Use Amazon Comprehend DetectPiiEntities API for standard PII, then use Amazon Bedrock with a prompt engineered to identify legal-specific entities, combining both outputs for comprehensive redaction
B) Fine-tune an Amazon Bedrock foundation model on 5,000 labeled legal documents showing correct redaction patterns for both standard and legal-specific PII, then use the fine-tuned model for all redaction
C) Use Amazon Comprehend custom entity recognition trained on legal-specific entities combined with the standard DetectPiiEntities API, implementing a multi-pass redaction process with human review of edge cases
D) Use Amazon Textract to extract text, send to Amazon Translate for English normalization, use Amazon Comprehend DetectPiiEntities, then use Amazon Bedrock to verify no PII was missed

---

**Q45.** A manufacturing company wants to implement predictive maintenance by analyzing equipment sensor data (vibration, temperature, pressure) along with maintenance logs, repair manuals, and technician notes. The system should predict failures 48 hours in advance and provide natural language explanations citing specific manual sections. Current data includes 3 years of sensor data (time-series) and 500 maintenance incidents with notes. Which architecture BEST addresses this requirement?

A) Use Amazon Lookout for Equipment to predict failures from sensor data, then use a RAG architecture with Amazon Bedrock where repair manuals are in the knowledge base to generate explanations when failures are predicted
B) Fine-tune Amazon Bedrock on maintenance logs and manuals, then send time-series sensor data directly to the fine-tuned model to predict failures and generate explanations simultaneously
C) Use Amazon Forecast for time-series prediction on sensor data, Amazon Comprehend to analyze maintenance notes for patterns, and Amazon Bedrock to synthesize insights from both into actionable maintenance recommendations
D) Embed sensor data and maintenance logs into Amazon OpenSearch Service vector database, use Amazon Bedrock to query the vector database when anomalies are detected, generating explanations based on similar historical incidents

---

**Q46.** A customer service organization is building an AI assistant that must handle 10,000 concurrent conversations across chat, email, and voice channels. The assistant needs to maintain conversation context, access a knowledge base of 50,000 product documents, and escalate to humans when confidence is low. Average conversation length is 8-12 turns. Which architecture provides the MOST cost-effective solution at scale?

A) Use Amazon Lex for conversation management and slot filling, Amazon Kendra for knowledge base search, and Amazon Bedrock only for final response generation when Lex confidence is high
B) Implement a RAG architecture with Amazon Bedrock as the primary engine, storing conversation history in Amazon DynamoDB, and using Amazon Kendra for document retrieval on each turn
C) Use Amazon Bedrock with Converse API for multi-turn conversations, implement conversation memory using the API's built-in context management, and use Bedrock's knowledge base integration for document retrieval
D) Deploy a fine-tuned model on Amazon SageMaker with conversation state managed in ElastiCache, use Amazon Kendra for document retrieval, and implement custom confidence scoring for escalation logic

---

**Q47.** A pharmaceutical company needs to analyze research papers to identify potential drug-drug interactions not explicitly mentioned in the papers. The system must reason across multiple papers (e.g., Paper A mentions Drug X affects Protein Y; Paper B mentions Drug Z affects Protein Y) to infer potential interactions. They have access to 500,000 papers and need to generate a report of potential new interactions monthly. Which approach is MOST effective?

A) Use Amazon Bedrock to create embeddings of all papers, store in a vector database, then use multi-hop retrieval where each paper retrieval triggers additional searches for related proteins and drugs mentioned
B) Fine-tune an Amazon Bedrock foundation model specifically on drug interaction literature and biological relationship extraction, then use the fine-tuned model to analyze papers and generate interaction hypotheses
C) Create a knowledge graph in Amazon Neptune from extracted entities (drugs, proteins, pathways) using Amazon Comprehend Medical, then use Amazon Bedrock to query the graph structure and reason about multi-hop relationships
D) Use Amazon Bedrock with extended context window to analyze batches of 50-100 papers simultaneously, prompting it to identify cross-paper interaction patterns and generate interaction reports

---

**Q48.** A media company needs to automatically generate video content descriptions for accessibility compliance across 20,000 archived videos (2-hour average length). Descriptions must include scene changes, on-screen text, speaker identification, and emotional context. The project has a 6-month deadline. Which solution is MOST efficient?

A) Use Amazon Rekognition Video for scene detection and label detection, Amazon Transcribe for speech-to-text with speaker diarization, Amazon Textract for on-screen text, then use Amazon Bedrock to synthesize all outputs into coherent natural language descriptions
B) Send video frames at 1-second intervals to Amazon Bedrock multimodal model (Claude or similar) with prompts asking for scene description, combine with Amazon Transcribe for audio, then use Bedrock to generate final descriptions
C) Fine-tune a multimodal foundation model on a labeled dataset of 500 videos with gold-standard descriptions, then deploy on SageMaker to process all videos in parallel
D) Use Amazon Rekognition Video for analysis, store results in DynamoDB, create rule-based templates for description generation based on detected labels and scenes, using Amazon Polly to convert text descriptions to audio descriptions

---

**Q49.** A global retailer wants to implement dynamic pricing that adjusts product prices based on demand, competitor pricing, inventory levels, and seasonal trends. The pricing model must explain each price change to category managers in natural language, citing the specific factors that influenced the decision. They have 3 years of historical pricing data, sales data, and competitor pricing. Which architecture BEST supports this requirement?

A) Train a custom reinforcement learning model on Amazon SageMaker for pricing optimization, store decision factors in metadata, then use Amazon Bedrock to generate natural language explanations from the metadata
B) Use Amazon Forecast to predict demand, implement rule-based pricing logic in AWS Lambda based on forecast and business rules, then use Amazon Bedrock to explain the pricing decisions
C) Fine-tune Amazon Bedrock on historical pricing decisions and outcomes, then use the model to directly set prices and generate explanations simultaneously
D) Create a machine learning model on SageMaker to predict optimal prices, use Amazon SageMaker Clarify for model explainability, and convert SHAP values to natural language using Amazon Bedrock

---

**Q50.** A financial institution needs to detect fraudulent loan applications by analyzing both structured data (income, credit score, employment history) and unstructured data (submitted documents, application essays, social media profiles). The system must process 5,000 applications daily and provide fraud probability scores with explanations. Historical data shows 2% fraud rate (1,000 fraudulent cases from 50,000 applications). Which approach provides the BEST fraud detection accuracy?

A) Use Amazon Fraud Detector for structured data analysis, Amazon Textract for document analysis, Amazon Comprehend for text analysis, then use Amazon Bedrock to analyze all outputs and generate a final fraud score with explanation
B) Fine-tune an Amazon Bedrock foundation model on the 1,000 fraudulent cases and 1,000 legitimate cases, then use the model to analyze both structured and unstructured data together, generating fraud scores and explanations
C) Build a gradient boosting model on Amazon SageMaker for structured data fraud detection, use Amazon Comprehend and Amazon Bedrock for unstructured data analysis, then use an ensemble approach combining both model scores with SageMaker Clarify for explanations
D) Use Amazon Bedrock with RAG where similar historical fraud cases are retrieved from a vector database, then prompt the model to compare the current application to retrieved fraud patterns

---

**Q51.** A pharmaceutical research team needs to summarize clinical trial results from 200-page PDF reports, extracting specific outcomes (efficacy rates, adverse events, patient demographics) and generating executive summaries. The summaries must be accurate to avoid regulatory issues. They process 50 reports monthly. Which solution ensures HIGHEST accuracy while minimizing manual review time?

A) Use Amazon Textract to extract text from PDFs, prompt Amazon Bedrock to summarize the entire document and extract key metrics, then have clinical staff review the summaries for accuracy
B) Use Amazon Textract for text extraction, Amazon Comprehend Medical for entity extraction (drugs, outcomes, conditions), create structured extraction templates for key metrics, then use Amazon Bedrock to generate narrative summaries from the structured data with citations to specific page numbers
C) Fine-tune Amazon Bedrock on 100 historical clinical trial reports with expert-created summaries, then use the fine-tuned model to process new reports with automatic extraction and summarization
D) Use Amazon Textract with Queries API to extract specific outcome fields, Amazon Bedrock to validate the extracted values are sensible, then use Bedrock again to generate the executive summary from validated structured data

---

**Q52.** An online education platform wants to generate personalized learning paths for 500,000 students based on their learning style, performance history, goals, and knowledge gaps. The system must create a sequence of recommended courses, estimate time to completion, and explain why each course is recommended. Students update their progress daily. Which architecture is MOST scalable and cost-effective?

A) Use Amazon Personalize to generate course recommendations based on student behavior, store learning paths in DynamoDB, and use Amazon Bedrock in batch mode overnight to generate explanations for the next day's recommendations
B) For each student request, use Amazon Bedrock to analyze their complete learning history and generate a personalized learning path with explanations in real-time
C) Pre-compute learning path templates based on common student profiles using clustering, store in S3, use Amazon Bedrock to customize templates for individual students when they log in
D) Use a graph database in Amazon Neptune to model course prerequisites and knowledge dependencies, use collaborative filtering to identify similar students, then use Amazon Bedrock to generate personalized path narratives based on graph queries

---

**Q53.** A healthcare provider wants to implement a medical diagnosis support system that analyzes patient symptoms, medical history, lab results, and medical imaging to suggest possible diagnoses. The system must cite medical literature supporting each diagnosis and explain the reasoning. Due to liability concerns, the system must NEVER generate diagnoses not supported by retrieved medical evidence. Which architecture provides the STRONGEST safeguards against unsupported medical claims?

A) Fine-tune Amazon Bedrock on medical textbooks and journals, use the fine-tuned model to generate diagnoses with built-in medical knowledge, then use a second Bedrock call to retrieve supporting literature from a vector database
B) Implement a strict RAG architecture where Amazon Bedrock can ONLY generate responses using content retrieved from a verified medical knowledge base in Amazon Kendra, with no diagnosis generation without retrieved evidence
C) Use Amazon Comprehend Medical to extract symptoms and conditions from patient data, match against a curated diagnosis database, then use Amazon Bedrock only to explain the matched diagnoses in natural language
D) Create a hybrid system where Amazon Bedrock generates initial diagnosis hypotheses, Amazon Kendra retrieves supporting evidence, and if sufficient evidence isn't found (confidence threshold), the hypothesis is discarded and not shown to clinicians

---

**Q54.** A financial services company needs to generate synthetic customer transaction data for testing their fraud detection system. The synthetic data must maintain statistical properties of real transactions (amounts, frequencies, merchant categories) while ensuring zero personally identifiable information leakage. The solution must support conditional generation based on customer segments and transaction types. Which approach BEST meets these requirements?

A) Use Amazon Bedrock with Anthropic Claude to generate transaction records by providing examples of real transactions in the prompt, then use Amazon Comprehend PII detection to redact sensitive fields
B) Fine-tune Amazon Titan Text on anonymized historical transactions, then use the custom model with structured prompts specifying segment parameters and statistical constraints to generate synthetic records
C) Use Amazon Bedrock Data Automation to extract patterns from real data, then generate synthetic transactions using Amazon Bedrock with guardrails configured to block PII in outputs
D) Create a RAG solution with Amazon Bedrock Knowledge Bases containing anonymized transaction samples, then query with specific segment criteria to generate similar synthetic records

---

**Q55.** A legal research platform processes thousands of court documents daily. Users need to query across multiple document types (case law, statutes, regulations) and receive answers that cite specific sections with exact legal language. The system must distinguish between binding precedent and persuasive authority, and responses must maintain legal precision without hallucination. Query response time must be under 3 seconds for 95th percentile. Which architecture BEST addresses these requirements?

A) Amazon Bedrock Knowledge Bases with OpenSearch Serverless vector store, using Cohere Embed for embeddings and Anthropic Claude 3 Sonnet for generation with citations enabled and custom metadata filtering for document hierarchy
B) Fine-tune Amazon Titan Text on legal corpus with reinforcement learning from human feedback (RLHF), deploy on SageMaker with real-time endpoint, and implement custom citation extraction post-processing
C) Amazon Kendra with legal document connector, using deep learning ranking, integrated with Amazon Bedrock using Anthropic Claude 3 Opus as the LLM for response generation with inline citations
D) Amazon Bedrock Agents with custom Lambda functions for document retrieval from S3, using AI21 Jurassic-2 for generation with RetrieveAndGenerate API and prompt engineering for citation formatting

---

**Q56.** An e-commerce company wants to generate product descriptions in 12 languages simultaneously while maintaining brand voice consistency and incorporating technical specifications from structured product databases. Descriptions must be optimized for SEO in each language (not direct translations) and include region-specific compliance statements. The solution processes 50,000 products daily with a budget constraint of $0.02 per product. Which implementation strategy is MOST cost-effective while meeting requirements?

A) Use Amazon Bedrock with Anthropic Claude 3.5 Haiku, batching requests with prompt caching enabled, structured prompts containing brand guidelines and product specs, and parallel inference for multiple languages with Amazon Translate for compliance statements
B) Deploy Meta Llama 3.1 70B on SageMaker with multi-GPU instance (ml.p4d.24xlarge), implement batch transform jobs for inference, and use few-shot prompting with brand voice examples and structured product data injection
C) Use Amazon Bedrock batch inference with Anthropic Claude 3 Sonnet, create language-specific prompt templates with embedded brand guidelines, retrieve compliance text from DynamoDB, and process all languages sequentially in single prompts
D) Fine-tune Amazon Titan Text Express separately for each language using brand content corpus, deploy as provisioned throughput, and use concurrent inference with product data passed as JSON in prompts with structured output formatting

---

**Q57.** A healthcare provider needs to extract structured clinical information from unstructured physician notes: diagnoses (ICD-10 codes), medications (with dosages), procedures, and patient risk factors. The solution must achieve >95% accuracy on medical entity extraction, maintain HIPAA compliance with audit trails, and process 10,000 notes per hour during peak times. Extracted data feeds directly into billing and clinical decision support systems. Which solution architecture is MOST appropriate?

A) Amazon Comprehend Medical for entity extraction, store results in Amazon HealthLake with FHIR formatting, use AWS CloudTrail for audit logging, and implement Amazon EventBridge for downstream system integration
B) Amazon Bedrock with Anthropic Claude 3.5 Sonnet using structured output mode with JSON schema, implement prompt engineering with medical ontologies, store in Amazon DynamoDB with encryption, and use AWS Lambda for data validation and system integration
C) Fine-tune Amazon Titan Text on labeled clinical notes dataset, deploy with SageMaker inference with VPC endpoint, use Amazon Textract for initial document processing, and implement custom NLP pipeline with medical terminology validation using Amazon Comprehend Medical as secondary validation
D) Amazon Bedrock Knowledge Bases with medical knowledge corpus, use retrieval-augmented generation with Cohere Command R+ for entity extraction, implement Amazon Bedrock Guardrails for PII protection, and store structured outputs in Amazon Aurora with encryption

---

**Q58.** A customer service platform handles 500,000 support conversations monthly across chat, email, and phone transcripts. The system must automatically classify conversations into 200+ granular categories, detect customer sentiment shifts within conversations, identify upsell opportunities, and generate summary reports for quality assurance. Classification accuracy must exceed 92% and processing must complete within 30 minutes of conversation end. Which solution provides the BEST balance of accuracy, cost, and operational simplicity?

A) Amazon Bedrock with Anthropic Claude 3.5 Sonnet using multi-task prompting, process conversations via Step Functions workflow with parallel branches for classification, sentiment analysis, and opportunity detection, aggregate results in Amazon S3 and generate reports using Amazon QuickSight
B) Fine-tune Amazon Titan Text on historical labeled conversations for classification, use Amazon Comprehend for sentiment analysis, deploy separate SageMaker models for opportunity detection, and orchestrate via AWS Lambda with results stored in Amazon RDS
C) Use Amazon Bedrock batch inference with Meta Llama 3.1 405B for comprehensive analysis in single prompt, Amazon SQS for queue management, process results with AWS Glue for aggregation, and store summaries in Amazon DynamoDB with scheduled QuickSight refreshes
D) Amazon Lex for intent classification, Amazon Comprehend for sentiment with sentiment modifier analysis, Amazon Personalize for opportunity detection, and implement Amazon Bedrock Agents to orchestrate analysis and report generation with results in Amazon Timestream

---

**Q59.** A media company needs to generate personalized video content descriptions for their streaming platform. Each video has existing metadata (genre, cast, themes) but requires descriptions tailored to user segments (families, thriller enthusiasts, documentary fans, etc.). The system must generate 50 different segment-specific descriptions per video for 10,000 videos weekly, maintain consistent quality and brand voice, and support A/B testing different description styles. Cost per video must not exceed $0.50. Which approach BEST meets these requirements?

A) Use Amazon Bedrock with Anthropic Claude 3.5 Haiku, implement prompt templates with segment personas and video metadata injection, enable prompt caching for brand guidelines and repeated metadata, and use Amazon Bedrock model evaluation for quality validation with A/B testing via CloudWatch Evidently
B) Fine-tune Amazon Titan Text on segment-specific description datasets, deploy with provisioned throughput for consistent latency, generate all 50 variations via parallel Lambda invocations, and implement custom A/B testing framework using Amazon DynamoDB and API Gateway
C) Deploy Meta Llama 3.1 8B on SageMaker Serverless Inference, create segment-specific prompt templates, use SageMaker Pipelines for batch processing, and implement MLflow for experiment tracking and A/B test management with results in Amazon S3
D) Use Amazon Bedrock Knowledge Bases with existing video descriptions as corpus, implement retrieval-augmented generation with Cohere Command R for style matching, generate variations via Amazon Bedrock Agents with segment-specific instructions, and use Amazon Personalize for A/B test optimization

---

**Q60.** A financial services company is building a system to analyze earnings call transcripts and generate investment recommendations. The system must: (1) extract sentiment from CEO statements, (2) identify mentions of specific financial metrics with their context, (3) generate a 2-page summary with risk factors highlighted, and (4) compare current quarter metrics to previous quarters. The company requires explainability for regulatory compliance. Which approach BEST meets these requirements?

A) Use Amazon Bedrock with Claude for multi-step reasoning: first extract entities and sentiment, then use those outputs as context in a second prompt for summary generation with chain-of-thought reasoning enabled, storing intermediate outputs for audit trails
B) Fine-tune a custom LLM on historical earnings transcripts and investment reports, then deploy it on Amazon SageMaker with a single end-to-end prompt that handles all four requirements simultaneously
C) Use Amazon Comprehend for sentiment and entity extraction, then pass results to Amazon Bedrock's Titan Text for summary generation, using separate API calls for each quarter comparison
D) Implement retrieval-augmented generation (RAG) with Amazon Kendra indexing past transcripts, then use Amazon Bedrock's Jurassic model to generate recommendations based solely on retrieved similar documents

---

**Q61.** A healthcare provider needs to generate patient education materials in 12 languages from clinical notes. The materials must: preserve medical accuracy, adapt reading level to patient's health literacy score (grades 3-12), remove any Protected Health Information (PHI), and maintain consistent terminology across languages. Average clinical note is 2,000 words; target output is 400 words per language. Which solution provides the MOST reliable approach?

A) Use Amazon Comprehend Medical to detect and redact PHI, then use Amazon Bedrock's Claude with custom prompts per language that specify reading level and medical terminology constraints, implementing a validation step that checks for terminology consistency across translations
B) Use Amazon Translate for multi-language conversion, then apply Amazon Bedrock's Titan Embeddings to verify semantic similarity across languages, using Amazon Comprehend Medical for PHI detection as a final step
C) Fine-tune a multilingual LLM on parallel medical corpora, then use a single prompt template with language and reading level parameters, relying on the model's training to handle PHI redaction implicitly
D) Use Amazon Bedrock's Claude to first simplify and redact the clinical note in English, then use Amazon Translate for each target language, applying reading level adjustments in a post-processing step with language-specific rules

---

**Q62.** An e-commerce company uses Amazon Bedrock to generate product descriptions. After deployment, they notice the model occasionally generates descriptions that include competitor brand names or make unsubstantiated claims about product benefits. Which combination of safeguards would MOST effectively prevent these issues while maintaining description quality?

A) Implement Guardrails for Amazon Bedrock with a denied topics filter for competitor brands and a custom regex pattern to detect unsubstantiated superlatives, combined with a fact-checking step that validates claims against product specification database before publishing
B) Use prompt engineering with few-shot examples of acceptable descriptions and explicit instructions to avoid competitor mentions, then implement a keyword-based post-processing filter that removes flagged terms
C) Enable Amazon Bedrock's built-in content moderation with high sensitivity settings and implement a human-in-the-loop review for all generated descriptions before publishing
D) Fine-tune the foundation model on a curated dataset of approved descriptions with competitor names removed, then use temperature=0 to ensure deterministic outputs

---

**Q63.** A legal firm is building a contract analysis system using RAG with Amazon Bedrock. Contracts are 50-200 pages with complex cross-references. Initial tests show the system sometimes contradicts itself when answering questions about clauses that reference other sections. The vector database returns the most semantically similar chunks, but these chunks lack context from referenced sections. What is the MOST effective way to improve answer consistency?

A) Implement hierarchical chunking where each chunk includes its parent section header and maintains metadata about cross-references, then use a multi-hop retrieval strategy that fetches referenced sections when initial chunks contain cross-reference indicators
B) Increase the chunk overlap from 10% to 50% to ensure cross-referenced content appears in multiple chunks, then retrieve top-10 chunks instead of top-3 to increase context coverage
C) Use Amazon Bedrock's Claude with an extended context window (100K tokens) and pass entire contracts rather than using RAG, implementing caching to manage API costs for repeated queries
D) Implement a reranking step using Amazon SageMaker that scores retrieved chunks based on cross-reference density, prioritizing chunks with fewer internal references for simpler answers

---

**Q64.** A research organization is using Amazon Bedrock to analyze scientific papers and generate literature reviews. They need to cite specific papers in generated text and ensure citations are accurate. When using RAG with a vector store of 50,000 papers, the system sometimes generates plausible-sounding but non-existent citations or attributes findings to wrong papers. Which approach would MOST effectively ensure citation accuracy?

A) Implement a two-stage process: use RAG to retrieve relevant papers and pass their metadata to the LLM with instructions to only cite provided sources, then implement a post-generation validation step that verifies each citation exists in the retrieved document set and the attributed claim appears in the cited paper
B) Store full paper text in the vector database rather than embeddings, then use exact string matching to verify that generated citations appear verbatim in the source documents
C) Use Amazon Bedrock's Titan Embeddings with a higher similarity threshold (0.9 instead of 0.7) to ensure only the most relevant papers are retrieved, reducing the chance of citation errors
D) Fine-tune the foundation model on a dataset of correctly formatted scientific papers with citations, then use prompt engineering to encourage the model to only use its fine-tuning knowledge for citations

---

**Q65.** A media company is building a content moderation system for user-generated videos using Amazon Bedrock. The system must: analyze video thumbnails for inappropriate imagery, transcribe audio for harmful speech, and evaluate overall context to distinguish artistic content from violations. Videos average 5 minutes, and the system must process 10,000 videos/day with decisions available within 10 minutes of upload. Moderation accuracy is critical to avoid incorrectly flagging artistic content. Which architecture provides the MOST cost-effective solution while meeting requirements?

A) Use Amazon Rekognition for thumbnail analysis, Amazon Transcribe for audio-to-text, then send combined results to Amazon Bedrock's Claude with a detailed moderation prompt that includes context evaluation guidelines, processing videos in parallel using AWS Step Functions with Express Workflows
B) Use Amazon Bedrock's multimodal capabilities to analyze video frames directly by sampling 1 frame per second, then use the same model to transcribe and evaluate audio, processing everything in a single API call per video
C) Use Amazon Rekognition Content Moderation for both thumbnails and video frames, Amazon Comprehend for transcribed text toxicity detection, then only send flagged content to Amazon Bedrock for context evaluation to reduce LLM usage costs
D) Deploy a fine-tuned multimodal model on Amazon SageMaker that handles all three tasks (image analysis, speech recognition, context evaluation) in a single inference, using GPU instances with batch processing to meet throughput requirements

---

**Q66.** A financial services company is building a system to analyze quarterly earnings call transcripts and extract key financial metrics, sentiment about future outlook, and comparison to analyst expectations. The system must handle transcripts of varying lengths (5,000-50,000 tokens), maintain context across the entire document, and provide structured JSON output with specific fields. The solution must minimize latency for real-time analysis during live calls. Which approach BEST meets these requirements?

A) Use Amazon Bedrock with Claude 3.5 Sonnet, implement prompt caching for repeated system instructions and company context, structure the prompt to return JSON with required fields, and leverage the 200K token context window to process full transcripts in a single API call
B) Use Amazon Bedrock with Titan Text Premier, split long transcripts into chunks using a sliding window approach with overlap, aggregate results from multiple API calls, and use a final summarization step to combine outputs into the required JSON structure
C) Use Amazon SageMaker to deploy a fine-tuned Llama 3.1 405B model on ml.p5.48xlarge instances with streaming inference enabled, implement custom tokenization to handle long documents, and create a specialized output parser for JSON formatting
D) Use Amazon Bedrock with Claude 3 Haiku for speed, implement a map-reduce pattern where each transcript section is processed independently, use Amazon Bedrock Agents to orchestrate the workflow, and merge results using a deterministic rule-based system

---

**Q67.** A financial services company is deploying an AI system to assess loan applications. During model validation, the team discovers that while overall accuracy is 94%, the approval rate for applicants from historically marginalized communities is 23% lower than other groups with similar credit profiles. The AI Safety team recommends either retraining with balanced data or implementing post-processing adjustments to equalize approval rates. The business team argues this will reduce profitability. Which action BEST aligns with AWS responsible AI guidelines?

A) Deploy the current model but add a disclaimer that AI decisions may vary across demographic groups, ensuring transparency
B) Implement demographic parity constraints during retraining to equalize approval rates across groups, even if overall accuracy decreases slightly
C) Use the current model but route applications from affected communities to human reviewers for final decisions
D) Retrain the model after removing all demographic features from the training data to ensure fairness

---

**Q68.** A healthcare AI startup is building a diagnostic assistant using Amazon Bedrock. The model will suggest potential diagnoses based on patient symptoms. During testing, a physician notices the model occasionally hallucinates rare disease names that don't exist and sometimes contradicts itself when asked to explain reasoning. The team plans to add a confidence score to outputs. Regulatory approval requires demonstrating model reliability. Which combination of actions BEST addresses responsible AI requirements for this use case? (Choose TWO)

A) Implement Retrieval-Augmented Generation (RAG) with a verified medical knowledge base to ground responses in factual sources
B) Add confidence scores and deploy with a threshold that filters out responses below 85% confidence
C) Include a prominent human-in-the-loop requirement where physicians must verify all AI suggestions before acting
D) Fine-tune the model on a larger dataset of medical cases to reduce hallucinations

---

**Q69.** An e-commerce company uses Amazon Personalize to recommend products. A data scientist discovers that the recommendation model creates a feedback loop: it recommends popular items, which get more clicks, which makes them more popular, while niche products rarely appear. The business is satisfied because conversion rates are high. Three months later, the catalog diversity has decreased by 40% as vendors of niche products leave the platform. Which responsible AI principle was violated, and what should have been implemented?

A) Fairness was violated; implement equal exposure guarantees for all products regardless of popularity
B) Transparency was violated; provide explanations for why certain products are recommended more frequently
C) Governance was violated; implement ongoing monitoring of catalog diversity metrics and intervention thresholds
D) Robustness was violated; use exploration strategies in the recommendation algorithm to prevent filter bubble formation

---

**Q70.** A global retailer is implementing an AI-powered dynamic pricing system using Amazon SageMaker. The model adjusts prices based on demand, inventory, competitor pricing, and customer browsing behavior. During a regulatory audit, the team is asked to explain why Customer A was charged $149 for a product while Customer B was charged $127 for the same item at the same time. The data science team cannot provide a clear explanation because the model uses a complex ensemble of neural networks. Which responsible AI requirement is at risk, and what is the appropriate remediation?

A) Explainability; switch to an inherently interpretable model like linear regression or decision trees that can be fully explained
B) Transparency; implement SageMaker Clarify to generate post-hoc explanations of individual pricing decisions and maintain explanation logs
C) Fairness; ensure pricing variations don't correlate with protected attributes like location or demographic factors
D) Accountability; document the model architecture and training process so that the business can defend the pricing strategy

---

**Q71.** A social media company uses Amazon Rekognition to detect and remove harmful content. The AI system flags content for review, which is then evaluated by human moderators. An internal audit reveals that the AI system has a 12% false positive rate for content from users in Southeast Asian countries (incorrectly flagging benign content as harmful) compared to 3% for users in North America, due to underrepresentation of Southeast Asian cultural contexts in training data. Affected users experience account restrictions. The company has limited resources to retrain the model immediately. Which approach BEST demonstrates responsible AI while addressing the immediate harm?

A) Adjust the decision threshold for Southeast Asian users to reduce false positives, even if this slightly increases false negatives for that region
B) Accelerate human moderator review for flagged content from Southeast Asian users and provide cultural context training to moderators
C) Pause automated content moderation for Southeast Asian users until the model can be retrained with representative data
D) Implement a user appeal process where affected users can contest automated decisions and have their content manually reviewed

---

**Q72.** A pharmaceutical company is developing an AI system using Amazon Bedrock to accelerate drug discovery by predicting molecular interactions. The model will identify promising compounds for further laboratory testing. During deployment planning, the AI ethics board raises concerns about how to handle situations where the model's predictions might be influenced by biases in historical research data (certain disease categories or patient populations were historically underrepresented in clinical trials). The model will be used by research scientists, not directly by patients. Which responsible AI consideration is MOST critical for this use case?

A) Implement rigorous model cards documenting known limitations, historical data biases, and appropriate use cases for the research team
B) Require diverse representation in the training data by oversampling underrepresented disease categories and populations
C) Establish a human-in-the-loop process where senior scientists review all AI-generated compound predictions before laboratory testing
D) Deploy the model only for well-researched disease categories where historical data is robust and representative

---

**Q73.** A healthcare company is deploying a Amazon Bedrock application that processes patient diagnostic data. The company must ensure that all prompt inputs and model outputs containing Protected Health Information (PHI) are encrypted at rest and in transit, with the company maintaining full control over encryption keys. The solution must support automatic key rotation every 90 days and provide detailed audit logs of all key usage. Which approach BEST meets these requirements?

A) Enable AWS KMS encryption for Amazon Bedrock with AWS managed keys and use CloudTrail to log key usage events
B) Create a customer managed KMS key with automatic rotation enabled, configure Amazon Bedrock to use this key, and enable AWS KMS key usage logging in CloudTrail
C) Use AWS Certificate Manager (ACM) to generate certificates for TLS encryption and store them in AWS Secrets Manager with automatic rotation
D) Enable S3 bucket encryption with SSE-S3 for storing model outputs and use Amazon Bedrock's default encryption for in-transit data

---

**Q74.** A financial services company uses Amazon SageMaker to deploy credit risk assessment models. Regulatory auditors require proof that model predictions have not drifted beyond acceptable thresholds and that all prediction requests are traceable to specific data inputs. The company has deployed 15 models across multiple AWS accounts. Which combination of services provides the MOST operationally efficient solution? (Choose TWO)

A) Configure SageMaker Model Monitor with DataCaptureConfig to automatically detect model drift and store baseline statistics in S3
B) Implement AWS Config rules to track SageMaker endpoint configuration changes and send alerts to SNS
C) Use Amazon SageMaker Clarify to generate bias reports and store them in a centralized S3 bucket with versioning enabled
D) Enable AWS CloudTrail data events for all SageMaker endpoints and use Amazon Athena to query prediction request/response logs

---

**Q75.** A company is building a RAG-based chatbot using Amazon Bedrock and Amazon Kendra. The system will access confidential documents stored in S3 across multiple departments (Finance, Legal, HR). Each department has strict requirements that users can only access documents and receive AI-generated responses based on documents they are authorized to view. The company needs to prevent prompt injection attacks where users might try to bypass access controls through crafted prompts. Which solution provides the MOST secure implementation?

A) Implement S3 bucket policies for each department, use AWS IAM Identity Center for user authentication, configure Bedrock Guardrails to filter unauthorized content, and enable Kendra user context filtering with token-based authorization
B) Create separate Kendra indexes for each department with VPC endpoints, use Amazon Cognito for authentication, implement prompt validation using AWS Lambda, and configure Bedrock with department-specific IAM roles
C) Use S3 Access Points with delegation to IAM roles per department, configure Kendra with access control lists (ACLs) mapped to user groups, enable Bedrock Agents with action groups that validate user permissions before retrieval, and implement AWS WAF rules to block prompt injection patterns
D) Deploy separate Bedrock endpoints per department, use SageMaker with custom authorization logic, implement document-level encryption with separate KMS keys per department, and use API Gateway with Lambda authorizers

---

**Q76.** A global media company is using Amazon Transcribe to convert customer support calls to text, then using Amazon Comprehend to analyze sentiment. The company operates in the EU and must comply with GDPR, requiring that all personal data is processed only within EU regions and that customers can request complete deletion of their data within 30 days. Call recordings are stored in S3 for up to 7 years for regulatory compliance, but transcripts containing PII must be deletable. Which architecture BEST satisfies these requirements?

A) Store call recordings in S3 Standard in eu-west-1 with Object Lock enabled for 7 years, use Transcribe with PII redaction enabled, store redacted transcripts in a separate S3 bucket with lifecycle policies, and implement a Lambda function to handle deletion requests by removing objects with specific customer tags
B) Use S3 in eu-central-1 with replication to eu-west-1, enable Amazon Macie to detect and tag PII in transcripts, store original recordings with S3 Glacier vault lock, maintain a DynamoDB table mapping customer IDs to transcript S3 keys, and use Step Functions to orchestrate deletion of transcripts while preserving locked recordings
C) Deploy all services in eu-west-1, use Transcribe with vocabulary filtering to mask PII, implement S3 Object Lock compliance mode on recordings, store transcripts in a separate bucket without Object Lock, create an Amazon Athena table with customer ID partitions for efficient deletion, and use S3 Batch Operations for deletion processing
D) Enable S3 Cross-Region Replication to multiple EU regions for high availability, use Transcribe Custom Vocabulary to identify PII, encrypt all data with KMS keys that can be deleted to render data unrecoverable, and maintain deletion requests in Amazon SQS with Dead Letter Queue for retry logic

---

**Q77.** A pharmaceutical company is fine-tuning a foundation model using Amazon Bedrock for drug discovery research. The training data contains proprietary molecular structures and clinical trial results worth billions of dollars. The company's security team requires that the fine-tuned model weights never leave the company's control, all training jobs must be traceable to specific data scientists with non-repudiation, and any attempt to export model artifacts must be blocked and immediately investigated. Which combination of controls BEST meets these requirements?

A) Use Amazon Bedrock custom model import with models stored in a private S3 bucket, enable S3 Block Public Access, configure VPC endpoints for Bedrock, implement IAM policies with explicit deny on bedrock:GetCustomModel for users outside the security team, enable CloudTrail with S3 data events and EventBridge rules to trigger SNS alerts on export attempts, and require MFA for all Bedrock API calls
B) Deploy Bedrock in a VPC with no internet gateway, use AWS PrivateLink for all API access, store fine-tuned models in S3 with bucket policies that deny all access except from specific VPC endpoints, implement SCP policies at the organization level to prevent bedrock:CreateModelCopyJob, require all API calls to be signed with AWS SigV4 with user identity logging, enable CloudTrail Insights for anomaly detection, and use S3 Object Lock in governance mode on model artifacts
C) Configure Bedrock with AWS KMS customer managed keys for model encryption, create service control policies (SCPs) that deny bedrock:ExportModel and s3:GetObject on model buckets from all accounts except a designated security account, implement AWS CloudHSM for key storage, enable AWS Config rules to detect configuration changes, require all training jobs to use temporary credentials from AWS STS with session tags identifying the data scientist, enable VPC Flow Logs and GuardDuty for network monitoring
D) Use Amazon Bedrock with custom models encrypted using AWS KMS, implement IAM permission boundaries on all data scientist roles that explicitly deny export operations, enable AWS Organizations service control policies to prevent cross-account model sharing, configure S3 bucket policies with aws:PrincipalOrgID conditions, require all Bedrock API calls to include request signing with IAM role session names containing employee IDs, enable CloudTrail log file integrity validation and send logs to a separate security account with write-once S3 bucket

---

**Q78.** An insurance company uses Amazon Textract to extract data from claim forms, then Amazon Comprehend Medical to identify medical conditions. A recent audit revealed that some processed documents contained incorrect PII redaction, and there's no reliable way to trace which human reviewers approved specific ML predictions before data entered downstream systems. The company needs to implement a governance framework that ensures all ML predictions above 85% confidence are automatically approved, predictions between 60-85% are sent for human review with full audit trails, and predictions below 60% are rejected. Which solution provides the MOST comprehensive governance and auditability?

A) Implement Amazon Augmented AI (A2I) with custom task templates, configure prediction confidence thresholds in the A2I workflow definition, integrate with Amazon Cognito for human reviewer authentication, store all human review decisions in DynamoDB with reviewer identity and timestamp, enable CloudTrail for A2I API calls, and use S3 versioning on processed documents
B) Use Step Functions to orchestrate the workflow with conditional branching based on confidence scores, implement a custom web interface with Amazon API Gateway and Lambda for human review, store review decisions in Amazon RDS with foreign key constraints to user tables, enable database audit logging, use Amazon SNS to notify reviewers, and implement AWS WAF on the API Gateway
C) Create an Amazon SageMaker Ground Truth labeling job for human review tasks, configure conditional workflows in SageMaker Processing jobs, use IAM roles to identify reviewers, store all decisions in S3 with object metadata, enable S3 access logging and CloudTrail data events, implement Amazon EventBridge rules to route documents based on confidence scores
D) Deploy a custom application on Amazon ECS with Application Load Balancer, implement confidence-based routing in application code, use Amazon Cognito User Pools for reviewer authentication with MFA, store audit logs in Amazon CloudWatch Logs with retention policies, enable AWS Config to track ECS task definitions, and use Amazon SNS for review notifications

---

