# Omni-Channel

Verified technical documentation for TVM **Omni-Channel configuration (routing, service channels, presence, queues)**.

- Document only configuration and metadata verified in `Fullsandox` (`TVM_WORKING_ORG`) or retrieved source.
- Never invent API names.
- One file per component, named after its API name.
- Link each document to its related REQ/CHG records.

See [../README.md](../README.md) for the document skeleton.

## Documents

Verified from Fullsandox on 2026-10-08 (REQ-2026-10-08-001). Each document covers a tightly related group of components.

| Document | Covers | Count |
|---|---|---|
| [Service_Channels.md](Service_Channels.md) | Service channels and their status-based capacity mappings | 3 |
| [Routing_Configurations.md](Routing_Configurations.md) | Routing configurations (`QueueRoutingConfig`) and the queues that use them | 7 |
| [Queues.md](Queues.md) | Omni-Channel routed queues, queues targeted by routing flows, and the full queue inventory | 64 (12 routed) |
| [Presence.md](Presence.md) | Presence statuses, presence configurations, decline reasons | 7 / 2 / 3 |
| [Skills_and_Skill_Based_Routing.md](Skills_and_Skill_Based_Routing.md) | Skills, service resource skill counts, and the `Skill_based_rules_for_cases` rule set | 8 skills, 56 rules |
| [Routing_Flows.md](Routing_Flows.md) | Omni-Channel routing flows (`RoutingFlow`): inventory and active-version logic | 22 (12 active: 7 org-defined, 5 Salesforce templates) |
| [Voice_and_Messaging.md](Voice_and_Messaging.md) | Call centers, Service Cloud Voice vendor, Messaging channel (redacted) | 2 / 1 / 1 |

## How it fits together

```
Case (record-triggered flow Assign_Case_Queue_Based_on_Priority sets the owner queue)
  └─ High / Medium / Low Priority Case Queue, Enterprise Queue
       └─ High / Medium / Low_Priority_Case_Routing_Config  (MOST_AVAILABLE, priority 1/2/3, skills-based)
            └─ skills from Skill_based_rules_for_cases (Routing_Skill__c, Case_Request__c, Case_Subcategory__c)
                 └─ service channel "Case" → agents in a presence status that includes Case

VoiceCall (Service Cloud Voice, call center TVMSBCC / Amazon Connect)
  └─ active routing flows → Phone Support Queue / FD Phone Support Queue (queue-based)
                          → TVM Voice Routing Config with General/Inventory skill (skills-based)
       └─ service channel "sfdc_phone" → agents in a presence status that includes Phone
```

This summary is built only from the verified facts in the documents above. Entry-point wiring that was not retrieved, such as which routing flow a contact-center or messaging channel calls, is marked NOT VERIFIED in those documents.

## `metadata/`

Unmodified source retrieved from Fullsandox on 2026-10-08:

| Folder | Contents |
|---|---|
| [metadata/serviceChannels/](metadata/serviceChannels/) | ServiceChannel XML (3) |
| [metadata/queueRoutingConfigs/](metadata/queueRoutingConfigs/) | QueueRoutingConfig XML (7) |
| [metadata/servicePresenceStatuses/](metadata/servicePresenceStatuses/) | ServicePresenceStatus XML (7) |
| [metadata/presenceDeclineReasons/](metadata/presenceDeclineReasons/) | PresenceDeclineReason XML (3) |
| [metadata/skills/](metadata/skills/) | Skill XML (8) |
| [metadata/workSkillRoutings/](metadata/workSkillRoutings/) | WorkSkillRouting XML (1) |
| [metadata/messagingChannels/](metadata/messagingChannels/) | MessagingChannel XML (1) |
| [metadata/flows/](metadata/flows/) | Active versions of the 7 active org-defined routing flows (5 XML, 2 Tooling API JSON) |

**Not stored, because this GitHub repository is public:**

- Queue XML and PresenceUserConfig XML: they contain individual usernames and email addresses.
- CallCenter XML and ConversationVendorInfo XML: they contain AWS account IDs, ARNs and a certificate.

Their configuration is summarised in the documents above, with those values left out.
