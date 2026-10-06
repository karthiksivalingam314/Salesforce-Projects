# Salesforce Working Instructions — TVM

These are the permanent operating principles Claude follows for all Salesforce work in the TVM project. They are based on the "Claude Salesforce Working Instructions" principles supplied by the user during project setup on 2026-10-06.

> **Source note:** The full original "Claude Salesforce Working Instructions" document was not present in the repository during setup. This file records the operating principles the user listed explicitly. If the full document is provided later, add it here or link it from here, and keep these principles.

The TVM-specific org rules are in [Org_Selection_Rules.md](Org_Selection_Rules.md).

---

## 1. Sandbox-first development

- All implementation, testing and validation happen in the approved TVM sandbox (`TVM_WORKING_ORG`, see [Org_Selection_Rules.md](Org_Selection_Rules.md)).
- Never use Production as an implementation target.

## 2. Never assume the Salesforce target org

- Several orgs are authenticated on this machine. The VS Code default org and the global or project `target-org` config are **not** trusted.
- Before any Salesforce operation, verify the **alias, username, Org ID and instance URL**.
- Pass `--target-org "<TVM_WORKING_ORG>"` explicitly on every Salesforce CLI command.

## 3. Never guess Salesforce API names

- Confirm object, field, flow, class, component, permission set, queue, report and dashboard API names from org metadata or local source before using them.
- If an API name cannot be verified, stop and ask.

## 4. Inspect before changing

- Retrieve or inspect the relevant metadata and source before modifying anything.
- Understand the current state ("before state") and record it in the change record.

## 5. Impact analysis before implementation

Before implementing, identify:

- the components affected directly
- dependent components (flows, Apex, validation rules, layouts, permissions, integrations, reports)
- the effect on existing data and users
- the risks, and how to roll back

## 6. Stay within scope

- Implement only what the current requirement asks for.
- Do not refactor, clean up, or "improve" unrelated components without approval.
- Raise out-of-scope findings as notes or open questions. Do not act on them.

## 7. Do not expose secrets or production data

- Never write access tokens, refresh tokens, auth URLs, passwords, or client secrets to files, commits, logs, or chat output.
- Never copy production data into documentation, test classes, or the repository.

## 8. Tests must verify real behaviour

- Tests must assert actual business outcomes, not just execute code for coverage.
- Do not write tests that are designed only to pass.
- Report test failures faithfully, with their output.

## 9. Production deployment remains human-controlled

- Claude does not deploy to Production.
- Claude may prepare deployment artifacts and documentation for a human to review and run.

## 10. Stop and ask when required information cannot be verified

- If the org, API names, scope, acceptance criteria, or any other required fact cannot be verified, **stop and ask the user**. Do not guess.

---

## Documentation obligations

For each piece of work, Claude records only facts that actually occurred, using these locations:

| Event | Record |
|---|---|
| New requirement | `Requirements/YYYY-MM-DD/REQ-YYYY-MM-DD-###.md` |
| Implemented change | `Change Records/YYYY-MM-DD/CHG-YYYY-MM-DD-###.md` |
| Meaningful failure | `Conflicts/YYYY-MM-DD/CON-YYYY-MM-DD-###.md` |
| Deployment or validation | `Deployment/YYYY-MM-DD/DEP-YYYY-MM-DD-###.md` |
| Technical change | `Technical Documents/<Category>/` |

Each folder's `README.md` contains the required template.
