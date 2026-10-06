# Assign Case Queue Based on Priority (`Assign_Case_Queue_Based_on_Priority`)

> Verified from Salesforce on 2026-10-06. Org: Fullsandox · `sandipp@unitedtechno.com.tvmprod.fullsando` · Org ID `00DVa000006Eh6TMAS`. Read-only retrieval; no changes were made to this flow.

## Summary

| Field | Value |
|---|---|
| Label | Assign Case Queue Based on Priority |
| API name | `Assign_Case_Queue_Based_on_Priority` |
| Flow definition ID | `300Va00000PG2x9IAD` |
| Active version | **12** (`301Va000014BxLKIA0`) |
| Active version status | Active |
| Latest version | 13 (`301Va000014BoMvIAK`), status Obsolete |
| Active version = latest version | **No** |
| Process type | AutoLaunchedFlow |
| Trigger type | RecordBeforeSave |
| Trigger object | `Case` |
| Record trigger type | Create |
| API version (active version) | 67 |
| Namespace | None |
| Description (active version) | — |
| Definition last modified | 2026-09-18 by Sandip Patel |
| Active version last modified | 2026-09-18 |

## Entry criteria (active version)

Filter logic: `and`

| # | Field | Operator | Value |
|---|---|---|---|
| 1 | `Case_Category__c` | EqualTo | `General Support` (stringValue) |
| 2 | `Foundation_Record__c` | NotEqualTo | `true` (booleanValue) |

First element: `Get_Account`

## Elements (active version)

| Type | API name | Label |
|---|---|---|
| assignments | `Set_Priority_is_High` | Set Priority is High |
| assignments | `Update_Priority_to_High` | Update Priority to High |
| decisions | `Check_Priority_for_Case` | Check Priority for Case |
| decisions | `Is_Lithia_Auto_Group` | Is Lithia Auto Group? |
| decisions | `Is_Red_Fire_Dealer` | Is Red Fire Dealer? |
| recordLookups | `Get_Account` | Get Account |
| recordUpdates | `Assign_Enterprise_Queue` | Assign Enterprise QueueOwner |
| recordUpdates | `Assign_High_Priority_Queue` | Assign High Priority Queue |
| recordUpdates | `Assign_Low_Priority_Queue` | Assign Low Priority Queue |
| recordUpdates | `Assign_Medium_Priority_Queue` | Assign Medium Priority Queue |

## Hard-coded record IDs referenced

Resolved read-only via SOQL on `Group` in Fullsandox. Sandbox record IDs normally differ from Production.

| ID in flow | Name | DeveloperName | Type |
|---|---|---|---|
| `00GVa000006hsCz` | High Priority Case Queue | `High_Priority_Case_Queue` | Queue |
| `00GVa000006pbWj` | Low Priority Case Queue | `Low_Priority_Case_Queue` | Queue |
| `00GVa000006pbYL` | Medium Priority Case Queue | `Medium_Priority_Case_Queue` | Queue |
| `00GVa000006tXzB` | Enterprise Queue | `Enterprise_Queue` | Queue |

## Difference between active v12 and latest v13

Compared via the Tooling API `Metadata` of both versions. Only these differ:

- `status`: active = `Active`, latest = `Obsolete`
- `start.filters`: active has 2 filter(s), latest has 3. Latest version filters:

  | # | Field | Operator | Value |
  |---|---|---|---|
  | 1 | `Case_Category__c` | EqualTo | `General Support` (stringValue) |
  | 2 | `Foundation_Record__c` | NotEqualTo | `true` (booleanValue) |
  | 3 | `CreatedDate` | GreaterThanOrEqualTo | `2026-09-18T04:09:00.000+0000` (dateTimeValue) |

## Version history

| Version | Status | API version | Last modified | Version ID |
|---|---|---|---|---|
| 6 | Obsolete | 67 | 2026-07-03 | `301Va00000z3MvVIAU` |
| 7 | InvalidDraft | 67 | 2026-07-18 | `301Va0000100gejIAA` |
| 8 | Obsolete | 67 | 2026-07-18 | `301Va0000100VTGIA2` |
| 9 | Obsolete | 67 | 2026-09-03 | `301Va0000100dLvIAI` |
| 10 | Obsolete | 67 | 2026-09-01 | `301Va0000134SrZIAU` |
| 11 | Obsolete | 67 | 2026-09-17 | `301Va0000149GgqIAE` |
| 12 (active) | Active | 67 | 2026-09-18 | `301Va000014BxLKIA0` |
| 13 | Obsolete | 67 | 2026-09-18 | `301Va000014BoMvIAK` |

Only versions returned by the Tooling API are listed (8).

## Active version metadata

[metadata/Assign_Case_Queue_Based_on_Priority-v12.active-metadata.json](metadata/Assign_Case_Queue_Based_on_Priority-v12.active-metadata.json): the `Metadata` field of Tooling API `Flow` record `301Va000014BxLKIA0` (version 12, the active version), saved as returned (pretty-printed JSON, content unchanged).

> **Why not XML:** a Metadata API retrieve of `Flow:Assign_Case_Queue_Based_on_Priority` returns the **latest** version (v13, status `Obsolete`), not the active version (v12); this was observed on 2026-10-06 (the retrieved XML contained `<status>Obsolete</status>`). That XML was not stored, to avoid presenting a non-active version as active. The Tooling API `Flow` record is version-specific and returns the active version's own metadata.

## Sources and verification

- `FlowDefinitionView` (SOQL): API name, label, process/trigger type, active/latest version IDs, last modified.
- Tooling API `FlowDefinition` / `Flow`: version numbers, statuses, active version `Metadata`.
- Metadata API retrieve: XML (used only where active = latest).

## Related records

- Requirement: [REQ-2026-10-06-001](../../03%20-%20Requirements/2026-10-06/REQ-2026-10-06-001.md)
- Historical deployment record: [DEP-2026-10-06-016](../../06%20-%20Deployment/2026-10-06/DEP-2026-10-06-016.md)
