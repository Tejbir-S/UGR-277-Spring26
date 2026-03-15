# Model Comparison Report — Week 4
**Name:** Tejbir Singh

**Date:** 3/15/2025

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
**Where models agreed:** All models agreed on the 2 routine records that showed normal activity. The hugging face snetiment analyzer defined them as negative, the zero-shot classifier labeled them as routine activity, the NER model did not detect meaningful entities, and Groq concluded them as informational.

**Where models disagreed:** The sentiment model labaled every record as negative because it is designed to detect emotional tone rather than security risks; every technical log entry appear as negative regardless of being a threat or not. The zero-shot and Groq models were able to better interpret the meaning of the text and distinguish them as suspicious activity.  

**Most accurate model overall:** Based on the 5 records, Groq Llama 3 8B gave the most sensisble results. Groq was able to correctly separate high-risk events from routine activities and provide detailed reasoning for these classifications. 

**Fastest/most practical:** The Hugging Face models are always going to be faster and easier to integrate because of they require simple API calls and structured outputs. However, Groq's LLM provides detailed analysis, resulting at a higher computational call and a bit slower delivery. A real-world application would be able to utilize both to filter events that require deeper investigation.

## Recommended Models for My Capstone Component
**Component:** Case Management

**Primary model:** Groq Llama 3 8B — This model is able to display contextual undestanding and reasoning, making it well equipped for analyzing suspicious activity and giving a brief description that analysts can use to prioritize cases.

**Secondary model (if applicable):** Facebook/bartl-large-mnli — The zero-shot classifier is a quick filter to label events as routine activity or potential anomalies before deeper analysis is conducted.

**Rejected models and why:**
- Distilbert-base-uncased-finetuned-sst-2-english: A sentiment analyzer is simply incompatiable with the needs of cybersecurity analysis. Every record was labeled as negative regardless of the event presented.
- Dslim/bert-large-NER: The NER model extracted entities such as locations and organizations, but failed to present any useful information to determine what type of event had occurred. 

## Failure Cases and Limitations
One notable limitation was depicted by the sentiment analysis model, which failed to recognize obvious threats and labeled everything as negative. This illustrates that models trained for language may not perform well on speciailzied cybersecurity logs when attempting to identify fraudulent activity. The NER model also depicted limitations by extracting information that failed to be relevant to determining whether the activity presented was malicious. It is important that the AI model integrated in your workflow is aligned with the task and system you are attempting to create. 

## Next Steps
If more time was available, additional testing would include a larger dataset of varied cyebrsecurity events, rather than the limited five. Incorporating other models trained for anomaly detection would also be valuable to identify which would be best to incorporate. Another potential improvement is combining multiple models in a pieline, where lightweight classifers are able to filter routine events from potential anomalies, and an LLM can perform deeper analysis for what needs attention.
