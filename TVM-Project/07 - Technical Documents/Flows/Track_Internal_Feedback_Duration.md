# Track Internal Feedback Duration (`Track_Internal_Feedback_Duration`)

> Verified from Salesforce on 2026-10-06. Org: Fullsandox · `sandipp@unitedtechno.com.tvmprod.fullsando` · Org ID `00DVa000006Eh6TMAS`. Read-only retrieval; no changes were made to this flow.

## Summary

| Field | Value |
|---|---|
| Label | Track Internal Feedback Duration |
| API name | `Track_Internal_Feedback_Duration` |
| Flow definition ID | `300Va00000PW2I2IAL` |
| Active version | **3** (`301Va000012RBCGIA4`) |
| Active version status | Active |
| Latest version | 10 (`301Va000014jd0wIAA`), status Obsolete |
| Active version = latest version | **No** |
| Process type | AutoLaunchedFlow |
| Trigger type | RecordAfterSave |
| Trigger object | `Case` |
| Record trigger type | Update |
| API version (active version) | 67 |
| Namespace | None |
| Description (active version) | — |
| Definition last modified | 2026-10-05 by Sandip Patel |
| Active version last modified | 2026-10-05 |

## Entry criteria (active version)

Filter logic: `and`

| # | Field | Operator | Value |
|---|---|---|---|
| 1 | `Status_Filtered__c` | IsChanged | `true` (booleanValue) |

First element: `Check_Feedback_Status`

## Elements (active version)

| Type | API name | Label |
|---|---|---|
| decisions | `Check_Feedback_Status` | Check Feedback Status |
| recordUpdates | `Set_External_Feedback_Start` | Set External Feedback Start |
| recordUpdates | `Set_Internal_Feedback_Start` | Set Internal Feedback Start |
| recordUpdates | `Update_External_Feedback_Duration` | Update Internal Feedback Duration |
| recordUpdates | `Update_Internal_Feedback_Duration` | Update Internal Feedback Duration |

## Resources (active version)

| Type | API name | Data type |
|---|---|---|
| formulas | `ExternalFeedbackDuration` | Number |
| formulas | `InternalFeedbackDuration` | Number |

## Difference between active v3 and latest v10

Compared via the Tooling API `Metadata` of both versions. Only these differ:

- `status`: active = `Active`, latest = `Obsolete`
- `start.filters`: active has 1 filter(s), latest has 2. Latest version filters:

  | # | Field | Operator | Value |
  |---|---|---|---|
  | 1 | `Status_Filtered__c` | IsChanged | `true` (booleanValue) |
  | 2 | `Case_Category__c` | EqualTo | `General Support` (stringValue) |

## Version history

| Version | Status | API version | Last modified | Version ID |
|---|---|---|---|---|
| 1 | Obsolete | 67 | 2026-07-08 | `301Va00000zKpmXIAS` |
| 2 | Obsolete | 67 | 2026-07-09 | `301Va00000zOvoVIAS` |
| 3 (active) | Active | 67 | 2026-10-05 | `301Va000012RBCGIA4` |
| 4 | Obsolete | 67 | 2026-08-19 | `301Va000012RQBYIA4` |
| 5 | Obsolete | 67 | 2026-08-19 | `301Va000012Ri6dIAC` |
| 6 | Obsolete | 67 | 2026-08-20 | `301Va000012USy5IAG` |
| 7 | Obsolete | 67 | 2026-09-26 | `301Va000012UG4CIAW` |
| 8 | Obsolete | 67 | 2026-08-21 | `301Va000012WsjdIAC` |
| 9 | Obsolete | 67 | 2026-09-28 | `301Va000014jxQvIAI` |
| 10 | Obsolete | 67 | 2026-09-28 | `301Va000014jd0wIAA` |

Only versions returned by the Tooling API are listed (10).

## Active version metadata

[metadata/Track_Internal_Feedback_Duration-v3.active-metadata.json](metadata/Track_Internal_Feedback_Duration-v3.active-metadata.json): the `Metadata` field of Tooling API `Flow` record `301Va000012RBCGIA4` (version 3, the active version), saved as returned (pretty-printed JSON, content unchanged).

> **Why not XML:** a Metadata API retrieve of `Flow:Track_Internal_Feedback_Duration` returns the **latest** version (v10, status `Obsolete`), not the active version (v3); this was observed on 2026-10-06 (the retrieved XML contained `<status>Obsolete</status>`). That XML was not stored, to avoid presenting a non-active version as active. The Tooling API `Flow` record is version-specific and returns the active version's own metadata.

## Sources and verification

- `FlowDefinitionView` (SOQL): API name, label, process/trigger type, active/latest version IDs, last modified.
- Tooling API `FlowDefinition` / `Flow`: version numbers, statuses, active version `Metadata`.
- Metadata API retrieve: XML (used only where active = latest).

## Related records

- Requirement: [REQ-2026-10-06-001](../../03%20-%20Requirements/2026-10-06/REQ-2026-10-06-001.md)
- Historical deployment record: [DEP-2026-10-06-020](../../06%20-%20Deployment/2026-10-06/DEP-2026-10-06-020.md)
