# Track Agent-to-Agent Case Transfers (`Track_Agent_to_Agent_Case_Transfers`)

> Verified from Salesforce on 2026-10-06. Org: Fullsandox · `sandipp@unitedtechno.com.tvmprod.fullsando` · Org ID `00DVa000006Eh6TMAS`. Read-only retrieval; no changes were made to this flow.

## Summary

| Field | Value |
|---|---|
| Label | Track Agent-to-Agent Case Transfers |
| API name | `Track_Agent_to_Agent_Case_Transfers` |
| Flow definition ID | `300Va00000PTn5PIAT` |
| Active version | **2** (`301Va00000zDoHFIA0`) |
| Active version status | Active |
| Latest version | 2 (`301Va00000zDoHFIA0`), status Active |
| Active version = latest version | Yes |
| Process type | AutoLaunchedFlow |
| Trigger type | RecordAfterSave |
| Trigger object | `Case` |
| Record trigger type | Update |
| API version (active version) | 67 |
| Namespace | None |
| Description (active version) | Tracks agent-to-agent Case owner transfers, creates Case Transfer records, and updates Agent Transfer Summary records to support reporting on Cases Passed, Cases Received, and Transfer Rate by month and year. |
| Definition last modified | 2026-07-07 by Sandip Patel |
| Active version last modified | 2026-07-07 |

## Entry criteria (active version)

Filter logic: `and`

| # | Field | Operator | Value |
|---|---|---|---|
| 1 | `OwnerId` | IsChanged | `true` (booleanValue) |

First element: `Get_Previous_Owner`

## Elements (active version)

| Type | API name | Label |
|---|---|---|
| assignments | `Increment_From_Agent_Passed` | Increment From Agent Passed |
| assignments | `Increment_To_Agent_Received` | Increment To Agent Received |
| decisions | `From_Agent_Summary_Exists` | From Agent Summary Exists? |
| decisions | `Is_Agent_To_Agent_Transfer` | Is Agent To Agent Transfer? |
| decisions | `To_Agent_Summary_Exists` | To Agent Summary Exists? |
| recordCreates | `Create_Case_Transfer` | Create Case Transfer |
| recordCreates | `Create_From_Agent_Summary` | Create From Agent Summary |
| recordCreates | `Create_To_Agent_Summary` | Create To Agent Summary |
| recordLookups | `Get_Current_Owner` | Get Current Owner |
| recordLookups | `Get_From_Agent_Summary` | Get From Agent Summary |
| recordLookups | `Get_Previous_Owner` | Get Previous Owner |
| recordLookups | `Get_To_Agent_Summary` | Get To Agent Summary |
| recordUpdates | `Save_From_Agent_Summary` | Save From Agent Summary |
| recordUpdates | `Save_To_Agent_Summary` | Save To Agent Summary |

## Resources (active version)

| Type | API name | Data type |
|---|---|---|
| formulas | `CurrentMonth` | String |
| formulas | `CurrentYear` | Number |
| formulas | `FromAgentSummaryKey` | String |
| formulas | `ToAgentSummaryKey` | String |

## Version history

| Version | Status | API version | Last modified | Version ID |
|---|---|---|---|---|
| 1 | Obsolete | 67 | 2026-07-07 | `301Va00000zDafJIAS` |
| 2 (active) | Active | 67 | 2026-07-07 | `301Va00000zDoHFIA0` |

Only versions returned by the Tooling API are listed (2).

## Active version metadata

[metadata/Track_Agent_to_Agent_Case_Transfers.flow-meta.xml](metadata/Track_Agent_to_Agent_Case_Transfers.flow-meta.xml): Metadata API retrieve (`sf project retrieve start`), unmodified. Verified as the active version: the active version is also the latest, and the XML contains `<status>Active</status>`.

## Sources and verification

- `FlowDefinitionView` (SOQL): API name, label, process/trigger type, active/latest version IDs, last modified.
- Tooling API `FlowDefinition` / `Flow`: version numbers, statuses, active version `Metadata`.
- Metadata API retrieve: XML (used only where active = latest).

## Related records

- Requirement: [REQ-2026-10-06-001](../../03%20-%20Requirements/2026-10-06/REQ-2026-10-06-001.md)
- Historical deployment record: [DEP-2026-10-06-019](../../06%20-%20Deployment/2026-10-06/DEP-2026-10-06-019.md)
