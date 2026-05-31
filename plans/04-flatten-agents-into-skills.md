# Plan 4: Flatten Agents into Orchestrator Skills

**Status:** Pending
**Priority:** After Plans 1 and 3
**Estimated effort:** 1-2 weeks
**Depends on:** Plan 1 (ecosystem cleanup)

## Objective

Move all agents from the `agents/` directory into `skills/` as "orchestrator" type skills across all 3 skill repositories. This eliminates the agents/skills conceptual confusion and aligns with the unified skill abstraction (`type: atomic | orchestrator`).

## Rationale

Current "agents" are deterministic sequences (tdd, review, setup, quality, etc.) — not autonomous agents. They don't have tool selection, goal decomposition, or error recovery. They are workflows that sequence atomic skills under defined behavioral rules. Renaming them as orchestrator skills is architecturally honest and eliminates confusion.

Modern LLM clients (Cursor Agent, Claude Code, Codex) already perform implicit ReAct loops. They don't need a separate "agent" abstraction to sequence steps — they need clear instructions about when to invoke which capability.

## Changes to igmarin/rails-agent-skills

### 1. Create new directory structure

```
skills/
├── api/
├── code-quality/
├── context/
├── engines/
├── infrastructure/
├── testing/
└── workflows/  ← NEW — for orchestrator skills
```

### 2. Move and rename agent files

| From | To |
|------|-----|
| `agents/tdd/SKILL.md` | `skills/workflows/tdd-workflow.md` |
| `agents/quality/SKILL.md` | `skills/workflows/quality-workflow.md` |
| `agents/review/SKILL.md` | `skills/workflows/review-workflow.md` |
| `agents/setup/SKILL.md` | `skills/workflows/setup-workflow.md` |
| `agents/bug-fix/SKILL.md` | `skills/workflows/bug-fix-workflow.md` |
| `agents/migration/SKILL.md` | `skills/workflows/migration-workflow.md` |
| `agents/graphql/SKILL.md` | `skills/workflows/graphql-workflow.md` |
| `agents/background-job/SKILL.md` | `skills/workflows/background-job-workflow.md` |
| `agents/engine/SKILL.md` | `skills/workflows/engine-workflow.md` |

### 3. Update frontmatter for each moved file

Add `type: orchestrator` and new metadata fields. Example for `tdd-workflow.md`:

```yaml
---
name: tdd-workflow
type: orchestrator
license: MIT
description: >
  Orchestrates the full Rails test-driven development cycle...
metadata:
  version: 1.0.0
  user-invocable: "true"
  entry_point: "Invoke when practicing test-driven development..."
  phases: "Phase 1: Context & Test Design, Phase 2: Implementation, Phase 3: Iterate, Phase 4: Finish"
  hard_gates: "Test Feedback, Proposal Checkpoint, Implementation Verification, Quality Check"
  dependencies:
    - source: self
      skills: [load-context, plan-tests, write-tests, code-review]
    - source: ruby-core-skills
      skills: [tdd-process, write-yard-docs]
  triggers:
    - "implement feature"
    - "add behavior"
    - "new code"
    - "tdd"
    - "test-driven development"
  keywords: rails, tdd, workflow, feature, implementation, testing, orchestration
---
```

Change titles from "# TDD Agent" to "# TDD Workflow" in the content body.

### 4. Update directory.json

Add the new orchestrator skills to the `"skills"` section:

```json
"skills": {
  "tdd-workflow":            { "path": "skills/workflows/tdd-workflow.md" },
  "quality-workflow":        { "path": "skills/workflows/quality-workflow.md" },
  "review-workflow":         { "path": "skills/workflows/review-workflow.md" },
  "setup-workflow":          { "path": "skills/workflows/setup-workflow.md" },
  "bug-fix-workflow":        { "path": "skills/workflows/bug-fix-workflow.md" },
  "migration-workflow":      { "path": "skills/workflows/migration-workflow.md" },
  "graphql-workflow":        { "path": "skills/workflows/graphql-workflow.md" },
  "background-job-workflow": { "path": "skills/workflows/background-job-workflow.md" },
  "engine-workflow":         { "path": "skills/workflows/engine-workflow.md" }
}
```

### 5. Delete obsolete files

- Delete `agents/` directory entirely
- Delete `agents.json`
- Delete `AGENTS.md`

### 6. Update README.md

- Remove references to "agents" directory
- Update count from "28 skills + 9 agents" to "28 atomic skills + 9 orchestrator workflows"
- Add a section:

```markdown
## Skill Types

**Atomic Skills:** Single-purpose capabilities (e.g., `refactor-code`, `write-tests`). These do one thing well.

**Orchestrator Workflows:** Multi-step processes that sequence atomic skills (e.g., `tdd-workflow`, `quality-workflow`). These define the order and hard gates for complex tasks.
```

### 7. Bump version to 7.0.0

This is a breaking change — bump major version in `directory.json` and `CHANGELOG.md`.

---

## Changes to igmarin/hanakai-yaku

Apply the same pattern:

1. Move `agents/` content to `skills/workflows/`
2. Add `type: orchestrator` to frontmatter of each moved file
3. Update `directory.json` — move agent entries to skills section
4. Delete `agents.json` and `AGENTS.md`
5. Update `README.md` to reflect "35 atomic skills + 10 orchestrator workflows"

---

## Changes to igmarin/agnostic-planning-skills

Apply the same pattern:

1. Move `agents/` content to `skills/workflows/`
2. Add `type: orchestrator` to frontmatter
3. Update `directory.json`
4. Delete `agents.json` and `AGENTS.md`
5. Update `README.md`

---

## New Vocabulary (Use Everywhere)

| Old Term | New Term | Definition |
|----------|----------|------------|
| Agent | Orchestrator Skill | A workflow that sequences atomic skills with hard gates |
| Skill | Atomic Skill | A single capability (write tests, review code, etc.) |
| Hard Gate | Process Gate | An eval-enforced checkpoint (was the rule followed?) |

Stop using the word "agent" in repositories. It creates expectations of autonomy that deterministic workflows cannot fulfill.

---

## Future: Real Autonomous Agents (Separate Phase)

After flattening is complete and validated, explore building **real autonomous agents** as a separate research project. These would be fundamentally different:

| Feature | Current Workflows | Real Agents |
|---------|-------------------|-------------|
| Tool selection | Pre-defined sequence | Dynamic, goal-based |
| Error recovery | Stop at hard gate | Adapt and retry |
| Autonomy | None — follows steps | Decides what to do |
| Memory | None | Cross-interaction context |
| Goal decomposition | Manual (you write the steps) | Automatic |

**Technologies to study:** LangGraph, AutoGen, CrewAI, Claude Code's agent architecture.

**Do not start this until:**
- Flattening is complete
- Demand for orchestrator workflows is validated
- Existing agent frameworks have been studied

---

## Success Criteria

- [ ] All 3 repos have `agents/` removed
- [ ] All 3 repos have `agents.json` and `AGENTS.md` removed
- [ ] All orchestrator skills live in `skills/workflows/`
- [ ] All orchestrator skills have `type: orchestrator` in frontmatter
- [ ] `directory.json` updated in all 3 repos
- [ ] READMEs updated with new vocabulary
- [ ] Major version bumped in all 3 repos
