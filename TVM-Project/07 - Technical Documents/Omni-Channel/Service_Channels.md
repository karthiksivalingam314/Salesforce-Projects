# Service Channels

> Verified from Salesforce on 2026-10-08. Org: Fullsandox · Org ID `00DVa000006Eh6TMAS`. Read-only retrieval (Metadata API + SOQL); nothing was changed. Related: REQ-2026-10-08-001.

| Field | Value |
|---|---|
| Type | ServiceChannel |
| Org | Fullsandox (00DVa000006Eh6TMAS) |
| Last verified | 2026-10-08 |
| Related records | REQ-2026-10-08-001 |

## Summary

| Label | API name | Record ID | Related object | Capacity model | Interruptible | Auto-accept | Minimize widget on accept | Status field |
|---|---|---|---|---|---|---|---|---|
| Case | `Case` | `0N9Vb00000006ILKAY` | `Case` | STATUS_BASED | true | false | true | `Status` |
| Phone | `sfdc_phone` | `0N95f000000pcExCAI` | `VoiceCall` | STATUS_BASED | false | false | true | `CallStatus` |
| Messaging | `sfdc_livemessage` | `0N95f000000d2X6CAI` | `MessagingSession` | TAB_BASED | true | false | false | — |

Other settings, as retrieved:

| API name | `doesCheckCapOnOwnerChange` | `doesCheckCapOnStatusChange` | `hasAfterConvoWorkTimer` |
|---|---|---|---|
| `Case` | false | false | not set |
| `sfdc_phone` | false | false | false |
| `sfdc_livemessage` | not set | not set | false |

## Case channel: status-based capacity mappings

With status-based capacity, work items count against an agent's capacity only while their `Status` is in an IN_PROGRESS value.

| Mapping type | `Case.Status` values |
|---|---|
| IN_PROGRESS | New, Assigned, In Progress, Production Complete, Digital Complete, Ready for Testing, Approved |
| PAUSED | On Hold, Waiting on Development, Escalated, Awaiting Approval, Selected for Dev, In Progress with Dev, External Feedback Needed |
| COMPLETED | Internal Feedback Provided, Closed, Cancelled, Upload Complete - Ready to Send to Dealer, External Feedback Provided, Future, Ready for QA, Initial Outreach, Scheduled, Merged, Recurring Meeting, FD Closed, Internal Feedback Needed, OEM Feedback Provided, On Hold - Third Party, On Hold  Client, On Hold - RPM, On Hold - Third Party, On Hold - Client |

Observations from the retrieved metadata, recorded as-is:

- `On Hold - Third Party` appears twice in the COMPLETED mappings.
- `On Hold  Client` (two spaces, no hyphen) and `On Hold - Client` are both mapped as COMPLETED.
- Several "On Hold" values are mapped COMPLETED, while `On Hold` itself is PAUSED. Whether this is intended is NOT VERIFIED.

## Phone channel: status-based capacity mappings

| Mapping type | `VoiceCall.CallStatus` values |
|---|---|
| IN_PROGRESS | ACTIVE, NEW |
| COMPLETED | COMPLETED |

## Where the channels are used

- Presence statuses that open each channel: see [Presence.md](Presence.md).
- Active routing flows that route work on the `Case` and `sfdc_phone` channels: see [Routing_Flows.md](Routing_Flows.md).

## Source metadata

[metadata/serviceChannels/](metadata/serviceChannels/): unmodified Metadata API XML.

## Change history

| Date | Change | Record |
|---|---|---|
| 2026-10-08 | Initial documentation (read-only retrieval) | REQ-2026-10-08-001 |
