# Orders API Contract

## General Rules

- The base path is `/v1`.
- Requests use JSON and responses use JSON unless the response has no body.
- Clients authenticate with an OAuth 2.0 bearer token.
- Order identifiers are opaque strings prefixed with `ord_`.
- Timestamps use UTC and RFC 3339 format.
- Monetary amounts are integers in the currency's smallest unit.

## Endpoints

### Create an order

`POST /v1/orders`

Requires an `Idempotency-Key` header. The request supplies a customer reference and at least one item containing a SKU and positive quantity. The service resolves current prices and calculates totals.

Returns `201 Created` with an order in `pending_payment`, or `200 OK` when replaying a previously successful idempotent request.

### Get an order

`GET /v1/orders/{orderId}`

Returns the order when it belongs to the authenticated account. An unknown order and an order owned by another account both return `404 Not Found` to avoid disclosing its existence.

### List orders

`GET /v1/orders?cursor={cursor}&limit={limit}`

Orders are sorted by creation time descending. `limit` defaults to 25 and may not exceed 100. When more results exist, the response includes an opaque `nextCursor`.

### Cancel an order

`POST /v1/orders/{orderId}/cancel`

Returns the cancelled order. Cancellation follows the rules in `../business/order-lifecycle.md`. Repeating a completed cancellation returns the current cancelled order.

## Errors

Errors have a stable machine-readable code and a human-readable message:

```json
{
  "error": {
    "code": "order_state_conflict",
    "message": "The order cannot be cancelled in its current state."
  }
}
```

Documented error codes remain stable within `/v1`. New optional response fields may be added without a version change; removing or changing the meaning of a field requires a new major API version.