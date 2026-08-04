# HyperPay (hyperpay)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
