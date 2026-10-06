# Technical Documents

Verified technical documentation of TVM Salesforce configuration and metadata. When a meaningful technical change occurs, Claude creates or updates the document in the right category.

## Categories

| Folder | Covers |
|---|---|
| [Flows/](Flows/README.md) | Record-triggered, screen, scheduled, autolaunched and platform-event flows |
| [Apex/](Apex/README.md) | Apex classes, triggers, test classes, batch/queueable/scheduled jobs |
| [LWC/](LWC/README.md) | Lightning Web Components |
| [Objects/](Objects/README.md) | Standard and custom objects, record types, validation rules, page layouts |
| [Fields/](Fields/README.md) | Standard and custom fields |
| [Omni-Channel/](Omni-Channel/README.md) | Routing configurations, service channels, presence, queues used for routing |
| [Integrations/](Integrations/README.md) | Named credentials, external services, APIs, platform events, connected apps |
| [Permission Sets/](Permission%20Sets/README.md) | Permission sets, permission set groups, related access |
| [Reports/](Reports/README.md) | Reports and report types |
| [Dashboards/](Dashboards/README.md) | Dashboards |

## Rules

- Document only **verified** Salesforce configuration and metadata, confirmed from the org or retrieved source.
- **Never invent API names.**
- Use one file per component (or tightly related group), named after its API name, e.g. `Account_Before_Save.md`.
- Each document should state the verified org (`Fullsandox`), the verification date, and links to related REQ/CHG records.

## Suggested document skeleton

```markdown
# <Component label> (`<API name>`)

| Field | Value |
|---|---|
| Type | |
| API name | |
| Org | Fullsandox (00DVa000006Eh6TMAS) |
| Last verified | YYYY-MM-DD |
| Related records | REQ-... / CHG-... |

## Purpose
## Configuration / logic
## Dependencies
## Change history
```
