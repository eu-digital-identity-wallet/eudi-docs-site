# Revocation Status Provider

The Revocation Status Provider (RSP) is a supporting ecosystem service responsible for providing the current revocation status of a PID and/or EAA. In other words, it’s the “source of truth” that tells verifiers whether a PID or EAA is still valid or has been revoked.

## RSP role in the EUDI Wallet Ecosystem

In the EUDI Wallet ecosystem, the Revocation Status Provider (RSP) plays a pivotal and indispensable role in maintaining trust and integrity across the entire digital identity framework. As the authoritative source of revocation information, the RSP ensures that verifiers — whether public authorities, service providers, or relying parties — can reliably determine the current validity of any credential (PID or EAA) presented by a Wallet holder. Without such a mechanism, verifiers would be unable to distinguish between credentials that are legitimately valid and those that have been withdrawn, compromised, or invalidated for any reason, potentially undermining the security and trust of the ecosystem.

## Reference Implementation RSP

The Reference Implementation of the Revocation Status Provider (RSP) is designed solely to support experimentation, validation, and interoperability testing, enabling stakeholders, implementers, and participating Member States to explore and verify the functionality, behavior, and integration of revocation mechanisms in a safe and controlled environment.

It is important to note that this Reference Implementation is not intended to provide production-level performance, scalability, or security guarantees, and it should not be used as an operational service for issuing or verifying credentials in live environments. Its primary value lies in allowing developers and testers to validate interactions, test interoperability between wallets and verifiers, and gain confidence in the technical standards underpinning the EUDI Wallet framework.

By providing this controlled experimentation environment, the Reference Implementation RSP functions as a sandbox and validation tool, offering a safe, predictable, and fully auditable environment in which the critical aspects of credential revocation — such as status queries, updates, and offline verification — can be explored, tested, and refined prior to deployment in a real-world, production-grade EUDI Wallet ecosystem.

### Reference Implementation RSP service

For testing purposes, a hosted instance of the Reference Implementation Revocation Status Provider (RSP) component is included within the Issuer Provider and is accessible at <https://issuer.eudiw.dev>.

It provides the following API endpoints ([Swagger UI](https://dev.issuer.eudiw.dev/tslswagger/swagger)):

+ /token_status_list/get - Retrieves the status of a token from the revocation list (for debug and testing purposes only).
+ /token_status_list/set - Sets or updates the status of a token in the revocation list.
+ /token_status_list/take - Generates a new status structure to be included in a credential as well as a new entry in the attestation status list.

### Supported status lists and formats

The following status lists are supported:

+ Token Status List (TSL) as specified in IETF Draft <https://datatracker.ietf.org/doc/html/draft-ietf-oauth-status-list-12>, in JWT and CWT format;
+ Token Identifier List (TIL), as specified in ISO/IEC CD 18013-5 (second edition), in JWT and CWT format.

### Reference Implementation RSP deployment and configuration

The complete source code, deployment instructions, and configuration details for the Revocation Status Provider (RSP) Reference Implementation are publicly available in the GitHub repository at [eudi-srv-statuslist-py](https://github.com/eu-digital-identity-wallet/eudi-srv-statuslist-py).
