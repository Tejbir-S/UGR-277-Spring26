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
[2-3 sentences: Is your model better at precision or recall? Which errors did it
make?
What would improve it?]
---
## Part B: Generic vs Fine-Tuned Model Comparison
### Models Tested
1. **Generic:** distilbert-base-uncased-finetuned-sst-2-english (sentiment)
2. **Fine-Tuned A:** [model name] — [what it does]
3. **Fine-Tuned B:** [model name] — [what it does]
### Results
| Input | Generic Label (Score) | Fine-Tuned A Label (Score) | Fine-Tuned B Label
(Score) | Best Model |
|-------|-----------------------|-----------------------------|-------------------
--------|------------|
| Record 1 | | | | |
| Record 2 | | | | |
| Record 3 | | | | |
| Record 4 | | | | |
| Record 5 | | | | |
### Analysis
**Generic model strengths:** [When did the generic model perform well?]
**Generic model weaknesses:** [When did it fail or give low confidence?]
**Fine-tuned model advantage:** [Where did the fine-tuned models clearly
outperform the generic one?]
**Biggest surprise:** [What result did you not expect?]
### Recommended Model for My Capstone Component
**Component:** [Your capstone component name]
**Primary model:** [Name] — [Why this model for your task]
**Confidence threshold:** [What threshold would you use? Why?]
**Priority metric:** [Precision, Recall, or F1? Why does this matter for your
project?]
---
## Limitations & Next Steps
[What would you do differently with more data or time? Would you fine-tune your
own
model? What additional models would you test?]
