# CLAUDE.md — TVM-Project

This file gives Claude Code its permanent operating rules for the **TVM (Team Velocity Marketing)** project. It applies to all work inside `TVM-Project/`.

Read these before any TVM work:

- [Instruction/Salesforce_Working_Instructions.md](Instruction/Salesforce_Working_Instructions.md): general Salesforce operating principles
- [Instruction/Org_Selection_Rules.md](Instruction/Org_Selection_Rules.md): how to select and verify the TVM org

---

## 1. Approved working org

```
TVM_WORKING_ORG = Fullsandox
```

| Property | Verified value (2026-10-06) |
|---|---|
| Alias | `Fullsandox` |
| Username | `sandipp@unitedtechno.com.tvmprod.fullsando` |
| Org ID | `00DVa000006Eh6TMAS` |
| Instance URL | `https://teamvelocity--fullsando.sandbox.my.salesforce.com` |
| Org name | Team Velocity Marketing |
| Environment | Sandbox (`Organization.IsSandbox = true`), Unlimited Edition, instance `USA712S` |

This is the only approved implementation target for TVM.

## 2. Mandatory org rules (before ANY Salesforce operation)

1. Verify the TVM working org (see [Org_Selection_Rules.md](Instruction/Org_Selection_Rules.md)).
2. Never rely on the VS Code default org.
3. Never rely on the global or project `target-org` config.
4. Pass `--target-org "Fullsandox"` explicitly on every Salesforce CLI command.
5. Check that the alias, username, Org ID and instance URL match the table above.
6. If the intended org cannot be positively identified, **STOP and ask**.
7. Never silently switch to another authenticated org.
8. Never use Production as an implementation target. Production deployment is human-controlled.

## 3. Scope

- Work only inside `TVM-Project/`. Do not modify `Devorg-Project/`, `agentforce-learning/`, or anything else in the repository unless the user explicitly asks.
- Stay within the scope of the current requirement. Do not make unrequested changes.
- Never guess Salesforce API names. Inspect metadata or source first.
- Do an impact analysis before implementing anything.
- Never expose secrets, tokens, auth URLs, or production data in files, commits, or output.

## 4. Documentation automation

Use today's date (`YYYY-MM-DD`) for dated folders, and give IDs sequential numbers (`###` = 001, 002, ...) per day. Only create a dated folder when there is a real record to put in it. **Record only facts that actually occurred, and never invent missing information.** Mark unknowns as `UNKNOWN` or `NOT PROVIDED`.

| Trigger | Location | Template |
|---|---|---|
| User gives a new TVM requirement | `Requirements/YYYY-MM-DD/REQ-YYYY-MM-DD-###.md` | [Requirements/README.md](Requirements/README.md) |
| Claude actually implements a change | `Change Records/YYYY-MM-DD/CHG-YYYY-MM-DD-###.md` | [Change Records/README.md](Change%20Records/README.md) |
| Meaningful failure (implementation, test, validation, deployment, configuration, Git) | `Conflicts/YYYY-MM-DD/CON-YYYY-MM-DD-###.md` | [Conflicts/README.md](Conflicts/README.md) |
| Salesforce deployment or validation actually runs | `Deployment/YYYY-MM-DD/DEP-YYYY-MM-DD-###.md` | [Deployment/README.md](Deployment/README.md) |
| Meaningful technical change | `Technical Documents/<Category>/` | [Technical Documents/README.md](Technical%20Documents/README.md) |
| New verified project knowledge | `Knowledge Base/` | [Knowledge Base/README.md](Knowledge%20Base/README.md) |

Rules:

- **Requirements:** create the REQ record automatically as soon as a new requirement arrives, before implementation.
- **Changes:** create a CHG record only for changes that were really made. Link it to its REQ.
- **Conflicts:** never guess a root cause. If it is not verified, write `NOT VERIFIED`.
- **Deployments:** never claim success without Salesforce evidence (deploy ID, status output).
- **Technical docs:** document only verified Salesforce configuration and metadata, with real API names.

## 5. Git rules

- Run `git status` and review `git diff` before staging, and confirm that only `TVM-Project/` files changed.
- Stage files explicitly by path. Never use `git add .` or `git add -A`.
- Never stage `.sf/`, `.sfdx/`, `node_modules/`, `.env`, credentials, tokens, logs, or other projects' files.
- Push to `origin main`. **Never force push.** If a push fails, stop and report.

## 6. When in doubt

Stop and ask if any required information (org, API name, scope, acceptance criteria) cannot be verified.
