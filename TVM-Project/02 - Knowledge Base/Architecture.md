# Architecture — TVM

> Starter document. Record only architecture that has been verified from the org or source, or that the user has provided. Do not infer.

## Environments

| Environment | Alias | Org ID | Type | Status |
|---|---|---|---|---|
| TVM working sandbox | `Fullsandox` | `00DVa000006Eh6TMAS` | Sandbox (Unlimited Edition) | VERIFIED 2026-10-06 |
| TVM production | — | — | Production | UNKNOWN (not authenticated or verified; human-controlled) |

## Data model (key objects)

UNKNOWN

## Automation (flows, Apex, triggers)

UNKNOWN

## User interface (Lightning apps, LWC, page layouts)

UNKNOWN

## Omni-Channel / routing

**VERIFIED** (source: Fullsandox metadata, 2026-10-08, REQ-2026-10-08-001)

- Service channels: `Case` (Case), `sfdc_phone` (VoiceCall) and `sfdc_livemessage` (MessagingSession).
- Cases are routed through 3 priority-based, skills-based routing configs (High/Medium/Low) and an overflow config for General Support. Skills come from the `Skill_based_rules_for_cases` rule set.
- Voice uses Service Cloud Voice with Amazon Connect (call center `TVMSBCC`). 6 active voice routing flows send calls to Phone Support / FD Phone Support queues, or skills-based through `TVM_Voice_Routing_Config`. One active Case routing flow (`Case_General_Support_Router`) routes Cases to a queue that is passed in as an input.
- Presence configuration `TVM_V1`: capacity 10.

Details: [07 - Technical Documents/Omni-Channel/](../07%20-%20Technical%20Documents/Omni-Channel/README.md)

## Integrations

UNKNOWN

## Security model (profiles, permission sets, sharing)

UNKNOWN

## Known dependencies

UNKNOWN
