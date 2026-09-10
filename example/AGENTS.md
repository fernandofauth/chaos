# Agent Instructions

## Repository Role

This repository implements the Acme Orders API and demonstrates the CHAOS convention. It owns order creation, order state transitions, payment coordination, and fulfillment readiness. Client applications must use this API and must not access the orders database directly.

## Context Navigation

Read only the context relevant to the change:

- Architecture or data ownership: `.chaos/architecture/system-overview.md`
- Order behavior or state transitions: `.chaos/business/order-lifecycle.md`
- HTTP endpoints or response behavior: `.chaos/contracts/orders-api.md`
- Payment processing or webhooks: `.chaos/integrations/payment-provider.md`

## Rules

- Preserve the order lifecycle invariants documented in `.chaos/business/order-lifecycle.md`.
- Treat payment-provider callbacks as untrusted and potentially duplicated.
- Keep API changes backward compatible within the current major version.
- Do not place temporary plans, task notes, or source-code copies in `.chaos/`.

## Source of Truth

`.chaos/` is the canonical source of truth for system behavior, rules, constraints, contracts, and architectural decisions. Source code implements that context and must not contradict it.

Before completing any code change:

1. Review the changed behavior against the relevant `.chaos/` documents.
2. Update the owning `.chaos/` document in the same change whenever behavior, rules, constraints, contracts, or architecture have changed.
3. Do not complete the task while the source code and `.chaos/` describe different behavior.

No Shared CHAOS repository is required for this standalone example. If a future contract becomes authoritative across multiple repositories, move that contract to Shared CHAOS and replace the local definition with a reference.