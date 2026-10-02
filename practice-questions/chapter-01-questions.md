## Chapter 1: Domain 1: AI/ML Fundamentals & AWS Service Portfolio — Practice Questions

**Q1.** A healthcare startup needs to analyze patient feedback surveys to understand satisfaction levels and identify common complaints. The surveys are unstructured text responses averaging 200 words each. Which AWS service BEST meets this requirement?

A) Amazon Rekognition with custom labels trained on text images
B) Amazon Comprehend with built-in sentiment analysis and entity recognition
C) Amazon Transcribe with custom vocabulary for medical terms
D) Amazon SageMaker with a custom NLP model trained from scratch

<details>
<summary>Answer</summary>

**Correct: B**

Comprehend is purpose-built for text analysis including sentiment analysis (satisfaction levels) and entity recognition (common complaint topics). No custom training needed for basic sentiment and entity detection.

**Why the others are wrong:**
- Rekognition is for image/video analysis, not text analysis. Even with custom labels, it processes visual content, not raw text.
- Transcribe converts speech to text. The surveys are already text, and Transcribe doesn't perform sentiment or entity analysis.
- SageMaker could work but requires significant ML expertise, training data labeling, and custom model development. Comprehend provides these capabilities out-of-box, making it the BEST choice for this straightforward use case.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A company has 50,000 customer service call recordings and wants to convert them to text for compliance auditing. The calls contain technical product names and the company needs to identify which agent handled each call. Which combination of AWS services accomplishes this MOST efficiently?

A) Amazon Comprehend for speech-to-text conversion with custom entity recognition for product names
B) Amazon Transcribe with custom vocabulary for product names and speaker identification enabled
C) Amazon Rekognition with audio analysis and Amazon SageMaker for speaker detection
D) Amazon SageMaker Ground Truth to manually transcribe calls, then Comprehend for speaker identification

<details>
<summary>Answer</summary>

**Correct: B**

Transcribe is the AWS speech-to-text service. Custom vocabulary handles technical product names, and speaker identification (diarization) identifies different speakers (agents). This is the exact use case Transcribe was designed for.

**Why the others are wrong:**
- Comprehend analyzes text but doesn't convert speech to text. It cannot process audio files directly.
- Rekognition processes images and videos, not audio. It has no audio analysis capability, and SageMaker for speaker detection would require custom model development.
- Manual transcription via Ground Truth is extremely inefficient for 50,000 calls and expensive. Comprehend cannot identify speakers from text alone without timestamps and audio features.

</details>

---

**Q3.** A retail company trained a supervised learning model to predict customer churn using 2 years of historical data with labels (churned=1, retained=0). After deploying to production via SageMaker endpoint, the model's accuracy dropped from 85% to 62% after 6 months. What is the MOST likely cause?

A) The SageMaker endpoint instance type is undersized for production traffic
B) The model is experiencing data drift as customer behavior patterns changed
C) Supervised learning models naturally degrade over time and need retraining every 3 months
D) The training data was too small (only 2 years) and caused overfitting

<details>
<summary>Answer</summary>

**Correct: B**

Data drift occurs when real-world data distribution changes from training data distribution. Customer behavior changing over 6 months means the model's learned patterns no longer match current patterns. This is the primary cause of accuracy degradation in production ML models and requires monitoring and retraining.

**Why the others are wrong:**
- Undersized instances cause latency/throughput issues, not accuracy drops. Prediction accuracy is determined by the model, not the infrastructure running it.
- While models do need retraining, there's no fixed '3-month rule.' The degradation here is caused by specific data drift, not natural time-based decay. Monitoring determines retraining frequency.
- 2 years of data is typically sufficient. Overfitting would cause poor initial performance, not degradation after deployment. The model performed well initially (85%), indicating training data was adequate.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** An e-commerce company wants to group customers into segments based on browsing and purchase patterns, but they don't have predefined customer categories. They have 5 million customer records with 47 features each (page views, time on site, purchase frequency, etc.). Which ML approach should they use?

A) Supervised learning with classification using manually created customer segment labels
B) Unsupervised learning with clustering to discover natural customer groupings
C) Supervised learning with regression to predict customer lifetime value
D) Reinforcement learning to optimize customer segment assignments over time

<details>
<summary>Answer</summary>

**Correct: B**

Unsupervised learning with clustering (like K-means) is specifically designed to find natural groupings in unlabeled data. The company lacks predefined categories, making this the only viable approach. Clustering will automatically discover patterns and group similar customers.

**Why the others are wrong:**
- Supervised classification requires labeled data (predefined segment labels). The company explicitly lacks these labels, making supervised learning impossible for this use case.
- Regression predicts continuous values (like revenue), not customer segments. While predicting customer lifetime value uses supervised learning, it doesn't solve the segmentation problem.
- Reinforcement learning optimizes sequential decision-making through trial-and-error. It's not designed for customer segmentation and requires a reward function, which doesn't apply here.

</details>

---

**Q5.** A video streaming platform needs to automatically detect and blur faces in user-generated content before publishing. They process 10,000 videos per day, each 2-5 minutes long. They also need to detect if videos contain inappropriate content. Which AWS service combination handles this MOST cost-effectively?

A) Amazon SageMaker with custom-trained face detection model and content moderation model, deployed on ml.g4dn.xlarge instances
B) Amazon Rekognition Video with face detection and content moderation APIs called per video
C) Amazon Transcribe to convert audio to text, then Comprehend to detect inappropriate language
D) Amazon Rekognition Image processing each video frame individually with face detection and unsafe content detection

<details>
<summary>Answer</summary>

**Correct: B**

Rekognition Video is purpose-built for video analysis including face detection and content moderation. It processes videos asynchronously, handles video-specific features (temporal consistency), and uses pay-per-use pricing with no infrastructure management. Most cost-effective for this scale.

**Why the others are wrong:**
- SageMaker with custom models requires ML expertise, training data, model development, and continuous infrastructure costs (ml.g4dn.xlarge runs 24/7). Far more expensive and complex than using managed Rekognition APIs.
- Transcribe and Comprehend only process audio/text, not visual content. They cannot detect or blur faces, which is a visual detection task.
- Rekognition Image processes static images, not videos. Processing each frame individually loses temporal context, costs significantly more (paying per frame vs per video), and requires custom frame extraction and video reassembly logic.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** A data scientist completed training a SageMaker model and needs to make it available for real-time predictions from a web application. The application expects response times under 100ms and will have variable traffic (10-500 requests/minute). What is the correct deployment approach?

A) Create a SageMaker batch transform job that runs hourly to generate predictions for all possible inputs
B) Deploy the model to a SageMaker real-time endpoint with automatic scaling enabled
C) Export the model and deploy it to AWS Lambda for serverless inference
D) Use SageMaker Processing jobs triggered by API Gateway to run predictions on-demand

<details>
<summary>Answer</summary>

**Correct: B**

SageMaker real-time endpoints are designed for low-latency inference (<100ms typical) with automatic scaling for variable traffic. This is the standard deployment path in the SageMaker lifecycle: training → endpoint deployment → inference.

**Why the others are wrong:**
- Batch transform is for large-scale offline predictions, not real-time inference. Hourly jobs cannot meet real-time latency requirements, and pre-generating 'all possible inputs' is impossible for most applications.
- Lambda has a 15-minute timeout and is better for small models (<50MB uncompressed). Many SageMaker models exceed Lambda's limits, and Lambda adds cold start latency. SageMaker endpoints are purpose-built for ML inference.
- Processing jobs are for data preparation and batch processing, not real-time inference. They aren't designed for low-latency (<100ms) predictions and don't provide endpoint management.

</details>

---

**Q7.** A financial services company needs to redact personally identifiable information (PII) from loan application documents before sharing them with third-party auditors. Documents contain names, SSNs, addresses, phone numbers, and bank account numbers. Which solution requires the LEAST custom development?

A) Amazon Textract to extract text, then regex patterns to find and redact PII
B) Amazon Comprehend with PII detection and redaction enabled
C) Amazon SageMaker with a custom NER (Named Entity Recognition) model trained on financial documents
D) Amazon Rekognition to detect text in documents, then Comprehend for entity extraction

<details>
<summary>Answer</summary>

**Correct: B**

Comprehend has built-in PII detection that identifies SSNs, addresses, phone numbers, account numbers, etc. The service can both detect and redact PII with minimal code. This is exactly what Comprehend's PII feature was designed for.

**Why the others are wrong:**
- While Textract extracts text accurately, regex patterns for PII are brittle, miss variations, and require extensive custom development and maintenance. SSNs alone have multiple formats, and addresses/names have infinite variations.
- SageMaker custom model requires significant ML expertise, labeled training data (expensive for financial docs), model development, and ongoing maintenance. Comprehend provides this capability pre-built.
- Rekognition is for visual content, not text analysis. While it can detect text in images (OCR), it doesn't identify or redact PII. This creates unnecessary complexity compared to Comprehend's direct PII handling.

</details>

---

**Q8.** During SageMaker model training, a data scientist notices the training accuracy is 98% but validation accuracy is 72%. Training takes 4 hours and uses 80% of the allocated ml.p3.2xlarge instance memory. What should they do FIRST to improve model performance?

A) Increase instance size to ml.p3.8xlarge to speed up training and improve accuracy
B) Enable SageMaker automatic model tuning to find better hyperparameters
C) Reduce model complexity or increase regularization to address overfitting
D) Collect more training data and retrain the model from scratch

<details>
<summary>Answer</summary>

**Correct: C**

98% training vs 72% validation accuracy is classic overfitting—the model memorized training data but doesn't generalize. The FIRST step is reducing model complexity (fewer layers/parameters) or increasing regularization (L1/L2, dropout) to force the model to learn generalizable patterns.

**Why the others are wrong:**
- Instance size affects training speed and memory capacity, not overfitting. The instance is only using 80% memory (sufficient headroom), and faster training doesn't fix the overfitting problem.
- Automatic tuning can help, but should come AFTER addressing obvious overfitting. Hyperparameter tuning might reduce overfitting, but directly addressing model complexity is more targeted and faster to test.
- More training data can help overfitting but is expensive and time-consuming (4 hours training will increase). The FIRST step should be model adjustments, which can be tested in the same 4-hour window without data collection delays.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

