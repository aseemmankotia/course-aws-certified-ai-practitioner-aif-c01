## Chapter 10: Full Practice Exam + Test-Taking Strategy (65 Questions) — Practice Questions

**Q1.** A healthcare company needs to analyze patient feedback from emails, identify sentiment, and extract medical entities like disease names and medications. The solution must comply with HIPAA and process data within their AWS account without sending PHI to third-party models. Which combination meets these requirements? (Choose TWO)

A) Use Amazon Comprehend Medical to extract entities and Amazon Comprehend for sentiment analysis
B) Use Amazon Bedrock with Anthropic Claude to extract entities and analyze sentiment
C) Use Amazon Textract to extract text, then Amazon Comprehend Medical for entity extraction
D) Use Amazon Q Business to analyze the emails and extract medical information

<details>
<summary>Answer</summary>

**Correct: A**

Amazon Comprehend Medical is purpose-built for extracting medical entities (diseases, medications, dosages) and is HIPAA-eligible. Amazon Comprehend (standard) handles sentiment analysis. Both process data within AWS without sending to external models, meeting HIPAA requirements.

**Why the others are wrong:**
- Bedrock sends data to foundation models hosted by AWS but managed by third parties (Anthropic). While Bedrock is building HIPAA compliance, Comprehend Medical is the established HIPAA-eligible service for medical entity extraction.
- Textract is for extracting text from PDFs/images, not plain email text. This adds unnecessary complexity and cost. The question states emails (already text format).
- Q Business is for enterprise search and chat over business documents, not for extracting specific medical entities or sentiment analysis. It's not designed for structured entity extraction.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A company runs a chatbot using Amazon Bedrock with Claude v2. Users report the bot sometimes provides outdated product information despite the knowledge base being updated weekly. Average query response time is 1.2 seconds. The company wants responses to always reflect current data (updated daily) while maintaining sub-2-second response times. What is the MOST cost-effective solution?

A) Fine-tune Claude v2 model daily with the updated product catalog
B) Implement Retrieval Augmented Generation (RAG) using Amazon Kendra to query the updated product database
C) Switch to provisioned throughput for faster inference and reduce latency
D) Increase the knowledge base sync frequency to daily instead of weekly

<details>
<summary>Answer</summary>

**Correct: B**

RAG with Kendra retrieves current data at query time from the live product database, ensuring responses always reflect latest information. Kendra indexes can be updated continuously. RAG adds ~200-400ms latency, keeping total under 2 seconds. More cost-effective than daily fine-tuning.

**Why the others are wrong:**
- Fine-tuning daily is extremely expensive ($1000s per training run) and time-consuming (hours). Fine-tuning is for changing model behavior/style, not for frequently changing factual data. The exam heavily tests this distinction.
- Provisioned throughput reduces latency but doesn't solve the outdated data problem. The model still only knows what it was trained on or what's in its static knowledge base. This wastes money without addressing the core issue.
- The knowledge base already exists but syncs weekly. Even with daily sync, static knowledge bases lag real-time data. RAG queries live data sources, providing always-current information. This is the 'frequently changing data' keyword the exam tests.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** An e-commerce company processes 50,000 product images monthly for automated categorization using Amazon Rekognition Custom Labels. Current cost is $4 per 1,000 images analyzed ($200/month). Traffic is steady throughout the month. They're considering provisioned throughput at $0.008 per inference unit hour. An inference unit processes 5 images per second. What is the break-even point?

A) Provisioned throughput is never cost-effective for this use case
B) Provisioned throughput becomes cheaper at approximately 83,000 images per month
C) Provisioned throughput is immediately cheaper at current volume of 50,000 images
D) Provisioned throughput becomes cheaper at approximately 125,000 images per month

<details>
<summary>Answer</summary>

**Correct: A**

On-demand: $200/month. Provisioned: 1 inference unit runs 24/7 = 720 hours/month × $0.008 = $5.76/month. BUT this gives capacity for 5 images/sec × 3600 sec × 720 hours = 12.96M images/month. To process just 50K images takes only 2.8 hours. Provisioned only makes sense for continuous high-volume workloads. At steady 50K/month, on-demand is always cheaper.

**Why the others are wrong:**
- At 83K images: on-demand = $332, provisioned still $5.76 for full month BUT you're paying for 99.4% unused capacity. The trap is comparing unit costs without considering utilization. Provisioned works for continuous load, not batch processing.
- At 50K images (current volume), on-demand costs $200 vs provisioned $5.76 for a full month of capacity. However, you only use a tiny fraction of that provisioned capacity. This is a classic exam trap testing whether you understand utilization vs raw cost.
- At 125K images: on-demand = $500, provisioned = $5.76/month. But if processing is batched (common for image categorization), you use provisioned capacity for only hours, not full month. Provisioned makes sense only for continuous 24/7 inference workloads.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A financial services company is deploying a document analysis system using Amazon Textract to extract data from loan applications (PDFs with forms, tables, and signatures). They need to extract form fields, table data, and detect signatures. Documents are submitted irregularly, averaging 500 per day with peaks of 2,000. Processing must complete within 15 minutes of submission. Which Textract configuration meets these requirements at LOWEST cost?

A) Use Textract synchronous API with DetectDocumentText for text extraction
B) Use Textract asynchronous API with AnalyzeDocument (FORMS and TABLES features) for all documents
C) Use Textract synchronous API with AnalyzeDocument (FORMS, TABLES, SIGNATURES features)
D) Use Textract asynchronous API with AnalyzeDocument (FORMS, TABLES, SIGNATURES features)

<details>
<summary>Answer</summary>

**Correct: D**

Async API is cheaper than sync ($1.50 vs $1.80 per 1000 pages for AnalyzeDocument). With irregular traffic and 15-minute SLA, async handles peaks better. FORMS extracts key-value pairs from forms, TABLES extracts tabular data, SIGNATURES detects signature locations. All three features needed per requirements.

**Why the others are wrong:**
- DetectDocumentText only extracts raw text without structure - doesn't extract form fields or tables as required. This is the cheapest option ($1.00/1000 pages) but doesn't meet functional requirements. Exam tests whether you choose cheapest vs. fit-for-purpose.
- Sync API is $0.30/1000 pages more expensive than async. With irregular peaks of 2000 docs, sync API might hit rate limits (designed for real-time single-doc processing). The 15-minute SLA doesn't require sync response - this is overpaying for unneeded speed.
- Sync API costs more and isn't designed for batch processing of 500-2000 documents. Sync is for real-time (<1 sec response) scenarios. The 15-minute SLA clearly indicates async is acceptable and more cost-effective. Classic 'cost-optimized' keyword test.

</details>

---

**Q5.** A media company uses Amazon Transcribe to generate subtitles for videos. They need to support 15 languages and handle custom terminology (brand names, technical terms). Videos are 30-90 minutes long. They currently use standard Transcribe with custom vocabularies. Users report inaccurate transcription of industry jargon and inconsistent brand name spelling. What change provides the MOST accuracy improvement?

A) Switch to Amazon Transcribe Medical for better accuracy on technical terms
B) Create custom language models using domain-specific training data for each language
C) Increase custom vocabulary size from 100 to 5000 terms per language
D) Use Amazon Bedrock to post-process transcripts and correct terminology

<details>
<summary>Answer</summary>

**Correct: B**

Custom language models (CLMs) in Transcribe are trained on your domain-specific text data, significantly improving accuracy for industry jargon and context. CLMs understand word relationships and context, not just vocabulary lists. This is the most effective solution for systematic terminology issues.

**Why the others are wrong:**
- Transcribe Medical is specifically for medical terminology (medications, procedures, anatomy). It doesn't help with general industry jargon or brand names in media/entertainment. Exam tests whether you choose specialized vs general-purpose services correctly.
- Custom vocabularies support up to 256KB (roughly 50K words), not just 100. Size isn't the issue - custom vocabularies only handle individual words, not context or phrases. They help with spelling but not understanding jargon usage. CLMs handle context and relationships.
- Post-processing with Bedrock adds latency and cost. While possible, it's addressing the symptom (bad transcripts) not the cause. Transcribe CLMs fix accuracy at the source. Exam tests whether you solve root cause vs. add workarounds. Also, this requires maintaining correction prompts.

</details>

---

**Q6.** A research team needs to train a computer vision model to detect rare defects in manufacturing. They have 50,000 images, but only 200 show defects (0.4% positive class). Training with Amazon SageMaker using a standard CNN results in 99.6% accuracy, but the model predicts 'no defect' for all images. Which approach BEST addresses this problem?

A) Increase training epochs from 10 to 100 to allow the model more time to learn defect patterns
B) Use class weighting or focal loss to penalize misclassification of the minority class more heavily
C) Reduce the dataset to 1,000 images with 50/50 split between defect and non-defect classes
D) Switch from SageMaker to Amazon Rekognition Custom Labels which handles imbalanced data automatically

<details>
<summary>Answer</summary>

**Correct: B**

Class imbalance problem: model learns that predicting 'no defect' gives 99.6% accuracy without learning defect features. Class weighting assigns higher loss to minority class errors. Focal loss focuses on hard examples. Both techniques force the model to learn defect patterns. This is the standard ML solution for imbalanced datasets.

**Why the others are wrong:**
- More epochs doesn't fix the fundamental issue. The model has already converged to the easy solution (predict majority class). Training longer just reinforces the wrong behavior. It's not a problem of insufficient training time but incorrect optimization objective.
- Reducing to 50/50 split throws away 49,800 images of valuable data and creates only 400 training samples (200 defect + 200 non-defect). This is severely underfitting. While balancing helps, undersampling this aggressively loses critical information. Oversampling or class weighting is better.
- Rekognition Custom Labels does handle some imbalance but requires minimum 1,000 images per label. With only 200 defect images, this doesn't meet requirements. Also, Rekognition is more expensive than SageMaker. SageMaker with proper techniques is the right tool here.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** A company built a customer service chatbot using Amazon Lex with Lambda backend. During peak hours (9am-5pm weekdays), they experience 500 concurrent conversations. Off-peak, there are 50 concurrent conversations. Lambda functions have a warm-up time of 2 seconds (cold start) and 200ms when warm. Users complain about slow responses during peak start (9am). What is the MOST cost-effective solution to improve performance?

A) Enable provisioned concurrency for Lambda functions set to 500 concurrent executions 24/7
B) Enable provisioned concurrency for Lambda functions set to 450 concurrent executions during business hours only (9am-5pm weekdays)
C) Increase Lambda function memory from 128MB to 1024MB to reduce execution time
D) Implement connection pooling and caching in Lambda to reduce cold starts

<details>
<summary>Answer</summary>

**Correct: B**

Provisioned concurrency keeps functions warm, eliminating the 2-second cold start. Setting to 450 (not full 500) allows some on-demand burst for variance. Scheduling it only during business hours (40 hours/week vs 168 hours/week) saves 76% vs 24/7 provisioning. This is the 'cost-optimized' keyword in action.

**Why the others are wrong:**
- Provisioning 500 concurrent executions 24/7 wastes money during off-peak (50 concurrent). Provisioned concurrency costs ~$0.015/hour per GB-hour. Running 500 when you need 50 off-peak is 90% waste. Exam tests whether you right-size and schedule based on actual usage patterns.
- Increasing memory speeds execution but doesn't eliminate cold starts. A 2-second cold start at 1024MB is still ~2 seconds (cold start is initialization, not execution). This also increases cost proportionally to memory. Doesn't address the root cause of the complaint (slow 9am responses).
- Connection pooling and caching help but don't eliminate cold starts. When traffic spikes from 50 to 500 at 9am, 450 new Lambda instances must start cold. These optimization techniques reduce cold start duration slightly but can't prevent them. Provisioned concurrency is the direct solution.

</details>

---

**Q8.** An AI team is evaluating foundation models in Amazon Bedrock for a content generation system. They need to generate product descriptions (200-500 tokens) for 100,000 products. Testing shows all models produce acceptable quality. Current costs: Claude v2 ($0.011/1K input + $0.033/1K output tokens), Titan Text G1 ($0.0008/1K input + $0.0016/1K output tokens), Llama 2 70B ($0.00195/1K input + $0.00256/1K output tokens). Average input: 50 tokens (product specs), output: 350 tokens. Which model is MOST cost-effective?

A) Claude v2 because it produces higher quality outputs requiring less editing
B) Titan Text G1 because it has the lowest per-token cost
C) Llama 2 70B because it balances cost and performance
D) Run a hybrid approach: use Titan for 80% and Claude for 20% requiring better quality

<details>
<summary>Answer</summary>

**Correct: B**

Calculate total cost: Claude: (50×$0.011 + 350×$0.033)/1000 × 100K = $1,210. Titan: (50×$0.0008 + 350×$0.0016)/1000 × 100K = $60. Llama 2: (50×$0.00195 + 350×$0.00256)/1000 × 100K = $99.40. Titan is 95% cheaper than Claude, 40% cheaper than Llama 2. Question states all produce acceptable quality - choose cheapest.

**Why the others are wrong:**
- Claude v2 costs $1,210 for the job vs Titan's $60. The question explicitly states 'all models produce acceptable quality' - this means editing isn't a differentiator. Exam tests if you do the math and follow the 'cost-effective' constraint when quality is equal.
- Llama 2 70B costs $99.40 vs Titan's $60 (66% more expensive). While Llama 2 is mid-priced, when the question says all models meet requirements, always choose lowest cost. There's no 'balance' consideration when quality requirements are met. This is an exam trap for overthinking.
- Hybrid approach adds operational complexity (routing logic, two model deployments, managing 80/20 split). Cost savings would be minimal vs 100% Titan: 80% Titan + 20% Claude = 0.8×$60 + 0.2×$1,210 = $290 (still 5× more than pure Titan). Overcomplicates when simple solution exists.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

