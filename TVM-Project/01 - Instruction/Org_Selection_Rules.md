# Org Selection Rules — TVM

```
TVM_WORKING_ORG = Fullsandox
```

## Verified TVM working org

Verified on 2026-10-06 with Salesforce CLI (`sf org list`, `sf org display --target-org "Fullsandox"`, and a read-only SOQL query on `Organization`).

| Property | Verified value |
|---|---|
| Alias | `Fullsandox` |
| Username | `sandipp@unitedtechno.com.tvmprod.fullsando` |
| Org ID | `00DVa000006Eh6TMAS` |
| Instance URL | `https://teamvelocity--fullsando.sandbox.my.salesforce.com` |
| Login URL | `https://test.salesforce.com/` |
| Organization name | Team Velocity Marketing |
| Sandbox | Yes (`Organization.IsSandbox = true`) |
| Edition | Unlimited Edition |
| Instance | `USA712S` |
| Connection status at verification | Connected |

Why this org was identified as the TVM environment:

- The organization name is **Team Velocity Marketing** (TVM).
- The My Domain is `teamvelocity--fullsando` (a sandbox named `fullsando` of the `teamvelocity` domain).
- The username suffix is `.tvmprod.fullsando`.
- It is the only authenticated org whose organization name is Team Velocity Marketing.

## CLI default org

On 2026-10-08, at the user's request, `Fullsandox` was set as the global Salesforce CLI default (`sf config set target-org=Fullsandox --global`; it was previously `agentforce-dev`). `TVM-Project/` has no `sfdx-project.json`, so a project-local default is not possible. Commands must still pass `--target-org "Fullsandox"` explicitly (rules 3 and 4 below).

## Mandatory rules before ANY Salesforce operation

1. Verify the TVM working org.
2. Never rely on the VS Code default org.
3. Never rely on the global or project `target-org` config.
4. Use `--target-org "Fullsandox"` on every Salesforce CLI command.
5. Verify the alias, username, Org ID and instance URL against the table above.
6. If the intended org cannot be positively identified, **STOP and ask**.
7. Never silently switch to another authenticated org.
8. Never use Production as an implementation target.

## Verification procedure

Run this at the start of any session that will touch Salesforce, and again before any deployment:

```bash
sf org display --target-org "Fullsandox" --json
```

Check that `id`, `username`, `instanceUrl` and `alias` match the table above. **Never print or record `accessToken` or `sfdxAuthUrl`.**

To confirm the sandbox status (read-only):

```bash
sf data query --target-org "Fullsandox" --query "SELECT Id, Name, IsSandbox FROM Organization"
```

Expected: `Id = 00DVa000006Eh6TMAS`, `Name = Team Velocity Marketing`, `IsSandbox = true`.

If any value differs (for example, after a sandbox refresh changes the Org ID), **stop and ask the user** before continuing. Update this file only after the user confirms the new values.

## Other authenticated orgs (NOT for TVM)

Other orgs authenticated on this machine at setup time are **not** TVM targets. They include Developer Edition orgs and orgs belonging to other clients, one of which is a production org (alias `PROD`, not TVM). Never use any of them for TVM work.
