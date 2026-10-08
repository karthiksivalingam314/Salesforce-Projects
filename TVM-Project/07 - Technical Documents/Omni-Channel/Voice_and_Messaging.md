# Voice and Messaging Configuration

> Verified from Salesforce on 2026-10-08. Org: Fullsandox · Org ID `00DVa000006Eh6TMAS`. Read-only retrieval (Metadata API); nothing was changed. Related: REQ-2026-10-08-001.

| Field | Value |
|---|---|
| Type | CallCenter, ConversationVendorInfo, MessagingChannel |
| Org | Fullsandox (00DVa000006Eh6TMAS) |
| Last verified | 2026-10-08 |
| Related records | REQ-2026-10-08-001 |

These components feed the `sfdc_phone` and `sfdc_livemessage` service channels. See [Service_Channels.md](Service_Channels.md).

> **Redaction.** The GitHub repository is public. The raw `CallCenter` and `ConversationVendorInfo` XML hold AWS account IDs, IAM and CloudFormation ARNs, the Amazon Connect instance ID, a telephony integration certificate and an AWS root email address. Those files are **not** stored here, and those values are shown as `[REDACTED]`. The full values are in the org (Setup → Call Centers / Contact Centers).

## Call centers (2)

### `TVMSBCC`: TVM Sandbox Call Center (Service Cloud Voice with Amazon Connect)

| Setting | Value |
|---|---|
| Display name | TVM Sandbox Call Center |
| Version | 21.1 |
| CTI adapter URL | `/hvcc/amz/index.html` |
| Use CTI API | true |
| Softphone height × width | 300 × 500 |
| Compatibility mode | Lightning |
| Telephony provider | AMAZON_CONNECT |
| Instance name | `TVMSBCC00DVa000006Eh6T` |
| Region | us-west-2 |
| Contact center channels | 1 voice channel (phone number not recorded here) |
| Connected App Id / REST API Connected App Id | `0H4Va0000003SFt` / `0H4Va0000003SFu` |
| Salesforce API version | 66.0 |
| Telephony integration key pair expiration | 27/07/2027 17:18:01 (as stored) |
| Unified routing enabled | true |
| Universal call recording access | true |
| Presence status sync access | false |
| Provider presence status sync | false |
| Omni connector readiness | false |
| Enhanced agent stability | false |
| Voice ID | false |
| Always show voice extension | false |
| Voice extension FlexiPage | `opencti__Amazon_voiceExtension_L` |
| Quick Connect for Omni-Channel flow transfers | "Quick Connect for Omni-Channel Flow Transfers" (ARN `[REDACTED]`) |
| Instance ID, service role, recording role, trusted role, stack ID, relay states, certificate | `[REDACTED]` |

### `RingCentral`: RingCentral (Open CTI)

| Setting | Value |
|---|---|
| Display name | RingCentral |
| CTI adapter URL | `https://teamvelocity--rcsfl.vf.force.com/apex/OpenCTIIndex` |
| Use CTI API | true |
| Softphone height × width | 450 × 300 |
| Compatibility mode | Classic_and_Lightning |
| Dialing prefixes (outside / long distance / international) | 9 / 1 / 01 |

The RingCentral adapter URL points at the `teamvelocity--rcsfl` domain, not at Fullsandox (`teamvelocity--fullsando`). Whether this call center is in use is NOT VERIFIED.

## Conversation vendor: `SERVICE_CLOUD_VOICE`

| Setting | Value |
|---|---|
| Label | Service Cloud Voice |
| Vendor type | Amazon_Connect |
| AWS tenant version | 1.18 |
| Connector URL | `https://teamvelocity--fullsando.sandbox.my.salesforce.com/hvcc/amz/index.html` |
| AWS account key, AWS root email | `[REDACTED]` |
| Unified routing supported | false |
| Queue management supported | false |
| Agent SSO supported | false |

The org also lists a second vendor, `awsac__awsscc`. The retrieve returned no file for it (probably a managed-package component), so it is not documented.

## Messaging channel: `WebChat`

| Setting | Value |
|---|---|
| Label | WebChat |
| Type | EmbeddedMessaging |
| Auth mode | UnAuth |
| Attachments | enabled; max 5 MB; types: xml, xls, xlsx, csv, docx, doc, txt, pdf, png, jpg, bmp, tiff, gif |
| Save transcript | true |
| Anonymous user JWT expiration | 360 |
| Agent availability check | false |
| Estimated wait time / queue position | false / false |
| Fallback message | false |
| Synchronous chat | false |
| Voice mode | false |
| Opt-out keywords (en_US) | cancel, end, quit, stop, stopall, unsubscribe |
| Help keyword (en_US) | help |
| Auto-responses (en_US) | OptOutConfirmation; HelpResponse |

The routing target of the `WebChat` channel (flow or queue) is not in the retrieved metadata. It is NOT VERIFIED.

## Source metadata

- [metadata/messagingChannels/](metadata/messagingChannels/): unmodified Metadata API XML.
- Call center and conversation vendor XML: not stored, for the redaction reason above.

## Change history

| Date | Change | Record |
|---|---|---|
| 2026-10-08 | Initial documentation (read-only retrieval) | REQ-2026-10-08-001 |
