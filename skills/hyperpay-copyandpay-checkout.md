---
name: Accept a card payment with the COPYandPAY widget
description: Prepare a hosted checkout, load the COPYandPAY widget in the browser, and read the result — keeping raw card data off your server.
api: openapi/hyperpay-openapi.yml
operations: [createCheckout, getCheckoutStatus]
---

# Accept a card payment with COPYandPAY

Use this flow to collect a card, mada, STC Pay, or Apple Pay payment without handling raw card data on your server (minimizes PCI scope).

## Auth
Every request needs BOTH: `Authorization: Bearer <access-token>` header AND an `entityId` (channel identifier). Content type is `application/x-www-form-urlencoded`. Use `https://test.oppwa.com` for testing, `https://eu-prod.oppwa.com` for live.

## Steps
1. **Prepare the checkout** — `createCheckout` (POST /v1/checkouts) with `entityId`, `amount` (decimal string, e.g. `92.00`), `currency` (`SAR`), and `paymentType` (`DB` debit or `PA` pre-authorization). Read `id` from the response.
2. **Render the widget** — load `paymentWidgets.js?checkoutId={id}` and drop a `<form class="paymentWidgets" data-brands="VISA MASTER AMEX MADA STC_PAY APPLEPAY">` on your page (see components/). The shopper submits card data directly to the platform.
3. **Read the result** — after the widget redirects back, call `getCheckoutStatus` (GET /v1/checkouts/{id}/payment) with the `entityId` query param.

## Success / error handling
Success is decided by `result.code`, not HTTP status. Match against the success regex `^(000\.000\.|000\.100\.1|...)`. In test mode a success returns `000.100.110`; in live, `000.000.000`. Decline and risk codes are in errors/hyperpay-decline-codes.yml.

## Idempotency
There is no Idempotency-Key. If a call times out (`900.*`), do NOT blindly retry — reconcile first with `queryPayment` (GET /v1/query/{id}).
