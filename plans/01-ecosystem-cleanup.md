# Plan 1: Ecosystem Cleanup and Consulting Launch Prep

**Status:** Pending
**Priority:** Immediate (this week)
**Estimated effort:** 1-2 days

## Objective

Clean up repository portfolio to align with "Rails AI Tooling Engineer" positioning. Archive dead projects, update stale READMEs, and configure GitHub profile for consulting credibility.

## Tasks

### 1. igmarin/hanakai-yaku — Update README

- Update README.md line 6 to accurately reflect the actual skill count (35 skills + 10 agents) instead of the stale "3 initial skills and 1 agent (expanding to 18 skills + 3 agents)". The `directory.json` already lists all 35 skills. Make the README match reality.
- Add a "Status" section near the top:

> **Status:** Experimental — used to validate skill format portability across Ruby frameworks. Not actively maintained as a product. For production Rails AI tooling, see [rails-ai-bridge](https://github.com/igmarin/rails-ai-bridge).

### 2. igmarin/agent-mcp-runtime — Archive

- Update README.md to add an archive notice at the top:

> **⚠️ Archived:** This project served as a Rust learning project and ecosystem prototype. The registry resolution logic (PackResolverService, RegistryManifest, TileManifest) is being ported to rails-ai-bridge. This repository is archived.

- Archive the repository on GitHub (Settings > Archive)

### 3. igmarin/agnostic-planning-skills — Reposition

- Update README.md to add honest positioning:

> Internal planning workflow for consulting engagements, open-sourced. These skills are used by the maintainer for structured project discovery and PRD workflows. They are not a standalone product.

### 4. igmarin/rails-agent-skills — No changes yet

- The `agents/` directory stays as-is until Plan 4 (flatten agents into skills) is executed.

### 5. GitHub Profile (igmarin/igmarin)

- Pin only: `rails-ai-bridge` and `ruby-skill-bench`
- Ensure profile bio reflects "Rails AI Tooling Engineer" positioning, not "AI ecosystem architect"

## Success Criteria

- [ ] hanakai-yaku README matches directory.json skill count
- [ ] agent-mcp-runtime is archived on GitHub
- [ ] agnostic-planning-skills README has honest positioning
- [ ] GitHub profile pins only rails-ai-bridge and ruby-skill-bench
