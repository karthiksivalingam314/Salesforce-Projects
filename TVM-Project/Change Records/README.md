# Change Records

Claude creates a change record whenever it actually implements a change. Planned or proposed changes do not get a record.

## Structure

```
Change Records/
└── YYYY-MM-DD/
    └── CHG-YYYY-MM-DD-###.md
```

- Create a dated folder only when a real change occurred on that date.
- Record only facts that actually occurred. Put anything unconfirmed under **Unverified items**.

## Template

```markdown
# CHG-YYYY-MM-DD-###

| Field | Value |
|---|---|
| Change ID | CHG-YYYY-MM-DD-### |
| Related requirement | REQ-YYYY-MM-DD-### |
| Date | YYYY-MM-DD |
| Salesforce org | Fullsandox / Org ID 00DVa000006Eh6TMAS (verified at time of change) |

## Reason

## Before state

## After state

## Components changed
| Type | API name | Action (created/modified/deleted) |
|---|---|---|

## Local files changed

## Impact analysis

## Tests
<test classes/commands run, and results>

## Validation
<validation command, ID and result>

## Deployment result
<deploy ID, status, or "Not deployed"; link DEP-...>

## Git commit
<hash, or "Not committed">

## Git push
<result, or "Not pushed">

## Assumptions

## Unverified items

## Risks
```
