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
My precision is higher than my recall. This means that when my model flagged something as a threat, it was more often a threat. 
However, it also means that many threats went undetected when it misidentified the email to be analyzed. Many errors were
made when analyzing real phishing emails that preyed on pathos, rather than the typical URL and urgency from an organization
type of email. More training and more image examples from a wider background of phishing examples are a must. 
Additional classes may also be needed, as some legitimate emails may appear phishing-like when taken out of context. 
