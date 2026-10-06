# 06 - Deployment

## Official deployment reference

**[TVM - Deployment Document.xlsx](TVM%20-%20Deployment%20Document.xlsx)** is the official TVM deployment reference and template. It is preserved here unchanged, as provided by the user. (The original file is named `TVM - Deployment Document .xlsx`; the content is byte-identical.)

- Every Markdown deployment record in this folder must follow its structure, item categories, and status columns.
- The workbook is **not** evidence that a deployment occurred in this project. Do not create Markdown deployment records from its rows.
- Read the workbook before creating or updating any deployment record.

### Workbook structure

| Sheet | Columns | Items it tracks |
|---|---|---|
| `Omni Configurations and Queues` | Component Name · Description · Deployment Status · Deployment Rollback Status | Queues (case and voice), routing configurations, service channels, presence statuses, skills and user assignments (service resources), skill-based routing rules, permission sets, permission set groups, supervisor configurations, static resources, skills |
| `Salesforce Flows -Cases and Voi` (full title: "Salesforce Flows - Cases and Voice") | Flow name · Flow Type · Links · Deployment status · Status | Salesforce flows (Record Triggered Flow, Record Triggered Flow (For reports), Omni Flow), each with a Flow Builder link |
| `Amazon Connect Flows` | Flow name · Flow Type · Links · Deployment status · Status | Amazon Connect contact flows and transfer flows, each with a Connect designer link |
| `Amazon Connect Configurations` | Component Type · Component name · Status | Amazon Connect queues, routing profiles, contact center queues/groups/channels/users, Unified Routing |
| `Reports` | Report Name · Deployment status · Status | Salesforce reports |
| `Quick Connect Users` | Users · Flow Name | Users mapped to the Amazon Connect transfer flow used for quick connects |

Status vocabulary used in the workbook:

- **Deployment status:** `Deployed`, `Deployed to Production`, `Deployed in Production`, `Added in Production`, `Present in Production`
- **Rollback / current status:** `Active in Prod`, `Active`, `Deactivated from prod`, `Deleted from prod`

Each component group or individual component has its **own** deployment status and its **own** rollback/current status. Deployment records must keep the same per-item granularity.

## Deployment history (Markdown records)

Real deployment and validation events are recorded as dated Markdown records:

```
06 - Deployment/
├── TVM - Deployment Document.xlsx      ← reference/template (do not modify)
├── README.md
└── YYYY-MM-DD/
    └── DEP-YYYY-MM-DD-###.md          ← one per actual deployment/validation event
```

- Create a record **only** when an actual Salesforce deployment or validation (check-only) event occurs. A requirement that merely mentions "deployment" does not create one.
- Number `###` sequentially per day. Create the dated folder only when a record exists.
- Record **actual results only**, never assumptions. Never claim success without Salesforce evidence (deploy ID or CLI/org status output).
- Target org: `Fullsandox` (`TVM_WORKING_ORG`). **Production deployment remains human-controlled.**

## Related records

| Record type | Location |
|---|---|
| Requirements | `03 - Requirements/` |
| Change records | `04 - Change Records/` |
| Conflicts | `05 - Conflicts/` |
| Technical documentation | `07 - Technical Documents/` |

## Deployment record template

Use the workbook's sheet that matches each item's category, and its columns, for the item tables. Include only the sections and tables that apply to the actual deployment.

```markdown
# DEP-YYYY-MM-DD-###

## Deployment information

| Field | Value |
|---|---|
| Deployment ID | DEP-YYYY-MM-DD-### |
| Date | YYYY-MM-DD |
| Type | Validation (check-only) / Deployment |
| Target Salesforce org | Fullsandox · <username> · <Org ID> · <instance URL> (verified at time of deployment) |
| Salesforce deploy ID(s) | 0Af... |
| Related requirement | REQ-YYYY-MM-DD-### |
| Related change record | CHG-YYYY-MM-DD-### |
| Overall status | <actual result> |

## Pre-deployment checks

| Check | Status | Details |
|---|---|---|
| Target org verified (alias, username, Org ID, instance URL) | | |
| Requirement and change record reviewed | | |
| Components identified (verified API names) | | |
| Dependencies / impact analysis | | |
| Tests identified | | |
| Rollback / recovery plan prepared | | |

## Deployment items

### Omni configurations and queues
| # | Component Name | Description (verified API name) | Deployment Status | Deployment Rollback Status |
|---|---|---|---|---|

### Salesforce flows
| # | Flow name | Flow Type | Link | Deployment status | Status |
|---|---|---|---|---|---|

### Amazon Connect flows
| # | Flow name | Flow Type | Link | Deployment status | Status |
|---|---|---|---|---|---|

### Amazon Connect configurations
| # | Component Type | Component name | Status |
|---|---|---|---|

### Reports
| # | Report Name | Deployment status | Status |
|---|---|---|---|

### Quick Connect users
| # | User | Flow Name |
|---|---|---|

### Other components (Apex, LWC, objects, fields, permission sets, etc.)
| # | Component type | API name | Action | Deployment status | Status |
|---|---|---|---|---|---|

## Validation and test results
<commands run, test classes, pass/fail counts, coverage: verbatim results>

## Deployment results
<verbatim status summary from Salesforce; per-item failures>

## Post-deployment verification
| Check | Result | Evidence |
|---|---|---|

## Rollback / recovery
- Rollback required: <yes/no, based on actual results>
- Rollback / recovery plan:
- Rollback actions taken and per-item rollback status (Deactivated / Deleted / Active):

## Overall status
<actual final status>

## Git
- Commit: <hash, recorded after the actual commit>
- Push: <actual result>

## Conflicts
<CON-... links, if any failures occurred>
```
