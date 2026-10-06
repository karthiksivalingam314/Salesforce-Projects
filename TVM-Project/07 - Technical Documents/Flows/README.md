# Flows

Verified technical documentation for TVM **Flows (record-triggered, screen, scheduled, autolaunched)**.

- Document only configuration and metadata verified in `Fullsandox` (`TVM_WORKING_ORG`) or retrieved source.
- Never invent API names.
- One file per component, named after its API name.
- Link each document to its related REQ/CHG records.

See [../README.md](../README.md) for the document skeleton.

## Documents

Verified from Fullsandox on 2026-10-06 (REQ-2026-10-06-001). All six flows trigger on `Case`.

| Flow | API name | Active version | Latest version | Trigger | Active version metadata |
|---|---|---|---|---|---|
| [Assign Case Queue Based on Priority](Assign_Case_Queue_Based_on_Priority.md) | `Assign_Case_Queue_Based_on_Priority` | 12 | 13 (Obsolete) | RecordBeforeSave / Create | [Assign_Case_Queue_Based_on_Priority-v12.active-metadata.json](metadata/Assign_Case_Queue_Based_on_Priority-v12.active-metadata.json) |
| [Case Skill Mapping for same request types](Case_Skill_Mapping_for_same_request_types.md) | `Case_Skill_Mapping_for_same_request_types` | 2 | 2 (Active) | RecordBeforeSave / CreateAndUpdate | [Case_Skill_Mapping_for_same_request_types.flow-meta.xml](metadata/Case_Skill_Mapping_for_same_request_types.flow-meta.xml) |
| [Cases disposition](Cases_disposition.md) | `Cases_disposition` | 4 | 4 (Active) | RecordAfterSave / Update | [Cases_disposition.flow-meta.xml](metadata/Cases_disposition.flow-meta.xml) |
| [Email-to-case case category auto fill](Email_to_case_case_category_auto_fill.md) | `Email_to_case_case_category_auto_fill` | 1 | 1 (Active) | RecordBeforeSave / Create | [Email_to_case_case_category_auto_fill.flow-meta.xml](metadata/Email_to_case_case_category_auto_fill.flow-meta.xml) |
| [Track Agent-to-Agent Case Transfers](Track_Agent_to_Agent_Case_Transfers.md) | `Track_Agent_to_Agent_Case_Transfers` | 2 | 2 (Active) | RecordAfterSave / Update | [Track_Agent_to_Agent_Case_Transfers.flow-meta.xml](metadata/Track_Agent_to_Agent_Case_Transfers.flow-meta.xml) |
| [Track Internal Feedback Duration](Track_Internal_Feedback_Duration.md) | `Track_Internal_Feedback_Duration` | 3 | 10 (Obsolete) | RecordAfterSave / Update | [Track_Internal_Feedback_Duration-v3.active-metadata.json](metadata/Track_Internal_Feedback_Duration-v3.active-metadata.json) |

`metadata/` holds the active version of each flow:

- `*.flow-meta.xml`: Metadata API XML, unmodified. Used only when the active version is also the latest.
- `*-v<N>.active-metadata.json`: Tooling API `Flow.Metadata` of the active version. Used when a newer, non-active version exists, because the Metadata API retrieve returned that latest version instead.
