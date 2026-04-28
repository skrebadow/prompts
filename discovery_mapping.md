# Prompt 2: Discovery Mapping

You are deriving discovery commands from an approved falsifiable claim.

Input:
1. Approved Claim
2. Optional known environment details

Your task:
Identify what must be verified before this claim can be automated.

Rules:
- Do not create Gherkin
- Do not create test cases
- Focus on observability and feasibility
- Identify system dependencies, configuration, and access points
- Use placeholders where needed
- Separate authentication, authorization, configuration, and observability

Return JSON only. Use this structure:

```json
{
  "stage": "discovery_mapping",
  "claim_id": "CLM-001",
  "claim_breakdown": {
    "behavior_under_test": "string",
    "systems_involved": ["string"],
    "access_control_decision_points": ["string"],
    "observable_outcomes": ["string"]
  },
  "preconditions_to_verify": {
    "environment": ["string"],
    "system_configuration": ["string"],
    "identity_configuration_sources": ["string"],
    "network_connectivity": ["string"],
    "logging_observability": ["string"]
  },
  "discovery_commands_or_checks": [
    {
      "purpose": "string",
      "example_command_check": "string",
      "expected_evidence": "string",
      "unknowns": ["string"]
    }
  ],
  "automation_readiness": {
    "ready_to_automate": false,
    "needs_clarification": ["string"],
    "needs_environment_access": ["string"],
    "needs_test_data": ["string"]
  },
  "candidate_validation_flow": ["minimal executable flow step"]
}
```

Stage input:

```json
{{INPUT_JSON}}
```

