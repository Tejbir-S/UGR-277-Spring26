# Week 5 Report: AutoML Training & Fine-Tuned Model Evaluation
**Name:** Tejbir Singh

**Date:** 3/21/2026

**Capstone Project:** Financial Fraud Detection System

**My Component:** Case Management

## Part A: Teachable Machine Training
### Training Setup
- **Task:** Phishing vs Legitimate email screenshot classification
- **Training images per class:** 20-30
- **Test images per class:** 5
- **Total training time:** ~16 seconds

### Test Results
| # | Actual Class | Predicted Class | Confidence | Correct? |
|---|--------------|-----------------|------------|----------|
| 1 | Phishing | Phishing | 79% | Yes |
| 2 | Phishing | Legitimate | 96% | No |
| 3 | Phishing | Phishing | 94% | Yes |
| 4 | Phishing | Legitimate | 99% | No |
| 5 | Phishing | Legitimate | 84% | No |
| 6 | Legitimate | Phishing | 81% | No |
| 7 | Legitimate | Legitimate | 80% | Yes |
| 8 | Legitimate | Legitimate | 100% | Yes |
| 9 | Legitimate | Phishing | 99% | No |
| 10 | Legitimate | Legitimate | 96% | Yes |

### Confusion Matrix
| | Predicted: Phishing | Predicted: Legitimate |
|---|---|---|
| **Actual: Phishing** | TP = 2 | FN = 3 |
| **Actual: Legitimate** | FP = 2 | TN = 3 |

### Calculated Metrics
- **Accuracy:** 50%
- **Precision:** 50%
- **Recall:** 40%
- **F1 Score:** 44%

### Interpretation
My precision is higher than my recall. This means that when my model flagged something as a threat, it was more often a threat. However, it also means that many threats went undetected when it misidentified the email to be analyzed. Many errors were made when analyzing real phishing emails that preyed on pathos, rather than the typical URL and urgency from an organization type of email. More training and more image examples from a wider background of phishing examples are a must. Additional classes may also be needed, as some legitimate emails may appear phishing-like when taken out of context.

## Part B: Generic vs Fine-Tuned Model Comparison
### Models Tested
1. **Generic:** distilbert-base-uncased-finetuned-sst-2-english (sentiment)
2. **Fine-Tuned A:** cybersectony/phishing-email-detection-distilbert_v2.4.1 — This model has been fine-tuned for multilabel classification of Emails and URLs as safe or potentially phishing.
3. **Fine-Tuned B:** mrm8488/bert-tiny-finetuned-sms-spam-detection — This model detects spam emails.

### Results
| Input | Generic Label (Score) | Fine-Tuned A Label (Score) | Fine-Tuned B Label(Score) | Best Model |
|-------|-----------------------|-----------------------------|---------------------------|------------|
| Record 1 | 0.9961 | 0.9989 | 0.7045 | Fine-Tuned A |
| Record 2 | 0.9986 | 1.0000 | 0.5376 | Fine-Tuned A |
| Record 3 | 0.9959 | 0.9997 | 0.7415 | Fine-Tuned A |
| Record 4 | 0.9994 | 0.9471 | 0.5719 | Fine-Tuned A |
| Record 5 | 0.9880 | 0.9999 | 0.8388 | Fine-Tuned A |

### Analysis
**Generic model strengths:** [When did the generic model perform well?]
**Generic model weaknesses:** [When did it fail or give low confidence?]
**Fine-tuned model advantage:** [Where did the fine-tuned models clearly
outperform the generic one?]
**Biggest surprise:** [What result did you not expect?]

### Recommended Model for My Capstone Component
**Component:** Case Management

**Primary model:** [Name] — [Why this model for your task]
**Confidence threshold:** [What threshold would you use? Why?]
**Priority metric:** [Precision, Recall, or F1? Why does this matter for your
project?]
---
## Limitations & Next Steps
[What would you do differently with more data or time? Would you fine-tune your
own
model? What additional models would you test?]
