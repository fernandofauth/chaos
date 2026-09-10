# Order Lifecycle

## States

An order has one of these states:

- `pending_payment` — created and awaiting payment authorization.
- `paid` — payment has been authorized and the order may be prepared for fulfillment.
- `fulfilling` — accepted by the fulfillment service.
- `fulfilled` — handed to the carrier or otherwise completed.
- `cancelled` — terminated before fulfillment.

## Allowed Transitions

```text
pending_payment --> paid --> fulfilling --> fulfilled
       |             |
       +-------------+-----> cancelled
```

- A new order starts in `pending_payment`.
- Payment authorization moves it to `paid`.
- Fulfillment acceptance moves it from `paid` to `fulfilling`.
- Fulfillment completion moves it from `fulfilling` to `fulfilled`.
- Only `pending_payment` and `paid` orders may be cancelled.
- `fulfilled` and `cancelled` are terminal states.

Repeating a transition request that has already succeeded returns the current order without causing the side effect again. Any other invalid transition is rejected with `order_state_conflict`.

## Invariants

- An order must contain at least one line item with a positive quantity.
- Prices and totals are fixed when the order is created.
- A payment authorization must match the order ID, amount, and currency.
- An order cannot enter `paid` until payment authorization is confirmed.
- An order cannot enter `fulfilling` before it is `paid`.
- Cancelling a paid order requires a successful authorization reversal before the cancellation becomes final.

## Idempotency

Order creation requires an idempotency key scoped to the authenticated client. Reusing the same key with the same payload returns the original result. Reusing it with a different payload returns `idempotency_conflict`.

Idempotency records are retained for 24 hours. Provider events are deduplicated permanently by provider event ID.