# Presence: Statuses, Configurations and Decline Reasons

> Verified from Salesforce on 2026-10-08. Org: Fullsandox · Org ID `00DVa000006Eh6TMAS`. Read-only retrieval (Metadata API); nothing was changed. Related: REQ-2026-10-08-001.

| Field | Value |
|---|---|
| Type | ServicePresenceStatus, PresenceUserConfig, PresenceDeclineReason |
| Org | Fullsandox (00DVa000006Eh6TMAS) |
| Last verified | 2026-10-08 |
| Related records | REQ-2026-10-08-001 |

## Presence statuses (7)

A status with channels is an online status: agents in it receive work from those channels. A status with no channels is a busy/away status.

| Label | API name | Case | Phone (`sfdc_phone`) | Messaging (`sfdc_livemessage`) |
|---|---|---|---|---|
| Available for All Support | `Available_for_All_Support` | ✔ | ✔ | ✔ |
| Ready for Cases Only | `Available_for_Cases_Only` | ✔ | | ✔ |
| Ready for Voice Only | `AvailableforVoice` | | ✔ | |
| Voice Call Available | `Voice_Call_Available` | | ✔ | |
| Available for back up | `Available_for_back_up` | | ✔ | |
| Available for high priority | `Available_for_high_priority` | | ✔ | |
| Voice Call Busy | `Voice_Call_Busy` | | | |

Observations, recorded as-is:

- The API name `Available_for_Cases_Only` has the label "Ready for Cases Only", and its channels include Messaging as well as Case.
- `Available_for_high_priority` opens only the Phone channel, not Case.

Which profiles or permission sets give users access to these statuses was not retrieved. It is NOT VERIFIED in this document.

## Presence configurations (2)

| Setting | `TVM_V1` (TVM V1) | `default_presence_config` (Default Presence Configuration) |
|---|---|---|
| Capacity | 10 | 10 |
| Interruptible capacity | 10 | not set |
| Auto-accept | false | false |
| Allow decline | true | true |
| Require decline reason | false | false |
| Request sound | true | true |
| Disconnect sound | true | true |
| After-conversation work timer | false | false |
| Assigned users | 34 | none in metadata |
| Assigned profiles | none in metadata | none in metadata |

> **Privacy.** The raw `PresenceUserConfig` XML lists the 34 assigned usernames. The GitHub repository is public, so that file is not stored here. The assignments are in the org (Setup → Presence Configurations).

## Presence decline reasons (3)

| Label | API name |
|---|---|
| Too Busy | `Too_Busy` |
| Close to EOD | `Close_to_EOD` |
| On Break | `On_Break` |

Both presence configurations have `enableDeclineReason = false`, so agents are not asked for one of these reasons when they decline work.

## Source metadata

- [metadata/servicePresenceStatuses/](metadata/servicePresenceStatuses/)
- [metadata/presenceDeclineReasons/](metadata/presenceDeclineReasons/)

All files are unmodified Metadata API XML.

## Change history

| Date | Change | Record |
|---|---|---|
| 2026-10-08 | Initial documentation (read-only retrieval) | REQ-2026-10-08-001 |
