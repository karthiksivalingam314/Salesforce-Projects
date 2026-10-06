# Deployment

Claude creates a deployment record whenever a Salesforce deployment or validation (check-only) actually runs.

## Structure

```
Deployment/
└── YYYY-MM-DD/
    └── DEP-YYYY-MM-DD-###.md
```

- Create a dated folder only when a real deployment or validation occurred on that date.
- **Never claim success without Salesforce evidence** (deploy ID and status from the CLI or the org).
- Target only `Fullsandox` (`TVM_WORKING_ORG`). **Production deployment remains human-controlled.** Claude does not deploy to Production.

## Template

```markdown
# DEP-YYYY-MM-DD-###

| Field | Value |
|---|---|
| Deployment ID | DEP-YYYY-MM-DD-### |
| Salesforce deploy ID | 0Af... |
| Date | YYYY-MM-DD |
| Target org | Fullsandox / 00DVa000006Eh6TMAS |
| Type | Validation (check-only) / Deployment |
| Related | REQ-... / CHG-... |
| Final status | Succeeded / Failed / Partially Succeeded / Cancelled |

## Components
| Type | API name |
|---|---|

## Pre-deployment checks
- [ ] Target org verified (alias, username, Org ID, instance URL)
- [ ] Impact analysis completed
- [ ] Local tests/lint run

## Validation

## Tests
<test level, classes run, pass/fail, coverage>

## Deployment result
<verbatim status summary>

## Post-deployment verification

## Rollback / recovery plan

## Final status
```
