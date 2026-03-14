# Model Comparison Report — Week 4
**Name:** Tejbir Singh

**Date:** 3/14/2025

**Capstone Project:** Financial Fraud Detection System

**My Component:** Case Management

## Test Setup
**Input dataset:** 5 cybersecurity text samples covering:
- 2 clearly concerning/high-severity records
- 1 ambiguous/edge case record
- 2 routine/benign records

**Models tested:**
1. distilbert-base-uncased-finetuned-sst-2-english (sentiment)
2. facebook/bart-large-mnli (zero-shot classification)
3. dslim/bert-large-NER (named entity recognition)
4. Groq Llama 3 8B (LLM classification)

**Evaluation criteria:** label accuracy, confidence score, speed, ease of integration in n8n

## Results Summary
| Record | Sentiment | Zero-Shot | NER Entities | Groq |
|--------|-----------|-----------|-------------|------|
| 1 | NEGATIVE (0.9961) | possible anomaly | {"entity_group":"LOC","score":0.9996966,"word":"Moscow","start":50,"end":56} | HIGH |
| 2 | NEGATIVE (0.9986) | routine activity | {} | INFORMATIONAL |
| 3 | NEGATIVE (0.9959) | possible anomaly | {"entity_group":"ORG","score":0.99667954,"word":"Amazon","start":28,"end":34} | HIGH |
| 4 | NEGATIVE (0.9994) | possible anomaly | {"entity_group":"MISC","score":0.9697967,"word":"SS","start":16,"end":18} | HIGH |
| 5 | NEGATIVE (0.9880) | routine activity | {} | INFORMATIONAL |

## Analysis
**Where models agreed:** All models agreed on the 2 routine records that showed normal activity.

**Where models disagreed:** [Which records got different classifications? What might explain the difference?] 

**Most accurate model overall:** Based on the 5 records, Groq Llama 3 8B gave the most sensisble results.

**Fastest/most practical:** [Which model would be easiest to use at scale?]

## Recommended Models for My Capstone Component
**Component:** Case Management

**Primary model:** Groq Llama 3 8B — [1 sentence: why this one for your task]

**Secondary model (if applicable):** [Name] — [1 sentence: what role it plays]

**Rejected models and why:**
- [Model name]: [1-2 sentences on why it's not the right fit]
- [Model name]: [1-2 sentences on why it's not the right fit]

## Failure Cases and Limitations
[Describe at least one case where a model gave a wrong or surprising result.
What does this tell you about using this model in production?]

## Next Steps
[What would you test next if you had more time? More records? Different labels?
A different model you didn't test this week?]
