## Chapter 4: Domain 2 (Continued): Amazon Bedrock, PartyRock & Amazon Q — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Amazon Bedrock on-demand pricing for Titan Text G1 (input and output tokens)? | $0.00125 per 1K input tokens, $0.00625 per 1K output tokens. Exam tip: Input is 5× cheaper than output. Calculate both separately in cost questions. |
| 2 | Bedrock provisioned throughput break-even point? | ~1M tokens per hour. Below 1M/hour → use on-demand. Above 1M/hour → provisioned is cheaper. Provisioned costs $8.40/hour for 50 tokens/sec (180K tokens/hour capacity). |
| 3 | When to use Claude vs Titan vs Jurassic models in Bedrock? | Claude: complex reasoning, analysis. Titan: AWS-native, embeddings, basic text. Jurassic: long context (200K tokens). Exam tip: Reasoning task = Claude, Embeddings = Titan, Long docs = Jurassic. |
| 4 | What is Amazon Bedrock? | Managed service for foundation models via API. No infrastructure management, pay-per-use. Access to Claude, Titan, Jurassic, Llama 2. Exam tip: 'Managed' = no servers to provision. |
| 5 | Amazon Q Business vs Amazon Q Developer use cases? | Q Business: chat with enterprise data (S3, SharePoint, Salesforce), for ALL employees. Q Developer: code suggestions, CLI autocomplete, $19/month, for DEVELOPERS only. Exam tests which Q for which user. |
| 6 | What is PartyRock? | No-code GenAI app builder with drag-and-drop interface. Build and deploy apps without coding. Free tier available. Exam tip: No code + quick prototype = PartyRock. |
| 7 | What is Bedrock Studio? | No-code playground for testing prompts and comparing models. Used for experimentation before production. Exam tip: Studio = testing prompts, NOT deploying apps (that's PartyRock). |
| 8 | Amazon Q Developer pricing? | $19 per month per user. Includes IDE plugins (VS Code, IntelliJ), CLI autocomplete, code suggestions. Exam tip: Only Q service with explicit pricing mentioned in exam. |
| 9 | Which Bedrock model for AWS-native embeddings? | Amazon Titan Embeddings. Purpose-built for embedding generation, AWS-native integration. Exam tip: Embeddings question = always Titan, not Claude/Jurassic/Llama. |
| 10 | Data sources supported by Amazon Q Business? | S3, SharePoint, Salesforce, and 40+ enterprise connectors. Built-in security and access controls. Exam tip: Question mentions 'enterprise data across multiple sources' = Q Business. |
| 11 | Bedrock provisioned throughput cost for 50 tokens/sec? | $8.40 per hour. At 730 hours/month = $6,132/month for 50 tokens/sec capacity (180K tokens/hour). Exam tip: Calculate hourly cost × 730 hours for monthly. |
| 12 | AI21 Jurassic-2 maximum context length? | 200K tokens context window. Best for long document processing. Exam tip: Longest context window in Bedrock catalog = Jurassic. But reasoning = Claude, not Jurassic. |
