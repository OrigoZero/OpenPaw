# 🐾 OpenPaw

> **Coming Soon** — An advanced safety first AI agent framework written in Rust with persistent memory, dynamic skills, adaptive learning and multi-platform support.

[![Rust](https://img.shields.io/badge/rust-%23000000.svg?style=for-the-badge&logo=rust&logoColor=white)](https://www.rust-lang.org/)
[![License](https://img.shields.io/badge/license-LGPL%20%2F%20Commercial-blue.svg?style=for-the-badge)](LICENSE)

---

## Overview

**OpenPaw** is a sophisticated AI agent framework built in Rust that combines the power of modern language models with a robust skill system, persistent memory, and multi-platform integration. Designed for developers who want to build intelligent, context-aware assistants with enterprise-grade safety and extensibility.

### Why OpenPaw?

- **🧠 Persistent Memory** — Three-tiered memory system (Critical/Essential/Context) ensures your agent never forgets important information
- **🔌 Multi-Provider Support** — Seamlessly switch between Anthropic Claude, OpenAI, Google Gemini, and more
- **🛡️ Safety-First Architecture** — Configurable guardrails (pattern + AI-based), secret vault protection, and granular permission system
- **🎯 Dynamic Skill System** — Extensible plugin architecture with marketplace integration for community skills
- **💬 Multi-Platform** — Telegram bot, CLI REPL, and web UI — use your agent anywhere
- **🌐 MCP Integration** — Native Model Context Protocol support for external tool and service integration
- **🔄 Smart Context Management** — Automatic conversation compaction with tool I/O archival keeps context lean while preserving critical data

---

## Key Features

### Core Architecture
- **Modular Crate Design** — 12+ specialized crates for clean separation of concerns
- **SQLite Persistence** — Conversation history, notes, skills, and scheduled tasks all persisted
- **Workspace Isolation** — Per-user and per-conversation workspaces for secure multi-tenant operation
- **Event-Driven** — Internal event bus for system-wide coordination

### Intelligence Layer
- **Provider Failover** — Automatic fallback when primary provider is unavailable
- **Thinking Modes** — Support for extended thinking (Claude, Gemini) for complex reasoning tasks
- **Image Generation** — Built-in support for Imagen 4 and Gemini-based image generation

#### Supported Providers
- **Anthropic** — Claude 3.5 Sonnet, Claude 3.5 Opus, Claude 3 Haiku
- **OpenAI** — GPT-4, GPT-4 Turbo, GPT-3.5 Turbo
- **Google** — Gemini 3.0 Pro, Gemini 3.0 Flash, Gemini 2.0 Flash
- **More coming soon** — Azure OpenAI, Mistral, Cohere, local models via Ollama

### Skills & Tools
- **Dynamic Tool Loading** — Skills can inject custom tools at runtime via YAML definitions
- **Browser Automation** — Headless Chromium integration for web interaction and screenshots
- **Code Execution** — Sandboxed execution environment with configurable isolation
- **Task Scheduling** — Natural language schedule parsing with cron/one-time/manual tasks
- **Subagent System** — Spawn specialized agents for complex multi-step operations

### Safety & Security
- **Guardrail Engine** — Dual-phase evaluation (pattern-based + AI-based) with configurable actions
- **Secret Vault** — In-memory secret storage with automatic I/O scanning to prevent leaks
- **Permission System** — Fine-grained control over tool access with session-based grants
- **Sandbox Execution** — Process isolation for code execution with path restrictions

### Memory & Context
- **Tiered Notes** — Critical (always loaded), Essential (first message), Context (on-demand)
- **Tool I/O Archival** — Automatic archival of large tool outputs with dual-cutoff hydration
- **Smart Compaction** — AI-powered conversation analysis preserves context while reducing tokens
- **Tool Call Filtering** — Model can mark redundant/failed tool calls to keep history clean

### Clients
- **Telegram Bot** — Full-featured bot with inline keyboards, file upload/download, rich permissions
- **Web UI** — Dark-themed control panel with real-time WebSocket streaming
- **CLI REPL** — Interactive terminal interface with full tool access
- **More coming soon** — Discord bot, Slack integration, HTTP API, desktop app

### Integrations
- **MCP (Model Context Protocol)** — Calendar, filesystem, GitHub, and custom MCP server support
- **Marketplace** — Browse and install skills from ClawHub and Claude Code plugin registries
- **More coming soon** — Zapier, n8n, Home Assistant, IFTTT, REST API webhooks

---

## Architecture Highlights

```
OpenPaw/
├── crates/
│   ├── dbot-core        # Shared types, config, workspace resolver
│   ├── dbot-agent       # Main agent loop, tool dispatch, skills
│   ├── dbot-providers   # LLM provider implementations
│   ├── dbot-permissions # Permission engine and evaluation
│   ├── dbot-browser     # Headless browser automation
│   ├── dbot-mcp         # Model Context Protocol bridge
│   ├── dbot-telegram    # Telegram bot backend
│   ├── dbot-web         # Web UI with axum + WebSocket
│   ├── dbot-marketplace # Skill registry and vetting
│   ├── dbot-scheduler   # Task scheduling and cron
│   └── ...
├── data/
│   ├── config/          # System configs (read-only for AI)
│   │   ├── skills/      # Default skill definitions
│   │   ├── agents/      # Subagent definitions
│   │   └── guardrails/  # Safety guardrail configs
│   └── workspace/       # AI-generated content
│       └── {userId}/
│           ├── dbot/    # Per-user global workspace
│           └── {convId}/
│               ├── dbot/       # Per-conversation workspace
│               ├── tool_output/ # Tool results
│               └── files/       # User files
├── migrations/          # SQLite schema migrations
└── scripts/            # Build and dev scripts
```

---

## Use Cases

- **Personal Assistant** — Manage tasks, schedule appointments, browse the web, execute code
- **Development Aid** — Code review, documentation generation, test writing, debugging assistance
- **Research Agent** — Web scraping, data analysis, report generation with persistent notes
- **Automation Hub** — Schedule recurring tasks, monitor services, integrate with external APIs
- **Multi-User Platform** — Deploy as a shared service with per-user isolation and permissions

---

## Roadmap

### Phase 1: Core Framework ✅
- [x] Multi-provider LLM support
- [x] Tool dispatch and execution
- [x] Persistent conversation storage
- [x] Permission system
- [x] Telegram bot interface

### Phase 2: Skills & Safety ✅
- [x] Dynamic skill plugin system
- [x] Browser automation
- [x] Guardrail engine
- [x] Secret vault protection
- [x] MCP integration

### Phase 3: Advanced Features ✅
- [x] Tiered memory system
- [x] Tool I/O archival
- [x] Subagent orchestration
- [x] Task scheduling
- [x] Web UI

### Phase 4: Marketplace & Community 🚧
- [x] Skill marketplace integration
- [ ] Public skill registry
- [ ] Community skill templates
- [ ] Plugin development documentation

### Phase 5: Open Source Release 🔜
- [ ] Code cleanup and documentation
- [ ] Contribution guidelines
- [ ] Deployment guides
- [ ] Docker images
- [ ] Public launch

---

## Technology Stack

- **Language:** Rust 2021 Edition
- **LLM Providers:** Anthropic, OpenAI, Google Gemini
- **Database:** SQLite with sqlx
- **Web:** axum, WebSocket, tokio
- **Browser:** headless_chrome
- **Protocols:** MCP (Model Context Protocol)
- **Security:** Secret scanning, sandboxed execution, guardrails

---

## Coming Soon

OpenPaw is currently in active development. We're working hard to:

- Polish the codebase for open source release
- Complete comprehensive documentation
- Create example skill plugins
- Build deployment guides
- Set up CI/CD pipelines

**Want to be notified when we launch?** Star this repository and watch for updates!

---

## Contact

For early access inquiries, collaboration opportunities, or questions:

- **GitHub Issues:** [Report bugs or request features](../../issues)
- **Discussions:** Coming soon
- **Discord:** Coming soon

---

## License

OpenPaw is dual-licensed under:

- **[LGPL-3.0](LICENSE)** — Free for open source and personal use
- **[Commercial License](LICENSE-COMMERCIAL)** — For proprietary/commercial applications

**Important:** Certain entities are permanently excluded from using this software under any license. See [LICENSE](LICENSE) file for complete terms including exclusions.

To apply for a commercial license: Contact **licenses@OrigoZero.com** or see [LICENSE-COMMERCIAL](LICENSE-COMMERCIAL) for details.

---

<div align="center">

**Built with 🐾 by developers who believe AI agents should be powerful, safe, and extensible.**

</div>
