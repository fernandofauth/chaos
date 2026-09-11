# CHAOS — Context for Human-AI Organization of Systems

## Definition

**CHAOS (Context for Human-AI Organization of Systems)** is an open convention for organizing the context required to understand, develop, maintain, and evolve software systems by both humans and AI agents.

CHAOS provides a structured, canonical context layer without depending on a specific AI provider, IDE, programming language, or development tool.

CHAOS is free to use, adapt, and extend.

The convention uses a dedicated system-context directory:

```text
project/
├── README.md
├── AGENTS.md
└── .chaos/
```

- `README.md` — Human entry point
- `AGENTS.md` — AI agent entry point
- `.chaos/` — canonical system context

For systems composed of multiple repositories, shared knowledge can be maintained in a dedicated shared CHAOS repository.

---

## Getting Started

Use [`STARTER-PROMPT.md`](STARTER-PROMPT.md) with an AI agent to implement CHAOS in an existing repository. The prompt guides the agent through a complete project audit, a proposed context structure for approval, implementation of `README.md`, `AGENTS.md`, and `.chaos/`, and a final coverage and consistency review.

---

## Why the Name CHAOS

The name is intentionally distinctive.

Terms such as *context*, *documentation*, *system*, *specification*, *architecture*, and *knowledge base* already have broad and overlapping meanings across software engineering and AI tooling. A generic directory name such as `.context` can therefore be interpreted in many different ways.

**CHAOS** is different. It is a new, deliberately unusual name for this specific convention. The goal is to create a strong and unambiguous association between the name, the convention, and the `.chaos/` directory.

This matters particularly in AI-assisted development. As AI agents and future models encounter the convention across repositories, a distinctive term can become a recognizable semantic signal: **CHAOS → persistent system context for humans and AI**.

The name is not intended to describe documentation, specifications, source code, or any existing software-engineering category. It identifies the convention itself.

The unusual name also creates a useful conceptual contrast:

> **Chaos precedes order.**

Software systems naturally accumulate distributed knowledge and complexity. CHAOS provides the structure through which that complexity can become organized, persistent, and shared.

The objective is therefore not to compete with existing concepts such as documentation or architecture. It is to establish a distinct concept that can reference and organize them when they form part of the canonical system context.

> **A distinctive name creates a distinctive concept.**

---

## CHAOS vs AI Skills

AI skills and CHAOS solve different problems.

A skill represents a **capability**:

> **Skill: Be a mechanic.**

It can teach an AI how to perform a class of tasks, such as changing a brake system, diagnosing an engine, or performing an electrical repair.

CHAOS represents the **specific system being worked on**:

> **CHAOS: Here is the car. Here is how it is built, what has been modified, what constraints exist, what depends on what, and what must not be broken.**

The distinction is:

```text
Skill
"What can you do?"

CHAOS
"What are you working on?"
```

Or:

```text
Skill → Capability
CHAOS → System Context
```

### Why this matters

A highly capable AI may already know how to perform a task. What it cannot reliably infer is the **specific intent, constraints, relationships, and history of the system in front of it**.

For example, imagine an AI agent working on an e-commerce platform.

A skill might tell the agent:

> "You are capable of implementing payment integrations."

CHAOS can tell the agent:

```text
This system uses Stripe.

The checkout service owns payment creation.

The frontend must never create Stripe payments directly.

Payment webhooks are untrusted and may be delivered more than once.

The order can only enter "paid" after the backend verifies the payment.

Three applications depend on this contract.
```

The skill provides the ability to work with payments.

CHAOS provides the knowledge required to work with **this payment system correctly**.

The same principle applies to the mechanic analogy:

```text
AI
│
├── Skills
│   └── "Be a mechanic."
│
└── CHAOS
    └── "Here is the car."
        ├── Architecture
        ├── Components
        ├── Modifications
        ├── Constraints
        └── Relationships
```

When the agent understands the system, it can determine what kind of expertise is actually required.

> **"I need a mechanic specialized in this engine."**

This also means that humans should not necessarily have to decide which skills an AI needs for every task.

As AI models become increasingly capable of reasoning and decision-making, the AI can use the system context itself to determine what capabilities are required and how the task should be approached.

> **Give the AI the context. Let the AI decide how to act.**

The same principle applies to maintaining context and skills.

If a skill is required to work correctly within a specific system, humans should not have to manually maintain the skill and the system context as separate sources of truth.

The AI should be able to determine when a change in the system context also requires a change in the relevant skill, and vice versa.

> **Context and capability should evolve together when the system requires it.**

This is why CHAOS does not need to replace AI capabilities or teach an AI how to perform every possible task. The capability may already exist in the model, in a skill, or in another tool.

CHAOS supplies the missing piece:

> **The persistent context of the actual system.**

### Capability is becoming general. Context remains specific.

AI models increasingly provide broad technical capabilities. They can reason, write code, use tools, learn APIs, and adapt to unfamiliar technologies.

What remains unique to each project is its system context:

- Why the architecture exists this way
- Which rules must never be violated
- Which components own which responsibilities
- Which contracts connect projects
- Which integrations have special constraints
- Which business behaviors are intentional
- Which decisions were made and why

CHAOS makes that knowledge discoverable and persistent instead of leaving it in the memory of a developer, a previous AI agent, or a temporary conversation.

> **Skills provide capability. CHAOS provides context.**

Together, they allow an AI to not only know **how to do something**, but understand **what it is doing it to and why**.

### Let the AI decide

The goal is not to make humans manually orchestrate the combination of context, skills, and tasks.

Instead, provide the AI with the context of the actual system and let it determine which capabilities, skills, tools, or reasoning are required for the task at hand.

```text
Human
  ↓
System Context
  ↓
AI understands the system
  ↓
AI decides how to act
```

## From Chaos to Order

Software systems naturally accumulate complexity.

Knowledge becomes distributed across source code, documentation, conversations, tickets, design files, decisions, repositories, and — most importantly — the people who understand how everything fits together.

When that knowledge is not explicitly organized, the system's understanding becomes dependent on individuals and temporary interactions.

**Chaos precedes order.**

CHAOS does not attempt to eliminate complexity. It provides a place and structure through which the knowledge of a system can be organized into a shared, persistent understanding.

The goal is not to create more documentation.

The goal is to make the system's understanding part of the system itself.

> **From chaos to shared understanding.**

---

## Purpose

CHAOS makes the knowledge required to understand, develop, maintain, and evolve a system:

- Discoverable
- Structured
- Canonical
- Human-readable
- AI-readable
- Tool-agnostic
- Shared when necessary
- Persistent across people, agents, and development sessions

The goal is to reduce the need for humans to manually transfer context between projects, developers, or AI agents.

The system should not depend on a human being the carrier of its context.

---

## Core Principle

> **The source code contains the implementation. CHAOS contains the context required to understand and evolve the system.**

Source code answers:

> How is this implemented?

CHAOS answers:

> What is this system? Why does it work this way? What are its rules, constraints, relationships, and expected behaviors?

Humans and AI agents should be able to arrive at the same system understanding without relying on previous conversations or a specific individual.

---

## Architecture is Context

A project structure is not only a technical detail.

It is also a map of meaning.

A clear architecture communicates:

- where domain logic lives
- where integrations live
- where shared contracts live
- where infrastructure code lives
- which boundary is authoritative
- which parts are local versus shared

This reduces ambiguity for both humans and AI agents.

A well-designed repository structure provides immediate context before the code is even read.

That is a major token-efficiency gain.

### Naming is Context

Folder and file names are not cosmetic.

They are part of the system's communication layer.

Good names reduce the need to inspect implementation details.

Examples:

```text
payments/
webhooks/
orders/
contracts/
shared/
platform/
```

These names immediately suggest meaning.

By contrast, vague or inconsistent naming forces the AI to open files and infer intent from code, which increases:

- reading time
- token consumption
- ambiguity
- risk of wrong assumptions

> **Architecture and naming are not just organization. They are lightweight system context.**

### Why this matters for AI

AI agents work best when they can locate the correct domain quickly.

If the project structure is clear, they can:

- quickly identify the relevant boundary
- avoid reading unrelated modules
- locate contracts and integrations faster
- infer responsibilities from the structure itself
- reduce repeated exploration and token waste

This matters especially in multi-repository systems.

Without structure, the agent must reconstruct the system from scattered code and assumptions.

This is a costly and error-prone pattern.

---

## Project Structure

Every CHAOS-compliant project should expose:

```text
project/
├── README.md
├── AGENTS.md
└── .chaos/
```

### README.md — Human entry point

Used for:

- Project purpose
- Overview
- Installation
- Development commands
- Technology stack
- Basic usage
- Repository information

The README is optimized for human onboarding.

### AGENTS.md — AI agent entry point

Used for:

- Repository role
- Agent instructions
- Location of `.chaos/`
- Important rules
- Shared CHAOS references
- Project-specific constraints

`AGENTS.md` should remain concise. It is an entry point, not the complete knowledge base.

### .chaos/ — System Context

Contains the knowledge required to understand and work on the project.

It may include:

- Architecture
- Business logic
- Feature behavior
- Design
- UX/UI behavior
- Integrations
- Contracts
- Security constraints
- System relationships
- Operational knowledge
- Technical decisions
- Important limitations
- Project-specific conventions

The internal structure of `.chaos/` is flexible and should evolve according to the project's needs.

---

## Example

See [`example/`](example/) for a realistic CHAOS-compliant order-management API showing the human entry point, AI agent entry point, and categorized canonical context.

---

## Shared CHAOS

When multiple repositories are part of the same system, knowledge shared across those repositories may live in a dedicated shared CHAOS repository.

Example:

```text
company-shared-chaos/
├── branding/
├── assets/
├── prompts/
├── integrations/
├── contracts/
└── shared/
```

Shared CHAOS may contain:

- Branding
- Design assets
- Shared assets
- Prompts
- Shared components
- Shared conventions
- Cross-project integrations
- API contracts
- Data contracts
- Shared behaviors
- System-wide constraints
- Other reusable system knowledge

Shared CHAOS is not a task manager and should not become a repository of temporary communication.

---

## Local vs Shared Context

> **Project-specific knowledge belongs in the project's `.chaos/`. Knowledge required by multiple projects belongs in Shared CHAOS.**

Example:

```text
company-api/.chaos/
```

may contain API internal architecture, internal services, database behavior, and API-specific business logic.

While:

```text
company-shared-chaos/
```

may contain company branding, shared assets, API ↔ App integration, API ↔ Admin integration, shared prompts, shared contracts, and system-wide design rules.

---

## Single Source of Truth

> **One concept should have one canonical source.**

Avoid:

```text
company-api/FE-INTEGRATION.md
company-app/FE-INTEGRATION.md
company-admin/FE-INTEGRATION.md
```

Prefer:

```text
company-shared-chaos/
└── integrations/
    └── app-api.md
```

Projects should reference canonical shared knowledge instead of duplicating it.

---

## Human and AI Access

Human flow:

```text
Human
  ↓
README.md
  ↓
.chaos/ when deeper context is required
  ↓
Source Code
```

AI flow:

```text
AI Agent
  ↓
AGENTS.md
  ↓
.chaos/
  ↓
Shared CHAOS when required
  ↓
Source Code
```

Both audiences ultimately use the same canonical system context.

---

## AI Agent Rules

An AI agent entering a CHAOS-compliant project should:

1. Read `AGENTS.md`.
2. Understand the role of the repository.
3. Identify relevant `.chaos/` documents.
4. Read the required context before making significant changes.
5. Determine whether the change affects another project.
6. Consult Shared CHAOS when necessary.
7. Implement the change.
8. Update the relevant CHAOS when canonical system behavior changes.

The agent should not assume that source code alone represents the complete system requirements.

### When CHAOS must be consulted

Especially when working on:

- Architecture
- Business logic
- Feature behavior
- UX/UI behavior
- Design
- Branding
- Assets
- Integrations
- API contracts
- Data flows
- Authentication
- Security-sensitive behavior
- Cross-project functionality
- System-wide conventions
- Existing technical decisions
- Non-obvious constraints

Agents do not need to read the entire CHAOS repository for every change. Context should be consumed according to relevance.

---

## Cross-Project Changes

When a change affects multiple repositories, the agent must consider the relevant shared context.

Example:

```text
company-api
     ↓
API behavior changes
     ↓
company-app
     ↓
company-admin
```

The shared specification should describe the canonical expected behavior where appropriate.

Agents should not independently redefine shared behavior in ways that create incompatible implementations.

When canonical system behavior changes, the relevant CHAOS should be updated as part of the change.

---

## CHAOS vs Source Code

CHAOS describes system context and intended behavior.

Source code implements that behavior.

CHAOS should not become a copy of the implementation.

Good:

```text
The Admin application obtains account information through
the API and must not access the database directly.
```

Unnecessary:

```text
A complete copy of the AccountService implementation.
```

The specification should contain information that helps humans and AI correctly understand and evolve the system.

---

## CHAOS vs README.md

| File | Purpose |
|---|---|
| `README.md` | Human onboarding |
| `AGENTS.md` | AI onboarding and instructions |
| `.chaos/` | Canonical project context |

README focuses on getting into the project.

CHAOS contains deeper system knowledge.

Large duplication between README and CHAOS should be avoided.

---

## CHAOS vs AGENTS.md

`AGENTS.md` tells an AI agent **how to enter and navigate the project**.

`.chaos/` tells the agent **what it needs to know about the system**.

```text
AGENTS.md
    ↓
Where should I look?
    ↓
.chaos/
    ↓
What do I need to know?
```

`AGENTS.md` should therefore remain concise.

---

## Shared Assets

Shared CHAOS may contain assets when those assets are part of the canonical system context or are intentionally reused across projects.

Examples:

```text
company-shared-chaos/
└── assets/
    ├── logos/
    ├── icons/
    ├── images/
    ├── fonts/
    └── ...
```

Project-specific assets should remain inside the project that owns them.

---

## Prompts

Shared CHAOS may contain prompts when those prompts represent reusable or canonical system knowledge.

Example:

```text
company-shared-chaos/
└── prompts/
    ├── prompt-1.md
    └── prompt-2.md
```

Prompts specific to one project may remain in that project's `.chaos/`.

---

## CHAOS Is Not a Task Manager

CHAOS does not replace:

- GitHub Issues
- Linear
- Jira
- Pull Requests
- Task management
- Project management

Temporary work does not automatically belong in CHAOS.

CHAOS represents system knowledge and context.

---

## CHAOS and Git

CHAOS represents the current canonical context.

Git represents its historical evolution.

```text
.chaos/
    ↓
Current system context

Git
    ↓
History of changes
```

A separate `changes/` system is not required.

When system knowledge changes, update the canonical specification and allow Git to record the change.

---

## Tool Agnostic

CHAOS is intentionally independent of any particular AI provider or development tool.

The system should not require separate copies of context such as:

```text
CLAUDE.md
CODEX.md
GEMINI.md
CURSOR.md
```

`AGENTS.md` is the standard AI entry point.

> **The agent may change. The system context does not.**

---

## Use Cases

### Multiple AI Agents

Different agents can work on different repositories while consulting the same system context.

```text
Agent A → API
Agent B → App
Agent C → Admin
```

### AI Agent Handoff

One agent can make a system-level change and update the canonical CHAOS. Another agent can continue from the updated context without requiring a manually written explanation.

### New Developer Onboarding

A developer can start with `README.md` and consult `.chaos/` when deeper system knowledge is required.

### New AI Agent

A completely different AI agent can enter through `AGENTS.md` and discover the project's CHAOS and shared CHAOS without requiring previous conversation history.

### Repository Rewrites

A repository can be rewritten or replaced while preserving the system's canonical context.

### Multiple Frontends

Several applications can share the same API and system rules while maintaining their own local implementation context.

### Shared Branding and Assets

Multiple projects can consume canonical branding and shared assets from Shared CHAOS.

### Shared Prompts

Multiple projects or agents can use canonical shared prompts without maintaining duplicated versions.

---

## Rules

1. Every project has a `README.md`.
2. Every project has an `AGENTS.md`.
3. Every project has a `.chaos/`.
4. `README.md` is the human entry point.
5. `AGENTS.md` is the AI entry point.
6. `.chaos/` is the canonical project context.
7. Shared knowledge belongs in Shared CHAOS.
8. One concept should have one canonical source.
9. Do not unnecessarily duplicate shared knowledge.
10. AI agents should consult relevant CHAOS before context-sensitive changes.
11. Cross-project changes must consider Shared CHAOS.
12. Update CHAOS when canonical system behavior changes.
13. CHAOS is not a task-management system.
14. Git provides historical change tracking.
15. CHAOS must remain tool-agnostic.
16. Do not create vendor-specific copies of system context.
17. Do not use CHAOS as a source-code dump.
18. Do not allow contradictory specifications to remain authoritative.
19. Keep `AGENTS.md` concise.
20. Keep CHAOS simple and evolve it only when necessary.
21. Shared CHAOS may contain reusable assets when they are intentionally canonical or shared.
22. Project-specific assets remain in the project that owns them.
23. Humans and AI agents should consume the same canonical system context.

---

## Recommended Company Structure

```text
company-api/
├── README.md
├── AGENTS.md
└── .chaos/

company-app/
├── README.md
├── AGENTS.md
└── .chaos/

company-admin/
├── README.md
├── AGENTS.md
└── .chaos/

company-shared-chaos/
├── branding/
├── assets/
├── prompts/
├── shared/
├── integrations/
└── contracts/
```

The exact structure should evolve according to the system.

---

## Mental Model

```text
                    PROJECT

                       │

          ┌────────────┼────────────┐

          ↓            ↓            ↓

     README.md     AGENTS.md      .chaos/
       Human           AI         Context
      Entry Point   Entry Point     Layer

          │            │             │

          └────────────┴─────────────┘

                       │

                       ↓

                  Source Code
```

For a multi-repository system:

```text
                       SYSTEM

                          │

             ┌────────────┴────────────┐

             │                         │

        Local CHAOS                Shared CHAOS

             │                         │

       ┌─────┼─────┐                   │

       ↓     ↓     ↓                   ↓

      API   APP   ADMIN       Shared System Knowledge
```

---

## Fundamental Statement

> **CHAOS (Context for Human-AI Organization of Systems) is an open, tool-agnostic convention for organizing the context required by humans and AI agents to understand, develop, maintain, and evolve software systems.**

The CHAOS project convention is:

> **README.md is the human entry point. AGENTS.md is the AI entry point. `.chaos/` is the canonical system context. Shared CHAOS provides canonical context that crosses project boundaries.**

The ultimate goal is:

> **The system should not depend on a human being the carrier of its context.**

The deeper principle is:

> **Chaos precedes order. Context enables shared understanding.**

The relevant knowledge should be discoverable, structured, current, and accessible to both humans and AI agents.

---

## Author

CHAOS was created by [Fernando Fauth](https://github.com/fernandofauth).
