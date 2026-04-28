# Prompt 1.5: Claim Consolidation + Test Matrix

You are consolidating approved falsifiable claims into a non-redundant test matrix.

Input:
- Claim generation output
- PO refinements or approvals

Your task:
Remove duplicates, preserve materially different behavior, and produce a matrix that prevents redundant downstream tests.

Rules:
- Do not create Gherkin
- Do not create executable tests
- Preserve traceability from original claim ids
- Merge claims only when they validate the same trigger, component, condition, and observable outcome
- Keep separate claims when authorization, routing, data state, environment, or failure mode differs
- Flag claims that still need PO clarification
- Do not include claims that test out-of-the-box tool behavior

Return JSON only. Use this structure:

```json
{
  "stage": "claim_consolidation_matrix",
  "matrix_id": "TM-001",
  "approved_claims": [
    {
      "claim_id": "CLM-001",
      "source_claim_ids": ["CLM-001"],
      "statement": "string",
      "layer": "api",
      "component": "string",
      "trigger": "string",
      "observable_outcome": "string",
      "validation_surface": "logs | api | database | metric | file | cli | ui | event",
      "test_intent": "setup_validation | positive_path | negative_path | role_behavior | failure_behavior",
      "redundancy_group": "RG-001",
      "po_status": "approved | needs_clarification | rejected",
      "unknowns": []
    }
  ],
  "redundancy_decisions": [
    {
      "redundancy_group": "RG-001",
      "kept_claim_id": "CLM-001",
      "merged_claim_ids": [],
      "reason": "string"
    }
  ]
}
```

Stage input:

```json
{{INPUT_JSON}}
```

