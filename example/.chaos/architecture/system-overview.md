# System Overview

## Responsibility

The Acme Orders API is the system of record for an order from creation through fulfillment or cancellation. It coordinates payment authorization but does not store card details or execute fulfillment itself.

## Boundaries

- Commerce clients create and read orders through the HTTP API.
- The Orders API is the only service permitted to read or write the orders database.
- The payment provider owns payment credentials, authorization, and capture execution.
- The fulfillment service consumes orders only after they become ready for fulfillment.
- Redis may support request idempotency and short-lived caching, but PostgreSQL remains authoritative.

## Components

```text
Commerce clients
       |
       v
Orders HTTP API ---> PostgreSQL
       |
       +-----------> Redis
       |
       +-----------> Payment provider
       |
       +-----------> Fulfillment service
```

The domain layer validates order transitions before persistence. HTTP handlers and provider adapters must not bypass those rules.

## Data Ownership

An order owns its line items, totals, currency, customer reference, status, and payment reference. Product descriptions and customer profiles belong to their respective systems; the order stores only the immutable values needed to preserve the transaction record.

All monetary amounts are stored as integers in the currency's smallest unit. Every order uses one currency, and totals must be calculated by the service rather than accepted from clients.

## Reliability

Order writes and their corresponding outbox events must commit in the same database transaction. External calls occur outside the transaction and may be retried. Consumers must therefore tolerate duplicate events.