# Omni-Channel Routing Flows

> Verified from Salesforce on 2026-10-08. Org: Fullsandox · Org ID `00DVa000006Eh6TMAS`. Read-only retrieval (SOQL on `FlowDefinitionView`, Tooling API `Flow`, Metadata API); nothing was changed. Related: REQ-2026-10-08-001.

| Field | Value |
|---|---|
| Type | Flow (process type `RoutingFlow`) |
| Org | Fullsandox (00DVa000006Eh6TMAS) |
| Last verified | 2026-10-08 |
| Related records | REQ-2026-10-08-001 |

Omni-Channel flows route work items (cases, voice calls) to queues, agents or skills with the **Route Work** action. They are documented here, not in [../Flows/](../Flows/README.md), because they are part of the Omni-Channel configuration.

## Inventory (22 routing flows)

### Org-defined flows

| Label | API name | Active | Active version | Last modified |
|---|---|---|---|---|
| Case - General Support Router | `Case_General_Support_Router` | Yes | 2 | 2025-03-18 |
| Voice Calls Routed to Agents and Queues2 | `Voice_Calls_Routed_to_Agents_and_Queues1` | Yes | 16 | 2026-07-26 |
| Voice Calls Primary Inbound (version label: Voice Calls Routed to Agents and Queues) | `Voice_Calls_Routed_to_Agents_and_Queues` | Yes | 2 (latest is v3, Draft) | 2024-10-23 |
| Voice Calls Routed TVM | `Voice_Calls_Routed_TVM` | Yes | 7 (latest is v8, Draft) | 2023-08-15 |
| Voice Calls Routed FD | `Voice_Calls_Routed_FD` | Yes | 1 | 2023-08-14 |
| Voice Calls Default Test | `Voice_Calls_Default_Test` | Yes | 1 | 2024-10-23 |
| Voice Calls Routed to Basic Queue with Case Creation | `Voice_Calls_Routed_to_Basic_Queue_with_Case_Creation` | Yes | 2 | 2024-10-23 |
| Basic Routing with Case Creation | `Basic_Routing_with_Case_Creation` | No | — | 2026-02-02 |
| Configured Queued callback | `Configured_Queued_callback` | No | — | 2026-06-26 |
| Route Voice Calls to a Skill | `Route_Voice_Calls_to_a_Skill` | No | — | 2026-06-26 |
| Route Voice call to skills | `Route_Voice_call_to_skills` | No | — | 2026-06-26 |
| Skill Based Routing For Case | `Skill_Based_Routing_For_Case` | No | — | 2026-07-01 |
| Skilled Based Omni Flow for Cases | `Skilled_Based_Omni_Flow_for_Cases` | No | — | 2026-07-21 |
| Voice Calls Routed to Agents and Queues for TVM | `Voice_Calls_Routed_to_Agents_and_QueuesforTVM` | No | — | 2026-07-04 |
| Voice Calls Routing TVM | `Voice_Calls_Routing_TVM` | No | — | 2023-08-15 |
| Voice Skill based routing1 | `Voice_Skill_based_routing` | No | — | 2026-07-03 |

### Salesforce-provided template flows (namespaced; not retrieved)

| Label | API name | Namespace | Active |
|---|---|---|---|
| Chats Routed to Agents and Queues | `QueuesChat` | `omnichannel_chat` | Yes |
| Chats Routed to Agents with the Right Skills | `SkillsChat` | `omnichannel_chat` | Yes |
| Messages Routed to Agents and Queues | `MsgRouting` | `omnichannel_messaging` | Yes |
| Voice Calls Routed to Agents and Queues | `VoiceRouting` | `omnichannel_voice` | Yes |
| Draft Service Email | `DraftServiceEmail` | `service_email` | Yes |
| Voice Calls Routed to Basic Queue with Case Creation | `SCV_Basic_Routing_Flow` | `opencti` | No |

Which routing flow is attached to which entry point (Messaging channel routing, contact-center routing, or a record-triggered flow that calls a router) was **not** retrieved. It is NOT VERIFIED here.

## Active org-defined flows: what they do

Each description below comes from the active version's metadata.

### `Case_General_Support_Router` (v2, API 63.0)

Description: "Obj Case | Module | Omnichannel router"

- Inputs: `RouteQueue` (String) and `InputUser` (SObject).
- `GetQueue`: looks up `Group` where `Name` = `{!RouteQueue}`.
- Decision `Route_Case`: rule "Pit Crew" applies when `InputUser` is not null, and rule "Regular Case" when `recordId` is not null.
- Route Work `Route_to_Queue`: channel `Case` (`0N9Vb00000006ILKAY`), queue-based routing to `{!GetQueue.Id}`.

### `Voice_Calls_Routed_to_Agents_and_Queues1` (v16, API 67.0)

Label: "Voice Calls Routed to Agents and Queues2"

- `Get_Voice_call`: looks up `VoiceCall`.
- Decision `Determine_Skills`: outcomes General and Inventory.
- Add Skill Requirements: `General_Skill` adds `General` (level 0), and `Inventory_Skill` adds `Inventory` (level 0).
- Route Work `Route_Work_for_General` / `Route_Work_for_Inventory`: channel `sfdc_phone`, routing type **SkillsBased**, routing config `TVM Voice Routing Config`.

### `Voice_Calls_Routed_to_Agents_and_Queues` (v2, API 58)

- `GetContact`: looks up `Contact`, then the Screen Pop action `Pop_Contact_Account` pops the Contact.
- Route Work `RouteToQueueB`: channel `sfdc_phone` (`0N95f000000pcExCAI`), queue-based routing to **Phone Support Queue** (`00G5f000000sdDOEAY`).

### `Voice_Calls_Routed_TVM` (v7, API 58)

- Lookups: `GetContact` (Contact), `Get_Account` (Account) and `Get_AG` (`Auto_Group__c`).
- Decision `What_Pops`: outcomes All, Contact/AG and Contact/Account.
- Screen pops: Contact + Account + Auto Group, Contact + Auto Group, or Contact + Account.
- Route Work `Route_to_Queue_A`, `RouteToQueueB` and `Route_to_Queue_C` all route to **Phone Support Queue** (`00G5f000000sdDOEAY`) on `sfdc_phone`.

### `Voice_Calls_Routed_FD` (v1, API 58.0)

- `GetContact` → Screen Pop `Pop_Contact_Account` (Contact, Account, `Auto_Group__c`).
- Route Work `RouteToQueueB`: `sfdc_phone`, queue-based routing to **FD Phone Support Queue** (`00G5f000000shayEAA`).

### `Voice_Calls_Routed_to_Basic_Queue_with_Case_Creation` (v2, API 56.0)

Description: "Routes each call to the default queue (Basic Queue) and, if the agent accepts, screen pops the new case for this call and identifies the caller."

- Lookups: `Get_ARN` (`CallCenterRoutingMap`), `Get_Contact` (Contact by `Phone` = incoming number) and `Get_Case` (Case by `ContactPhone` = incoming number).
- If no Contact or Case is found, it creates one (`Create_Contact`, `Create_Case`).
- Screen pops: Case and Contact, or the existing Contact.
- Route Work `Route_to_Main_Queue`: `sfdc_phone`, queue-based routing to **Phone Support Queue** (`00G5f000000sdDOEAY`).

### `Voice_Calls_Default_Test` (v1, API 56.0)

The description and Case/Contact logic are the same as `Voice_Calls_Routed_to_Basic_Queue_with_Case_Creation`. The difference is the target queue:

- `Get_ARN`: `CallCenterRoutingMap` where `MasterLabel` = `SCV_BASIC_QUEUE_MAPPING`.
- `Get_SCV_Basic_Queue`: `Group` where `Type` = `Queue` and `DeveloperName` = `SCV_BASIC_QUEUE`.
- Route Work `Route_to_Basic_Queue`: `sfdc_phone`, queue-based routing to `{!Get_SCV_Basic_Queue.Id}`.
- No queue with exactly the developer name `SCV_BASIC_QUEUE` appears in the retrieved queue metadata. Runtime behavior is NOT VERIFIED.

## Source metadata (active versions)

Stored in [metadata/flows/](metadata/flows/):

| Flow | File | Format |
|---|---|---|
| `Case_General_Support_Router` v2 | `Case_General_Support_Router.flow-meta.xml` | Metadata API XML (active = latest) |
| `Voice_Calls_Routed_to_Agents_and_Queues1` v16 | `Voice_Calls_Routed_to_Agents_and_Queues1.flow-meta.xml` | Metadata API XML (active = latest) |
| `Voice_Calls_Routed_FD` v1 | `Voice_Calls_Routed_FD.flow-meta.xml` | Metadata API XML (active = latest) |
| `Voice_Calls_Default_Test` v1 | `Voice_Calls_Default_Test.flow-meta.xml` | Metadata API XML (active = latest) |
| `Voice_Calls_Routed_to_Basic_Queue_with_Case_Creation` v2 | `Voice_Calls_Routed_to_Basic_Queue_with_Case_Creation.flow-meta.xml` | Metadata API XML (active = latest) |
| `Voice_Calls_Routed_TVM` v7 | `Voice_Calls_Routed_TVM-v7.active-metadata.json` | Tooling API `Flow.Metadata` JSON. The Metadata API returns the latest version (v8, Draft). |
| `Voice_Calls_Routed_to_Agents_and_Queues` v2 | `Voice_Calls_Routed_to_Agents_and_Queues-v2.active-metadata.json` | Tooling API `Flow.Metadata` JSON. The Metadata API returns the latest version (v3, Draft). |

Inactive flows were not retrieved.

## Change history

| Date | Change | Record |
|---|---|---|
| 2026-10-08 | Initial documentation (read-only retrieval) | REQ-2026-10-08-001 |
