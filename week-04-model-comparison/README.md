# Week 4: Model Comparison
Tested 4 AI models on 5 cybersecurity text samples to evaluate their suitability for the case management component of my team's capstone project: a 
Finanacial Fraud Detection System.

## Models Tested
- HF Sentiment (distilbert-sst-2)
- HF Zero-Shot (bart-large-mnli)
- HF NER (bert-large-NER)
- Groq Llama 3 8B

## Finding
Recommended Groq Llama 3 8B for the case management component because it is able to digest and understand the complex instructions needed to  transform a 
flagged transaction into a structured investigation workflow; Groq is the only one that would be able to reason through established thresholds, while the 
rest are built for narrow tasks.

See `report.md` for full analysis.
