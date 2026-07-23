---
name: Initiate a domestic payment (PIS)
description: Create a domestic payment consent, obtain PSU authorisation, then submit an idempotent domestic payment under OBIE Read/Write v4.0 PIS.
api: openapi/obie-payment-initiation-standard-openapi.yaml
operations: [CreateDomesticPaymentConsents, GetDomesticPaymentConsentsConsentId, CreateDomesticPayments, GetDomesticPaymentsDomesticPaymentId]
---

# Initiate a domestic payment (PIS)

Secure Trust Bank's payment products conform to the OBIE Read/Write v4.0 Payment
Initiation standard. FAPI-secured, consent-mediated, with PSD2 Strong Customer
Authentication. Never invent payment or consent ids or amounts.

## Auth
- Client-credentials token (`TPPOAuth2Security`, scope `payments`) to set up the consent.
- Authorization-code token (`PSUOAuth2Security`) after PSU SCA to submit the payment.
- Sign write requests with `x-jws-signature`; send the FAPI headers.

## Steps
1. `CreateDomesticPaymentConsents` — register the payment consent (creditor, amount, reference). Capture the `ConsentId`.
2. Redirect the PSU for SCA to authorise the consent; exchange the code for a PSU access token.
3. `GetDomesticPaymentConsentsConsentId` — confirm the consent `Status` is `Authorised`.
4. `CreateDomesticPayments` — submit the payment against the authorised consent. **Send a unique `x-idempotency-key` header** (max 40 chars); retrying the same key with the same payload returns the original result rather than double-paying.
5. `GetDomesticPaymentsDomesticPaymentId` — poll the payment `Status` (e.g. `AcceptedSettlementInProcess` → `AcceptedSettlementCompleted`).

## Conventions & errors
- Idempotency, tracing and pagination: `conventions/secure-trust-bank-conventions.yml`.
- A `409` signals idempotency-key reuse with a differing payload; `422` a business-rule failure — see `errors/secure-trust-bank-problem-types.yml`.
