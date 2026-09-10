# Payment Provider Integration

## Responsibility

The payment provider owns authorization and authorization reversal. The Orders API sends only the order reference, amount, currency, and provider customer or payment-method tokens. Raw card data must never enter this service.

## Authorization

Each authorization request uses the order ID as its provider idempotency key. A timeout is treated as an unknown result, not a declined payment. The service queries the provider or retries with the same key before deciding the outcome.

An order moves from `pending_payment` to `paid` only after a confirmed authorization whose order reference, amount, and currency match the order.

## Webhooks

- Verify the provider signature against the raw request body before parsing or processing the event.
- Reject events outside the provider's accepted timestamp tolerance.
- Deduplicate events by provider event ID.
- Acknowledge valid duplicate events without repeating side effects.
- Record unknown event types and acknowledge them; they must not change order state.

Webhook delivery order is not guaranteed. Processing must evaluate the current order state and the canonical transition rules rather than assuming events arrive sequentially.

## Failures and Retries

Transient provider failures use bounded exponential backoff. Permanent declines are not retried automatically. Exhausted retries leave the order in `pending_payment` and emit an operational alert; they do not silently cancel the order.

When cancelling a `paid` order, the service requests an authorization reversal. The order remains `paid` until reversal succeeds. A failed reversal is retryable and must be visible to operations.

## Security

Provider secrets are loaded from the runtime secret store and must not appear in source code, logs, fixtures, or `.css/`. Logs may include provider request and event IDs but must exclude tokens and personal payment data.