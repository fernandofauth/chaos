**# CHAOS Implementation Starter Prompt**

Use the prompt below with an AI agent inside an existing software repository.

**---**

**## Prompt**

You are responsible for implementing the Context for Human-AI Organization of Systems (CHAOS) in this repository.

CHAOS gives humans and AI agents a canonical, tool-agnostic context layer for understanding, maintaining, and evolving the system. The required top-level structure is:

\`\`\`text

project/

├── README.md

├── AGENTS.md

└── .chaos/

\`\`\`

\- \`README.md\` is the human entry point.

\- \`AGENTS.md\` is the AI agent entry point.

\- \`.chaos/\` is the canonical source of truth for system context.

Your work has two stages. First audit the repository and propose a plan. Do not create or modify project files until I explicitly approve that plan. After approval, implement the plan and validate the result.

**### Non-Negotiable Principles**

1\. Review the entire meaningful project, not only its README or primary source directory.

2\. Base every conclusion on repository evidence or an explicit answer from me.

3\. Do not invent requirements, intent, architecture, or behavior.

4\. When sources disagree, report the contradiction and ask which behavior is canonical.

5\. Document durable system context, not a copy or narration of the source code.

6\. Give each concept one canonical owner. Link to that owner instead of duplicating it.

7\. Keep temporary plans, task status, investigation notes, and conversation history out of \`.chaos/\`.

8\. Never include secrets, credentials, tokens, private keys, personal data, or sensitive runtime values.

9\. Derive the internal \`.chaos/\` structure from this project. Do not impose categories that the system does not need.

10\. The final source code, tests, schemas, README, AGENTS, and CHAOS must not describe contradictory behavior.

**## Stage 1: Audit and Plan**

**### 1. Establish Scope**

Identify:

\- The purpose and role of the repository.

\- Whether it is an application, service, library, package, monorepo, infrastructure repository, or shared-context repository.

\- Its users, clients, dependent systems, and upstream or downstream dependencies.

\- The languages, frameworks, runtimes, package managers, and major tools in use.

\- Its entry points, deployable units, packages, applications, and ownership boundaries.

\- Existing \`README.md\`, \`AGENTS.md\`, \`.chaos/\`, architecture documents, ADRs, API specifications, schemas, runbooks, and other sources of system knowledge.

\- Any related repository or Shared CHAOS location referenced by the project.

Exclude dependency directories, vendored code, generated output, caches, build artifacts, binary files, and secret values from detailed inspection. Review generated schemas or artifacts only when they are the authoritative description of a contract and their source is unavailable.

**### 2. Build a Repository Inventory**

Inspect all meaningful files and map the system before proposing documentation. Cover every applicable area below:

\- Product purpose, users, capabilities, and limitations.

\- Features and user-visible behavior.

\- User journeys and operational workflows.

\- Major modules, services, components, packages, and important functions.

\- Domain concepts, business rules, invariants, calculations, permissions, and state transitions.

\- Data models, ownership, persistence, migrations, retention, and consistency rules.

\- Public and internal APIs, commands, events, schemas, protocols, error behavior, and compatibility guarantees.

\- UI structure, navigation, interaction behavior, accessibility, responsive behavior, and design constraints.

\- Authentication, authorization, trust boundaries, data protection, and security-sensitive behavior.

\- External services, third-party providers, webhooks, imports, exports, and cross-project integrations.

\- Background jobs, queues, schedules, event processing, concurrency, retries, deduplication, and idempotency.

\- Configuration, environment variables, feature flags, runtime modes, and environment-specific behavior.

\- Build, test, development, release, deployment, observability, recovery, and operational workflows.

\- Reliability requirements, failure modes, fallback behavior, performance constraints, and known limitations.

\- Testing strategy, fixtures, quality gates, and behavior protected by tests.

\- Coding conventions or implementation constraints that materially affect how the system evolves.

\- Technical decisions and rationale that cannot be reliably inferred from implementation alone.

Do not turn this inventory into function-by-function documentation. Important functions are evidence for system behavior; CHAOS should explain the capability, rule, boundary, contract, or decision they implement.

**### 3. Gather and Compare Evidence**

Use source code, tests, schemas, migrations, configuration, automation, commit-visible documentation, and existing context as evidence.

For each important finding:

1\. Identify the behavior or constraint.

2\. Identify the evidence supporting it.

3\. Decide whether it is durable context that belongs in CHAOS.

4\. Identify its single canonical document.

5\. Record uncertainty or contradictions without guessing.

Prefer stable references to relevant files, modules, types, commands, or symbols when a source reference helps future readers. Avoid relying on line numbers that will become stale. Do not treat implementation as intended behavior when code, tests, documentation, or user expectations conflict.

**### 4. Design the CHAOS Structure**

Propose categories and documents based on the concepts the project actually contains. Use topic directories containing descriptively named documents, for example:

\`\`\`text

.chaos/

├── architecture/

│   └── system-boundaries.md

├── features/

│   └── checkout.md

├── business/

│   └── order-lifecycle.md

├── contracts/

│   └── public-api.md

└── integrations/

    └── payment-provider.md

\`\`\`

This is an example, not a mandatory taxonomy. Add, remove, rename, or reorganize categories according to the repository.

Follow these structural rules:

\- Do not place loose Markdown documents directly inside \`.chaos/\`.

\- Do not create generic \`README.md\` files inside topic directories when a descriptive document name is possible.

\- Do not create empty categories for symmetry or anticipated future work.

\- Keep each document focused on a coherent concept with a clear ownership boundary.

\- Split documents when independent concepts would otherwise acquire different owners or change for different reasons.

\- Combine documents when separation would create repetition or navigation overhead without clearer ownership.

**### 5. Identify Shared Context**

Determine whether any knowledge is authoritative across multiple repositories. Examples include branding, shared contracts, integrations, prompts, assets, design rules, and system-wide constraints.

Recommend Shared CHAOS for genuinely cross-project knowledge. Do not duplicate shared concepts locally. If the Shared CHAOS repository is unavailable, identify the required reference and gap in the plan instead of inventing a local canonical copy.

**### 6. Present the Plan**

Before editing files, present:

1\. **\*\*Repository summary\*\*** — purpose, role, stack, boundaries, and reviewed scope.

2\. **\*\*Proposed tree\*\*** — the complete proposed \`README.md\`, \`AGENTS.md\`, and \`.chaos/\` structure.

3\. **\*\*Document responsibilities\*\*** — one concise description of what each proposed document owns.

4\. **\*\*Coverage matrix\*\*** — every discovered feature, workflow, domain area, contract, integration, security concern, and operational concern mapped to its canonical document.

5\. **\*\*Existing documentation treatment\*\*** — what will be retained, updated, absorbed, linked, or marked non-authoritative.

6\. **\*\*Shared CHAOS candidates\*\*** — concepts that belong outside this repository and why.

7\. **\*\*Contradictions and ambiguities\*\*** — conflicting evidence, unclear intent, and questions that block canonical documentation.

8\. **\*\*Exclusions\*\*** — reviewed content that should not enter CHAOS and why.

9\. **\*\*Validation plan\*\*** — checks you will run after implementation.

Ask only questions whose answers are necessary to establish accurate canonical context. Do not hide uncertainty inside confident prose.

Stop after presenting the plan and wait for my explicit approval.

**## Stage 2: Implement After Approval**

After I approve the plan, implement it completely.

**### 1. Maintain the Entry Points**

Create or update \`README.md\` for human onboarding. It should contain the project purpose, overview, setup, development commands, technology stack, basic usage, and repository information. Link to deeper context instead of duplicating it.

Create or update a concise \`AGENTS.md\` that contains:

\- The repository's role and boundaries.

\- A navigation map from common change types to relevant \`.chaos/\` documents.

\- Critical project-specific rules and constraints.

\- Relevant Shared CHAOS references.

\- Instructions to read only the context relevant to the task.

\- The mandatory source-of-truth synchronization rule defined below.

**### 2. Write Canonical Context**

Create or update the approved \`.chaos/\` documents. Depending on the subject, a document may define:

\- Purpose, responsibilities, and ownership.

\- Expected behavior and user-visible outcomes.

\- Business rules, calculations, invariants, and state transitions.

\- System boundaries, relationships, and data flows.

\- Contracts, inputs, outputs, errors, and compatibility guarantees.

\- Authentication, authorization, privacy, and security constraints.

\- Integration responsibilities, failure handling, retries, and idempotency.

\- Operational expectations, recovery behavior, and important limitations.

\- Technical decisions and their rationale when that rationale is known.

Use concise prose, lists, tables, examples, and diagrams according to what communicates the concept most clearly.

Do not include:

\- Copies of source files or large implementation snippets.

\- Exhaustive descriptions of classes, functions, or control flow.

\- Facts that are obvious from reading the implementation and carry no durable context.

\- Guessed intent or unsupported requirements.

\- Temporary migration notes, task lists, progress logs, or historical narratives better preserved by Git.

\- The same canonical rule in multiple documents.

**### 3. Reconcile Existing Documentation**

For each existing source of system knowledge:

\- Preserve it if it has a distinct purpose and remains authoritative.

\- Move or absorb durable system context into its canonical \`.chaos/\` owner when appropriate.

\- Replace duplicated explanations with links.

\- Clearly identify obsolete or non-authoritative material.

\- Never leave contradictory documents appearing equally authoritative.

Do not delete valuable existing documentation without explicit approval.

**### 4. Enforce the Source of Truth**

Add the following policy to \`AGENTS.md\`, adapted to the project without weakening it:

\> \`.chaos/\` is the canonical source of truth for system behavior, rules, constraints, contracts, relationships, and architectural decisions. Source code implements that context and must not contradict it.

\>

\> Before completing any code change:

\>

\> 1. Review the changed behavior against the relevant \`.chaos/\` documents.

\> 2. Update the owning \`.chaos/\` document in the same change whenever behavior, rules, constraints, contracts, relationships, or architecture have changed.

\> 3. Do not complete the task while the source code and \`.chaos/\` describe different behavior.

This policy applies to future work, not only the initial CHAOS implementation.

**## Final Validation**

After writing the files, repeat the repository inventory and compare it with the implemented context.

Verify that:

\- Every significant feature, workflow, business rule, data concern, contract, integration, security boundary, and operational behavior has one canonical location or an explicit reason for exclusion.

\- \`README.md\` remains the human entry point and does not duplicate deep context.

\- \`AGENTS.md\` remains concise and routes agents to the correct context.

\- \`.chaos/\` contains durable context rather than source-code copies or temporary work.

\- Internal links and referenced local files resolve.

\- Documents use consistent terminology and do not contradict one another.

\- CHAOS does not contain unsupported claims, secrets, sensitive values, or stale implementation details.

\- Existing documentation no longer competes ambiguously with CHAOS as the source of truth.

\- Code, tests, schemas, configuration, README, AGENTS, and CHAOS agree on current canonical behavior.

\- Shared knowledge has not been unnecessarily duplicated into local CHAOS.

\- No meaningful repository area was skipped merely because it was difficult to classify.

Run available Markdown linting, link checking, repository diagnostics, and relevant project validation commands. Fix issues introduced by the CHAOS implementation.

**## Completion Report**

When finished, report:

1\. Files created and updated.

2\. System areas covered and their canonical locations.

3\. Existing documentation reconciled.

4\. Contradictions resolved and the authority used to resolve them.

5\. Remaining ambiguities or unavailable evidence.

6\. Shared CHAOS candidates or unresolved cross-project dependencies.

7\. Intentionally excluded content and the reason for exclusion.

8\. Validation commands run and their results.

Do not claim complete coverage if important files, packages, behavior, or dependencies were not reviewed. State the remaining gap precisely.

**---**

End of prompt.