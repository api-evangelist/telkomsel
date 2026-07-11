# Telkomsel (telkomsel)

Telkomsel (PT Telekomunikasi Selular) is Indonesia's largest mobile network operator. Through DigiHub ([digihub.telkomsel.com](https://digihub.telkomsel.com)), its API marketplace, Telkomsel exposes network and subscriber APIs to developers and enterprises - A2P SMS and USSD messaging, subscriber status checks, identity verification (NIK/KTP matching), location verification, SIM swap detection (including a CAMARA-style API), consent management, and telco-data scoring products. Telkomsel is a GSMA Open Gateway participant, launching Number Verify, SIM Swap, and Device Location network APIs alongside the other Indonesian carriers, and partners with Vonage to distribute its network APIs globally.

**Access model:** documentation and DigiHub's per-endpoint OpenAPI documents are public (no login needed), but calling any endpoint requires a DigiHub account and a subscribed plan. Retail users get a one-time free Sandbox trial and prepaid Quota packages; Tier and PAYU (pay-as-you-use) plans are enterprise-only and require a signed NDA or commercial contract. Per-product prices (in IDR) are shown in the portal after login and are not published openly. Most APIs authenticate with an `api_key` header plus an `x-signature` header of `SHA256(API Key + Secret Key + epoch timestamp)`; the CAMARA-style SIM Swap API uses OIDC CIBA bearer tokens. Several subscriber-data products also require a registered customer consent ID per query.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/telkomsel/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/telkomsel/refs/heads/main/apis.yml)

## Tags

- Telecommunications
- Indonesia
- SMS
- Mobile Network
- CPaaS
- Network APIs
- Identity Verification

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

### Telkomsel DigiHub SMS API

Application-to-person SMS to Telkomsel subscribers - send regular and premium SMS with a registered (masked) Sender ID and pre-approved SMS templates, and poll delivery status for submitted messages. Sender IDs and templates are registered and approved through the DigiHub dashboard.

- **Human URL:** [https://digihub.telkomsel.com/documentation/consumer-guide/sender-id-sms-template](https://digihub.telkomsel.com/documentation/consumer-guide/sender-id-sms-template)
- **Base URL:** `https://api.digitalcore.telkomsel.com`

#### Properties

- [Documentation](https://digihub.telkomsel.com/documentation/consumer-guide/sender-id-sms-template)
- [API Reference](https://digihub.telkomsel.com/apis/V2/endpoint/71)
- [OpenAPI](openapi/telkomsel-openapi.yml)

### Telkomsel DigiHub USSD API

Broadcast USSD messages to Telkomsel subscribers and check the delivery status of USSD sends. Uses the same DigiHub `api_key` plus `x-signature` authentication as the rest of the marketplace.

- **Human URL:** [https://digihub.telkomsel.com/api/landing](https://digihub.telkomsel.com/api/landing)
- **Base URL:** `https://api.digitalcore.telkomsel.com`

#### Properties

- [Documentation](https://digihub.telkomsel.com/documentation)
- [API Reference](https://digihub.telkomsel.com/apis/V2/endpoint/77)
- [OpenAPI](openapi/telkomsel-openapi.yml)

### Telkomsel DigiHub Subscriber Check API

Query the state of a Telkomsel MSISDN - active status (ACTIVE, GRACE, EXPIRED, or CHURN, sold as the Active Status v3 product), subscriber type, roaming status, call-forwarding status, and whether a number has been recycled and reassigned to a new owner (Recycle v2).

- **Human URL:** [https://digihub.telkomsel.com/api/product/138](https://digihub.telkomsel.com/api/product/138)
- **Base URL:** `https://api.digitalcore.telkomsel.com`

#### Properties

- [Documentation](https://digihub.telkomsel.com/api/product/138)
- [API Reference](https://digihub.telkomsel.com/apis/V2/endpoint/137)
- [OpenAPI](openapi/telkomsel-openapi.yml)

### Telkomsel DigiHub Identity Verification API

Verify a customer's identity against Telkomsel SIM-registration data - check whether a NIK (Indonesian national identity number) and MSISDN are paired (NIK Matching v4), match KTP identity-card fields, and run general ID verification. An IoT KYC product covers know-your-customer checks for IoT SIMs.

- **Human URL:** [https://digihub.telkomsel.com/api/product/128](https://digihub.telkomsel.com/api/product/128)
- **Base URL:** `https://api.digitalcore.telkomsel.com`

#### Properties

- [Documentation](https://digihub.telkomsel.com/api/product/128)
- [API Reference](https://digihub.telkomsel.com/apis/V2/endpoint/142)
- [OpenAPI](openapi/telkomsel-openapi.yml)

### Telkomsel DigiHub Location API

Verify a subscriber's home or work location against Telkomsel network data (Location Verification v3) - submit a longitude/latitude, address, or zip code with the customer's consent ID and receive a match score - or retrieve a subscriber's last known location.

- **Human URL:** [https://digihub.telkomsel.com/api/product/131](https://digihub.telkomsel.com/api/product/131)
- **Base URL:** `https://api.digitalcore.telkomsel.com`

#### Properties

- [Documentation](https://digihub.telkomsel.com/api/product/131)
- [API Reference](https://digihub.telkomsel.com/apis/V2/endpoint/145)
- [OpenAPI](openapi/telkomsel-openapi.yml)

### Telkomsel DigiHub SIM Swap API

Detect whether a Telkomsel number's SIM card was recently swapped, to defend SMS one-time-password flows against account-takeover fraud. Two surfaces exist - the marketplace SIM Swap v2 product with DigiHub key-based auth, and a CAMARA-style `/sim-swap/v0/check` endpoint that follows the GSMA Open Gateway definition and authenticates with OIDC CIBA (`/bc-authorize` plus `/token`) bearer tokens.

- **Human URL:** [https://digihub.telkomsel.com/api/product/142](https://digihub.telkomsel.com/api/product/142)
- **Base URL:** `https://digihub.telkomsel.com`

#### Properties

- [Documentation](https://digihub.telkomsel.com/api/product/142)
- [API Reference](https://digihub.telkomsel.com/apis/V2/endpoint/189)
- [OpenAPI](openapi/telkomsel-openapi.yml)

### Telkomsel DigiHub Consent Management API

Register and manage customer consent before querying subscriber-data APIs - online consent registration plus an offline variant for consent collected out-of-band. Consent IDs issued here are required parameters on data products such as Location Verification and the scoring APIs.

- **Human URL:** [https://digihub.telkomsel.com/documentation](https://digihub.telkomsel.com/documentation)
- **Base URL:** `https://api.digitalcore.telkomsel.com`

#### Properties

- [Documentation](https://digihub.telkomsel.com/documentation)
- [API Reference](https://digihub.telkomsel.com/apis/V2/endpoint/138)
- [OpenAPI](openapi/telkomsel-openapi.yml)

### Telkomsel DigiHub Scoring and Insights API

Telco-data scoring and enrichment products for lenders, fintechs, and e-commerce - tScore telco credit scores, Income Score, Social Economy Status (SES), Interest v2 segments, Lifestyle Score, Loyalist, and TDI Tenure Score Category. Each returns a score or category for an MSISDN supplied with the customer's consent ID.

- **Human URL:** [https://digihub.telkomsel.com/api/product/108](https://digihub.telkomsel.com/api/product/108)
- **Base URL:** `https://api.digitalcore.telkomsel.com`

#### Properties

- [Documentation](https://digihub.telkomsel.com/api/product/108)
- [API Reference](https://digihub.telkomsel.com/apis/V2/endpoint/129)
- [OpenAPI](openapi/telkomsel-openapi.yml)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/telkomsel)
- [Website](https://www.telkomsel.com/en)
- [Portal](https://digihub.telkomsel.com)
- [Documentation](https://digihub.telkomsel.com/documentation)
- [Authentication](https://digihub.telkomsel.com/documentation/consumer-guide/api-authentication)
- [Plans](plans/telkomsel-plans-pricing.yml)
- [Rate Limits](rate-limits/telkomsel-rate-limits.yml)
- [Fin Ops](finops/telkomsel-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
