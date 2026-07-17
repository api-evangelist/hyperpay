---
name: Take a server-to-server payment
description: Submit a card / mada / Apple Pay payment directly server-to-server (requires PCI-DSS scope) and confirm its status.
api: openapi/hyperpay-openapi.yml
operations: [createPayment, queryPayment]
---

# Take a server-to-server payment

Use this when you hold PCI-DSS scope and want to send payment data directly from your server (no browser widget).

## Auth
`Authorization: Bearer <access-token>` + `entityId` on every request. Body is `application/x-www-form-urlencoded`. Test host `https://test.oppwa.com`, live `https://eu-prod.oppwa.com`.

## Steps
1. **Submit the payment** — `createPayment` (POST /v1/payments) with `entityId`, `amount`, `currency` (`SAR`), `paymentBrand` (`VISA`/`MASTER`/`AMEX`/`MADA`/`STC_PAY`/`APPLEPAY`), `paymentType` (`PA` pre-auth or `DB` debit), and the `card.number` / `card.holder` / `card.expiryMonth` / `card.expiryYear` / `card.cvv` fields.
2. **Confirm status** — read `result.code` from the response; if uncertain (timeout `900.*`) confirm with `queryPayment` (GET /v1/query/{id}) using the `entityId` query param.

## Success / error handling
Decide success by matching `result.code` against the success pattern (test success `000.100.110`, live `000.000.000`). Bank declines (`800.100.*`), risk rejections (`100.400.*`), and 3DS failures (`100.390.*`) are catalogued in errors/hyperpay-decline-codes.yml.

## Money-movement guardrail
This operation moves money and handles raw card data — treat as `physical` consequence: require human-in-the-loop for agent execution (see agentic-access/hyperpay-agentic-access.yml). No idempotency key exists — reconcile via queryPayment instead of retrying.
