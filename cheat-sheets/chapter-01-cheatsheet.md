# AIF-C01 Domain 1 Quick Reference

## AI/ML/DL Hierarchy (Exam Definitions)
| Term | Definition | Exam Key Point |
|------|------------|----------------|
| **AI** | Machines mimicking human intelligence | Broadest category—includes rule-based systems |
| **ML** | Systems that learn from data without explicit programming | Subset of AI—requires training data |
| **DL** | ML using neural networks with multiple layers | Subset of ML—for complex patterns (images, speech) |

## Supervised vs Unsupervised Learning
| Aspect | Supervised | Unsupervised |
|--------|------------|-------------|
| **Training Data** | Labeled (input + correct output) | Unlabeled (input only) |
| **Goal** | Predict outcomes for new data | Discover hidden patterns |
| **Exam Use Cases** | Classification, regression, churn prediction | Clustering, anomaly detection, customer segmentation |
| **Example Algorithms** | Linear regression, decision trees, XGBoost | K-means, Random Cut Forest, PCA |
| **Exam Trigger Words** | "historical outcomes", "labeled examples", "predict" | "no predefined categories", "discover groups", "segment" |

## SageMaker Training Job Lifecycle (HEAVILY TESTED)
1. **Data Preparation** → Store in S3 (input data channel)
2. **Training** → Choose algorithm, set hyperparameters, select instance type
3. **Model Artifacts** → Saved to S3 (model.tar.gz) automatically
4. **Deployment** → Create endpoint OR use batch transform
5. **Monitoring** → Track accuracy, latency, data drift

**Exam Gotcha**: Model artifacts save to S3 automatically. Deployment is a SEPARATE step—not automatic.

## AWS AI Service Selection Matrix (Choose Correct Service)
| Service | Input Type | Output | Exam Scenario Keywords |
|---------|-----------|--------|------------------------|
| **Comprehend** | Text | Sentiment, entities, PII, language | "analyze reviews", "extract entities", "redact PII", "detect language" |
| **Rekognition** | Image/Video | Objects, faces, text-in-image, content moderation | "detect faces", "identify objects", "blur faces", "inappropriate content" |
| **Transcribe** | Audio | Text transcript | "call recordings", "speech to text", "meeting transcripts", "speaker identification" |
| **Textract** | Documents | Extracted text, tables, forms | "extract from PDFs", "read forms", "parse tables from scans" |

## Comprehend Key Features
- **Sentiment Analysis**: Positive/Negative/Neutral/Mixed (0-1 confidence scores)
- **Entity Recognition**: People, places, organizations, dates (built-in, no training)
- **PII Detection**: SSN, credit cards, addresses, phone, email, names (redaction available)
- **Custom Classification**: Train custom models (requires 50+ labeled docs per class)
- **Exam Trap**: Comprehend does NOT process audio—use Transcribe first

## Rekognition Limits & Features
| Feature | Limit/Detail | Exam Note |
|---------|--------------|----------|
| **Image Size** | Max 15MB (S3), 5MB (bytes) | Exam asks "which format" → use S3 for large images |
| **Custom Labels Training** | Min 10 images/label (recommend 50+) | "Only 5 samples" → insufficient |
| **Face Detection** | Max 100 faces per image | Built-in, no training needed |
| **Video Processing** | Async only (not real-time) | Returns JobId, poll for results |
| **Content Moderation** | Detects suggestive, violence, drugs | Use confidence threshold (80% typical) |

## Transcribe Key Points
- **Custom Vocabulary**: 50,000 words max (for technical terms, product names)
- **Speaker Identification**: Max 10 speakers (diarization)
- **Medical Vocabulary**: Transcribe Medical (PHI-aware, HIPAA eligible)
- **Language Support**: 30+ languages (auto-detect or specify)
- **Exam Scenario**: Call center → custom vocab + speaker ID

## SageMaker Endpoint Deployment
| Aspect | Detail | Exam Key |
|--------|--------|----------|
| **Instance Types** | ml.t2.medium to ml.p3.16xlarge | Right-size for latency/cost |
| **Autoscaling** | Based on invocations/instance | Default target: 1000 req/min/instance |
| **Real-time vs Batch** | Real-time = <100ms latency; Batch = large-scale offline | Exam asks about latency requirements |
| **Multi-Model Endpoints** | Host multiple models on 1 endpoint (cost savings) | Use when models share framework/instance |

## Common Exam Traps
1. **Service Confusion**: Image of text → Textract (extract) + Comprehend (analyze), NOT Rekognition
2. **Training vs Inference**: "After training completes" → artifacts save to S3, NOT automatic deployment
3. **Supervised Learning Requirement**: Labeled data is MANDATORY. "No labels" → must use unsupervised
4. **Overfitting**: High training accuracy + low validation accuracy → reduce complexity FIRST, not more data
5. **Rekognition Custom Labels**: Needs 10+ images minimum. "5 samples" → insufficient

## ML Lifecycle Monitoring (Often Forgotten)
- **Model Monitor**: Detects data drift, quality issues
- **Retraining Triggers**: Accuracy drop, data drift detected
- **Exam Question**: "What happens after deployment?" → Answer includes MONITORING, not just serving predictions
