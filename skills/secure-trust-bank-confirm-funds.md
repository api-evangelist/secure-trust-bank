---
name: Confirm funds availability (CBPII)
description: Create a confirmation-of-funds consent and check whether funds are available on an account under OBIE Read/Write v4.0 CBPII.
api: openapi/obie-confirmation-of-funds-standard-openapi.yaml
operations: [CreateFundsConfirmationConsents, CreateFundsConfirmations]
---

# Confirm funds availability (CBPII)

Secure Trust Bank's confirmation-of-funds surface conforms to the OBIE Read/Write v4.0
CBPII standard, for card-based payment instrument issuers. FAPI-secured and
consent-mediated. Returns a yes/no funds-available answer, never a balance.

## Auth
- Client-credentials token (`TPPOAuth2Security`, scope `fundsconfirmations`) for the consent.
- Authorization-code token (`PSUOAuth2Security`) after PSU SCA authorises the consent.
- Send the FAPI headers; sign write requests with `x-jws-signature`.

## Steps
1. `CreateFundsConfirmationConsents` — create the funds-confirmation consent naming the account; capture the `ConsentId`.
2. Have the PSU authorise the consent via SCA; confirm it is `Authorised`.
3. `CreateFundsConfirmations` — submit an amount; read the boolean `FundsAvailable` result.

## Conventions & errors
- Envelope, tracing and error semantics per `conventions/secure-trust-bank-conventions.yml` and `errors/secure-trust-bank-problem-types.yml`.
- A `403` means the consent is not authorised for this account or has expired.
