---
name: Tokenize a card and charge it for recurring / one-click
description: Store a payment instrument as a registration token, then charge it later without re-collecting card data.
api: openapi/hyperpay-openapi.yml
operations: [createRegistration, createRegistrationPayment, getRegistration, deleteRegistration]
---

# Tokenize a card and charge it for recurring / one-click

Use this to save a shopper's payment instrument once and reuse it for one-click or recurring charges.

## Auth
`Authorization: Bearer <access-token>` + `entityId` on every request. Test `https://test.oppwa.com`, live `https://eu-prod.oppwa.com`.

## Steps
1. **Register (tokenize)** — `createRegistration` (POST /v1/registrations) with `entityId`, `paymentBrand`, and the card fields. Store the returned registration token `id`.
2. **Charge the token** — `createRegistrationPayment` (POST /v1/registrations/{id}/payments) with `entityId`, `amount`, `currency`, `paymentType` (`DB`). No card data needed.
3. **Inspect a token** — `getRegistration` (GET /v1/registrations/{id}) with the `entityId` query param.
4. **Delete a token** — `deleteRegistration` (DELETE /v1/registrations/{id}) when the shopper removes the instrument or you must stop recurring.

## Success / error handling
Check `result.code` (test success `000.100.110`, live `000.000.000`). A recurring charge can still be declined (`800.100.*`) or blocked by risk (`100.400.*`) — see errors/hyperpay-decline-codes.yml.

## Guardrails
Tokenization stores payment credentials and recurring charges move money — both default to human-in-the-loop for agents (agentic-access/). No idempotency key: reconcile with queryPayment before re-charging.
