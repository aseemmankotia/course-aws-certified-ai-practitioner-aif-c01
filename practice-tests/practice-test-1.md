# Practice Test 1: AWS AI Practitioner (AIF-C01): First-Attempt Certification

- **Questions:** 78
- **Time limit:** 90 minutes
- **Passing score:** 70%%

> Answers are in `answer-key-1.md`. Track results in `score-tracker.md`.

---

**Q1.** A healthcare company needs to analyze patient X-ray images to detect potential fractures. The system must learn from thousands of labeled X-ray images showing fractured and non-fractured bones, and then classify new images accordingly. Which type of machine learning approach is MOST appropriate for this requirement?

A) Unsupervised learning with clustering algorithms
B) Supervised learning with classification algorithms
C) Reinforcement learning with reward-based training
D) Generative AI with foundation models

---

**Q2.** A retail company wants to group customers into segments based on purchasing behavior without predefined categories. They have transaction history data but no labeled customer segments. Which ML approach should they use?

A) Supervised learning with regression
B) Supervised learning with classification
C) Unsupervised learning with clustering
D) Reinforcement learning with policy optimization

---

**Q3.** What is the PRIMARY difference between AI, machine learning, and deep learning?

A) AI is the broadest concept encompassing any intelligent behavior; ML is a subset using data-driven learning; deep learning is a subset of ML using neural networks with multiple layers
B) Deep learning is the broadest field; ML is a specialized subset; AI is a subset of ML focused on simple tasks
C) AI and ML are the same thing; deep learning is completely separate and unrelated to both
D) ML requires labeled data; deep learning works only with unlabeled data; AI requires no data

---

**Q4.** A financial services company is building a fraud detection system that must learn from historical transaction data labeled as 'fraudulent' or 'legitimate' to predict whether new transactions are fraudulent. During testing, the model achieves 98% accuracy on training data but only 75% accuracy on new real-world transactions. What problem is the model experiencing?

A) Underfitting - the model is too simple to capture patterns
B) Overfitting - the model memorized training data instead of learning generalizable patterns
C) Bias in the dataset - the training data is not representative
D) Class imbalance - there are too few fraud examples

---

**Q5.** A manufacturing company needs to predict the remaining useful life (in hours) of industrial equipment based on sensor readings like temperature, vibration, and pressure. Which type of machine learning task is this?

A) Classification - predicting categorical equipment failure states
B) Regression - predicting continuous numerical values
C) Clustering - grouping equipment by similarity
D) Dimensionality reduction - reducing sensor data complexity

---

**Q6.** An e-commerce company wants to build a recommendation system that learns optimal product suggestions through trial and error, receiving positive feedback (sales) when recommendations lead to purchases and negative feedback when users ignore suggestions. Which ML paradigm is MOST suitable?

A) Supervised learning with labeled purchase history
B) Unsupervised learning with collaborative filtering
C) Reinforcement learning with reward-based optimization
D) Semi-supervised learning with partial labels

---

**Q7.** During model development, a data scientist splits available data into three sets: training set (70%), validation set (15%), and test set (15%). What is the PRIMARY purpose of the validation set?

A) To train the model parameters and weights
B) To tune hyperparameters and prevent overfitting during development
C) To provide the final unbiased evaluation of model performance
D) To generate synthetic data for data augmentation

---

**Q8.** A startup is choosing between training a custom machine learning model from scratch versus using a pre-trained foundation model. They have limited labeled data (500 examples) and need to classify industry-specific documents. Which approach is MOST cost-effective and likely to perform better?

A) Train a deep learning model from scratch using only their 500 labeled examples
B) Use a pre-trained foundation model and fine-tune it with their 500 labeled examples
C) Use unsupervised learning since they have limited labeled data
D) Collect at least 100,000 labeled examples before starting any model development

---

**Q9.** What is the key characteristic that distinguishes generative AI models from discriminative AI models?

A) Generative models create new data instances similar to training data; discriminative models classify or predict labels for existing data
B) Generative models only work with images; discriminative models only work with text
C) Generative models require more training data; discriminative models work with less data
D) Generative models are always more accurate; discriminative models are faster but less precise

---

**Q10.** A healthcare startup is building a system to analyze patient symptoms described in natural language and suggest potential diagnoses. The system must understand context, handle medical terminology, and generate human-readable explanations. Which type of AI model is MOST appropriate for this use case?

A) A supervised learning model trained on labeled symptom-diagnosis pairs
B) A large language model (LLM) with domain-specific fine-tuning on medical texts
C) A clustering algorithm to group similar symptom patterns
D) A rule-based expert system with predefined medical decision trees

---

**Q11.** A machine learning engineer is evaluating a binary classification model that predicts whether a financial transaction is fraudulent. The model achieves 98% accuracy, but only catches 45% of actual fraud cases. Which metric should the engineer prioritize to improve the model's effectiveness for this business problem?

A) Precision
B) Recall
C) Accuracy
D) F1 Score

---

**Q12.** A data scientist is preparing a dataset of 50,000 customer reviews for sentiment analysis. The reviews are split into 40,000 for training and 10,000 for testing. During model development, the data scientist needs to tune hyperparameters and select the best model architecture. What is the BEST practice for using the available data?

A) Use the 40,000 training samples for both training and hyperparameter tuning, then evaluate final performance on the 10,000 test samples
B) Further split the 40,000 training samples into training and validation sets, tune hyperparameters on the validation set, and use the 10,000 test samples only for final evaluation
C) Use all 50,000 samples for training with cross-validation to maximize model performance
D) Combine training and test sets, shuffle them, and create new 80/20 splits for each hyperparameter configuration

---

**Q13.** An e-commerce company wants to implement a recommendation system that suggests products to users based on their browsing history and past purchases. The system should provide recommendations even for new users with minimal interaction history. Which approach combines BOTH collaborative filtering and content-based filtering advantages?

A) Matrix factorization using singular value decomposition (SVD)
B) K-nearest neighbors clustering on user purchase patterns
C) Hybrid recommendation system combining user-item interactions with product feature similarity
D) Deep learning autoencoder trained on user purchase sequences

---

**Q14.** A manufacturing company is implementing predictive maintenance for factory equipment. They have sensor data (temperature, vibration, pressure) collected every minute, along with maintenance records indicating when equipment failed. The goal is to predict equipment failure 24-48 hours in advance. Which machine learning task type and algorithm category is MOST appropriate?

A) Supervised learning regression to predict time until failure
B) Supervised learning classification to predict failure probability within the next 48 hours
C) Unsupervised learning anomaly detection to identify unusual sensor patterns
D) Reinforcement learning to optimize maintenance scheduling decisions

---

**Q15.** A data scientist observes that their computer vision model performs well on the training dataset (95% accuracy) but poorly on the test dataset (65% accuracy). After analysis, they notice the training images are all high-resolution professional photos, while test images include lower-resolution user-uploaded photos with varying lighting conditions. What is the PRIMARY issue affecting model performance?

A) Overfitting due to insufficient training data diversity
B) Underfitting due to model complexity being too low
C) Data leakage from test set into training process
D) Class imbalance in the training dataset

---

**Q16.** A healthcare startup is building a system to analyze patient symptoms and suggest possible conditions. The system needs to understand context from previous messages in a conversation, handle ambiguous descriptions, and provide explanations for its suggestions. The team has limited ML expertise. Which AWS AI service BEST meets these requirements?

A) Amazon Comprehend Medical with custom entity recognition
B) Amazon Bedrock with Claude or other foundation models
C) Amazon SageMaker with a custom-trained deep learning model
D) Amazon Lex with fulfillment Lambda functions

---

**Q17.** A data scientist needs to evaluate a binary classification model that predicts whether customers will churn. The business priority is minimizing false negatives (predicting a customer won't churn when they actually will) because retaining customers is more valuable than the cost of retention campaigns sent to non-churning customers. Which evaluation metric should be the PRIMARY focus?

A) Precision
B) Accuracy
C) Recall (Sensitivity)
D) F1 Score

---

**Q18.** An e-commerce company is implementing a recommendation system. During the initial data analysis phase, the team discovers that 30% of user interaction records have missing values for 'product_category' and 'user_age_group' fields. Which data preprocessing approach is MOST appropriate before training a machine learning model?

A) Remove all records with any missing values to ensure data quality
B) Use forward-fill imputation to copy values from previous records
C) Apply appropriate imputation strategies: mode for categorical fields and create a separate 'missing' indicator feature
D) Replace all missing values with the string 'Unknown' for both fields

---

**Q19.** A healthcare company wants to generate synthetic patient data for training purposes while ensuring the generated data maintains the statistical properties of the original dataset but doesn't expose actual patient information. Which generative AI approach is MOST appropriate for this requirement?

A) Use a fine-tuned large language model to generate patient records based on prompts
B) Use a Generative Adversarial Network (GAN) to generate synthetic tabular data
C) Use a variational autoencoder with differential privacy mechanisms
D) Use prompt engineering with ChatGPT to create fictional patient profiles

---

**Q20.** A research team is comparing different foundation models for their document summarization project. They observe that Model A with 70B parameters performs better on their task than Model B with 175B parameters. What is the MOST likely explanation for this outcome?

A) Model A was trained on a larger dataset than Model B
B) Model B is overfitted to its training data
C) Model A was specifically fine-tuned or optimized for summarization tasks while Model B is a general-purpose model
D) The 70B parameter model has better architecture than the 175B model

---

**Q21.** What is the primary purpose of the temperature parameter in generative AI model inference?

A) To control the computational resources used during generation
B) To adjust the training speed of the model
C) To control the randomness and creativity of the model's outputs
D) To set the maximum length of generated responses

---

**Q22.** A company is building an AI system to generate product descriptions. During testing, they notice the model sometimes produces factually incorrect specifications. Which phenomenon is MOST likely responsible for this behavior?

A) Overfitting to the training data
B) Catastrophic forgetting
C) Hallucination
D) Mode collapse

---

**Q23.** An e-commerce platform wants to use a generative AI model to create personalized product recommendations in natural language. They need to process 10,000 requests per minute with latency under 100ms. Which deployment consideration is MOST critical for meeting these requirements?

A) Using the largest available foundation model for best quality
B) Implementing model quantization and optimized inference infrastructure
C) Fine-tuning the model on customer data
D) Increasing the temperature parameter to generate more diverse recommendations

---

**Q24.** What is the key difference between discriminative AI models and generative AI models?

A) Discriminative models require less training data than generative models
B) Discriminative models learn the boundary between classes while generative models learn the distribution of data
C) Generative models are always more accurate than discriminative models
D) Discriminative models can only work with structured data while generative models work with unstructured data

---

**Q25.** A financial services company is evaluating foundation models for analyzing earnings call transcripts. They need to extract specific financial metrics mentioned in 50-page documents. Which model characteristic is MOST important for this use case?

A) The model's parameter count (number of parameters)
B) The model's context window size
C) The model's training data cutoff date
D) The model's temperature setting

---

**Q26.** In the transformer architecture that powers most modern generative AI models, what is the primary function of the self-attention mechanism?

A) To reduce the computational cost of training large models
B) To allow the model to weigh the importance of different parts of the input when processing each element
C) To prevent overfitting during training
D) To compress the input into a fixed-size representation

---

**Q27.** A development team is implementing a text generation system and notices that setting top-k=50 produces more diverse outputs than top-k=10, but sometimes generates less coherent text. What does the top-k parameter control?

A) The number of training iterations for the model
B) The number of highest-probability tokens the model considers when selecting the next token
C) The number of examples used for few-shot learning
D) The maximum number of tokens in the generated output

---

**Q28.** A media company wants to generate realistic images of products that don't exist yet for marketing purposes. They're deciding between using a Variational Autoencoder (VAE) and a Diffusion Model. What is the primary advantage of diffusion models over VAEs for this use case?

A) Diffusion models train faster than VAEs
B) Diffusion models generate higher quality, more detailed images than VAEs
C) Diffusion models require less training data than VAEs
D) Diffusion models have a simpler architecture than VAEs

---

**Q29.** An AI system uses a large language model to answer customer service queries. The company notices that the model sometimes provides outdated information about products launched after the model's training cutoff date. Which technique would BEST address this limitation while maintaining the model's general capabilities?

A) Retrain the entire model from scratch with new data
B) Increase the temperature parameter to generate more creative responses
C) Implement Retrieval-Augmented Generation (RAG) to provide current information from a knowledge base
D) Use a larger foundation model with more parameters

---

**Q30.** A financial services company wants to generate personalized investment reports for clients. The reports must include market analysis text, performance charts, and recommendations based on client portfolios. The solution should handle both text generation and data visualization. Which type of generative AI model is MOST appropriate for the text generation component of this use case?

A) Multimodal foundation model that can process both text and images
B) Large language model (LLM) fine-tuned on financial domain data
C) Diffusion model optimized for document generation
D) Variational autoencoder (VAE) trained on financial reports

---

**Q31.** A machine learning team is evaluating foundation models for a content moderation system. They need to understand model behavior during inference. During the inference process, what is the PRIMARY purpose of the temperature parameter when generating outputs from a large language model?

A) To control the computational resources allocated to the inference request
B) To determine the maximum length of the generated response in tokens
C) To adjust the model's response time and latency characteristics
D) To control the randomness and creativity of the generated output

---

**Q32.** An e-commerce company is implementing a product recommendation system using embeddings. They want to find products similar to a given item based on product descriptions. The team has generated embeddings for all product descriptions using a transformer-based model. What mathematical operation should they use to measure similarity between product embeddings?

A) Euclidean distance calculation between embedding vectors
B) Matrix multiplication of embedding vectors
C) Cosine similarity calculation between embedding vectors
D) Element-wise addition of embedding vectors

---

**Q33.** A healthcare startup is building a medical diagnosis assistant using a foundation model. During testing, they notice the model sometimes generates plausible-sounding but factually incorrect medical information that isn't present in the training data. What is this phenomenon called, and what is its PRIMARY cause?

A) Model drift, caused by distribution shift between training and inference data
B) Hallucination, caused by the model's tendency to generate confident predictions even with insufficient information
C) Overfitting, caused by the model memorizing training examples too closely
D) Catastrophic forgetting, caused by the model losing previously learned information

---

**Q34.** A company is developing a generative AI application that creates marketing copy. They need to implement Retrieval-Augmented Generation (RAG) to ground responses in their product documentation. In a RAG architecture, what is the PRIMARY purpose of the retrieval component?

A) To cache frequently requested prompts and reduce inference latency
B) To fetch relevant context from external knowledge sources based on the input query
C) To validate generated outputs against company compliance guidelines
D) To fine-tune the foundation model on domain-specific data in real-time

---

**Q35.** A research team is comparing different generative AI architectures for a text-to-image application. They are evaluating models based on training efficiency and output quality. What is the KEY architectural difference between Generative Adversarial Networks (GANs) and diffusion models for image generation?

A) GANs use a discriminator network to distinguish real from generated images, while diffusion models iteratively denoise images from random noise
B) GANs require labeled training data, while diffusion models can be trained on unlabeled data only
C) GANs generate images by encoding and decoding latent representations, while diffusion models use attention mechanisms
D) GANs are transformer-based architectures, while diffusion models use convolutional neural networks exclusively

---

**Q36.** A research team is building a generative AI application that needs to create novel protein sequences for drug discovery. The sequences must be biologically plausible but not exist in nature. Which type of generative AI model is MOST appropriate for this task?

A) A large language model (LLM) fine-tuned on protein sequence data
B) A diffusion model trained on protein structure images
C) A variational autoencoder (VAE) trained on known protein sequences
D) A retrieval-augmented generation (RAG) system with a protein database

---

**Q37.** A company is evaluating foundation models for their customer service chatbot. They need to understand the difference between model parameters and hyperparameters. During inference, which statement is correct about these components?

A) Parameters are learned during training and fixed during inference; hyperparameters like temperature can be adjusted during inference to control output randomness
B) Both parameters and hyperparameters are fixed during inference and cannot be modified without retraining
C) Parameters can be adjusted during inference through prompt engineering; hyperparameters remain fixed from training
D) Hyperparameters are learned during training; parameters like temperature are set during inference

---

**Q38.** A financial services company wants to use a generative AI model to create synthetic transaction data for testing fraud detection systems. The synthetic data must preserve statistical patterns and correlations from real data while protecting customer privacy. They are considering different approaches. Which technique BEST addresses both requirements?

A) Using a GAN (Generative Adversarial Network) trained on anonymized real transaction data
B) Fine-tuning a large language model on customer transaction descriptions
C) Applying random perturbation and noise to existing real transaction records
D) Using a pre-trained foundation model with few-shot examples of transactions

---

**Q39.** An AI team is explaining model architecture concepts to stakeholders. They need to clarify what happens during the 'attention mechanism' in transformer-based generative models. Which description is MOST accurate?

A) The model assigns importance weights to different parts of the input sequence, allowing it to focus on relevant tokens when generating each output token
B) The model filters out unnecessary tokens from the input to reduce computational cost during generation
C) The model randomly samples from high-probability tokens to increase output diversity and creativity
D) The model compares the input to examples in its training data to find the most similar patterns

---

**Q40.** A healthcare organization is implementing a generative AI solution to draft patient education materials. They need to understand model 'hallucination' risks. During a review, the model generates a medically accurate paragraph but includes a reference to a non-existent clinical study. Which characteristic of foundation models BEST explains this behavior?

A) The model was trained on outdated medical literature and needs retraining on current research
B) The model's temperature parameter was set too high, causing excessive randomness in generation
C) Foundation models generate text by predicting probable next tokens based on patterns, not by retrieving verified facts from a knowledge base
D) The model lacks sufficient medical training data and is extrapolating beyond its domain knowledge

---

**Q41.** A healthcare company needs to extract patient information from thousands of handwritten medical forms daily. The forms contain structured fields (name, date of birth) and unstructured notes. The solution must achieve 95%+ accuracy and handle various handwriting styles. Which AWS AI service BEST meets these requirements?

A) Amazon Comprehend Medical with custom entity recognition
B) Amazon Textract with Queries and Forms features
C) Amazon Rekognition Custom Labels trained on form images
D) Amazon Bedrock with Claude for OCR tasks

---

**Q42.** A financial services firm wants to implement a chatbot that answers customer questions about investment products. The chatbot must reference the company's proprietary investment guides (500+ PDF documents) and provide accurate, source-cited responses. The firm wants to use foundation models without fine-tuning. Which approach BEST meets these requirements?

A) Use Amazon Lex with Lambda functions that query a vector database
B) Implement Retrieval Augmented Generation (RAG) with Amazon Bedrock Knowledge Bases
C) Fine-tune Amazon Titan on the investment guide documents
D) Use Amazon Comprehend to extract entities and Amazon Lex for responses

---

**Q43.** An e-commerce company processes customer support tickets and needs to automatically classify them into 15 categories (returns, shipping issues, product defects, etc.) and route to appropriate teams. They receive 50,000 tickets per day with an average of 200 words each. Which solution provides the MOST cost-effective classification?

A) Amazon Comprehend custom classification with a trained model
B) Amazon Bedrock with Claude Instant for zero-shot classification
C) Amazon SageMaker with a fine-tuned BERT model
D) AWS Lambda calling Amazon Titan Text Express for each ticket

---

**Q44.** A legal firm needs to redact personally identifiable information (PII) from court documents before sharing them publicly. Documents contain names, addresses, Social Security numbers, and case-specific details. The solution must handle 10,000+ pages daily and support both text documents and scanned PDFs. What combination of services provides the BEST solution?

A) Amazon Textract for extraction, Amazon Comprehend for PII detection, custom Lambda for redaction
B) Amazon Bedrock with prompt engineering to identify and redact PII
C) Amazon Rekognition to detect text, AWS Entity Resolution to identify PII
D) Amazon Comprehend Medical for PHI detection and redaction

---

**Q45.** A media company wants to generate article summaries for their news website. Articles average 2,000 words and need to be summarized to approximately 150 words. They publish 500 articles daily and need summaries within 5 minutes of publication. Cost is a primary concern. Which solution is MOST appropriate?

A) Amazon Bedrock with Claude Haiku using prompt engineering for summarization
B) Amazon Comprehend custom entity recognition to extract key points
C) Amazon Bedrock with Titan Text Lite for text summarization
D) Amazon SageMaker JumpStart with a fine-tuned BART model

---

**Q46.** A customer service team wants to analyze call transcripts to detect customer sentiment and identify the specific product features being discussed. They process 1,000 calls daily, each generating 3,000-5,000 word transcripts. The analysis must identify sentiment at the feature level (e.g., 'negative sentiment about battery life'). Which AWS service configuration BEST meets this requirement?

A) Amazon Comprehend Sentiment Analysis and Amazon Comprehend Custom Entity Recognition
B) Amazon Transcribe with sentiment analysis and entity recognition enabled
C) Amazon Bedrock with a prompt that analyzes sentiment per feature
D) Amazon Comprehend Targeted Sentiment with custom entity recognition

---

**Q47.** A pharmaceutical company needs to analyze 50,000 clinical trial reports to identify adverse drug reactions mentioned in unstructured physician notes. The reports contain medical terminology, drug names, dosages, and patient outcomes. Accuracy is critical and results must be auditable. Which solution BEST meets these requirements?

A) Amazon Comprehend Medical DetectEntities-v2 API with PROTECTED_HEALTH_INFORMATION detection
B) Amazon Bedrock with Claude for medical entity extraction with confidence scores
C) Amazon Comprehend Medical with ontology linking to RxNorm and ICD-10-CM
D) Amazon HealthLake to ingest FHIR resources and query adverse events

---

**Q48.** A retail company wants to implement semantic search across their product catalog of 2 million items. Customers should find relevant products even when using different terminology (e.g., 'sneakers' should return 'athletic shoes'). The solution must support real-time updates when new products are added. Which architecture BEST supports this requirement?

A) Amazon Kendra with a custom data source connector to the product database
B) Amazon OpenSearch Service with k-NN search using Titan Embeddings
C) Amazon Bedrock Knowledge Bases configured with the product catalog
D) Amazon Comprehend custom classification to map queries to product categories

---

**Q49.** A financial institution needs to generate personalized investment reports for 100,000 clients monthly. Each report requires combining client portfolio data with market analysis and must follow strict regulatory language requirements. Reports average 5 pages with charts and tables. The institution wants to use generative AI while ensuring compliance. What approach BEST meets these requirements?

A) Amazon Bedrock with guardrails configured for financial compliance and prompt templates
B) Amazon Personalize to generate recommendations, then use Lambda to create reports
C) Amazon QuickSight with ML insights to generate automated reports
D) Amazon SageMaker with a fine-tuned model on past compliant reports

---

**Q50.** An insurance company receives claim forms via email with attachments (PDFs, images, handwritten notes). They need to extract claim amounts, dates, incident descriptions, and supporting document types, then route claims based on complexity. Processing time must be under 2 minutes per claim. Which solution provides the BEST automation?

A) Amazon Textract for document extraction, Amazon Comprehend for text analysis, EventBridge for routing
B) Amazon Bedrock with Claude and vision capabilities to process all document types
C) Amazon Rekognition for image analysis, Amazon Lex for natural language understanding
D) Amazon Transcribe for handwritten text, Amazon Comprehend Medical for claim analysis

---

**Q51.** A social media monitoring company needs to analyze 10 million posts daily across multiple languages to detect trending topics and categorize sentiment by geographic region. They must support 15 languages and provide results within 6 hours. Which solution MOST cost-effectively meets these requirements?

A) Amazon Comprehend with language auto-detection, sentiment analysis, and topic modeling in batch mode
B) Amazon Translate for all posts to English, then Amazon Bedrock for analysis
C) Amazon Bedrock with Claude supporting multiple languages for real-time analysis
D) Amazon Textract to extract text, Amazon Comprehend for single-language analysis

---

**Q52.** A software company wants to build a code review assistant that analyzes pull requests, identifies potential bugs, suggests improvements, and explains complex code sections to junior developers. The assistant must understand context across multiple files in a repository. Which approach BEST meets these requirements?

A) Amazon CodeWhisperer for code suggestions with custom security scans
B) Amazon Bedrock with Claude using RAG over the repository codebase
C) Amazon SageMaker with a fine-tuned CodeBERT model
D) Amazon DevOps Guru for anomaly detection in code deployments

---

**Q53.** A logistics company needs to extract shipment information from various document types: Bills of Lading, customs forms, delivery receipts, and handwritten driver notes. Documents arrive in mixed formats (PDF, JPEG, TIFF) and contain tables with shipment details. They process 5,000 documents daily. The solution must achieve 98%+ accuracy for structured data extraction. Which combination of services BEST meets these requirements?

A) Amazon Textract with AnalyzeDocument API using Tables and Forms features, custom post-processing for validation
B) Amazon Rekognition to detect text, Amazon Comprehend custom entities for shipment data
C) Amazon Bedrock with Claude with vision for document understanding
D) Amazon Textract with Queries feature and Amazon A2I for human review of low-confidence extractions

---

**Q54.** A financial services company needs to analyze thousands of quarterly earnings call transcripts to extract key financial metrics, sentiment about market conditions, and competitive mentions. The solution must handle multi-page documents, preserve context across pages, and provide structured output. Which AWS AI service is BEST suited for this requirement?

A) Amazon Comprehend with custom entity recognition
B) Amazon Textract with Queries feature
C) Amazon Bedrock with Claude models using prompt engineering for extraction
D) Amazon Transcribe with custom vocabulary

---

**Q55.** A healthcare provider wants to build a patient support chatbot that answers questions about medication schedules, appointment procedures, and general health information. The chatbot must NOT provide medical diagnoses or treatment recommendations. The solution should minimize hallucinations and ensure responses stay within approved knowledge boundaries. What implementation approach BEST meets these requirements?

A) Use Amazon Bedrock with Retrieval Augmented Generation (RAG) connected to a curated knowledge base of approved patient information documents
B) Fine-tune a foundation model on historical patient interaction data using Amazon SageMaker
C) Use Amazon Lex with pre-built intents and slot types for healthcare
D) Deploy a foundation model with prompt engineering that instructs it to refuse medical advice

---

**Q56.** An e-commerce company processes product reviews in English, Spanish, French, and German. They need to extract product features mentioned, determine sentiment for each feature, and identify whether reviews mention competitor products. The solution must handle all four languages without building separate models. Which approach provides the MOST efficient solution?

A) Train four separate Amazon Comprehend custom classifiers, one for each language
B) Use Amazon Translate to convert all reviews to English, then use Amazon Comprehend
C) Use a multilingual foundation model through Amazon Bedrock with structured prompts for extraction
D) Use Amazon Comprehend's built-in multilingual sentiment analysis for all languages

---

**Q57.** A legal firm needs to generate first-draft contract summaries from 50-page commercial agreements. The summaries must identify key clauses (termination, liability, payment terms), highlight non-standard provisions, and maintain legal accuracy. Lawyers will review all output. The firm wants to minimize per-document processing cost. What solution BEST balances cost and capability?

A) Amazon Bedrock with Claude Haiku model using prompt engineering with few-shot examples
B) Amazon Comprehend custom classification with pre-labeled contracts
C) Amazon Bedrock with Claude Opus model for highest accuracy
D) Amazon SageMaker hosting a fine-tuned open-source LLM

---

**Q58.** A manufacturing company wants to enable factory floor workers to query equipment maintenance manuals, troubleshooting guides, and safety procedures using natural language questions via a mobile app. The documents are stored in Amazon S3 and contain technical diagrams, tables, and multi-step procedures. Workers need accurate, source-cited answers. Which architecture BEST supports this use case?

A) Amazon Kendra for intelligent search with deep learning-based ranking
B) Amazon Bedrock Knowledge Bases with Amazon Titan Embeddings and citation support
C) Amazon OpenSearch Service with keyword search and filters
D) Amazon Comprehend for document extraction with Amazon Lex for conversation

---

**Q59.** A content creation platform needs to generate unique product descriptions for 100,000 items daily. Each description must be 150-200 words, match brand voice guidelines provided in a 50-page style guide, and incorporate specific product attributes from a database. The solution must process this volume cost-effectively while maintaining quality. What approach BEST meets these requirements?

A) Amazon Bedrock batch inference using Claude Haiku with the style guide embedded in the system prompt
B) Amazon Bedrock on-demand inference using Claude Sonnet with RAG to retrieve relevant style guide sections
C) Fine-tune Amazon Titan Express on the style guide and historical product descriptions
D) Amazon SageMaker batch transform with a fine-tuned open-source model

---

**Q60.** A financial services company needs to generate personalized investment reports for 50,000 customers daily. Each report must incorporate the customer's portfolio data, current market conditions, and comply with SEC disclosure requirements. The reports average 3-4 pages and must maintain consistent formatting and terminology. Which approach BEST meets these requirements?

A) Use Amazon Bedrock with Anthropic Claude and Prompt Flows to create a multi-step workflow that retrieves customer data, generates compliant content, and formats the output
B) Fine-tune a foundation model on historical reports and use Amazon SageMaker endpoints for batch inference
C) Use Amazon Q Business to generate reports by connecting it to the customer database and compliance documentation
D) Implement retrieval augmented generation (RAG) with Amazon Kendra to search past reports and generate new ones

---

**Q61.** A healthcare provider wants to use a foundation model to extract medication names, dosages, and frequencies from unstructured clinical notes. The extracted data must be stored in a structured database for analytics. Accuracy is critical as errors could impact patient safety. Which solution provides the MOST reliable extraction with built-in validation?

A) Use Amazon Textract to extract text from clinical notes, then use Amazon Comprehend Medical to identify medical entities
B) Use Amazon Bedrock with a prompt that specifies JSON output format and includes few-shot examples of correct extractions
C) Fine-tune a foundation model specifically on the provider's historical clinical notes with medication extraction labels
D) Use Amazon Bedrock Guardrails with content filtering to validate model outputs against a medication database

---

**Q62.** An e-commerce platform needs to generate product descriptions in 12 languages for 100,000 SKUs. Descriptions must maintain brand voice, highlight key features differently based on regional preferences, and stay within 150-200 words. The solution must minimize translation costs while ensuring quality. What is the MOST cost-effective approach?

A) Use Amazon Translate to translate English descriptions to all languages, then use Amazon Bedrock to refine each translation for brand voice
B) Create a single multilingual prompt in Amazon Bedrock that generates descriptions directly in the target language with brand guidelines and regional preferences
C) Generate English descriptions with Amazon Bedrock, then use Amazon Translate with custom terminology for brand-specific terms
D) Fine-tune separate models for each language on existing product descriptions and regional examples

---

**Q63.** A legal firm needs to analyze contracts to identify non-standard clauses that deviate from their template agreements. The system must flag specific clause variations, explain why they're non-standard, and suggest template-compliant alternatives. Contracts are 20-50 pages each. Which Amazon Bedrock capability is MOST appropriate?

A) Use Retrieval Augmented Generation (RAG) with template contracts stored in Amazon OpenSearch Service to compare against new contracts
B) Use a foundation model with extended context window (100K+ tokens) to process the entire contract and template in a single prompt
C) Use Agents for Amazon Bedrock to break down the contract analysis into multiple focused tasks with function calling
D) Use Amazon Bedrock Prompt Management to create versioned prompts that compare contracts section-by-section

---

**Q64.** A customer service team wants to implement an AI assistant that answers questions using the company's internal knowledge base (5,000 documents), escalates complex issues to human agents, and logs all interactions in Salesforce. The assistant must cite sources for its answers. Which architecture BEST supports these requirements?

A) Amazon Q Business connected to Amazon S3 with the knowledge base documents and integrated with Salesforce using built-in connectors
B) Agents for Amazon Bedrock with a knowledge base using Amazon Bedrock Knowledge Bases, action groups for Salesforce integration, and function definitions for escalation logic
C) Amazon Bedrock with RAG using Amazon Kendra for document search, AWS Lambda for Salesforce API calls, and Amazon EventBridge for orchestration
D) Amazon Lex bot with Amazon Bedrock for intent recognition, AWS AppSync for Salesforce integration, and Amazon DynamoDB for conversation history

---

**Q65.** A media company wants to generate social media posts from their long-form articles. Each article should produce 3 posts: one for LinkedIn (professional, 200 chars), one for Twitter/X (casual, 280 chars), and one for Instagram (engaging, 150 chars with emojis). They publish 50 articles daily. Cost optimization is important. What is the MOST efficient implementation?

A) Make three separate Amazon Bedrock API calls per article with platform-specific prompts to ensure optimal output for each platform
B) Use a single Amazon Bedrock API call with a structured prompt requesting all three versions in one response with JSON output format
C) Use Amazon Bedrock Batch Inference to process all 50 articles overnight with separate jobs for each social platform
D) Use Provisioned Throughput for Amazon Bedrock with a single model serving all requests to reduce per-token costs

---

**Q66.** A healthcare technology company is developing an application to help medical professionals generate patient discharge summaries from clinical notes. The summaries must maintain consistent medical terminology, follow a standardized format across all outputs, and reliably include specific required sections (medications, follow-up instructions, and diagnosis). During testing, the development team notices that the foundation model occasionally omits required sections or uses inconsistent formatting. Which approach would MOST effectively ensure the model generates summaries with the required structure and completeness?

A) Increase the temperature parameter to 0.9 and add examples of well-formatted summaries in the system prompt to encourage creative but structured outputs
B) Implement prompt engineering with output format instructions and few-shot examples, then use a deterministic parsing layer to verify all required sections are present before returning results
C) Fine-tune the foundation model on a dataset of 50,000 properly formatted discharge summaries to teach it the exact output structure required
D) Use retrieval-augmented generation (RAG) to pull similar discharge summaries from a vector database and instruct the model to mimic their format

---

**Q67.** A healthcare company is deploying an AI system to assist doctors in diagnosing rare diseases from medical images. The system will be used across multiple hospitals with diverse patient populations. During testing, the model shows 95% accuracy on the development dataset but only 78% accuracy on images from underrepresented demographic groups. What is the MOST responsible approach to address this issue before deployment?

A) Deploy the model immediately since 95% overall accuracy exceeds industry standards, and add a disclaimer about potential accuracy variations
B) Collect additional training data from underrepresented groups, retrain the model, and validate performance across all demographic segments before deployment
C) Lower the confidence threshold for predictions on underrepresented groups to increase sensitivity
D) Deploy the model only in hospitals that primarily serve the majority demographic group where accuracy is highest

---

**Q68.** An e-commerce company uses an AI-powered recommendation system that suggests products to customers. Users have reported that the system seems to reinforce stereotypes, such as showing baby products predominantly to women and power tools predominantly to men. Which action BEST aligns with AWS responsible AI principles?

A) Implement fairness metrics to detect and measure bias, then adjust the recommendation algorithm to reduce gender-based stereotyping while maintaining relevance
B) Add a feature allowing users to manually select their gender preferences for product categories
C) Remove gender as a feature from the model entirely and rely only on purchase history
D) Increase the diversity of recommendations by randomly showing 20% of suggestions from categories users haven't browsed

---

**Q69.** What is the PRIMARY purpose of implementing human review loops in high-stakes AI decision-making systems?

A) To reduce computational costs by having humans handle complex edge cases
B) To provide accountability and oversight for decisions that significantly impact individuals' lives, rights, or safety
C) To improve model accuracy by collecting feedback data for continuous training
D) To comply with data retention requirements for audit purposes

---

**Q70.** A financial services company is developing an AI model to detect fraudulent transactions. The model will automatically block transactions flagged as high-risk. During validation, you discover the model has a 2% false positive rate, meaning legitimate transactions are incorrectly blocked. The model processes 1 million transactions daily. Which approach BEST demonstrates responsible AI governance?

A) Deploy the model as-is since 98% accuracy is excellent, and implement a customer service hotline for users to report blocked legitimate transactions
B) Implement a tiered response system: automatically block only extremely high-risk transactions (99%+ confidence), require additional verification for medium-risk (90-99% confidence), and allow low-risk transactions through while logging them for review
C) Increase the detection threshold to reduce false positives to 0.5%, accepting that this will also reduce true fraud detection
D) Deploy the model in shadow mode indefinitely, flagging transactions for human review without blocking any transactions automatically

---

**Q71.** According to AWS responsible AI principles, which statement BEST describes the concept of transparency in AI systems?

A) Making the complete source code and training data publicly available for all AI models
B) Providing clear information about how AI systems make decisions, their limitations, and when AI is being used, appropriate to the audience and context
C) Publishing detailed technical documentation of model architecture and hyperparameters for peer review
D) Allowing users to see all input features and their weights used in every individual AI decision

---

**Q72.** A company is deploying a generative AI chatbot for customer service. During testing, the chatbot occasionally produces responses that include fabricated information presented as facts (hallucinations). The chatbot also sometimes generates responses that could be considered offensive to certain groups. What combination of measures BEST addresses these responsible AI concerns?

A) Implement content filtering, add disclaimers about potential inaccuracies, establish feedback mechanisms for users to report issues, and maintain human escalation paths for complex queries
B) Reduce the model's temperature parameter to zero to ensure deterministic outputs and eliminate creativity
C) Train the model on a larger dataset that includes examples of correct and incorrect responses with human feedback
D) Implement rate limiting to reduce the number of interactions and minimize exposure to problematic outputs

---

**Q73.** A healthcare company is deploying an AI-powered diagnostic assistant on Amazon Bedrock that processes patient medical records. The company must ensure that all prompts and model responses containing Protected Health Information (PHI) are encrypted both in transit and at rest, with full audit trails of all access. The solution must comply with HIPAA requirements while minimizing operational overhead. Which combination of AWS services BEST meets these requirements?

A) Enable Amazon Bedrock with AWS KMS customer-managed keys for encryption, use VPC endpoints for private connectivity, and enable AWS CloudTrail for audit logging of all Bedrock API calls
B) Deploy the model on Amazon SageMaker with server-side encryption, use Amazon Macie to scan for PHI, and enable VPC Flow Logs for network monitoring
C) Use Amazon Bedrock with AWS-managed encryption keys, enable Amazon GuardDuty for threat detection, and use Amazon CloudWatch Logs for audit trails
D) Implement client-side encryption before sending data to Amazon Bedrock, use AWS WAF for API protection, and enable AWS Config for compliance monitoring

---

**Q74.** A financial services company uses Amazon Bedrock to generate investment recommendations. Regulatory requirements mandate that the company must be able to explain how each AI-generated recommendation was produced and identify which training data influenced specific outputs. The company needs to implement a solution that provides explainability and traceability. Which approach BEST addresses these requirements?

A) Implement prompt engineering with chain-of-thought reasoning in the prompts, store all prompts and responses in Amazon S3 with metadata tags, and use Amazon Bedrock model evaluation jobs to assess output quality
B) Use Amazon SageMaker Clarify for model explainability, implement Amazon Bedrock Guardrails to filter outputs, and enable Amazon Bedrock model invocation logging to CloudWatch
C) Enable Amazon Bedrock Agents with detailed logging, implement retrieval-augmented generation (RAG) with Amazon Kendra to track source documents, and use provenance tracking to link outputs to specific knowledge base articles
D) Fine-tune a foundation model on Amazon Bedrock with labeled training data, use Amazon SageMaker Model Monitor for drift detection, and implement custom explainability algorithms

---

**Q75.** Which AWS service or feature should be used to detect and prevent the exposure of personally identifiable information (PII) in prompts sent to Amazon Bedrock foundation models?

A) Amazon Macie with automated PII discovery policies
B) Amazon Bedrock Guardrails with PII filters configured
C) AWS Secrets Manager with rotation policies enabled
D) Amazon Comprehend with custom entity recognition

---

**Q76.** A global e-commerce company is implementing an AI chatbot using Amazon Bedrock that will be deployed across multiple AWS regions to serve customers worldwide. The company must comply with GDPR requirements, including data residency restrictions that prevent EU customer data from being processed outside the EU. The company also needs to implement consent management and the right to be forgotten. Which architecture BEST meets these requirements?

A) Deploy Amazon Bedrock in all required regions, use Amazon DynamoDB global tables for conversation history with region-specific encryption keys, implement AWS Organizations SCPs to prevent cross-region data transfer, and use Amazon S3 with lifecycle policies for data deletion
B) Deploy Amazon Bedrock in eu-central-1 and eu-west-1 only for EU customers, use Amazon Aurora with regional endpoints, implement Amazon Bedrock Guardrails to block data export prompts, and use AWS Lambda for automated data deletion requests
C) Use Amazon Bedrock in eu-central-1 and eu-west-1 for EU customers with VPC endpoints for private connectivity, store conversation data in Amazon DynamoDB with on-demand backups disabled for EU tables, implement API Gateway with resource policies restricting cross-region access, and use AWS Step Functions to orchestrate data deletion workflows for GDPR requests
D) Deploy Amazon Bedrock globally with geo-routing, use Amazon ElastiCache for session data, implement AWS KMS with region-specific keys, and use Amazon EventBridge for data deletion automation

---

**Q77.** A company has deployed an Amazon Bedrock application that uses the Anthropic Claude model for customer service. Security requirements mandate that all model invocations must be logged with user identity, timestamp, input prompts, and model responses for compliance auditing. The logs must be retained for 7 years and protected from tampering. Which configuration BEST meets these requirements?

A) Enable Amazon Bedrock model invocation logging to Amazon CloudWatch Logs, set retention to 7 years, enable log encryption with AWS KMS, and use CloudWatch Logs Insights for querying
B) Enable Amazon Bedrock model invocation logging to Amazon S3, enable S3 Object Lock in compliance mode with 7-year retention, use AWS KMS for encryption, enable S3 bucket versioning, and use Amazon Athena for log analysis
C) Configure AWS CloudTrail to log all Bedrock API calls, store trails in S3 with MFA Delete enabled, use CloudTrail Log File Integrity Validation, and set S3 lifecycle policy for 7-year retention
D) Use AWS Lambda to intercept all Bedrock calls and write logs to Amazon DynamoDB with point-in-time recovery enabled, use DynamoDB streams for real-time monitoring, and export to S3 Glacier for long-term storage

---

**Q78.** An AI development team is using Amazon Bedrock to build a content generation application. The security team requires that the application must prevent the model from generating content that contains profanity, hate speech, or instructions for illegal activities. The solution must block violating content in real-time with minimal latency impact. Which solution should be implemented?

A) Amazon Comprehend with custom classification models to detect toxic content in model outputs
B) Amazon Bedrock Guardrails with denied topics and content filters configured for profanity, hate speech, and harmful content
C) AWS Lambda function using Amazon Rekognition to analyze generated text before returning to users
D) Amazon SageMaker with a separate toxicity detection model deployed on a real-time endpoint

---

