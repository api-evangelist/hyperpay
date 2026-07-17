# HyperPay (hyperpay)

HyperPay is a MENA / Saudi Arabia online payment gateway built on the ACI / OPPWA Open Payment Platform. Its REST API powers the COPYandPAY hosted widget and a Server-to-Server integration, accepting cards (VISA, MASTER, AMEX), the Saudi domestic mada scheme, STC Pay, and Apple Pay, priced and settled in SAR. Additional products include HyperSplit (marketplace payouts) and HyperBill (invoicing).

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/hyperpay/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/hyperpay/refs/heads/main/apis.yml)

## Tags

- Payments
- Payment Gateway
- Fintech
- MENA
- Saudi Arabia
- mada
- Apple Pay
- Cards

## Timestamps

- **Created:** 2026-07-17
- **Modified:** 2026-07-17

## APIs

### HyperPay COPYandPAY API

Prepare a checkout (POST /v1/checkouts) to initialize the COPYandPAY JavaScript widget in the shopper's browser, then read the result via GET /v1/checkouts/{id}/payment. Sensitive card data flows browser-to-platform, minimizing merchant PCI scope.

- **Human URL:** [https://hyperpay.docs.oppwa.com/tutorials/integration-guide](https://hyperpay.docs.oppwa.com/tutorials/integration-guide)
- **Base URL:** `https://eu-prod.oppwa.com/v1`

#### Tags

- Checkout
- Hosted Widget
- Cards

#### Properties

- [Documentation](https://hyperpay.docs.oppwa.com/tutorials/integration-guide)
- [API Reference](https://hyperpay.docs.oppwa.com/reference/parameters)
- [OpenAPI](openapi/hyperpay-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/hyperpay.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### HyperPay Server-to-Server Payments API

Direct server-to-server payments (POST /v1/payments) with paymentType PA (pre-authorization) or DB (debit) across VISA, MASTER, AMEX, mada, STC Pay and Apple Pay, plus back-office capture, refund and reversal via POST /v1/payments/{id}. Requires merchant PCI-DSS scope.

- **Human URL:** [https://hyperpay.docs.oppwa.com/tutorials/server-to-server](https://hyperpay.docs.oppwa.com/tutorials/server-to-server)
- **Base URL:** `https://eu-prod.oppwa.com/v1`

#### Tags

- Payments
- Server to Server
- mada
- Apple Pay

#### Properties

- [Documentation](https://hyperpay.docs.oppwa.com/tutorials/server-to-server)
- [API Reference](https://hyperpay.docs.oppwa.com/reference/parameters)
- [OpenAPI](openapi/hyperpay-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/hyperpay.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### HyperPay Registration Tokens API

Tokenize a payment instrument (POST /v1/registrations) and charge it later for one-click or recurring payments (POST /v1/registrations/{id}/payments), with retrieval and deletion of stored tokens.

- **Human URL:** [https://hyperpay.docs.oppwa.com/tutorials/manage-payments/registration](https://hyperpay.docs.oppwa.com/tutorials/manage-payments/registration)
- **Base URL:** `https://eu-prod.oppwa.com/v1`

#### Tags

- Tokenization
- Recurring
- One Click

#### Properties

- [Documentation](https://hyperpay.docs.oppwa.com/tutorials/manage-payments/registration)
- [OpenAPI](openapi/hyperpay-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/hyperpay.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### HyperPay Query API

Retrieve the status of a prior payment by id or by the resourcePath returned in a redirect/webhook notification (GET /v1/query/{id}).

- **Human URL:** [https://hyperpay.docs.oppwa.com/tutorials/reporting](https://hyperpay.docs.oppwa.com/tutorials/reporting)
- **Base URL:** `https://eu-prod.oppwa.com/v1`

#### Tags

- Reporting
- Status

#### Properties

- [Documentation](https://hyperpay.docs.oppwa.com/tutorials/reporting)
- [OpenAPI](openapi/hyperpay-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### HyperPay HyperSplit

HyperSplit distributes a single collected payment across multiple sub-merchants or beneficiaries for marketplace and platform payout scenarios. Onboarding and API access are arranged with a HyperPay account manager.

- **Human URL:** [https://www.hyperpay.com/hypersplit/](https://www.hyperpay.com/hypersplit/)
- **Base URL:** `https://www.hyperpay.com/hypersplit/`

#### Tags

- Payouts
- Marketplace
- Split Payments

#### Properties

- [Documentation](https://www.hyperpay.com/hypersplit/)

### HyperPay HyperBill

HyperBill issues invoices and shareable payment links that collect payment through the HyperPay platform without a custom checkout integration.

- **Human URL:** [https://www.hyperpay.com/hyperbill/](https://www.hyperpay.com/hyperbill/)
- **Base URL:** `https://www.hyperpay.com/hyperbill/`

#### Tags

- Invoicing
- Payment Links

#### Properties

- [Documentation](https://www.hyperpay.com/hyperbill/)

## Common Properties

- [Website](https://www.hyperpay.com/)
- [Documentation](https://hyperpay.docs.oppwa.com/)
- [LinkedIn](https://www.linkedin.com/company/hyperpay)
- [Plans](plans/hyperpay-plans-pricing.yml)
- [Rate Limits](rate-limits/hyperpay-rate-limits.yml)
- [Fin Ops](finops/hyperpay-finops.yml)
- [Blog](https://www.hyperpay.com/blog/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
