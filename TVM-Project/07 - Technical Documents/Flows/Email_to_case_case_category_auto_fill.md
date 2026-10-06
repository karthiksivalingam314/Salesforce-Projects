# Email-to-case case category auto fill (`Email_to_case_case_category_auto_fill`)

> Verified from Salesforce on 2026-10-06. Org: Fullsandox · `sandipp@unitedtechno.com.tvmprod.fullsando` · Org ID `00DVa000006Eh6TMAS`. Read-only retrieval; no changes were made to this flow.

## Summary

| Field | Value |
|---|---|
| Label | Email-to-case case category auto fill |
| API name | `Email_to_case_case_category_auto_fill` |
| Flow definition ID | `300Va00000RC1nEIAT` |
| Active version | **1** (`301Va0000126NrhIAE`) |
| Active version status | Active |
| Latest version | 1 (`301Va0000126NrhIAE`), status Active |
| Active version = latest version | Yes |
| Process type | AutoLaunchedFlow |
| Trigger type | RecordBeforeSave |
| Trigger object | `Case` |
| Record trigger type | Create |
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

First element: `Update_case_category`

## Elements (active version)

| Type | API name | Label |
|---|---|---|
| recordUpdates | `Update_case_category` | Update case category |

## Version history

| Version | Status | API version | Last modified | Version ID |
|---|---|---|---|---|
| 1 (active) | Active | 67 | 2026-08-14 | `301Va0000126NrhIAE` |

Only versions returned by the Tooling API are listed (1).

## Active version metadata

[metadata/Email_to_case_case_category_auto_fill.flow-meta.xml](metadata/Email_to_case_case_category_auto_fill.flow-meta.xml): Metadata API retrieve (`sf project retrieve start`), unmodified. Verified as the active version: the active version is also the latest, and the XML contains `<status>Active</status>`.

## Sources and verification

- `FlowDefinitionView` (SOQL): API name, label, process/trigger type, active/latest version IDs, last modified.
- Tooling API `FlowDefinition` / `Flow`: version numbers, statuses, active version `Metadata`.
- Metadata API retrieve: XML (used only where active = latest).

## Related records

- Requirement: [REQ-2026-10-06-001](../../03%20-%20Requirements/2026-10-06/REQ-2026-10-06-001.md)
- Historical deployment record: [DEP-2026-10-06-021](../../06%20-%20Deployment/2026-10-06/DEP-2026-10-06-021.md)
