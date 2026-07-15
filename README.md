# drxs-expo-orbit-workflow

AI-assisted workflows for the full software development lifecycle — brainstorm, plan, build, and review — as a Claude Code plugin. Tech-agnostic by design; forked from [VGV Wingspan](https://github.com/VeryGoodOpenSource/vgv-wingspan) and paired with [drxs-ai-expo-plugin](../drxs-ai-expo-plugin) for React Native/Expo-specific conventions.

## Philosophy

Each step of the development cycle should make subsequent steps clearer and closer to the user's intent. Build the right thing, build the thing right.

## Tech-Agnostic by Design

drxs-expo-orbit-workflow handles the software development lifecycle — brainstorming, planning, building, and quality review. It does not enforce or assume any specific programming language, framework, or toolchain.

Technology-specific concerns (linting, formatting, scaffolding, framework conventions) belong in companion plugins. drxs-expo-orbit-workflow's recommendation system detects project types and suggests the appropriate companion plugin automatically — see [drxs-ai-expo-plugin](../drxs-ai-expo-plugin) for React Native/Expo projects.

## Installation

```text
/plugin marketplace add <your-marketplace-repo>
/plugin install drxs-expo-orbit-workflow
```

## Workflow

1. **`/brainstorm`** — Explore requirements and approaches through collaborative dialogue. Produces a brainstorm document.
2. **`/plan`** — Transform brainstorm output into an actionable implementation plan. Includes codebase review, optional external research, flow analysis, and a mandatory quality review of the draft.
3. **`/build`** — Execute implementation plans: implement one phase per context window, run quality review, and ship a pull request.

Standalone skills:

- **`/review`** — Run quality review agents on demand.
- **`/debrief`** — Produce a structured, blameless debrief document after an incident or significant bug.
- **`/hotfix`** — Streamlined workflow for emergency fixes. Skips brainstorm/planning but enforces review and testing.
- **`/create`** — Scaffold a new project by routing to the right companion plugin.
- **`/create-pr`** — Validate, commit, and open a pull request.
- **`/rebase`** — Sync the feature branch with the base branch.
- **`/plan-technical-review`** — Review externally-authored plans.
- **`/refine-approach`** — Iterative document improvement.

## Skills Reference

| Skill | Command | Description |
|-------|---------|-------------|
| **Brainstorm** | `/brainstorm <feature or idea>` | Explore requirements and approaches through collaborative dialogue |
| **Refine Approach** | `/refine-approach` | Review and refine brainstorms or plans before proceeding |
| **Plan** | `/plan <feature, bug fix, or improvement>` | Transform brainstorm output into a reviewed, phased implementation plan |
| **Plan Technical Review** | `/plan-technical-review <plan path>` | Review an externally-authored plan |
| **Build** | `/build <plan file path>` | Execute a plan — write code and tests, run quality review, ship a PR |
| **Review** | `/review [path]` | Run quality review agents on demand |
| **Hotfix** | `/hotfix <bug description>` | Apply a minimal, targeted fix for emergency bugs |
| **Create** | `/create <what to create>` | Scaffold a new project by routing to the right companion plugin |
| **Create PR** | `/create-pr` | Validate, stage, commit, push, and open a pull request |
| **Rebase** | `/rebase` | Rebase the current feature branch onto the base branch |
| **Debrief** | `/debrief <incident or context>` | Produce a structured post-incident analysis |

## Agents

| Agent | Description |
| ----- | ----------- |
| **Codebase Review** | Structure, conventions, and consistent pattern usage |
| **Architecture Review** | Layer separation, dependency direction, package structure |
| **Test Quality Review** | Coverage and testing conventions |
| **Code Simplicity Review** | YAGNI violations and simplification opportunities |
| **PR Readiness Review** | Formatting, static analysis, debug artifacts, commit hygiene |
| **Plan Splitting** | Recommends splitting large plans into mergeable PRs |
| **User Flow Analysis** | Flow gaps and edge cases |
| **Best Practices Research** | Stack-appropriate conventions, official docs, industry standards |
| **Official Docs Research** | Framework/library documentation gathering |

## Better Together: drxs-ai-expo-plugin

drxs-expo-orbit-workflow operates at a higher level, orchestrating agentic workflows across the full software development lifecycle. [drxs-ai-expo-plugin](../drxs-ai-expo-plugin) embeds React Native/Expo-specific best practices — navigation, state management, testing, security — directly into Claude Code, so AI-generated code follows production-quality standards from the first line.

## Output Directories

- `docs/brainstorm/` — Brainstorm documents from `/brainstorm`
- `docs/plan/` — Implementation plans from `/plan`
- `docs/reviews/` — Consolidated review from `/build` (ephemeral)
- `docs/hotfix-review/` — Consolidated review from `/hotfix` (ephemeral)
- `docs/code-review/` — Reviews from `/review` (standalone, user-managed)
- `docs/debriefs/` — Debrief documents from `/debrief`

## Key Conventions

- **State management:** Enforce consistent usage of the project's chosen pattern. Flag deviations for review.
- **YAGNI:** Prefer the simplest solution that meets current requirements. Remove hypothetical features.
- **Architecture:** Respect the project's established layer boundaries and dependency direction.
- **Testing:** Non-negotiable. Every testable unit gets tests.
