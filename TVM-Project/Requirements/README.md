# Requirements

Claude creates a requirement record automatically whenever the user gives a new TVM requirement, before implementation starts.

## Structure

```
Requirements/
└── YYYY-MM-DD/
    └── REQ-YYYY-MM-DD-###.md
```

- Create a dated folder only when there is a real requirement for that date.
- Number `###` sequentially per day (001, 002, ...).
- Never invent missing information. Write `NOT PROVIDED`, `UNKNOWN`, or list it under Open questions.

## Template

```markdown
# REQ-YYYY-MM-DD-###

| Field | Value |
|---|---|
| Requirement ID | REQ-YYYY-MM-DD-### |
| Date | YYYY-MM-DD |
| Intended Salesforce org | Fullsandox (TVM_WORKING_ORG) |
| Status | New / In Analysis / Approved / In Progress / Implemented / Blocked / Cancelled |

## Requirement
<as provided by the user>

## Business purpose
<as provided, or NOT PROVIDED>

## Scope

## Out of scope

## Acceptance criteria
- [ ] ...

## Affected components
<verified API names only, or UNKNOWN pending inspection>

## Dependencies

## Open questions

## Related records
- Changes: CHG-...
- Conflicts: CON-...
- Deployments: DEP-...
```
