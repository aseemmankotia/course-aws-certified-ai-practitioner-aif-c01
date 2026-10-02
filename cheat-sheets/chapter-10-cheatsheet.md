# AIF-C01 Final Exam Cheatsheet

## Exam Format
- **Total Questions**: 65 (50 scored, 15 unscored pretest)
- **Time**: 90 minutes (1.38 min/question average)
- **Passing Score**: 700/1000 (scaled)
- **Question Types**: 40% scenario, 30% service selection, 20% configuration, 10% conceptual

## Time Management Strategy
1. **First Pass**: 1.5 min max per question
2. **Flag Hard Questions**: Mark 15-20 for review, don't spend >2 min
3. **Complete All Questions**: Get through all 65 first
4. **Final 15 Minutes**: Review flagged questions only
5. **Trust First Instinct**: Change answer only if you spot clear error

## Elimination Technique
1. **Cross Out 2**: Usually 2 answers are obviously wrong (wrong service, too expensive, doesn't meet requirement)
2. **Choose Between 2**: Look for keyword matches
3. **Common Wrong Answers**: Overengineered solutions, deprecated services, wrong service category

## Critical Keyword Map
| Keyword in Question | Correct Service/Approach |
|---------------------|-------------------------|
| Frequently changing data | RAG (not fine-tuning) |
| Change model style/tone | Fine-tuning (not RAG) |
| Highly available | Multi-AZ, multi-region |
| Cost-optimized | On-demand pricing, async APIs, right-sizing |
| Real-time | Synchronous APIs, provisioned throughput |
| Scanned documents/PDFs | Textract → Comprehend (order matters) |
| Current information | RAG with live data source |
| Industry jargon/terminology | Custom language model (CLM) |

## Service Comparison Quick Reference

### Bedrock vs SageMaker
- **Bedrock**: Pre-trained FMs, API access, no infra, quick start, prompt engineering
- **SageMaker**: Custom training, full ML pipeline, bring your own model, fine-grained control
- **Exam Tip**: "No ML expertise" or "quick deployment" → Bedrock

### Comprehend vs Textract
- **Comprehend**: NLP on TEXT (sentiment, entities, PII, language)
- **Textract**: Extract text from IMAGES/PDFs (OCR, forms, tables)
- **Exam Tip**: PDF/scanned docs → Textract FIRST, then Comprehend

### Kendra vs Q Business
- **Kendra**: Enterprise search, RAG data source, custom index
- **Q Business**: Conversational AI, integrates multiple sources, chat interface
- **Exam Tip**: "Search" or "retrieve documents" → Kendra. "Conversational" → Q Business

### Rekognition vs SageMaker (Vision)
- **Rekognition**: Pre-built vision APIs (labels, faces, text, custom labels)
- **SageMaker**: Custom vision models, full control, complex architectures
- **Exam Tip**: Standard use cases → Rekognition. Unique requirements → SageMaker

## Textract APIs
| API | Use Case | Cost | Speed |
|-----|----------|------|-------|
| Sync | Real-time, single doc | $1.80/1K pages | <1 sec |
| Async | Batch, multi-page | $1.50/1K pages | Minutes |
| **Exam Tip**: "Cost-optimized" + no real-time = async

## Transcribe Options
| Feature | Use Case |
|---------|----------|
| Custom Vocabulary | Brand names, acronyms (up to 256KB) |
| Custom Language Model | Industry jargon, context-aware |
| **Exam Tip**: "Terminology" or "context" → CLM. "Spelling" → vocabulary

## Pricing Math Shortcuts

### Provisioned vs On-Demand Break-Even
1. Calculate on-demand cost: (requests × $/request)
2. Calculate provisioned cost: ($/hour × hours in period)
3. Consider **utilization**: provisioned only makes sense if used >70% of time
4. **Exam Trap**: Don't just compare unit costs - factor in actual usage pattern

### Token Cost Calculation (Bedrock)
- Formula: (input_tokens × input_$/1K + output_tokens × output_$/1K) / 1000 × total_items
- **Exam Tip**: When quality is equal across models, always choose cheapest

## Common Exam Traps
1. **Imbalanced Dataset**: 99% accuracy but predicts all one class → Use class weighting/focal loss (NOT more epochs)
2. **RAG vs Fine-Tuning**: Frequently changing data = RAG. Behavior change = fine-tuning
3. **Provisioned Throughput**: Only cost-effective for continuous high-volume, not batch
4. **Service Selection**: Don't choose specialized service (like Comprehend Medical) for general use case
5. **Async vs Sync**: Async is cheaper - use unless real-time explicitly required

## Domain Weights
- **Domain 1** (AI/ML Fundamentals): 20%
- **Domain 2** (Generative AI): 24%
- **Domain 3** (FM Applications): 28%
- **Domain 4** (Responsible AI): 14%
- **Domain 5** (Security): 14%

## Final Review Checklist
- [ ] Flagged questions reviewed
- [ ] No questions left blank
- [ ] Checked for keyword matches in answers
- [ ] Verified math on cost calculations
- [ ] Trusted first instinct unless clear error found
