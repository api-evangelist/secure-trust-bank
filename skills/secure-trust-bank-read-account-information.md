---
name: Read account information with consent (AIS)
description: Obtain a PSU account-access consent, then read accounts, balances and transactions under the OBIE Read/Write v4.0 AIS standard.
api: openapi/obie-account-info-standard-openapi.yaml
operations: [CreateAccountAccessConsents, GetAccountAccessConsentsConsentId, GetAccounts, GetAccountsAccountIdBalances, GetAccountsAccountIdTransactions]
---

# Read account information with consent (AIS)

Secure Trust Bank's account products conform to the OBIE Read/Write v4.0 Account &
Transaction Information standard. This is a FAPI-secured, consent-mediated flow: a TPP
must be onboarded with OBIE/eIDAS certificates and use OAuth2 + mutual-TLS. Never invent
account or consent ids.

## Auth
- Client-credentials token (`TPPOAuth2Security`, scope `accounts`) for the consent.
- Authorization-code token (`PSUOAuth2Security`) after PSU Strong Customer Authentication for the data calls.
- Send FAPI headers: `x-fapi-interaction-id`, `x-fapi-auth-date`, `x-fapi-customer-ip-address`, and `x-jws-signature` where required.

## Steps
1. `CreateAccountAccessConsents` — create an account-access consent declaring the permissions and expiry. Capture the returned `ConsentId`.
2. Redirect the PSU to authenticate (SCA) and authorise the consent, then exchange the code for a PSU access token.
3. `GetAccountAccessConsentsConsentId` — confirm the consent `Status` is `Authorised` before reading data.
4. `GetAccounts` — list the accounts the PSU consented to share; capture each `AccountId`.
5. `GetAccountsAccountIdBalances` — read balances for an account.
6. `GetAccountsAccountIdTransactions` — read transactions; page with the `Links` (Next) / `Meta` (TotalPages) envelope and bound with the date-time query window.

## Conventions & errors
- Pagination and tracing per `conventions/secure-trust-bank-conventions.yml`.
- Errors use the OBErrorResponse1 envelope; a `403` means the consent lacks the permission or is revoked — see `errors/secure-trust-bank-problem-types.yml`.
