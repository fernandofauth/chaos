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

- `README.md` — Human Entry Point
- `AGENTS.md` — AI Agent Entry Point
- `.chaos/` — Canonical System Context

For systems composed of multiple repositories, shared knowledge can be maintained in a dedicated shared CHAOS repository.

---


## Getting Started

Use [$1STARTER-PROMPT.md$1]$1STARTER-PROMPT.md) with an AI agent to implement CHAOS in an existing repository. The prompt guides the agent through a complete project audit, a proposed context structure for approval, implementation of $1README.md$1, $1AGENTS.md$1, and $1.chaos/$1, and a final coverage and consistency review.

---

## Why the Name CHAOS

The name is intentionally distinctive.

Terms such as *context*, *documentation*, *system*, *specification*, *architecture*, and *knowledge base* already have broad and overlapping meanings across software engineering and AI tooling. A generic directory name such as `.context` can therefore be interpreted in many different ways.

**CHAOS** is different. It is a new, deliberately unusual name for this specific convention. The goal is to create a strong and unambiguous association between the name, the convention, and the `.chaos/` directory.

This matters particularly in AI-assisted development. As AI agents and future models encounter the convention across repositories, a distinctive term can become a recognizable semantic signal: **CHAOS → system context organization for humans and AI**.

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


## Project Structure

Every CHAOS-compliant project should expose:

$1$1$1text

project/

├── README.md

├── AGENTS.md

└── .chaos/

$1$1$1

### README.md — Human Entry Point

Used for:

$1 Project purpose

$1 Overview

$1 Installation

$1 Development commands

$1 Technology stack

$1 Basic usage

$1 Repository information

The README is optimized for human onboarding.

### AGENTS.md — AI Agent Entry Point

Used for:

$1 Repository role

$1 Agent instructions

$1 Location of $1.chaos/$1

$1 Important rules

$1 Shared CHAOS references

$1 Project-specific constraints

$1AGENTS.md$1 should remain concise. It is an entry point, not the complete knowledge base.

### .chaos/ — System Context

Contains the knowledge required to understand and work on the project.

It may include:

$1 Architecture

$1 Business logic

$1 Feature behavior

$1 Design

$1 UX/UI behavior

$1 Integrations

$1 Contracts

$1 Security constraints

$1 System relationships

$1 Operational knowledge

$1 Technical decisions

$1 Important limitations

$1 Project-specific conventions

The internal structure of $1.chaos/$1 is flexible and should evolve according to the project's needs.

---

## Example

See [$1example/$1]$1example/) for a realistic CHAOS-compliant order-management API showing the human entry point, AI agent entry point, and categorized canonical context.

---

## Shared CHAOS

When multiple repositories are part of the same system, knowledge shared across those repositories may live in a dedicated shared CHAOS repository.

Example:

$1$1$1text

company-shared-chaos/

├── branding/

├── assets/

├── prompts/

├── integrations/

├── contracts/

└── shared/

$1$1$1

Shared CHAOS may contain:

$1 Branding

$1 Design assets

$1 Shared assets

$1 Prompts

$1 Shared components

$1 Shared conventions

$1 Cross-project integrations

$1 API contracts

$1 Data contracts

$1 Shared behaviors

$1 System-wide constraints

$1 Other reusable system knowledge

Shared CHAOS is not a task manager and should not become a repository of temporary communication.

---

## Local vs Shared Context

$1 **$1$1Project-specific knowledge belongs in the project's $1.chaos/$1. Knowledge required by multiple projects belongs in Shared CHAOS.$1$1**

Example:

$1$1$1text

company-api/.chaos/

$1$1$1

may contain API internal architecture, internal services, database behavior, and API-specific business logic.

While:

$1$1$1text

company-shared-chaos/

$1$1$1

may contain Company branding, shared assets, API ↔ App integration, API ↔ Admin integration, shared prompts, shared contracts, and system-wide design rules.

---

## Single Source of Truth

$1 **$1$1One concept should have one canonical source.$1$1**

Avoid:

$1$1$1text

company-api/FE-INTEGRATION.md

company-app/FE-INTEGRATION.md

company-admin/FE-INTEGRATION.md

$1$1$1

Prefer:

$1$1$1text

company-shared-chaos/

└── integrations/

    └── app-api.md

$1$1$1

Projects should reference canonical shared knowledge instead of duplicating it.

---

## Human and AI Access

Human flow:

$1$1$1text

Human

  ↓

README.md

  ↓

.chaos/ when deeper context is required

  ↓

Source Code

$1$1$1

AI flow:

$1$1$1text

AI Agent

  ↓

AGENTS.md

  ↓

.chaos/

  ↓

Shared CHAOS when required

  ↓

Source Code

$1$1$1

Both audiences ultimately use the same canonical system context.

---

## AI Agent Rules

An AI agent entering a CHAOS-compliant project should:

1$1 Read $1AGENTS.md$1.

2$1 Understand the role of the repository.

3$1 Identify relevant $1.chaos/$1 documents.

4$1 Read the required context before making significant changes.

5$1 Determine whether the change affects another project.

6$1 Consult Shared CHAOS when necessary.

7$1 Implement the change.

8$1 Update the relevant CHAOS when canonical system behavior changes.

The agent should not assume that source code alone represents the complete system requirements.

### When CHAOS must be consulted

Especially when working on:

$1 Architecture

$1 Business logic

$1 Feature behavior

$1 UX/UI behavior

$1 Design

$1 Branding

$1 Assets

$1 Integrations

$1 API contracts

$1 Data flows

$1 Authentication

$1 Security-sensitive behavior

$1 Cross-project functionality

$1 System-wide conventions

$1 Existing technical decisions

$1 Non-obvious constraints

Agents do not need to read the entire CHAOS repository for every change. Context should be consumed according to relevance.

---

## Cross-Project Changes

When a change affects multiple repositories, the agent must consider the relevant shared context.

Example:

$1$1$1text

company-api

     ↓

API behavior changes

     ↓

company-app

     ↓

company-admin

$1$1$1

The shared specification should describe the canonical expected behavior where appropriate.

Agents should not independently redefine shared behavior in ways that create incompatible implementations.

When canonical system behavior changes, the relevant CHAOS should be updated as part of the change.

---

## CHAOS vs Source Code

CHAOS describes system context and intended behavior.

Source code implements that behavior.

CHAOS should not become a copy of the implementation.

Good:

$1$1$1text

The Admin application obtains account information through

the API and must not access the database directly.

$1$1$1

Unnecessary:

$1$1$1text

A complete copy of the AccountService implementation.

$1$1$1

The specification should contain information that helps humans and AI correctly understand and evolve the system.

---

## CHAOS vs README.md

$1 File | Purpose |

$1---|---|

$1 $1README.md$1 | Human onboarding |

$1 $1AGENTS.md$1 | AI onboarding and instructions |

$1 $1.chaos/$1 | Canonical project context |

README focuses on getting into the project.

CHAOS contains deeper system knowledge.

Large duplication between README and CHAOS should be avoided.

---

## CHAOS vs AGENTS.md

$1AGENTS.md$1 tells an AI agent **$1$1how to enter and navigate the project$1$1**.

$1.chaos/$1 tells the agent **$1$1what it needs to know about the system$1$1**.

$1$1$1text

AGENTS.md

    ↓

Where should I look?

    ↓

.chaos/

    ↓

What do I need to know?

$1$1$1

$1AGENTS.md$1 should therefore remain concise.

---

## Shared Assets

Shared CHAOS may contain assets when those assets are part of the canonical system context or are intentionally reused across projects.

Examples:

$1$1$1text

company-shared-chaos/

└── assets/

    ├── logos/

    ├── icons/

    ├── images/

    ├── fonts/

    └── ...

$1$1$1

Project-specific assets should remain inside the project that owns them.

---

## Prompts

Shared CHAOS may contain prompts when those prompts represent reusable or canonical system knowledge.

Example:

$1$1$1text

company-shared-chaos/

└── prompts/

    ├── prompt-1.md

    └── prompt-2.md

$1$1$1

Prompts specific to one project may remain in that project's $1.chaos/$1.

---

## CHAOS Is Not a Task Manager

CHAOS does not replace:

$1 GitHub Issues

$1 Linear

$1 Jira

$1 Pull Requests

$1 Task management

$1 Project management

Temporary work does not automatically belong in CHAOS.

CHAOS represents system knowledge and context.

---

## CHAOS and Git

CHAOS represents the current canonical context.

Git represents its historical evolution.

$1$1$1text

.chaos/

    ↓

Current system context

Git

    ↓

History of changes

$1$1$1

A separate $1changes/$1 system is not required.

When system knowledge changes, update the canonical specification and allow Git to record the change.

---

## Tool Agnostic

CHAOS is intentionally independent of any particular AI provider or development tool.

The system should not require separate copies of context such as:

$1$1$1text

CLAUDE.md

CODEX.md

GEMINI.md

CURSOR.md

$1$1$1

$1AGENTS.md$1 is the standard AI entry point.

$1 **$1$1The agent may change. The system context does not.$1$1**

---

## Use Cases

### Multiple AI Agents

Different agents can work on different repositories while consulting the same system context.

$1$1$1text

Agent A → API

Agent B → App

Agent C → Admin

$1$1$1

### AI Agent Handoff

One agent can make a system-level change and update the canonical CHAOS. Another agent can continue from the updated context without requiring a manually written explanation.

### New Developer Onboarding

A developer can start with $1README.md$1 and consult $1.chaos/$1 when deeper system knowledge is required.

### New AI Agent

A completely different AI agent can enter through $1AGENTS.md$1 and discover the project's CHAOS and shared CHAOS without requiring previous conversation history.

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

1$1 Every project has a $1README.md$1.

2$1 Every project has an $1AGENTS.md$1.

3$1 Every project has a $1.chaos/$1.

4$1 $1README.md$1 is the human entry point.

5$1 $1AGENTS.md$1 is the AI entry point.

6$1 $1.chaos/$1 is the canonical project context.

7$1 Shared knowledge belongs in Shared CHAOS.

8$1 One concept should have one canonical source.

9$1 Do not unnecessarily duplicate shared knowledge.

10$1 AI agents should consult relevant CHAOS before context-sensitive changes.

11$1 Cross-project changes must consider Shared CHAOS.

12$1 Update CHAOS when canonical system behavior changes.

13$1 CHAOS is not a task-management system.

14$1 Git provides historical change tracking.

15$1 CHAOS must remain tool-agnostic.

16$1 Do not create vendor-specific copies of system context.

17$1 Do not use CHAOS as a source-code dump.

18$1 Do not allow contradictory specifications to remain authoritative.

19$1 Keep $1AGENTS.md$1 concise.

20$1 Keep CHAOS simple and evolve it only when necessary.

21$1 Shared CHAOS may contain reusable assets when they are intentionally canonical or shared.

22$1 Project-specific assets remain in the project that owns them.

23$1 Humans and AI agents should consume the same canonical system context.

---

## Recommended Company Structure

$1$1$1text

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

$1$1$1

The exact structure should evolve according to the system.

---

## Mental Model

$1$1$1text

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

$1$1$1

For a multi-repository system:

$1$1$1text

                       SYSTEM

                          │

             ┌────────────┴────────────┐

             │                         │

        Local CHAOS                Shared CHAOS

             │                         │

       ┌─────┼─────┐                   │

       ↓     ↓     ↓                   ↓

      API   APP   ADMIN       Shared System Knowledge

$1$1$1

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

