## Checkpoint 2 Readiness Assessment

### Status: NOT READY

### What's Working
- Transaction Ingestion workflow; producing records in Airtable
- Streamlit Dashboard; displays transaction data
- Test data exists

### Critical Gaps (must fix before Checkpoint 2)
- Gap 1: Data Contract Between Ingestion and Anomaly Detection [OWNER: Jack + Joshua]

  Document exactly what fields Transaction Ingestion writes to the Transaction Records table

  Confirm: Does it include recipient_id? If not where does Case Management get it
- Gap 2: Data Contract Between Anomaly Detection and Case Management [OWNER: Joshua + Tejbir]

  Joshua must document what fields Anomaly Detection will write (or update) when it flags a transaction
  (specifically what are anomaly_score, risk_level, and anomaly_reason)

  Decision: Does Joshua create Case Records directly, or does he update Transaction Records
  (status -> case_created) and I create the Case Record?

- Gap 3: Trigger Mechanism Between Anomaly Detection and Case Management [OWNER: Joshua]

  How does Case Management know when a new case-worthy transaction exists

- Gap 4: Case Management AI Logic Undefined [OWNER: Tejbir]
  Define the prompt for Groq that will generate alert_description

  Define how you compute priority-tier (high anomaly score + high risk level = critical priority?)

  Define escalation conditions (what triggers it)

  Define audit_trail structure (is it a JSON array of timestamped actions?)

- Gap 5: Case Management n&n Workflow Not Started [OWNER: Tejbir]

  Once data contract (Gap 2) is locked, build the n&n workflow (read from Transaction Records, call Groq API to generate alert_description,
  compute priority_tier and escalation_flag, write to fraud investigation Case Records)

- Gap 6: Handoff Testing Undefined [OWNER: All]

  No one has tested Ingestion -> Anomaly Detection yet

  No one has tested Anomaly Detection -> Case Management yet

### Schema Issues Found
- Transaction Records Table and Fruad Investigation Case Records Table have missing fields

### Recommended Fix Order
1. Identify what Anomaly Detection will do in its entirety
2. Define Case Management AI logic
3. Integration
4. Run a complete transaction through all 4 components

### Test Data Gaps
- Current state: Unknown 
