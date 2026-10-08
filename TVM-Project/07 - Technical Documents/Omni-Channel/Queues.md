# Queues

> Verified from Salesforce on 2026-10-08. Org: Fullsandox · Org ID `00DVa000006Eh6TMAS`. Read-only retrieval (Metadata API + SOQL); nothing was changed. Related: REQ-2026-10-08-001.

| Field | Value |
|---|---|
| Type | Queue |
| Org | Fullsandox (00DVa000006Eh6TMAS) |
| Last verified | 2026-10-08 |
| Related records | REQ-2026-10-08-001 |

The org has **64 queues**. **12** have an Omni-Channel routing configuration (`queueRoutingConfig`), so Omni-Channel pushes their work to agents. The other 52 are listed in the inventory at the end. One of those 52, `FD_Phone_Support_Queue`, is still a routing target because an active routing flow sends calls to it directly.

> **Privacy.** The GitHub repository is public, so the raw Queue XML is **not** stored here: it contains individual usernames and queue email addresses. This document gives member **counts** by type and names only roles and public groups. The full membership is in the org (Setup → Queues).

## Omni-Channel routed queues (12)

| Queue label | API name | Routing configuration | Supported objects | Members: users / roles / public groups |
|---|---|---|---|---|
| High Priority Case Queue | `High_Priority_Case_Queue` | `High_Priority_Case_Routing_Config` | Case | 29 / 0 / 0 |
| Enterprise Queue | `Enterprise_Queue` | `High_Priority_Case_Routing_Config` | Case | 0 / 0 / 0 |
| Medium Priority Case Queue | `Medium_Priority_Case_Queue` | `Medium_Priority_Case_Routing_Config` | Case | 27 / 0 / 0 |
| Low Priority Case Queue | `Low_Priority_Case_Queue` | `Low_Priority_Case_Routing_Config` | Case | 27 / 0 / 0 |
| General Support | `General_Support` | `General_Support_Overflow` | Case | 1 / 1 (`Product_Manager`) / 1 (`General_Support`) |
| Supervisors Queue For Disposition | `Supervisors_Queue_for_dis` | `Supervisors_routing_config` | Case | 3 / 0 / 0 |
| Voice Queue | `Voice_Queue` | `TVM_Voice_Routing_Config` | VoiceCall | 11 / 0 / 0 |
| Phone Support Queue | `Phone_Support_Queue` | `Default_For_Voice` | VoiceCall | 1 / 0 / 0 |
| Phone Support Queue SING | `Phone_Support_Queue_SING` | `Default_For_Voice` | VoiceCall | 1 / 0 / 0 |
| FD Phone Admin Queue | `FD_Phone_Admin_Queue` | `Default_For_Voice` | VoiceCall | 0 / 0 / 0 |
| VM Phone Queue | `VM_Phone_Queue` | `Default_For_Voice` | VoiceCall | 0 / 0 / 0 |
| Testing Voice Queue | `Testing_Voice_Queue` | `Default_For_Voice` | VoiceCall | 0 / 0 / 0 |

The retrieved metadata has `queueRoutingConfig` set on exactly these 12 queues.

Observations, recorded as-is:

- `Enterprise_Queue`, `FD_Phone_Admin_Queue`, `VM_Phone_Queue` and `Testing_Voice_Queue` have a routing configuration but **no direct members** in the queue metadata. Whether agents receive work from them by another path is NOT VERIFIED.
- `Enterprise_Queue` shares `High_Priority_Case_Routing_Config` with `High_Priority_Case_Queue`.

## Queues referenced by active routing flows

| Queue | Referenced by | How |
|---|---|---|
| `Phone_Support_Queue` (`00G5f000000sdDOEAY`) | `Voice_Calls_Routed_TVM` (v7), `Voice_Calls_Routed_to_Agents_and_Queues` (v2), `Voice_Calls_Routed_to_Basic_Queue_with_Case_Creation` (v2) | Hard-coded queue ID in a Route Work action |
| `FD_Phone_Support_Queue` (`00G5f000000shayEAA`) | `Voice_Calls_Routed_FD` (v1) | Hard-coded queue ID in a Route Work action |
| Queue whose `Name` equals the flow input `RouteQueue` | `Case_General_Support_Router` (v2) | Lookup on `Group` at run time |
| Queue with `Type = Queue` and `DeveloperName = SCV_BASIC_QUEUE` | `Voice_Calls_Default_Test` (v1) | Lookup on `Group` at run time. No queue with exactly that developer name was found in the retrieved metadata (the SCV basic queues are named `SCV_Basic_Queue_CCQ_...`). Runtime behavior NOT VERIFIED. |

`FD_Phone_Support_Queue` has **no** routing configuration in its metadata, but `Voice_Calls_Routed_FD` routes to it directly. See [Routing_Flows.md](Routing_Flows.md).

## Full queue inventory (64)

Routing config "—" = none. Supported objects "—" = none in metadata.

| API name | Label | Routing config | Supported objects | Users / roles / groups |
|---|---|---|---|---|
| `Account_Coordinator` | Account Coordinator | — | — | 3 / 0 / 0 |
| `Action` | Action | — | Case | 6 / 0 / 0 |
| `Advid_Support` | Advid Support | — | Case | 3 / 0 / 0 |
| `Analyze` | Analyze | — | Case | 14 / 0 / 0 |
| `Apollo_Support` | Apollo Support | — | Case | 0 / 0 / 1 |
| `Apollo_Websites_Support` | Apollo Websites Support | — | Case | 4 / 0 / 1 |
| `Case_Queue` | Case Queue | — | Case | 1 / 0 / 0 |
| `Command_Center_Support` | Command Center Support | — | Case | 2 / 0 / 0 |
| `Data_Support` | Data Support | — | Case | 1 / 0 / 1 |
| `Dealer_Analytics` | Dealer Analytics | — | Case | 0 / 0 / 1 |
| `Digital_Analyst` | Digital Analyst | — | Case | 1 / 0 / 0 |
| `Digital_Coop` | Digital Coop | — | Case | 1 / 0 / 0 |
| `Digital_OEM` | Digital OEM | — | Case | 0 / 0 / 1 |
| `Digital_Reporting` | Digital Reporting | — | Case | 0 / 0 / 1 |
| `Digital_Support` | Digital Support | — | Case | 0 / 0 / 1 |
| `Director_of_Onboarding` | Director of Onboarding | — | — | 0 / 0 / 0 |
| `Enterprise_Queue` | Enterprise Queue | `High_Priority_Case_Routing_Config` | Case | 0 / 0 / 0 |
| `Escalation_Queue` | Escalation Queue | — | Case | 3 / 0 / 0 |
| `FD_Phone_Admin_Queue` | FD Phone Admin Queue | `Default_For_Voice` | VoiceCall | 0 / 0 / 0 |
| `FD_Phone_Support_Queue` | FD Phone Support Queue | — | VoiceCall | 1 / 0 / 0 |
| `FordDirect_Support` | FordDirect Support | — | Case | 0 / 1 / 0 |
| `Foundation_Digital_Support` | Foundation Digital Support | — | Case | 0 / 0 / 1 |
| `General_Support` | General Support | `General_Support_Overflow` | Case | 1 / 1 / 1 |
| `Handling_cases` | Handling cases | — | `maps__Analytic__c` | 2 / 0 / 0 |
| `Helpware` | Helpware | — | Case | 2 / 0 / 0 |
| `Helpware_Qualminds` | Helpware/Qualminds | — | Case | 0 / 0 / 0 |
| `High_Priority_Case_Queue` | High Priority Case Queue | `High_Priority_Case_Routing_Config` | Case | 29 / 0 / 0 |
| `Hybrid` | Hybrid | — | Case | 8 / 0 / 0 |
| `Hybrid_Weekly_QA` | Hybrid Weekly QA | — | Case | 2 / 0 / 0 |
| `Internal_Support` | Internal Support | — | `Audit_Log__c` | 3 / 0 / 0 |
| `Inventory_Support` | Inventory Support | — | Case | 1 / 0 / 0 |
| `IT` | IT | — | — | 3 / 0 / 0 |
| `Lithia` | Lithia | — | Case | 1 / 0 / 0 |
| `Low_Priority_Case_Queue` | Low Priority Case Queue | `Low_Priority_Case_Routing_Config` | Case | 27 / 0 / 0 |
| `Major_AG_General_Support` | Major AG General Support | — | Case | 1 / 0 / 0 |
| `Marketing_Support` | Marketing Support | — | Case | 0 / 0 / 1 |
| `Media_Team` | Media Team | — | ContactRequest | 2 / 0 / 0 |
| `Medium_Priority_Case_Queue` | Medium Priority Case Queue | `Medium_Priority_Case_Routing_Config` | Case | 27 / 0 / 0 |
| `OEM_SSO_Support` | OEM SSO Support | — | Case | 0 / 0 / 0 |
| `OEM_Support` | OEM Support | — | Case | 0 / 1 / 0 |
| `Onboarding_Director` | Onboarding Director | — | — | 3 / 0 / 0 |
| `Onboarding_Inventory_Pricing` | Onboarding Inventory & Pricing | — | Case | 2 / 0 / 0 |
| `Phone_Support_Queue` | Phone Support Queue | `Default_For_Voice` | VoiceCall | 1 / 0 / 0 |
| `Phone_Support_Queue_SING` | Phone Support Queue SING | `Default_For_Voice` | VoiceCall | 1 / 0 / 0 |
| `PreQual_Support` | PreQual Support | — | Case | 0 / 0 / 0 |
| `Production_Support` | Production Support | — | Case | 0 / 0 / 1 |
| `SCV_Basic_Queue_CCQ_04v5f000000wsg9` | SCV Basic Queue | — | VoiceCall | 0 / 0 / 0 |
| `SCV_Basic_Queue_CCQ_04vVa0000043ARx` | SCV Basic Queue | — | VoiceCall | 0 / 0 / 0 |
| `SCV_Basic_Queue_CCQ_04vVb00000002rR` | SCV Basic Queue | — | VoiceCall | 0 / 0 / 0 |
| `SD_Digital_Support` | SD Digital Support | — | Case | 0 / 0 / 1 |
| `SEO` | SEO Support | — | Case | 0 / 1 / 0 |
| `Service_Retention_Manager` | Service Retention Manager | — | — | 1 / 0 / 0 |
| `Strategist_Assignment` | Strategist Assignment | — | Case | 0 / 0 / 0 |
| `Supervisors_Queue` | Supervisors Queue | — | Case | 3 / 0 / 0 |
| `Supervisors_Queue_for_dis` | Supervisors Queue For Disposition | `Supervisors_routing_config` | Case | 3 / 0 / 0 |
| `Support_Afternoon_Shift` | Support Afternoon Shift | — | Case, VoiceCall | 0 / 0 / 1 |
| `Support_Morning_Shift` | Support Morning Shift | — | Case, VoiceCall | 0 / 0 / 1 |
| `Support_Weekend_Shift` | Support Weekend Shift | — | Case, VoiceCall | 0 / 0 / 1 |
| `Testing_Voice_Queue` | Testing Voice Queue | `Default_For_Voice` | VoiceCall | 0 / 0 / 0 |
| `trUnassigned` | TaskRay Unassigned | — | — | 0 / 0 / 0 |
| `VM_Phone_Queue` | VM Phone Queue | `Default_For_Voice` | VoiceCall | 0 / 0 / 0 |
| `Voice_Queue` | Voice Queue | `TVM_Voice_Routing_Config` | VoiceCall | 11 / 0 / 0 |
| `Website_Coordinator` | Website Coordinator | — | — | 3 / 0 / 0 |
| `Website_Director` | Website Director | — | — | 4 / 0 / 0 |

Role and public-group members by name (from queue metadata):

| Queue | Roles | Public groups |
|---|---|---|
| `Apollo_Support` | — | `Apollo_Support` |
| `Apollo_Websites_Support` | — | `Apollo_Websites_Support` |
| `Data_Support` | — | `Data_Support` |
| `Dealer_Analytics` | — | `Dealer_Analytics` |
| `Digital_OEM` | — | `Digital_OEM` |
| `Digital_Reporting` | — | `Digital_Reporting_Support` |
| `Digital_Support` | — | `Digital_Support` |
| `FordDirect_Support` | `Ford_Direct` | — |
| `Foundation_Digital_Support` | — | `Foundation_Digital_Support` |
| `General_Support` | `Product_Manager` | `General_Support` |
| `Marketing_Support` | — | `Marketing_Support` |
| `OEM_Support` | `OEM_Team` | — |
| `Production_Support` | — | `Production_Support` |
| `SD_Digital_Support` | — | `SD_Digital_Support` |
| `SEO` | `SEO` | — |
| `Support_Afternoon_Shift` | — | `Support_Afternoon_Shift` |
| `Support_Morning_Shift` | — | `Support_Morning_Shift` |
| `Support_Weekend_Shift` | — | `Support_Weekend_Shift` |

Only `Escalation_Queue` has `doesSendEmailToMembers = true`.

## Change history

| Date | Change | Record |
|---|---|---|
| 2026-10-08 | Initial documentation (read-only retrieval) | REQ-2026-10-08-001 |
