# Cases disposition (`Cases_disposition`)

> Verified from Salesforce on 2026-10-06. Org: Fullsandox · `sandipp@unitedtechno.com.tvmprod.fullsando` · Org ID `00DVa000006Eh6TMAS`. Read-only retrieval; no changes were made to this flow.

## Summary

| Field | Value |
|---|---|
| Label | Cases disposition |
| API name | `Cases_disposition` |
| Flow definition ID | `300Va00000PwbtfIAB` |
| Active version | **4** (`301Va0000126owXIAQ`) |
| Active version status | Active |
| Latest version | 4 (`301Va0000126owXIAQ`), status Active |
| Active version = latest version | Yes |
| Process type | AutoLaunchedFlow |
| Trigger type | RecordAfterSave |
| Trigger object | `Case` |
| Record trigger type | Update |
| API version (active version) | 67 |
| Namespace | None |
| Description (active version) | — |
| Definition last modified | 2026-08-14 by Sandip Patel |
| Active version last modified | 2026-08-14 |

## Entry criteria (active version)

Filter logic: `and`

| # | Field | Operator | Value |
|---|---|---|---|
| 1 | `Origin` | EqualTo | `Email` (stringValue) |
| 2 | `Case_Subcategory__c` | IsChanged | `true` (booleanValue) |
| 3 | `Case_Subcategory__c` | IsNull | `false` (booleanValue) |
| 4 | `Case_Request__c` | IsChanged | `true` (booleanValue) |
| 5 | `Case_Request__c` | IsNull | `false` (booleanValue) |

First element: `Check_for_Priority`

## Elements (active version)

| Type | API name | Label |
|---|---|---|
| decisions | `Check_for_Priority` | Check for Priority |
| recordUpdates | `Route_to_High_Priority_Queue` | Route to High Priority Queue |
| recordUpdates | `Route_to_Low_Priority_Queue` | Route to Low Priority Queue |
| recordUpdates | `Route_to_Medium_Priority_Queue` | Route to Medium Priority Queue |

## Hard-coded record IDs referenced

Resolved read-only via SOQL on `Group` in Fullsandox. Sandbox record IDs normally differ from Production.

| ID in flow | Name | DeveloperName | Type |
|---|---|---|---|
| `00GVa000006hsCz` | High Priority Case Queue | `High_Priority_Case_Queue` | Queue |
| `00GVa000006pbWj` | Low Priority Case Queue | `Low_Priority_Case_Queue` | Queue |
| `00GVa000006pbYL` | Medium Priority Case Queue | `Medium_Priority_Case_Queue` | Queue |

## Version history

| Version | Status | API version | Last modified | Version ID |
|---|---|---|---|---|
| 1 | Obsolete | 67 | 2026-08-14 | `301Va00000zxcPXIAY` |
| 2 | Obsolete | 67 | 2026-07-18 | `301Va0000100SjsIAE` |
| 3 | Obsolete | 67 | 2026-08-14 | `301Va0000126e7eIAA` |
| 4 (active) | Active | 67 | 2026-08-14 | `301Va0000126owXIAQ` |

Only versions returned by the Tooling API are listed (4).

## Active version metadata

[metadata/Cases_disposition.flow-meta.xml](metadata/Cases_disposition.flow-meta.xml): Metadata API retrieve (`sf project retrieve start`), unmodified. Verified as the active version: the active version is also the latest, and the XML contains `<status>Active</status>`.

## Sources and verification

- `FlowDefinitionView` (SOQL): API name, label, process/trigger type, active/latest version IDs, last modified.
- Tooling API `FlowDefinition` / `Flow`: version numbers, statuses, active version `Metadata`.
- Metadata API retrieve: XML (used only where active = latest).

## Related records

- Requirement: [REQ-2026-10-06-001](../../03%20-%20Requirements/2026-10-06/REQ-2026-10-06-001.md)
- Historical deployment record: [DEP-2026-10-06-018](../../06%20-%20Deployment/2026-10-06/DEP-2026-10-06-018.md)
