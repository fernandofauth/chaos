# Acme Orders API

Acme Orders API manages customer orders, payment status, and fulfillment for Acme's commerce applications.

This repository is a documentation-only example of the Context for Human-AI Organization of Systems (CHAOS). The commands and source layout below illustrate what a real service README could contain; they are not runnable from this example.

## Technology Stack

- Node.js 22
- TypeScript
- Fastify
- PostgreSQL
- Redis

## Development

In a complete implementation, a developer would use:

```sh
npm install
cp .env.example .env
npm run db:migrate
npm run dev
```

Run the test suite with:

```sh
npm test
```

## Basic Usage

Create an order:

```sh
curl -X POST http://localhost:3000/v1/orders \
  -H "Authorization: Bearer <token>" \
  -H "Content-Type: application/json" \
  -H "Idempotency-Key: 8f40af41-62e7-46e8-bad1-d197a15fe751" \
  -d '{"customerId":"cus_123","items":[{"sku":"SKU-RED-MUG","quantity":2}]}'
```

## Repository Structure

```text
acme-orders-api/
├── README.md
├── AGENTS.md
├── .chaos/
└── src/
```

- `README.md` helps developers install and use the service.
- `AGENTS.md` directs AI agents to the context required for a change.
- `.chaos/` contains the canonical architecture, business, contract, and integration context.
- `src/` contains the implementation in a complete project.

Developers should consult `.chaos/` when working on behavior or constraints that are not explained by setup instructions alone.