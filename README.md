# Secure Trust Bank (secure-trust-bank)

Secure Trust Bank PLC is an award-winning UK specialist bank, founded in 1952 in the West Midlands and headquartered in Solihull, providing savings accounts and specialist lending to over a million retail and business customers. It is a publicly listed company (London Stock Exchange: STB) rather than a mutual or building society, authorised by the Prudential Regulation Authority and regulated by the Financial Conduct Authority and the PRA (FRN 204550).

As a UK ASPSP under PSD2 and the CMA Open Banking framework, its regulated account products sit against the Open Banking Implementation Entity (OBIE) standards. Secure Trust Bank is a specialist lender and **not** one of the nine CMA9-mandated banks; at review time it publishes **no public developer portal or bank-branded Open Banking developer host**. The API surfaces below therefore reference the shared OBIE standard specifications the bank's products conform to, not proprietary Secure Trust Bank API contracts.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/secure-trust-bank/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/secure-trust-bank/refs/heads/main/apis.yml)

## Tags

- Financial Services
- Banking
- Open Banking
- PSD2
- OBIE
- United Kingdom
- Payments
- Account Information
- Specialist Lender
- Savings

## Timestamps

- **Created:** 2026-07-23
- **Modified:** 2026-07-23

## APIs

### Secure Trust Bank Open Data API (OBIE Standard)

The UK Open Banking Open Data API — a public, unauthenticated reference-data surface for ATMs, branches and product information, defined by the OBIE Open Data Standard v1.3. Represented as the shared standard; no Secure Trust Bank Open Data host was confirmed live at review time.

- **Human URL:** [https://openbankinguk.github.io/opendata-api-docs-pub/](https://openbankinguk.github.io/opendata-api-docs-pub/)

#### Tags

- Open Data
- Reference Data
- ATMs
- Branches
- Products

#### Properties

- [OpenAPI](openapi/obie-open-data-standard-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://openbankinguk.github.io/opendata-api-docs-pub/)
- [API Reference](https://github.com/OpenBankingUK/opendata-api-spec-compiled)

### Secure Trust Bank Account & Transaction Information API (OBIE Read/Write, AIS)

The OBIE Read/Write Account and Transaction Information (AIS) API — FAPI-secured access to account, balance, transaction, standing order, direct debit and statement data with customer consent. FAPI-grade OAuth2/OIDC, mutual-TLS and PSD2 strong customer authentication apply.

- **Human URL:** [https://openbankinguk.github.io/read-write-api-site3/](https://openbankinguk.github.io/read-write-api-site3/)

#### Tags

- Account Information
- AIS
- Transactions
- FAPI

#### Properties

- [OpenAPI](openapi/obie-account-info-standard-openapi.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://openbankinguk.github.io/read-write-api-site3/)
- [API Reference](https://github.com/OpenBankingUK/read-write-api-specs)

### Secure Trust Bank Payment Initiation API (OBIE Read/Write, PIS)

The OBIE Read/Write Payment Initiation (PIS) API — FAPI-secured initiation of domestic, scheduled, standing-order, international and file payments on behalf of a consenting customer, with PSD2 strong customer authentication.

- **Human URL:** [https://openbankinguk.github.io/read-write-api-site3/](https://openbankinguk.github.io/read-write-api-site3/)

#### Tags

- Payment Initiation
- PIS
- Payments
- FAPI

#### Properties

- [OpenAPI](openapi/obie-payment-initiation-standard-openapi.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://openbankinguk.github.io/read-write-api-site3/)
- [API Reference](https://github.com/OpenBankingUK/read-write-api-specs)

### Secure Trust Bank Confirmation of Funds API (OBIE Read/Write, CBPII)

The OBIE Read/Write Confirmation of Funds (CBPII) API — FAPI-secured yes/no confirmation that funds are available on an account, for card-based payment instrument issuers, under PSD2 strong customer authentication.

- **Human URL:** [https://openbankinguk.github.io/read-write-api-site3/](https://openbankinguk.github.io/read-write-api-site3/)

#### Tags

- Confirmation of Funds
- CBPII
- FAPI

#### Properties

- [OpenAPI](openapi/obie-confirmation-of-funds-standard-openapi.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://openbankinguk.github.io/read-write-api-site3/)
- [API Reference](https://github.com/OpenBankingUK/read-write-api-specs)

## Common Properties

- [Website](https://www.securetrustbank.com/)
- [About](https://www.securetrustbank.com/about-us)
- [Blog](https://www.securetrustbank.com/newsroom)
- [Security](https://www.securetrustbank.com/security)
- [Support](https://www.securetrustbank.com/contact-us)
- [Terms of Service](https://www.securetrustbank.com/website-terms)
- [Privacy Policy](https://www.securetrustbank.com/privacy-statement)
- [LinkedIn](https://www.linkedin.com/company/secure-trust-bank)
- [Open Banking Standard](https://www.openbanking.org.uk/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
