# Ismael G. Marín Cabrera

## Staff Software Engineer & AI Engineer

### 20 Years of Backend Expertise Architecture | Building High-Performance Agentic AI Runtimes & MCP Tools (Ruby, Python, Rust)

[![Website](https://img.shields.io/badge/Website-ismaelmarin.dev-000000?style=flat-square&logo=google-chrome&logoColor=white)](https://ismaelmarin.dev/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-ismaelmarin-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/ismaelmarin)
[![RubyGems](https://img.shields.io/badge/RubyGems-igmarin-CC0000?style=flat-square&logo=rubygems&logoColor=white)](https://rubygems.org/profiles/igmarin)
[![Medium](https://img.shields.io/badge/Medium-@igmarin-000000?style=flat-square&logo=medium&logoColor=white)](https://medium.com/@igmarin)
[![Email](https://img.shields.io/badge/Email-ismael.marin@gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:ismael.marin@gmail.com)

> Moving AI Agents from "Vibe Coding" to Deterministic Production Realities. I build the runtimes, tools, and evaluation frameworks that give LLMs architectural discipline.

---

## 🚀 About me

I am a product-led engineer who has spent two decades scaling mission-critical distributed backend SaaS systems handling **10,000+ transactions per hour**. Today, I bridge that foundational experience directly into **AI Engineering**—not just writing prompts, but engineering multi-step runtimes, Model Context Protocol (MCP) servers, and high-fidelity empirical validation loops that make coding agents production-ready.

* **The Problem:** Probabilistic LLMs write code based on "vibes," leading to context token waste, architectural boundary breakages, and silent regressions.
* **The Solution:** Deterministic grounding. I build secure, isolated execution runtimes, structural introspection tools, and explicit markdown hard-gates that force AI agents to adhere to TDD and DDD discipline before mutating a single line of production code.

---

## 🧠 The AI Skill Ecosystem — Architectural Overview

I am actively designing and maintaining a modular, multi-language agent framework built to scale framework-specific context awareness and inject strict process discipline into autonomous code-generation loops.

```mermaid
flowchart TB
    User[User / AI Agent Prompt] --> Runtime

    subgraph Runtime["agent-mcp-runtime (Safe Rust CLI)"]
        Registry[Registry Resolver<br/>Pack priority & deprecation aliases]
        ReAct[ReAct Runner<br/>Thought → Action → Observation loops]
        MCP[MCP Server<br/>list_skills, use_skill,<br/>list_agents, use_agent, list_packs]
    end

    Runtime -->|reads tile.json from each auto-detected pack| Packs

    subgraph Packs["Skill Packs"]
        Core[core<br/>Always]
        Rails[rails<br/>Auto-detect]
        Hanami[hanami<br/>Auto-detect]
        Planning[planning<br/>Default Stack]
    end

    Packs --> Implementations

    subgraph Implementations["Skill Implementations"]
        RubyCore[ruby-core-skills]
        RailsAgent[rails-agent-skills]
        HanakiYaku[hanakai-yaku]
        AgnosticPlanning[agnostic-planning-skills]
    end

    Core --> RubyCore
    Rails --> RailsAgent
    Hanami --> HanakiYaku
    Planning --> AgnosticPlanning
```

### ⚙️ Core Repositories & Components

#### ⚡ [agent-mcp-runtime](https://github.com/igmarin/agent-mcp-runtime) (The Flagship Safe Rust CLI Engine)

An agentic framework runtime built entirely in safe Rust to compose atomic skills from multiple separate packs via the Model Context Protocol.

* **Strict Compile-Time Safety:** Zero unsafe code permitted (`#[deny(unsafe_code)]`) with rigid workspace linting gates.
* **Asynchronous ReAct Runner:** Orchestrates multi-step reasoning and action loops using customizable LLM providers via a factory service (`LlmProviderFactory`).
* **Model Context Protocol (MCP) Client:** Integrates external tools by spawning long-running subprocesses and exchanging JSON-RPC 2.0 messages over standard I/O streams with isolated runners.
* **Dynamic Context Merging:** Automatically scans project roots (e.g., parses a `Gemfile`), auto-detects the active framework (Rails or Hanami), hot-loads matching local/remote skill packs, and maps outputs transparently into database, routing, or architectural model context tiers.
* **Mockable Skill Pack Caching:** Employs git resolvers (`SkillSourceResolver`) backed by a mockable `GitRunner` interface for fully offline, blazingly fast execution testing and safe error cleanup.
* **TDD Frontmatter Parser:** Parses Markdown frontmatter to seamlessly extract execution metadata and constraints for agent skills/tools.

#### 📦 Specialized Skill Packs (Independently validated on Tessel with scores >93%)

* **[rails-agent-skills](https://github.com/igmarin/rails-agent-skills):** Rails-specific development workflows compiling 43 available skills and 9 specialized autonomous agents (*tdd, review, setup, quality, engine, bug-fix, graphql, migration, background-job*).
* **[hanakai-yaku](https://github.com/igmarin/hanakai-yaku):** Dedicated agentic development skill library containing 50 available skills optimized explicitly for the Hanami 2.x, `dry-rb`, and Repository Object Mapper (ROM) ecosystem.
* **[ruby-core-skills](https://github.com/igmarin/ruby-core-skills):** Base orchestration layer providing 15 atomic skills covering foundational refactoring, code formatting, security audits, and automated test planning discipline.
* **[agnostic-planning-skills](https://github.com/igmarin/agnostic-planning-skills):** Language-agnostic project planning engine delivering 10 unique skills across 4 specialized management roles (*delivery-lead, product-owner, project-manager, tech-lead*).

#### 🛠️ Tooling & Context Layer

* **[ruby-skill-bench](https://github.com/igmarin/ruby-skill-bench):** An empirical evaluation engine measuring the direct "ROI of Context" for AI skills. Automatically orchestrates secure, isolated Git-based sandboxes ensuring 100% execution reproducibility and runs multi-dimensional LLM blind judging (*Correctness, Quality, Test Coverage*) to eliminate regressions.
* **[rails-ai-bridge](https://github.com/igmarin/rails-ai-bridge):** A zero-configuration MCP server providing instant, read-only system introspection tools (routes, models, database schemas, active jobs) directly to AI assistants. Reduces token overhead by ~15% via smart presets while accelerating response precision.

---

## 🛠️ Deep Technical Stack

| Core Frameworks                                                                                                | AI Engineering                                                                                                 | Agentic Tools                                                                                       | System Architecture                                                                     | Systems & Infra                                                                                               |
| :--------------------------------------------------------------------------------------------------------------| :-------------------------------------------------------------------------------------------------------------| :----------------------------------------------------------------------------------------------------| :----------------------------------------------------------------------------------------| :--------------------------------------------------------------------------------------------------------------|
| ![RoR](https://img.shields.io/badge/Ruby_on_Rails-CC0000?style=flat-square&logo=ruby-on-rails&logoColor=white) | ![MCP](https://img.shields.io/badge/MCP_Server_Design-1F4E79?style=flat-square)                                | ![Cursor](https://img.shields.io/badge/Cursor-13ADC7?style=flat-square&logo=cursor&logoColor=white) | ![DDD](https://img.shields.io/badge/DDD_/_DDD-8A2BE2?style=flat-square)                 | ![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=flat-square&logo=cloudflare&logoColor=white) |
| ![Ruby](https://img.shields.io/badge/Ruby-CC0000?style=flat-square&logo=ruby&logoColor=white)                  | ![LangGraph](https://img.shields.io/badge/LangGraph-2C3E50?style=flat-square)                                  | ![Claude Code](https://img.shields.io/badge/Claude_Code-D4A27F?style=flat-square)                   | ![TDD](https://img.shields.io/badge/TDD_/_RSpec-2E8B57?style=flat-square)               | ![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazon-aws&logoColor=white)             |
| ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)            | ![LLM APIs](https://img.shields.io/badge/LLM_APIs-8E75B2?style=flat-square&logo=google-gemini&logoColor=white) | ![Devin](https://img.shields.io/badge/Devin.ai-4B32C3?style=flat-square&logo=devdotto&logoColor=white)                               | ![Clean Arch](https://img.shields.io/badge/Clean_Architecture-007ACC?style=flat-square) | ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)           |
| ![Rust](https://img.shields.io/badge/Rust-000000?style=flat-square&logo=rust&logoColor=white)                  | ![DeepSeek](https://img.shields.io/badge/DeepSeek-000000?style=flat-square&logo=deepseek&logoColor=white)      | ![Sandboxing](https://img.shields.io/badge/Isolated_Sandboxes-10B981?style=flat-square)             | ![SOA](https://img.shields.io/badge/SOA_/_Microservices-FF570A?style=flat-square)       | ![Postgres](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) |

---

## 📈 Proven Production Impact

* **Dealerware (Software Technical Lead):** Directed cross-functional distributed squads across 20+ production codebases. Maintained exceptional individual contributor velocity (370+ merged PRs) on frameworks handling 10,000+ hourly transactions. Led a zero-downtime search infrastructure overhaul migrating from Elasticsearch to OpenSearch, and elevated core system test coverage from 55% to 80% via AI-assisted edge case discovery.
* **3Pillar Global (Lead Software Engineer):** Modernized legacy enterprise monolithic codebases by enforcing structured Domain-Driven Design (DDD) principles and Service Objects, and designed a comprehensive end-to-end multi-region i18n framework from scratch.
* **MagmaLabs (Senior Engineering Manager):** Guided company-wide high-throughput e-commerce integrations, scaling progressive checkout workflows, advanced subscription layers, and complex multi-region payment gateways across the Spree and Solidus ecosystems.

---

## 🤝 Let's Collaborate

I am actively open to **Senior Software Engineer (Ruby/Rust)** or **AI Engineering** roles (Remote, Americas or EMEA) where technical precision, structural code design, and robust automated workflows intersect.

* 💬 **Want to discuss agentic runtime internals or MCP tools?** Open an issue or a discussion thread directly in [agent-mcp-runtime](https://github.com/igmarin/agent-mcp-runtime).
* 💼 **Looking for a disciplined engineer to scale your backend platform or operationalize secure AI infrastructure?** Let's connect via [LinkedIn](https://linkedin.com/in/ismaelmarin) or reach out directly at [ismael.marin@gmail.com](mailto:ismael.marin@gmail.com).

![GitHub stats](https://github-readme-stats.vercel.app/api?username=igmarin&show_icons=true&theme=github_dark&hide_border=true&include_all_commits=true&count_private=true)
