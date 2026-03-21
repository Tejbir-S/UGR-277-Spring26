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
**Generic model strengths:** The generic sentiment model performed consistently in terms of confidence, often producing very high scores across all inputs. The model is effective at detecting emotional tone, especially phishing emails that will rely on urgency, fear, or excitement. Phishing emails that use exaggerated language will result in the model responding with high confidence. 

**Generic model weaknesses:** This model fails conceptually because it is not designed for phishing detection. Because the model reads sentiment rather than intent, it can easily misinterpret legitimate urgent emails as malicious, or fail to detect well-crafted emails that use neutral language. The scores and classifications are both misleading because it doesn't refelct the task meant to be done. 

**Fine-tuned model advantage:** Fine-Tuned model A consistently outperformed both the generic and spam model because it is specifically trained to read phishing-related patterns such as suspicious URLs, impersonation attempts, and deceptive structures. 

**Biggest surprise:** The biggest surprise was how confident the generic model was despite being poorly suited for the task. These scores ere very close to those of Fine-Tuned model A, which would easily mislead someone into believing the information provided is reliable.

### Recommended Model for My Capstone Component
**Component:** Case Management

**Primary model:** cybersectony/phishing-email-detection-distilbert_v2.4.1 — This model is the best fit because it is trained for phishing detection, aligning directly with the goals of identifying fraudulent communication in case management workflows. Its consistently high confidence and task-specific design make it more reliable than the other two models. However, it should be noted that model that can encompass cybersecurity reports for anomalous activity would be better suited for the project. 

**Confidence threshold:** A high threshold of 0.90 is necessary to reduce false positives in a case management sysem. Flagged cases require manual review or escalation, so maintaing high confidence ensures that resources are not wasted on benign inputs. 

**Priority metric:** Recall will be the priority metric because missing a phishing attempt is more dangerous than incorrectly flagging legitimate messages. Prioritizing recall ensures that as many potential threats as possible are captured, even if this includes in false positives. 

---
## Limitations & Next Steps
This current evaluation is limited by a small dataset and narrow range of test inputs, which does not fully represent real-world phishing attempts. More time and data would allow me to expand the dataset to include diverse phishing strategies and modern attack methods. It should also be considered that I may need to focus on fine-tuning the model for financial fraud scenarios to be more effective in my capstone project. 
