# Chapter 4: Amazon Bedrock, PartyRock & Amazon Q

## Amazon Bedrock Core Concepts

| Feature | Details |
|---------|----------|
| **What it is** | Managed service for foundation models via API |
| **Key benefit** | No infrastructure to manage, pay-per-use |
| **Access method** | API calls (REST/SDK) |
| **Available models** | Claude, Titan, Jurassic, Llama 2, Stable Diffusion |

## Bedrock Pricing Models

| Model | When to Use | Cost Details |
|-------|-------------|---------------|
| **On-Demand** | < 1M tokens/hour | Titan Text G1: $0.00125/1K input, $0.00625/1K output |
| **Provisioned Throughput** | > 1M tokens/hour | $8.40/hour for 50 tokens/sec (180K tokens/hour capacity) |
| **Break-even** | ~1M tokens/hour | Below = on-demand cheaper, Above = provisioned cheaper |

### Cost Calculation Examples
```
On-demand example:
- 500K conversations/month × 2K tokens each = 1B tokens/month
- 500M input × $0.00125/1K = $625
- 500M output × $0.00625/1K = $3,125
- Total: $3,750/month

Provisioned example:
- $8.40/hour × 730 hours = $6,132/month (base unit)
- Scales with required tokens/sec capacity
```

## Bedrock Model Catalog (HEAVILY TESTED)

| Model | Primary Use Case | Key Strengths | Exam Tip |
|-------|------------------|---------------|----------|
| **Claude (Anthropic)** | Complex reasoning, analysis | Best for logic, legal, medical | Reasoning task = Claude |
| **Titan (Amazon)** | Embeddings, basic text | AWS-native, cost-effective | Embeddings = always Titan |
| **Jurassic-2 (AI21)** | Long context processing | 200K token context window | Longest context in catalog |
| **Llama 2 (Meta)** | General-purpose | Open-source, flexible | General use, not specialized |

## Bedrock Studio

| Feature | Purpose |
|---------|----------|
| **What** | No-code playground for prompt testing |
| **Use for** | Experimenting with prompts before production |
| **Capabilities** | Test different models, compare outputs |
| **NOT for** | Deploying applications (use PartyRock) |

## PartyRock

| Feature | Details |
|---------|----------|
| **Purpose** | Build GenAI apps without code |
| **Interface** | Drag-and-drop app builder |
| **Deployment** | Can deploy web apps directly |
| **Pricing** | Free tier available |
| **Exam scenario** | Non-technical team + quick prototype = PartyRock |

## Amazon Q Services (HEAVILY TESTED)

### Amazon Q Business
| Feature | Details |
|---------|----------|
| **Purpose** | Chat with enterprise data |
| **Data sources** | S3, SharePoint, Salesforce, 40+ connectors |
| **Users** | All employees (not just developers) |
| **Use case** | Search company policies, compliance docs, guidelines |
| **Security** | Built-in access controls, respects source permissions |

### Amazon Q Developer
| Feature | Details |
|---------|----------|
| **Purpose** | Code suggestions and CLI autocomplete |
| **Pricing** | $19/month per user |
| **IDE support** | VS Code, IntelliJ, JetBrains |
| **Features** | Inline code completion, CLI command suggestions |
| **Users** | Developers only |

## Exam Traps & Gotchas

### Pricing Calculations
- **Trap**: Forgetting input tokens are 5× cheaper than output
- **Fix**: Always calculate input and output separately
- **Trap**: Not converting tokens/hour to monthly cost
- **Fix**: Multiply hourly provisioned cost by 730 hours

### Model Selection
- **Trap**: Choosing Jurassic for reasoning (it's for long context)
- **Fix**: Reasoning = Claude, Long context = Jurassic
- **Trap**: Not using Titan for embeddings
- **Fix**: Embeddings question = always Titan

### Q Services Confusion
- **Trap**: Using Q Developer for enterprise data chat
- **Fix**: Q Business = data chat, Q Developer = code only
- **Trap**: Thinking Q Business is only for developers
- **Fix**: Q Business = ALL employees, Q Developer = devs only

### Studio vs PartyRock
- **Trap**: Using Studio to deploy apps
- **Fix**: Studio = test prompts, PartyRock = deploy apps

## Quick Decision Tree

**Need to build an app without code?**
→ PartyRock

**Need to test prompts without code?**
→ Bedrock Studio

**Need embeddings?**
→ Titan

**Need complex reasoning?**
→ Claude

**Need to process 100-page documents?**
→ Jurassic (200K context)

**Developers need code help?**
→ Q Developer ($19/month)

**Employees need to search company data?**
→ Q Business

**Usage < 1M tokens/hour?**
→ On-demand pricing

**Usage > 1M tokens/hour?**
→ Provisioned throughput

## Key Numbers to Memorize

- Titan on-demand input: **$0.00125/1K tokens**
- Titan on-demand output: **$0.00625/1K tokens**
- Provisioned throughput: **$8.40/hour** for 50 tokens/sec
- Break-even point: **~1M tokens/hour**
- Q Developer: **$19/month per user**
- Jurassic context: **200K tokens**
- Provisioned capacity: **50 tokens/sec = 180K tokens/hour**
