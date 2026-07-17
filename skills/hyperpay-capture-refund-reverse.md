---
name: Capture, refund, or reverse a payment
description: Run back-office operations against a prior payment — capture a pre-auth, refund a debit, or reverse/void.
api: openapi/hyperpay-openapi.yml
operations: [managePayment, queryPayment]
---

# Capture, refund, or reverse a payment

Use this to settle or unwind a prior payment referenced by its `id`.

## Auth
`Authorization: Bearer <access-token>` + `entityId` on every request. Test `https://test.oppwa.com`, live `https://eu-prod.oppwa.com`.

## Steps
1. **Run the back-office op** — `managePayment` (POST /v1/payments/{id}) with `entityId`, `paymentType` set to:
   - `CP` — capture a prior `PA` pre-authorization (include `amount`/`currency`).
   - `RF` — refund a settled `DB`/captured payment (full or partial `amount`).
   - `RV` — reverse/void a not-yet-settled payment.
2. **Confirm** — read `result.code`; verify with `queryPayment` (GET /v1/query/{id}) if the result is a timeout (`900.*`).

## Success / error handling
Success is `result.code` matching the success pattern (test `000.100.110`, live `000.000.000`). A refund/reversal can be rejected for state reasons — inspect `result.description` and errors/hyperpay-result-codes.yml.

## Money-movement guardrail
Capture, refund, and reversal all move money — `physical` consequence, require human-in-the-loop for agent execution (agentic-access/). No idempotency key: reconcile with queryPayment rather than retrying a failed back-office call.
