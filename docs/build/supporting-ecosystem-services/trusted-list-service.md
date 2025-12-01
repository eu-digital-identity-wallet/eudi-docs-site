# Trusted List Provider (TLP)

The TLP is a supporting ecosystem service responsible for creating, maintaining, signing and publishing the national Trusted Lists (TLs) and the EU List of Trusted Lists (LoTL), which contain the trust anchors and status information of Wallet Providers, PID Providers, QEAA Providers, PuB-EAA Providers, Access Certificate Providers and Registration Certificate Providers. By providing authenticated, machine-readable TLs, the TLP enables Wallets, Relying Parties, and ecosystem components to verify that an entity is supervised and trusted, ensuring cross-border trust, interoperability and the integrity of cryptographic verification processes within the EUDI Wallet ecosystem.

## TLP Role in the EUDI Wallet Ecosystem

The TLP is a supporting service responsible for the management, maintenance and publication of TLs used across the EUDI Wallet ecosystem. TLs form a critical trust infrastructure: they contain trust anchors (public keys and identifiers) for all entities that must be recognised as trusted by relying parties and other ecosystem components.

A TLP ensures that the Wallet Providers, PID Providers, QEAA Providers, PuB-EAA Providers, Access Certificate Providers, and Registration Certificate Providers can be automatically and reliably verified by any stakeholder in the ecosystem.
An entity's trusted status is established by verifying its presence on the relevant TL.

TLPs operate at two levels:

1. National TLs – created, signed and managed by Member States;
2. EU LoTL – a unified list created, signed and managed by the European Commission that aggregates all national TLs.

The source of trust for the LoTL is the *Official Journal of the European Union* (OJEU).

## Reference Implementation TLP

The Reference Implementation TLP is designed solely to support experimentation, validation and interoperability testing within the EUDI Wallet ecosystem. It serves as an illustrative, non-production example of how TLs and the EU LoTLs can be created, managed and published, enabling developers, Member States, and ecosystem participants to familiarise themselves with the trust infrastructure envisioned by the Architecture and Reference Framework (ARF). This implementation is not subject to security, robustness, operational or compliance requirements applicable to production-grade TLPs and must therefore not be deployed or relied upon in real operational environments.

### Reference Implementation TLP service

For testing purposes, there is a hosted instance of the [Reference Implementation TLP](https://trustedlist.serviceproviders.eudiw.dev/).

It provides:

- a complete UI for managing TLs, TSPs, trust services and LoTL,
- integration with EUDI Wallet authentication,
- XML generation and signing for TL and LoTL,
- a configuration model based on environment variables,
- docker support for rapid deployment.

This service demonstrates the operational workflows of a TLP and can be used for creating TLs and LoTL for testing, development or conformance checks.

#### Core functionalities

##### TL Lifecycle Management

The RI TLP service provides capabilities for the Member State (TSL Operator) to:

- onboard and manage Trust Service Providers (TSPs) relevant to the EUDI Wallet ecosystem;
- manage trust services associated with each TSP;
- create, update and electronically sign the National TL;
- publish the TL in a secure and accessible location;
- maintain TL metadata and multilingual information.

##### LoTL Management (for European Commission Operators)

For the Commission, the TLP supports:

- aggregating all TLs published by Member States;
- creating and signing the EU LoTL;
- managing LoTL metadata and multilingual content;
- publishing the LoTL.

##### Trust Anchor Publication

Each TL contains:

- the public key (trust anchor) for each recognised entity;
- the identifier of the entity;
- status information and service metadata.

Relying Parties and Wallets use these trust anchors to verify:

- digital signatures,
- attestations,
- credential issuances,
- authentication responses.

#### Users and Access Model

The TLP supports three user roles:

- TSL Operator
- TSP User
- LoTL Operator.

The TSL Operator manages the national TL by:

- overseeing TSPs and trust services;
- creating, editing, and signing TLs;
- adding multilingual information;
- linking TSPs and services before generating the signed XML TL.

The TSP User manages their own TSP records and trust services by:

- creating and managing TSP entries;
- creating and managing trust services;
- maintaining multilingual service information. 

The LoTL Operator is the only role who may:

- create, update and sign the EU LoTL;
- manage LoTL metadata and multilingual content;
- aggregate TLs provided by Member States.

### Format of the TL and LoTL

The current Reference Implementation of the TLP focuses on demonstrating the fundamental trust-establishment mechanisms of the EUDI Wallet ecosystem. Its present capabilities are limited to the generation of national TLs and the EU LoTL strictly following the ETSI EN 119 612 specification. This means that all outputs – structure, metadata, signing model and publication format – adhere exclusively to the ETSI 119 612 schema. Other formats, profiles or alternative serialisation approaches are not supported at this stage but will be added after ETSI 119 602 is published.

### Reference Implementation TLP deployment and configuration

The complete source code, deployment instructions and configuration details for the TLP Reference Implementation are publicly available in the GitHub repository at [eudi-srv-web-trustedlist-manager-py](https://github.com/eu-digital-identity-wallet/eudi-srv-web-trustedlist-manager-py/).

The TLP can be run:

- locally (Python/Flask environment),
- with Docker (via provided docker-compose).

It supports configuration via environment variables covering:

- service URLs,
- trust anchor validation paths,
- verifier endpoints,
- XML signing certificate paths,
- logging,
- database configuration.
