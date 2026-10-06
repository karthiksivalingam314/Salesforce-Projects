# 06 - Deployment

## Official deployment reference

**[TVM - Deployment Document.xlsx](TVM%20-%20Deployment%20Document.xlsx)** is the official TVM deployment reference and template. It is preserved here unchanged, as provided by the user. (The original file is named `TVM - Deployment Document .xlsx`; the content is byte-identical.)

- It is the reference/template. Every Markdown deployment record in this folder follows its structure, item categories, and status columns.
- **Do not modify the workbook.** Searchable deployment information is kept in the Markdown records below.
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

Deployment information is kept as Markdown so it can be searched and tracked over time. **Each deployment item gets its own DEP record**, with its own status.

```
06 - Deployment/
├── TVM - Deployment Document.xlsx      ← reference/template (do not modify)
├── README.md                           ← this file, with the record index
└── YYYY-MM-DD/
    └── DEP-YYYY-MM-DD-###.md          ← one record per deployment item
```

There are two kinds of record:

| Record type | Source | Rules |
|---|---|---|
| **Historical** (extracted from the deployment document) | Rows of `TVM - Deployment Document.xlsx` | Must stay faithful to the source: values copied verbatim, original spelling kept, nothing inferred or "corrected". Values the source does not give are marked `NOT PROVIDED`. Not verified against Salesforce unless a record says otherwise. |
| **Actual deployment / validation event** (future work) | A real Salesforce deployment or check-only validation run by Claude | Created only when the event actually occurs (a requirement that merely mentions "deployment" does not create one). Record actual results only, with Salesforce evidence (deploy ID, CLI/org status output). Never claim success without evidence. |

General rules:

- Number `###` sequentially per day. Create the dated folder only when a record exists.
- Never invent components, statuses, IDs, test results, or deployment results. Use `UNKNOWN` or `NOT PROVIDED`.
- For new deployment work, the target org is `Fullsandox` (`TVM_WORKING_ORG`). **Production deployment remains human-controlled.**
- When a record is added, add it to the index below.

### Historical records extracted on 2026-10-06

The workbook has **no deployment dates**. The `2026-10-06` folder and ID date are the date the records were created, **not** the deployment date. Each record shows `Deployment date: NOT PROVIDED`.

How the rows were extracted:

- One record per workbook row. Each row has its own status, so each row is one deployment item. Rows that list several components with a single status (for example, row 2 lists all the queues) stay as one record, because the source gives one status for the whole group.
- Merged category cells (`A3:A4`, `A5:A7`, `A9:A10` on the Omni sheet) apply to each row they cover. Each affected record says so.
- The `Omni Configurations and Queues` sheet has a threaded comment on its header: *"We are not deploying these components"*. It is copied verbatim into all 15 Omni records. The source does not say what it refers to.
- The `Quick Connect Users` sheet maps users to a flow and has no status columns, so its 30 rows are kept together in one record (DEP-2026-10-06-039).

| Record | Source sheet | Source row | Item | Status (as recorded in source) |
|---|---|---|---|---|
| [DEP-2026-10-06-001](2026-10-06/DEP-2026-10-06-001.md) | Omni Configurations and Queues | row 2 | Queues (source row 2) | Deployment Status: Deployed; Deployment Rollback Status: Deleted from prod |
| [DEP-2026-10-06-002](2026-10-06/DEP-2026-10-06-002.md) | Omni Configurations and Queues | row 3 | Routing Configuration (source row 3) | Deployment Status: Deployed; Deployment Rollback Status: Deleted from prod |
| [DEP-2026-10-06-003](2026-10-06/DEP-2026-10-06-003.md) | Omni Configurations and Queues | row 4 | Routing Configuration (source row 4) | Deployment Status: Deployed; Deployment Rollback Status: Deactivated from prod |
| [DEP-2026-10-06-004](2026-10-06/DEP-2026-10-06-004.md) | Omni Configurations and Queues | row 5 | Service channel — Case | Deployment Status: Deployed; Deployment Rollback Status: Deactivated from prod |
| [DEP-2026-10-06-005](2026-10-06/DEP-2026-10-06-005.md) | Omni Configurations and Queues | row 6 | Service channel — Messaging | Deployment Status: Deployed; Deployment Rollback Status: Deactivated from prod |
| [DEP-2026-10-06-006](2026-10-06/DEP-2026-10-06-006.md) | Omni Configurations and Queues | row 7 | Service channel — Phone | Deployment Status: Deployed; Deployment Rollback Status: Deactivated from prod |
| [DEP-2026-10-06-007](2026-10-06/DEP-2026-10-06-007.md) | Omni Configurations and Queues | row 8 | Presence statuses (source row 8) | Deployment Status: Deployed; Deployment Rollback Status: Active in Prod |
| [DEP-2026-10-06-008](2026-10-06/DEP-2026-10-06-008.md) | Omni Configurations and Queues | row 9 | Skills and User assignment (Service resources) (source row 9) | Deployment Status: Deployed; Deployment Rollback Status: Active in Prod |
| [DEP-2026-10-06-009](2026-10-06/DEP-2026-10-06-009.md) | Omni Configurations and Queues | row 10 | Skills and User assignment (Service resources) (source row 10) | Deployment Status: Deployed; Deployment Rollback Status: Active in Prod |
| [DEP-2026-10-06-010](2026-10-06/DEP-2026-10-06-010.md) | Omni Configurations and Queues | row 11 | Skill Based Routing Rules — 1.Skill based rules for cases | Deployment Status: Deployed; Deployment Rollback Status: Deactivated from prod |
| [DEP-2026-10-06-011](2026-10-06/DEP-2026-10-06-011.md) | Omni Configurations and Queues | row 12 | Permission Set (source row 12) | Deployment Status: Deployed; Deployment Rollback Status: Active in Prod |
| [DEP-2026-10-06-012](2026-10-06/DEP-2026-10-06-012.md) | Omni Configurations and Queues | row 13 | Permission Set Groups — Omni Supervisor Access | Deployment Status: Deployed; Deployment Rollback Status: Active in Prod |
| [DEP-2026-10-06-013](2026-10-06/DEP-2026-10-06-013.md) | Omni Configurations and Queues | row 14 | Superviosr Configuration (source row 14) | Deployment Status: Deployed; Deployment Rollback Status: Active in Prod |
| [DEP-2026-10-06-014](2026-10-06/DEP-2026-10-06-014.md) | Omni Configurations and Queues | row 15 | Static Resource — silent | Deployment Status: Deployed; Deployment Rollback Status: Active in Prod |
| [DEP-2026-10-06-015](2026-10-06/DEP-2026-10-06-015.md) | Omni Configurations and Queues | row 16 | Skillls (source row 16) | Deployment Status: Deployed; Deployment Rollback Status: Active in Prod |
| [DEP-2026-10-06-016](2026-10-06/DEP-2026-10-06-016.md) | Salesforce Flows -Cases and Voi | row 2 | Assign Case Queue Based on Priority | Deployment status: Deployed to Production; Status: Active in Prod |
| [DEP-2026-10-06-017](2026-10-06/DEP-2026-10-06-017.md) | Salesforce Flows -Cases and Voi | row 3 | Case Skill Mapping for same request types | Deployment status: Deployed to Production; Status: Active in Prod |
| [DEP-2026-10-06-018](2026-10-06/DEP-2026-10-06-018.md) | Salesforce Flows -Cases and Voi | row 4 | Cases disposition | Deployment status: Deployed to Production; Status: Active in Prod |
| [DEP-2026-10-06-019](2026-10-06/DEP-2026-10-06-019.md) | Salesforce Flows -Cases and Voi | row 5 | Track Agent-to-Agent Case Transfers | Deployment status: Deployed to Production; Status: Active in Prod |
| [DEP-2026-10-06-020](2026-10-06/DEP-2026-10-06-020.md) | Salesforce Flows -Cases and Voi | row 6 | Track Internal Feedback Duration | Deployment status: Deployed to Production; Status: Active in Prod |
| [DEP-2026-10-06-021](2026-10-06/DEP-2026-10-06-021.md) | Salesforce Flows -Cases and Voi | row 7 | Email-to-case case category auto fill | Deployment status: Deployed to Production; Status: Active in Prod |
| [DEP-2026-10-06-022](2026-10-06/DEP-2026-10-06-022.md) | Salesforce Flows -Cases and Voi | row 8 | Voice Calls Routed to Agents and Queues2 | Deployment status: Deployed to Production; Status: Active in Prod |
| [DEP-2026-10-06-023](2026-10-06/DEP-2026-10-06-023.md) | Amazon Connect Flows | row 2 | Website Support IVR 3 | Deployment status: Added in Production; Status: Active |
| [DEP-2026-10-06-024](2026-10-06/DEP-2026-10-06-024.md) | Amazon Connect Flows | row 3 | Sample SCV Transcription Subflow with Contact Lens | Deployment status: Added in Production; Status: Active |
| [DEP-2026-10-06-025](2026-10-06/DEP-2026-10-06-025.md) | Amazon Connect Flows | row 4 | Sample SCV Transfer Flow For Omni Routing Transfers01 | Deployment status: Added in Production; Status: Active |
| [DEP-2026-10-06-026](2026-10-06/DEP-2026-10-06-026.md) | Amazon Connect Configurations | row 2 | Amazon Connect Queue — TVM Primary Support Queue | Status: Present in Production |
| [DEP-2026-10-06-027](2026-10-06/DEP-2026-10-06-027.md) | Amazon Connect Configurations | row 3 | Routing profile — Primary Phone Support | Status: Present in Production |
| [DEP-2026-10-06-028](2026-10-06/DEP-2026-10-06-028.md) | Amazon Connect Configurations | row 4 | Contact Center Queues — Phone Support Queue | Status: Present in Production |
| [DEP-2026-10-06-029](2026-10-06/DEP-2026-10-06-029.md) | Amazon Connect Configurations | row 5 | Contact Center Groups — Primary Phone Support | Status: Present in Production |
| [DEP-2026-10-06-030](2026-10-06/DEP-2026-10-06-030.md) | Amazon Connect Configurations | row 6 | Contact Center Channels — Primary | Status: Present in Production |
| [DEP-2026-10-06-031](2026-10-06/DEP-2026-10-06-031.md) | Amazon Connect Configurations | row 7 | Contact center Users (source row 7) | Status: Present in Production |
| [DEP-2026-10-06-032](2026-10-06/DEP-2026-10-06-032.md) | Amazon Connect Configurations | row 8 | Unified Routing — Enabled | Status: Present in Production |
| [DEP-2026-10-06-033](2026-10-06/DEP-2026-10-06-033.md) | Reports | row 2 | Internal Feedback Duration Report | Deployment status: Deployed in Production; Status: Active |
| [DEP-2026-10-06-034](2026-10-06/DEP-2026-10-06-034.md) | Reports | row 3 | Case Reopened Rate Report | Deployment status: Deployed in Production; Status: Active |
| [DEP-2026-10-06-035](2026-10-06/DEP-2026-10-06-035.md) | Reports | row 4 | Internal Feedback Status Report | Deployment status: Deployed in Production; Status: Active |
| [DEP-2026-10-06-036](2026-10-06/DEP-2026-10-06-036.md) | Reports | row 5 | Case Transfer History Report | Deployment status: Deployed in Production; Status: Active |
| [DEP-2026-10-06-037](2026-10-06/DEP-2026-10-06-037.md) | Reports | row 6 | Agent case transfer report | Deployment status: Deployed in Production; Status: Active |
| [DEP-2026-10-06-038](2026-10-06/DEP-2026-10-06-038.md) | Reports | row 7 | Agent Transfer Summary Report | Deployment status: Deployed in Production; Status: Active |
| [DEP-2026-10-06-039](2026-10-06/DEP-2026-10-06-039.md) | Quick Connect Users | rows 2–31 | Quick Connect Users | NOT PROVIDED |

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
