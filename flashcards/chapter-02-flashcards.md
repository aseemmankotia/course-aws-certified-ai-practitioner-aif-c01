## Chapter 2: Domain 1 (Continued): Vision, Speech & NLP Services Deep Dive — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Amazon Polly: Standard vs Neural voice pricing | Standard: $4 per 1M characters Neural: $16 per 1M characters (4× cost) Neural = more natural/human-like quality Exam tip: Neural always recommended for customer-facing applications despite cost |
| 2 | Amazon Lex: Cost per request | $0.004 per text or voice request No difference between text and voice pricing Exam tip: Voice requests don't cost extra - common trap answer |
| 3 | Amazon Personalize: Minimum dataset requirements | Minimum 25 items (products/content) Minimum 1,000 interactions (views/purchases/clicks) Exam tip: NOT 1 million interactions - that's a common wrong answer |
| 4 | Amazon Personalize: USER_PERSONALIZATION vs RELATED_ITEMS | USER_PERSONALIZATION: Recommendations based on user behavior ('You might like...') RELATED_ITEMS: Similar items ('Customers also bought...') Exam tip: 'Also bought' = RELATED_ITEMS, 'For you' = USER_PERSONALIZATION |
| 5 | Amazon Translate: Pricing and language support | $15 per 1 million characters translated 75 languages supported Same cost for real-time vs batch Exam tip: No premium for real-time translation |
| 6 | Amazon Forecast: Minimum data requirement | Minimum 300 data points per time series No minimum time duration requirement Cost: $0.60 per 1,000 predictions Exam tip: 300+ points can be achieved in weeks with frequent data (hourly/daily) |
| 7 | Amazon Lex: Intent, Slot, Fulfillment | Intent: What user wants to do Slot: Information needed (parameters) Fulfillment: Lambda function that executes action Exam tip: Fulfillment always requires Lambda integration |
| 8 | Comprehend vs Textract vs Translate | Comprehend: Entity extraction, sentiment (analyzes TEXT) Textract: OCR, extract text from images/PDFs Translate: Language translation Exam tip: Textract extracts text, Comprehend analyzes it |
| 9 | Amazon Polly: SSML usage | SSML = Speech Synthesis Markup Language Controls pronunciation, emphasis, pauses, pitch Works with both Standard and Neural voices Exam tip: SSML improves pronunciation but doesn't change voice quality Standard→Neural |
| 10 | Amazon Lex: Slot types | Built-in slots: AMAZON.DATE, AMAZON.TIME, AMAZON.NUMBER, etc. Custom slots: Your defined values (e.g., 'morning\|afternoon\|evening') Exam tip: Use custom slots for specific enumerated values, built-in for standard data types |
| 11 | Amazon Translate: Custom terminology | Custom terminology: Define specific translations for brand names, technical terms No additional cost (free feature) Improves translation accuracy for domain-specific content Exam tip: Use for brand consistency, doesn't reduce character costs |
| 12 | Amazon Personalize: Campaign types (all three) | USER_PERSONALIZATION: Individual recommendations RELATED_ITEMS: Similar/related items PERSONALIZED_RANKING: Reorder existing list by relevance Exam tip: Three distinct use cases - pick based on 'recommend new' vs 'find similar' vs 'reorder existing' |
