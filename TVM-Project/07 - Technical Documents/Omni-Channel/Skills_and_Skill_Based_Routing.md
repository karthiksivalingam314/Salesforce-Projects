# Skills and Skill-Based Routing

> Verified from Salesforce on 2026-10-08. Org: Fullsandox · Org ID `00DVa000006Eh6TMAS`. Read-only retrieval (Metadata API + SOQL); nothing was changed. Related: REQ-2026-10-08-001.

| Field | Value |
|---|---|
| Type | Skill, WorkSkillRouting (skill-based routing rule set) |
| Org | Fullsandox (00DVa000006Eh6TMAS) |
| Last verified | 2026-10-08 |
| Related records | REQ-2026-10-08-001 |

## Skills (8)

"Service resources with skill" = `ServiceResourceSkill` records per skill (SOQL aggregate, 2026-10-08).

| Label | API name | Skill type | Service resources with skill |
|---|---|---|---|
| General | `General` | Product | 22 |
| Inventory | `Inventory` | Product | 12 |
| English | `English` | Language | 1 |
| Spanish | `Spanish` | Language | 0 |
| Enterprise | `Enterprise` | Seniority_Level | 0 |
| Difficult Ticket | `Difficult_Ticket` | Seniority_Level | 0 |
| Red Dealer | `Red_Dealer` | Seniority_Level | 0 |
| Voice | `Voice` | — (not set) | 0 |

Service resources in the org (SOQL aggregate): 26 active with resource type `A`, 3 inactive with resource type `A`, and 1 active with resource type `T`.

## Skill-based routing rule set: `Skill_based_rules_for_cases`

| Field | Value |
|---|---|
| Label | Skill based rules for cases |
| API name | `Skill_based_rules_for_cases` |
| Active | true |
| Related object | `Case` |
| Rules (attributes) | 56 |

Each rule maps a Case field value to a skill. All rules have `isAdditionalSkill = false`. All skill levels are 0 except one (`Buy Sell`, level 4).

### `Case.Routing_Skill__c` (2 rules)

| Value | Skill |
|---|---|
| General | `General` |
| Inventory | `Inventory` |

### `Case.Case_Request__c` → `Inventory` (25 rules)

Inventory Quantity Issue; Feed Export Issue; Inventory Grouping Issue; Inventory Source Change; New HomeNet Feed/Order; Vehicle Information Issue; Vehicle Photos Issue; VDV Issue; Key Features Issue; Payment Disclaimer Issue; Pricing/Payment Issue; Pricing/Payments Update; Taxes & Fees Changes; Taxes & Fees Issues; Unlock Price/Discount Issue; Unlock Price/Discount Setup; Transact Issue; Transact Setup; Custom Badges; Meeting Request; Update Defaults; Payment Setup; Payment/Rebate Issues; Inventory Order Follow Up; Inventory Tagging/Comments

### `Case.Case_Request__c` → `General` (20 rules)

VDV Setup; Value Trade / Sell Us Your Car; Service Scheduler iFrame Setup; Service Scheduler Integration Setup; Schedule Test Drive Setup; Pre-Qual Setup; Pre-Qual Issue; Finance Application iFrame Setup; Finance Application Integration Setup; Finance Application Issue; Inbound Text Setup; Inbound Text Issue; Apollo Assistant Issue; Apollo Assistant Setup; Rollbacks; Payment Disclaimer Change; Inventory Grouping Setup; Feed Export Setup; Launch Audits; My Credit Drive Login Setup

### `Case.Case_Subcategory__c` (9 rules)

| Value | Skill | Skill level |
|---|---|---|
| Account Settings | `General` | 0 |
| Apollo Platform Support | `General` | 0 |
| Command Center | `General` | 0 |
| Offers & Specials | `General` | 0 |
| Websites - 3rd Party | `General` | 0 |
| Websites - Content | `General` | 0 |
| Websites - Leads & Forms | `General` | 0 |
| Buy Sell | `General` | 4 |
| Rebates & Incentives | `Inventory` | 0 |

## How skills are used

- **Cases.** The three attribute-based routing configs (`High_`, `Medium_` and `Low_Priority_Case_Routing_Config`) use skill-based routing, and this rule set supplies the skill requirements for Cases. See [Routing_Configurations.md](Routing_Configurations.md). The record-triggered flow [`Case_Skill_Mapping_for_same_request_types`](../Flows/Case_Skill_Mapping_for_same_request_types.md) is documented separately.
- **Voice.** The active routing flow `Voice_Calls_Routed_to_Agents_and_Queues1` adds a `General` or `Inventory` skill requirement and routes skills-based through `TVM_Voice_Routing_Config`. See [Routing_Flows.md](Routing_Flows.md).
- `Spanish`, `Enterprise`, `Difficult_Ticket`, `Red_Dealer` and `Voice` have no service resources assigned, and none of them appears in this rule set.

## Source metadata

- [metadata/skills/](metadata/skills/)
- [metadata/workSkillRoutings/](metadata/workSkillRoutings/)

All files are unmodified Metadata API XML.

## Change history

| Date | Change | Record |
|---|---|---|
| 2026-10-08 | Initial documentation (read-only retrieval) | REQ-2026-10-08-001 |
