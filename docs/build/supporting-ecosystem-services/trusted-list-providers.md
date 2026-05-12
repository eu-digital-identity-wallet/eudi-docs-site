# Trusted List Service (TLP)

## Overview

The Trusted List Provider (TLP) is a supporting ecosystem service within the European Digital Identity (EUDI) Wallet ecosystem. It is responsible for creating, maintaining, signing, and publishing Trusted Lists (TLs) and the EU List of Trusted Lists (LoTL). ([docs.eudi.dev][1])

Trusted Lists contain trust anchors and status information for entities such as:

* Wallet Providers
* PID Providers
* QEAA Providers
* PuB-EAA Providers
* Access Certificate Providers
* Registration Certificate Providers

These trusted lists enable wallets, relying parties, and ecosystem services to verify whether an entity is supervised and trusted within the EUDI ecosystem. ([docs.eudi.dev][1])

---

# TLP Role in the EUDI Wallet Ecosystem

The TLP provides the trust infrastructure required for interoperability and secure verification across Member States.

Trusted Lists are used to:

* Verify digital signatures
* Validate attestations
* Verify credential issuances
* Support authentication responses

Two levels of Trusted Lists exist:

1. **National Trusted Lists (TLs)**
   Managed and signed by Member States.

2. **EU List of Trusted Lists (LoTL)**
   Aggregated and managed by the European Commission.

The Official Journal of the European Union (OJEU) acts as the root source of trust for the LoTL. ([docs.eudi.dev][1])

---

# Reference Implementation TLP

The Reference Implementation Trusted List Provider is intended for:

* experimentation,
* interoperability validation,
* testing,
* developer onboarding.

It is not intended for production use. ([docs.eudi.dev][1])

Hosted instance:

[Trusted List Service Demo](https://trustedlist.serviceproviders.eudiw.dev/?utm_source=chatgpt.com)

GitHub repository:

[eudi-srv-web-trustedlist-manager-py](https://github.com/eu-digital-identity-wallet/eudi-srv-web-trustedlist-manager-py?utm_source=chatgpt.com)

---

# Core Functionalities

## TL Lifecycle Management

The TLP enables Member States to:

* onboard and manage Trust Service Providers (TSPs),
* manage trust services,
* create and sign Trusted Lists,
* publish Trusted Lists securely,
* maintain multilingual metadata. ([docs.eudi.dev][1])

---

## LoTL Management

The European Commission can:

* aggregate national Trusted Lists,
* create and sign the EU LoTL,
* maintain multilingual metadata,
* publish the LoTL. ([docs.eudi.dev][1])

---

## Trust Anchor Publication

Each Trusted List contains:

* public keys,
* identifiers,
* service metadata,
* status information.

These trust anchors are used to validate:

* signatures,
* credentials,
* attestations,
* authentication flows. ([docs.eudi.dev][1])

---

# Users and Roles

The TLP supports three main roles:

| Role          | Responsibilities                      |
| ------------- | ------------------------------------- |
| TSL Operator  | Manage national Trusted Lists         |
| TSP User      | Manage Trust Service Provider entries |
| LoTL Operator | Manage the EU LoTL                    |

The TSL Operator can:

* create and sign TLs,
* manage TSPs,
* maintain multilingual information.

The TSP User can:

* maintain trust services,
* manage service metadata.

The LoTL Operator can:

* aggregate national TLs,
* create and sign the EU LoTL. ([docs.eudi.dev][1])

---

# Standards and Compliance

The current Reference Implementation follows:

* ETSI EN 119 612 specification,
* eIDAS Regulation requirements,
* machine-readable XML trusted list structures. ([docs.eudi.dev][1])

Trusted Lists under eIDAS have legal significance:
a provider or service is considered qualified only if it appears in the Trusted List. ([Digital Strategy][2])

---

# Deployment and Configuration

The TLP supports:

* local deployment,
* Docker deployment,
* environment-based configuration.

Configuration includes:

* service URLs,
* verifier endpoints,
* XML signing certificates,
* logging,
* database configuration. ([docs.eudi.dev][1])

---

# Related Trusted List Ecosystem Resources

* [EU Trusted Lists Overview](https://digital-strategy.ec.europa.eu/en/policies/eu-trusted-lists?utm_source=chatgpt.com)
* [ETSI Trust Service Providers Information](https://portal.etsi.org/TBSiteMap/ESI/TrustServiceProviders.aspx?utm_source=chatgpt.com)
* [eSignature Trusted List Browser](https://ec.europa.eu/digital-building-blocks/wikis/display/DIGITAL/eSignature%2BTrusted%2BList%2BBrowser?utm_source=chatgpt.com)

[1]: https://docs.eudi.dev/latest/build/supporting-ecosystem-services/trusted-list-service/?utm_source=chatgpt.com "Trust List Service - European Digital Identity"
[2]: https://digital-strategy.ec.europa.eu/en/policies/eu-trusted-lists?utm_source=chatgpt.com "List of qualified trust service providers in the EU | Shaping Europe’s digital future"

