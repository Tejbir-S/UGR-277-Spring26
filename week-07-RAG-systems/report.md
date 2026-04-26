# Week 7: RAG Security Knowledge Assistant — Evaluation Report

## 1. Setup Summary
- **LLM:** llama-3.3-70b-versatile via Groq
- **Embeddings:** sentence-transformers/all-MiniLM-L6-v2 via HuggingFace
- **Vector Store:** In-Memory Vector Store
- **Documents loaded:** Brute force, Phishing, and Malware from MITRE ATT&CK

## 2. Test Results
| # | Question | Used Documents? | Quality | Notes |
|---|----------|----------------|---------|-------|
| 1 | How does phishing relate to initial access according to the MITRE documentation? | Yes | Good | N/A |
| 2 | What is the difference between spearphishing and mass malware spam campaigns? | Yes | Good | N/A |
| 3 | What role do malicious attachments and links play in the delivery of malware? | Yes | Good | N/A |
| 4 | What are the common methods used for brute force attacks according to the files? | Yes | Good | N/A |
| 5 | How do adversaries use 'thread hijacking' as a technique within phishing messages? | Yes | Good | N/A |

## 3. Edge Case Observations
- **Unrelated question:** When asked something off-topic, the Chatbot would explicitly state that it does not know the answer to such questions
  (the weather, politics, etc), and that you should ask it about cybersecurity-related questions instead.
- **Topic not in documents:** For topics not in the document, but related to cybersecurity, it would point out that it doesn't have direct
  knowledge of the matter, but does more broadly know how to answer them (DDoS attacks, latest CVEs, etc). The information given was accurate
  and not a hallucination. 

## 4. Reflection
- What surprised you about how RAG works?

  I was suprised by how much of the "knowledge" of the LLM is dependent on the retrieval method rather than just the model itself. Even when I
  encountered stream errors and utilized a manual RAG approach as well, the system was still able ground its answers in my specific data about
  brute force, phishing, and malware. RAG is quite flexible through a vector store, or simple text injection. 
- How could you improve this chatbot for real-world use?

  The most critical improvment would be moving from a "manual" text node or in-memory store to a persistent vector database. This would solve
  stream errors and allow the system to handle thousands of documents rather than just a few snippets. My models also struggled to recognize
  questions all the time, resulting in the user having to renter the question (usually 2 times) for it to answer accordingly.
- How might you use RAG in your capstone project?

  In my Financial Fraud Detection System, I can use RAG specifically within the Case Management portion. While the ingestion and detection
  layers flag the "what," RAG can help investigators with the "why." I would feed the RAG system SAR (suspicious activity report) filing
  guidelines and historical fraud patterns. WHen a case is generated, the investigator could ask the chatbot why it was flagged. The bot
  would then pull relevant internal protocols to help the investigator document the case more efficiently for the dashboard.
