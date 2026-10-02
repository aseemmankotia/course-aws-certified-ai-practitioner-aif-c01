# Chapter 2: Vision, Speech & NLP Services Deep Dive - Quick Reference

## Amazon Polly
| Feature | Standard Voices | Neural Voices |
|---------|----------------|---------------|
| **Pricing** | $4 per 1M chars | $16 per 1M chars |
| **Quality** | Robotic/synthetic | Natural/human-like |
| **Use Case** | Internal apps, IVR | Customer-facing, training |
| **SSML Support** | ✓ Yes | ✓ Yes |

**SSML**: Control pronunciation, pauses, pitch - works with both voice types
**Exam Trap**: Neural costs 4× more but required for "natural-sounding" requirements

## Amazon Translate
- **Pricing**: $15 per 1M characters (same for real-time & batch)
- **Languages**: 75 supported languages
- **Custom Terminology**: FREE - define brand/technical term translations
- **Exam Trap**: No premium for real-time translation

## Amazon Lex (Chatbot/Voice Assistant)
| Component | Purpose | Example |
|-----------|---------|----------|
| **Intent** | What user wants | BookAppointment, OrderFood |
| **Slot** | Required info | Date, Time, Location |
| **Fulfillment** | Action execution | Lambda function |

**Pricing**: $0.004 per request (text OR voice - same price)
**Slot Types**: Built-in (AMAZON.DATE) vs Custom (morning\|afternoon\|evening)
**Exam Trap**: Voice requests don't cost extra

## Amazon Personalize
| Campaign Type | Use Case | Example |
|---------------|----------|----------|
| **USER_PERSONALIZATION** | Individual recommendations | "Recommended for you" |
| **RELATED_ITEMS** | Similar items | "Customers also bought" |
| **PERSONALIZED_RANKING** | Reorder existing list | Prioritize search results |

**Minimums**:
- 25 items (products/content)
- 1,000 interactions (NOT 1 million!)

**Exam Traps**:
- "Also bought" = RELATED_ITEMS (not USER_PERSONALIZATION)
- 1K interactions minimum (commonly confused with 1M)

## Amazon Forecast
- **Purpose**: Time-series predictions (inventory, demand)
- **Minimum Data**: 300+ historical data points
- **Pricing**: $0.60 per 1,000 predictions
- **No minimum time range** - 300 points can be days/weeks with frequent collection

## Service Comparison Matrix
| Service | Primary Function | Input | Output |
|---------|-----------------|-------|--------|
| **Comprehend** | NLP/Entity extraction | Text | Entities, sentiment, syntax |
| **Textract** | OCR | Images/PDFs | Extracted text, tables, forms |
| **Translate** | Language conversion | Text (one language) | Text (another language) |
| **Polly** | Text-to-speech | Text | Audio (speech) |
| **Transcribe** | Speech-to-text | Audio | Text |
| **Lex** | Conversational AI | Text/Voice | Intent, slots, response |

## Exam Quick Checks
✓ **Polly Neural vs Standard**: Quality vs Cost tradeoff (4× cost for natural sound)
✓ **Lex Fulfillment**: Always requires Lambda function integration
✓ **Personalize minimums**: 25 items + 1K interactions (NOT 1M)
✓ **Translate pricing**: $15/1M chars, no real-time premium
✓ **Service selection**: Textract (OCR) → Comprehend (analyze) → Translate (language)
✓ **Forecast**: 300+ data points, $0.60/1K predictions
✓ **Lex pricing**: $0.004/request (text = voice)

## Common Exam Traps
1. Confusing 1K vs 1M minimums (Personalize: 1K interactions)
2. Thinking Neural Polly costs same as Standard ($4 vs $16)
3. Assuming real-time Translate costs more (same $15/1M)
4. Using Comprehend for OCR (it's Textract)
5. Thinking Lex voice costs more than text (same $0.004)
6. Wrong Personalize campaign ("also bought" = RELATED_ITEMS)
7. SSML changes Standard to Neural quality (it doesn't)
