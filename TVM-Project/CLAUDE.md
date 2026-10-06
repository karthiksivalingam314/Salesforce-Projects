# CLAUDE.md — TVM-Project

This file gives Claude Code its permanent operating rules for the **TVM (Team Velocity Marketing)** project. It applies to all work inside `TVM-Project/`.

Read these before any TVM work:

- [01 - Instruction/Salesforce_Working_Instructions.md](01%20-%20Instruction/Salesforce_Working_Instructions.md): general Salesforce operating principles
- [01 - Instruction/Org_Selection_Rules.md](01%20-%20Instruction/Org_Selection_Rules.md): how to select and verify the TVM org

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

1. Verify the TVM working org (see [Org_Selection_Rules.md](01%20-%20Instruction/Org_Selection_Rules.md)).
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
| User gives a new TVM requirement | `03 - Requirements/YYYY-MM-DD/REQ-YYYY-MM-DD-###.md` | [03 - Requirements/README.md](03%20-%20Requirements/README.md) |
| Claude actually implements a change | `04 - Change Records/YYYY-MM-DD/CHG-YYYY-MM-DD-###.md` | [04 - Change Records/README.md](04%20-%20Change%20Records/README.md) |
| Meaningful failure (implementation, test, validation, deployment, configuration, Git) | `05 - Conflicts/YYYY-MM-DD/CON-YYYY-MM-DD-###.md` | [05 - Conflicts/README.md](05%20-%20Conflicts/README.md) |
| Salesforce deployment or validation actually runs | `06 - Deployment/YYYY-MM-DD/DEP-YYYY-MM-DD-###.md` | [06 - Deployment/README.md](06%20-%20Deployment/README.md) |
| Meaningful technical change | `07 - Technical Documents/<Category>/` | [07 - Technical Documents/README.md](07%20-%20Technical%20Documents/README.md) |
| New verified project knowledge | `02 - Knowledge Base/` | [02 - Knowledge Base/README.md](02%20-%20Knowledge%20Base/README.md) |

Rules:

- **Requirements:** create the REQ record automatically as soon as a new requirement arrives, before implementation.
- **Changes:** create a CHG record only for changes that were really made. Link it to its REQ.
- **Conflicts:** never guess a root cause. If it is not verified, write `NOT VERIFIED`.
- **Deployments:** never claim success without Salesforce evidence (deploy ID, status output). See section 5.
- **Technical docs:** document only verified Salesforce configuration and metadata, with real API names.

## 5. Deployment documentation (permanent rule)

The official deployment reference/template is **`06 - Deployment/TVM - Deployment Document.xlsx`**. Its structure and record template are summarised in [06 - Deployment/README.md](06%20-%20Deployment/README.md). The workbook is a reference only. It is **not** evidence that any deployment occurred in this project, and it must never be modified or turned into deployment records.

Whenever a task **actually involves a deployment or validation event** in Salesforce, do the following automatically, without asking the user:

1. Read the deployment reference document (the workbook, plus the summary in `06 - Deployment/README.md`).
2. Follow its structure and relevant fields: item categories, columns, and per-item deployment and rollback/current status.
3. Create or update the dated record `06 - Deployment/YYYY-MM-DD/DEP-YYYY-MM-DD-###.md`.
4. Record every actual deployment item separately.
5. Record each item's actual status.
6. Record the overall deployment status.
7. Record pre-deployment checks and post-deployment verification.
8. Record testing and validation results.
9. Record rollback/recovery information.
10. Cross-reference the related Requirement (`REQ-...`) and Change Record (`CHG-...`), and record the actual target org (alias, username, Org ID, instance URL).
11. Record Git commit and push information only after the actual Git operation has happened.

Constraints:

- **Do not** create a deployment record just because the word "deployment" appears in a requirement. A record represents an actual deployment or validation event with Salesforce evidence.
- Record only what actually happened or was verified. Never record invented components, statuses, IDs, test results, or deployment results.
- Example records shown in conversation are format examples only, never project data.
- Production deployment remains human-controlled. Claude does not deploy to Production.

## 6. Git rules

- Run `git status` and review `git diff` before staging, and confirm that only `TVM-Project/` files changed.
- Stage files explicitly by path. Never use `git add .` or `git add -A`.
- Never stage `.sf/`, `.sfdx/`, `node_modules/`, `.env`, credentials, tokens, logs, or other projects' files.
- Push to `origin main`. **Never force push.** If a push fails, stop and report.

## 7. When in doubt

Stop and ask if any required information (org, API name, scope, acceptance criteria) cannot be verified.
