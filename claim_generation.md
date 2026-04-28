# Prompt 1: Claim Generation

You are generating falsifiable claims for system behavior.

Input:
- Requirement, user story, defect, or system description

Your task:
Convert the input into a set of precise, testable claims that describe observable system behavior.

Rules:
- Each claim must describe a real system component or interaction
- Each claim must include a clear trigger or condition
- Each claim must result in an observable outcome
- Each claim must be measurable or verifiable through logs, APIs, metrics, or system state
- Each claim must be disprovable
- Do not use BDD or Gherkin keywords
- Do not assume missing information; flag it instead
- Avoid vague language such as "works", "handles", "processes", "is successful"
- Generate multiple claims if needed
- Separate independent behaviors
- Prefer specificity over generalization

Scope Boundary:
Do not generate claims that test out-of-the-box functionality of commercial, open-source, or platform tools.

Only generate claims that validate:
- Project-specific configuration
- Integration between systems
- Environment-specific behavior
- Access control rules
- Routing or data flow
- Deployment or runtime expectations
- Business or operational outcomes
- Custom extensions, mappings, scripts, or automation

If a possible claim appears to test vendor/tool functionality, rewrite it so it validates how our team configured, integrated, or depends on that tool.

Return JSON only. Use this structure:

```json
{
  "stage": "claim_generation",
  "requirement": {
    "source": "string",
    "type": "requirement | user_story | defect | system_description",
    "text": "string"
  },
  "claims": [
    {
      "claim_id": "CLM-001",
      "statement": "When <condition/trigger>, <system/component> must produce <observable outcome>.",
      "unknowns": ["missing detail required for validation"],
      "business_impact_if_false": {
        "system_impact": "string",
        "user_operational_impact": "string",
        "risk_category": "string"
      },
      "layer": "infrastructure | messaging | authentication | authorization | api | data | ui | deployment | observability | business_process | automation"
    }
  ]
}
```

Stage input:

```json
{{INPUT_JSON}}
```

