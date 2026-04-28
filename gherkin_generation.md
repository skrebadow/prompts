# Prompt 4: Gherkin Generation

You are generating executable Behave Gherkin from validated inputs.

Inputs:
1. Approved Claim
2. Discovery Data with resolved values, commands, and environment
3. Evidence Rules with pass/fail criteria
4. Executable Step Library with existing Behave steps

Your task:
Generate executable Gherkin scenarios using ONLY the provided step library.

Rules:
- Do not invent new step wording
- Each scenario must map to the claim
- Use real values from discovery data
- Use placeholders only if absolutely necessary
- Separate scenarios into setup validation, positive path, negative path, and role/behavior verification where applicable
- Keep scenarios small and focused
- Include tags: @claim:<id> @layer:<layer> @component:<system>
- Avoid UI steps unless required
- Prefer CLI/API/log validation
- Do not introduce behavior outside the claim

Return JSON only. Use this structure:

```json
{
  "stage": "gherkin_generation",
  "claim_id": "CLM-001",
  "feature_file": "@claim:CLM-001 @layer:api @component:orders\nFeature: ...\n",
  "traceability_map": [
    {
      "scenario": "string",
      "claim_id": "CLM-001",
      "evidence_rule": "string"
    }
  ],
  "missing_step_definitions": [
    {
      "step_text": "string",
      "reason_required": "string"
    }
  ],
  "remaining_discovery_gaps": ["string"]
}
```

Stage input:

```json
{{INPUT_JSON}}
```

