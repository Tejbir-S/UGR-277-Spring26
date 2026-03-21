# Week 5: AutoML & No-Code Model Training
Trained a custom image classifier with Google Teachable Machine and compared
generic vs fine-tuned Hugging Face models for the Case Management component
of my group's Financial Fraud Detection System capstone project.

## Custom Model Training
- Built a [Phishing/Legitimate] image classifier with Teachable Machine
- Achieved 50% accuracy on 10 held-out test images
- Precision: 50% | Recall: 40% | F1: 44%

## Fine-Tuned Model Comparison
Compared 3 models (1 generic + 2 fine-tuned) on 5 test inputs:
- Generic: distilbert-sst-2 (sentiment)
- Fine-Tuned A: cybersectony/phishing-email-detection-distilbert_v2.4.1
- Fine-Tuned B: mrm8488/bert-tiny-finetuned-sms-spam-detection

## Finding
Recommended cybersectony/phishing-email-detection-distilbert_v2.4.1 for Case Management component because it had a higher accuracy of 
realizing potential threats; however, a model that is better equipped to deal with cybersecurity threat analysis would be preferred.
Fine-tuned models showed higher performance with more relevant labels/higher confidence/better handling of edge cases.
See `report.md` for full analysis.
