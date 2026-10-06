# Conflicts

Claude creates a conflict record whenever implementation, testing, validation, deployment, Salesforce configuration, or a Git operation hits a meaningful failure.

## Structure

```
05 - Conflicts/
└── YYYY-MM-DD/
    └── CON-YYYY-MM-DD-###.md
```

- Create a dated folder only when a real conflict occurred on that date.
- **Never guess the root cause.** If it is not confirmed by evidence, write `NOT VERIFIED`.
- Copy exact error text. Remove any tokens or secrets first.

## Template

```markdown
# CON-YYYY-MM-DD-###

| Field | Value |
|---|---|
| Conflict ID | CON-YYYY-MM-DD-### |
| Date | YYYY-MM-DD |
| Related requirement / change | REQ-... / CHG-... |
| Affected component | |
| Status | Open / Investigating / Resolved / Accepted Risk |

## Problem

## Exact error
<verbatim error output>

## Evidence

## Investigation

## Verified root cause
<or NOT VERIFIED>

## Resolution

## Remaining risk
```
