# Case Skill Mapping for same request types (`Case_Skill_Mapping_for_same_request_types`)

> Verified from Salesforce on 2026-10-06. Org: Fullsandox · `sandipp@unitedtechno.com.tvmprod.fullsando` · Org ID `00DVa000006Eh6TMAS`. Read-only retrieval; no changes were made to this flow.

## Summary

| Field | Value |
|---|---|
| Label | Case Skill Mapping for same request types |
| API name | `Case_Skill_Mapping_for_same_request_types` |
| Flow definition ID | `300Va00000Q088IIAR` |
| Active version | **2** (`301Va0000107ZLXIA2`) |
| Active version status | Active |
| Latest version | 2 (`301Va0000107ZLXIA2`), status Active |
| Active version = latest version | Yes |
| Process type | AutoLaunchedFlow |
| Trigger type | RecordBeforeSave |
| Trigger object | `Case` |
| Record trigger type | CreateAndUpdate |
| API version (active version) | 67 |
| Namespace | None |
| Description (active version) | — |
| Definition last modified | 2026-07-21 by Sandip Patel |
| Active version last modified | 2026-07-21 |

## Entry criteria (active version)

Filter logic: `(1 AND 2) OR (3 AND 4) OR (5 AND 6) OR (7 AND 8)`

| # | Field | Operator | Value |
|---|---|---|---|
| 1 | `Case_Subcategory__c` | EqualTo | `Inventory` (stringValue) |
| 2 | `Case_Request__c` | EqualTo | `Other` (stringValue) |
| 3 | `Case_Subcategory__c` | EqualTo | `Onboarding` (stringValue) |
| 4 | `Case_Request__c` | EqualTo | `Other` (stringValue) |
| 5 | `Case_Subcategory__c` | EqualTo | `Inventory` (stringValue) |
| 6 | `Case_Request__c` | EqualTo | `VDV Issue` (stringValue) |
| 7 | `Case_Subcategory__c` | EqualTo | `Websites - Apollo Apps` (stringValue) |
| 8 | `Case_Request__c` | EqualTo | `VDV Issue` (stringValue) |

First element: `Determine_Routing_Skill`

## Elements (active version)

| Type | API name | Label |
|---|---|---|
| assignments | `Set_General_Skill` | Set General Skill |
| assignments | `Set_General_Skills` | Set General Skill |
| assignments | `Set_Inventory_Skill` | Set Inventory Skill |
| assignments | `Set_Inventory_Skills` | Set Inventory Skill |
| decisions | `Determine_Routing_Skill` | Determine Routing Skill |

## Version history

| Version | Status | API version | Last modified | Version ID |
|---|---|---|---|---|
| 1 | Obsolete | 67 | 2026-07-21 | `301Va0000102FlpIAE` |
| 2 (active) | Active | 67 | 2026-07-21 | `301Va0000107ZLXIA2` |

Only versions returned by the Tooling API are listed (2).

## Active version metadata

[metadata/Case_Skill_Mapping_for_same_request_types.flow-meta.xml](metadata/Case_Skill_Mapping_for_same_request_types.flow-meta.xml): Metadata API retrieve (`sf project retrieve start`), unmodified. Verified as the active version: the active version is also the latest, and the XML contains `<status>Active</status>`.

## Sources and verification

- `FlowDefinitionView` (SOQL): API name, label, process/trigger type, active/latest version IDs, last modified.
- Tooling API `FlowDefinition` / `Flow`: version numbers, statuses, active version `Metadata`.
- Metadata API retrieve: XML (used only where active = latest).

## Related records

- Requirement: [REQ-2026-10-06-001](../../03%20-%20Requirements/2026-10-06/REQ-2026-10-06-001.md)
- Historical deployment record: [DEP-2026-10-06-017](../../06%20-%20Deployment/2026-10-06/DEP-2026-10-06-017.md)
