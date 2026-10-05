# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Salesforce development workflow (required)

Follow these steps for every Salesforce development task the user requests. The user has authorized the deploy, commit and push steps below in advance, so you don't need to ask again for each task.

1. **Scope:** work only inside `Devorg-Project/`. Don't touch `TVM-Project/`, `agentforce-learning/` or any other sibling project.
2. **Target org:** use `agentforce-dev`. Pass `--target-org agentforce-dev` explicitly on every `sf` command instead of relying on the default.
3. **Implement:** make the requested changes in the local project, under `force-app/`.
4. **Validate and test:** run the relevant checks before deploying:
   - Apex: `sf apex run test --tests <TestClass> --result-format human --synchronous --code-coverage --target-org agentforce-dev`
   - LWC/Aura: `npm run lint` and `npm test` (or the specific Jest file)
   - Metadata: `sf project deploy validate --source-dir <changed paths> --target-org agentforce-dev` (or `deploy start --dry-run`)
5. **Deploy:** `sf project deploy start --source-dir <changed paths> --target-org agentforce-dev`. Deploy only the components you changed.
6. **Review the diff** (only if tests and deploy succeeded): run `git status` and `git diff`, and confirm that every change belongs to this task and to `Devorg-Project/`. Leave unrelated changes unstaged. This includes pre-existing changes elsewhere in the repo, such as the `TVM-Project` files.
7. **Commit:** stage the relevant files explicitly by path (never `git add -A` or `git add .` from the repo root) and commit with a clear, descriptive message.
8. **Push:** `git push origin main`, without asking first.
9. **Never force push.** No `--force` or `--force-with-lease`. If the push is rejected, stop and report back instead of rewriting history.
10. **Never commit** credentials, tokens, auth URLs, `.sf/`, `.sfdx/`, `.env`, `node_modules/`, logs, or changes from unrelated projects.
11. **On failure:** if validation, tests or deployment fail, don't commit or push. Report the failure with the relevant error output.

## Repository layout

This repo is a container for several **independent Salesforce DX projects**. Each subfolder has its own `sfdx-project.json`, `package.json`, `.forceignore` and `.sf/config.json`. Run `sf` and `npm` commands from inside the project folder you're working on, not from the repo root.

| Project | Default target org (`.sf/config.json`) | API version | Notes |
|---|---|---|---|
| `Devorg-Project/` | `agentforce-dev` | 66.0 | Standard SFDX template (LWC Jest, ESLint, Prettier, Husky). No metadata in `force-app` yet. |
| `TVM-Project/` | `Fullsandox` | 66.0 | Same template as Devorg. **Points at a full sandbox**, so check before deploying. `TVM-Project-Backup/` is a leftover staged copy. |
| `agentforce-learning/` | `Fullsandox` | 67.0 | Agentforce DX sample (Local Info Agent). Only has Prettier, no lint or Jest. |
| `agentforce-learning/agentforce-learning/` | — | — | Nested copy of the Agentforce project with more work in it: `United_Techno_Support_Agent`, `My_Test_Agent`, `bots/`, `genAiPlannerBundles/`, `specs/agentSpec.yaml`, `temp/agent-preview/` session traces. Before editing, confirm with the user which copy is the real one. |

The root `.gitignore` excludes `.sf/`, `.sfdx/`, `node_modules/`, `.env` and logs.

## Commands

Template projects (`Devorg-Project`, `TVM-Project`):

```bash
npm install
npm run lint                 # eslint on aura/lwc JS
npm test                     # sfdx-lwc-jest (all LWC unit tests)
npx sfdx-lwc-jest -- path/to/__tests__/myComp.test.js   # single test file
npx sfdx-lwc-jest -- -t "test name"                     # single test by name
npm run test:unit:coverage
npm run prettier             # format cls/cmp/js/xml/etc.
npm run prettier:verify
```

The Husky pre-commit hook runs `lint-staged`: Prettier on staged files, ESLint on aura/lwc JS, and related LWC Jest tests. Note that `.husky/` lives inside each project, not at the git root, so `npm run prepare` from a subproject may not install the hook.

`agentforce-learning` only provides `npm run prettier` and `npm run prettier:verify`.

Salesforce CLI (any project):

```bash
sf project deploy start --source-dir force-app            # deploy to default target org
sf project deploy start --metadata ApexClass:CheckWeather
sf project retrieve start --metadata ApexClass:Foo
sf apex run test --tests WeatherServiceTest --result-format human --synchronous   # single Apex test class
sf apex run test --class-names CurrentDateTest --code-coverage --result-format human
sf apex run --file scripts/apex/hello.apex
sf data query --file scripts/soql/account.soql
sf org create scratch --definition-file config/project-scratch-def.json --alias AgentScratchOrg --set-default --target-dev-hub DevHub
```

Pass `--target-org <alias>` to override the project default. Several projects default to `Fullsandox`, so be careful with deploys.

## Agentforce architecture (`agentforce-learning`)

An agent is defined by an **Agent Script** file: `force-app/main/default/aiAuthoringBundles/<Name>/<Name>.agent`, with a `.bundle-meta.xml` beside it (metadata type `AiAuthoringBundle`). The script is a YAML-like DSL:

- `system`, `config` (`developer_name`, `default_agent_user`, which is still the placeholder `UPDATE_WITH_YOUR_DEFAULT_AGENT_USER` in `Local_Info_Agent`), `variables` (`mutable` typed vars), `language`.
- `start_agent agent_router` routes to `subagent` blocks with `@utils.transition to @subagent.<name>`.
- Each `subagent` has `reasoning.instructions` (supports `if/else` and `available when` gating) and `actions` that bind to backing metadata.

Actions are backed by three kinds of metadata, all of which must be deployed for live-mode preview (simulated mode mocks them):

- **Invocable Apex**: `CheckWeather` (uses `WeatherService`, which returns mock data) and `CurrentDate`. Inputs and outputs are `@InvocableVariable` inner classes whose `description`s are what the agent's LLM reads, so keep them accurate.
- **Prompt Template**: `genAiPromptTemplates/Get_Event_Info`.
- **Flow**: `flows/Get_Resort_Hours` (returns hours plus a reservation-required flag that feeds the `reservation_required` variable).

Permissions: the `Resort_Agent` (agent user) and `Resort_Admin` permission sets are bundled into the `AFDX_Agent_Perms` and `AFDX_User_Perms` permission set groups. When you add a new Apex class or flow used by an agent, grant access through these sets.

Publishing an agent from the authoring bundle produces `bots/` (Bot and BotVersion) and `genAiPlannerBundles/` metadata. Treat those as generated output and edit the `.agent` file instead.

Agentforce-specific skills (`developing-agentforce`, `observing-agentforce`, `testing-agentforce`) are available from https://github.com/forcedotcom/sf-skills if deeper Agent Script guidance is needed.
