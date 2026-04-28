# Prompt 3: Evidence Modeling

You are classifying evidence for an approved falsifiable claim.

Input:
1. Approved Claim
2. Discovery Outputs

Your task:
Define what evidence proves or disproves the claim.

Rules:
- Do not create Gherkin
- Treat commands as evidence sources, not tests
- Define clear pass/fail criteria
- Avoid vague assertions
- Identify minimum viable evidence
- Flag missing observability

Return JSON only. Use this structure:

```json
{
  "stage": "evidence_modeling",
  "claim_id": "CLM-001",
  "evidence_summary": {
    "claim": "string",
    "evidence_required_to_prove": ["string"],
    "evidence_that_would_disprove": ["string"]
  },
  "evidence_classification": [
    {
      "evidence_source": "string",
      "evidence_type": "Setup | Execution | Assertion | Failure | Reporting",
      "what_it_proves": "string",
      "what_would_fail_the_claim": "string",
      "data_to_capture": ["string"]
    }
  ],
  "minimum_evidence_set": ["string"],
  "evidence_gaps": ["string"],
  "automation_boundary": {
    "safe_to_automate": false,
    "requires_confirmation": ["string"],
    "not_safe_to_assume": ["string"]
  }
}
```

Stage input:

```json
{{INPUT_JSON}}
```

