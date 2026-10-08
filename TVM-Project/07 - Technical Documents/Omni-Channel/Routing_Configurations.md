# Routing Configurations (`QueueRoutingConfig`)

> Verified from Salesforce on 2026-10-08. Org: Fullsandox · Org ID `00DVa000006Eh6TMAS`. Read-only retrieval (Metadata API); nothing was changed. Related: REQ-2026-10-08-001.

| Field | Value |
|---|---|
| Type | QueueRoutingConfig |
| Org | Fullsandox (00DVa000006Eh6TMAS) |
| Last verified | 2026-10-08 |
| Related records | REQ-2026-10-08-001 |

## Summary

7 routing configurations exist. Values are exactly as retrieved; "—" means the element is not present in the metadata.

| Label | API name | Routing model | Routing priority | Capacity type | Capacity weight | Capacity % | Paused capacity weight | Push timeout (s) | Attribute based (skills) | Queues using it |
|---|---|---|---|---|---|---|---|---|---|---|
| High Priority Case Routing Config | `High_Priority_Case_Routing_Config` | MOST_AVAILABLE | 1 | INTERRUPTIBLE | 1.0 | — | — | — | true | `High_Priority_Case_Queue`, `Enterprise_Queue` |
| Medium Priority Case Routing Config | `Medium_Priority_Case_Routing_Config` | MOST_AVAILABLE | 2 | INTERRUPTIBLE | 1.0 | — | — | — | true | `Medium_Priority_Case_Queue` |
| Low Priority Case Routing Config | `Low_Priority_Case_Routing_Config` | MOST_AVAILABLE | 3 | INTERRUPTIBLE | 0.5 | — | — | — | true | `Low_Priority_Case_Queue` |
| General Support Overflow | `General_Support_Overflow` | MOST_AVAILABLE | 100 | INTERRUPTIBLE | 1.0 | — | 1.0 | 30 | false | `General_Support` |
| Supervisors routing config | `Supervisors_routing_config` | MOST_AVAILABLE | 1 | INTERRUPTIBLE | 1.0 | — | — | 60 | false | `Supervisors_Queue_for_dis` |
| TVM Voice Routing Config | `TVM_Voice_Routing_Config` | LEAST_ACTIVE | 1 | INHERITED | — | 100.0 | — | — | false | `Voice_Queue` |
| Default For Voice | `Default_For_Voice` | EXTERNAL_ROUTING | 1 | INHERITED | — | 100.0 | — | — | false | `Phone_Support_Queue`, `Phone_Support_Queue_SING`, `FD_Phone_Admin_Queue`, `VM_Phone_Queue`, `Testing_Voice_Queue` |

"Queues using it" comes from the `queueRoutingConfig` element of each retrieved Queue. See [Queues.md](Queues.md).

## Notes

- **Case routing.** The three priority configs (High 1, Medium 2, Low 3) are attribute-based, so work routed through them also uses skills. Skill attributes come from the `Skill_based_rules_for_cases` rule set. See [Skills_and_Skill_Based_Routing.md](Skills_and_Skill_Based_Routing.md).
- **Case queue assignment.** The record-triggered flow [`Assign_Case_Queue_Based_on_Priority`](../Flows/Assign_Case_Queue_Based_on_Priority.md) assigns Cases to the High, Medium, Low and Enterprise queues, which are routed by these configs.
- **Voice.** `TVM_Voice_Routing_Config` is referenced by name in the active routing flow `Voice_Calls_Routed_to_Agents_and_Queues1` for skills-based voice routing. See [Routing_Flows.md](Routing_Flows.md).
- `Default_For_Voice` uses EXTERNAL_ROUTING.

## Source metadata

[metadata/queueRoutingConfigs/](metadata/queueRoutingConfigs/): unmodified Metadata API XML.

## Change history

| Date | Change | Record |
|---|---|---|
| 2026-10-08 | Initial documentation (read-only retrieval) | REQ-2026-10-08-001 |
