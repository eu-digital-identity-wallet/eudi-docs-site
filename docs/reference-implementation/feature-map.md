
# EUDI Wallet Reference Implementation – Feature Map

Below you can find an overview of the user functionality provided by the EUDI Wallet Reference Implementation, along with links to relevant functional and technical documentation. 

## Standards, Protocols and Formats

The EUDI Wallet uses a set of standards and technical specifications essential for its implementation. These provide the foundation needed to ensure secure issuance, presentation, authentication, signing and certification of digital identity credentials.

For a comprehensive set of standards and technical specifications (STS), visit the [Essential Standards and Technical Specifications (STS)](https://eudi.dev/latest/technical-specifications/) section of the Architecture Reference Framework (ARF).

The following table indicates the credential formats supported by the EUDI Wallet Reference Implementation. 

| Format | Status | Description | 
| --- | --- | --- |
| `mso_mdoc` | Published (ISO/IEC 18013-5) | Credential format based on ISO/IEC 18013-5 using a signed Mobile Security Object (MSO) to bind and protect data elements. Supports selective disclosure. | 
| `SD-JWT-VC` | Draft (IETF / OpenID Foundation) | Credential format extending JSON Web Tokens with selective disclosure for web-native verifiable credentials. | 


## Features

The following table provides a high-level overview of the key user functionalities supported by the EUDI Wallet Reference Implementation.

| Features | Description | Status | 
| --- | --- | --- |
| [Issuance](#issuance) | Issuance of verifiable credentials | In Progress|
| [Presentation](#presentation) | Presentation of verifiable credentials | In Progress|
| [rQES](#rqes) | Electronic signing with EUDI Wallet | Completed |
| [Transaction Logs](#transaction-logs) | Log of historic transactions executed by the EUDI Wallet | In Progress|
| [Request data deletion from RPs](#request-data-deletion-from-rps) | Users requesting data deletion from Relying Parties they have previously interacted with |Planned |
| [Report unlawful or suspicious requests to DPA(s)](#report-unlawful-or-suspicious-requests) | Users reporting suspicious data requests to national Data Protection Authorities |Planned |
| [Attestation Revocation](#attestation-revocation) | Revoking issued attestations | Completed |
| [Pseudonyms](#pseudonyms) | Using pseudonyms (i.e. passkeys) for authentication | Planned |
| [Wallet Revocation](#wallet-revocation) | Revoking wallet instance | Planned |
| [Wallet to Wallet](#wallet-to-wallet) | Enabling the exchange of PID/attestations between two EUDI Wallets | Planned|
| [Wallet Backup and Restore](#wallet-backup-and-restore) | Supporting procedures for backing up and restoring attestations of an EUDI Wallet | Planned |
| [Migrate to a different wallet](#migrate-to-a-different-wallet) | Supporting procedures for migrating attestations to a different EUDI Wallet |Planned |
| [Support for ZKP](#support-for-zkp) | Supporting Zero-Knowledge Proofs in EUDI Wallet interactions |Planned|

You can explore the [EUDI Wallet Reference Implementation Roadmap](https://github.com/orgs/eu-digital-identity-wallet/projects/24){:target="_blank"} for more details about features and enhancements that are currently being developed or planned for future implementation.


The following sections provide detailed features supported by the EUDI Wallet Reference Implementation, grouped by functional area.

### Issuance

This covers applicable issuance flows in alignment with OpenID4VCI. Expand to explore detailed functional specifications for the "Issuance" capabilities.

The "Issuance" functionality is aligned with the OpenID4VCI protocol and is continuously updated to align with the [evolving standards and protocols](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/77){:target="_blank"}.


| Feature | Description | Status |
| --- | --- | --- |
| [Deferred Issuance](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/40){:target="_blank"} | Issue credentials with a deferred process | Completed |
| [Credential Offer](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/42){:target="_blank"} | Supporting issuer-initiated flows | Completed |
| [Pre-authorisation code flow](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/41){:target="_blank"} | Issuance decoupled from the user's authorisation, as it is performed outside of the issuance flow | Completed|
| [Batch Issuance](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/18){:target="_blank"} | Issuance of multiple instances of the same credential type | Completed|
| [Attestation Re-Issuance](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/52){:target="_blank"} | Enabling the re-issuance of Personal Identification Data (PID)/attestation before its expiration | Planned|
| [Alignment to latest version of the standard](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/77){:target="_blank"} | Enhancements to issuance functionalities as detailed by the latest version of the OpenID4VCI standard | In Progress|
| [Alignment to latest version of the HAIP profile](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/69){:target="_blank"} | Enhancements to issuance, remote presentation and trust management as detailed by the HAIP v1.0 profile | Planned|


---
### Presentation

This covers applicable presentation flows in alignment with OpenID4VP and ISO/IEC 18013-5. Expand to explore detailed functional specifications for the "Presentation" capabilities.
 

The "Presentation" functionality is aligned with the OpenID4VCP protocol (for remote presentation flows) and is continuously updated to align with the [evolving standards and protocols](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/64){:target="_blank"}.

| Feature | Description | Status |
| --- | --- | --- |
| [Remote Same-device presentation](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/64){:target="_blank"} | User uses a web browser or another application on the device on which the Wallet Unit is installed to share attestations to a requesting Relying Party. | Completed |
| [Remote Cross-device presentation](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/64){:target="_blank"} | User uses a web browser on a device other than the device on which their Wallet Unit is installed to share attestations to a requesting Relying Party. |Completed |
| [Proximity presentation](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/64){:target="_blank"} | User and their device are physically near the Relying Party Instance, and PIDs and attestations are exchanged via proximity technologies (e.g., NFC, Bluetooth), either under human supervision (Supervised) or directly to a machine without supervision (Unsupervised). | Completed |
| [Digital Credential API](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/34){:target="_blank"} | The Digital Credentials API enables the secure presentation of attestations from the EUDI Wallet, leveraging the web browser for the presentation flow. | Planned |
| [Proximity Verifier](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/43){:target="_blank"} | This includes implementation of an open source verifier application for Android, supporting stakeholders for developing their own proximity reader solutions. | Completed |
| [Alignment to latest version of the standard](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/64){:target="_blank"} | This provides enhancements to presentation functionalities as detailed by the latest version of the OpenID4VP standard (v1.0). | Completed|

---
### rQES

This covers scenarios for Remote qualified signatures. Expand to explore detailed functional specifications for the "rQES" capabilities.

| Feature | Description | Status |
| --- | --- | --- |
| [Wallet-Driven rQES (external SCA)](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/15){:target="_blank"} | Remote qualified signatures in a Wallet-driven model, using an external "Signature Creation Application" | Completed |
| [Wallet-Driven rQES (internal SCA)](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/27){:target="_blank"} | Remote qualified signatures in a Wallet-driven model, using an internal (i.e. wallet component) "Signature Creation Application" | Completed |
| [RP-Driven rQES (internal SCA)](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/16){:target="_blank"} | Remote qualified signatures in a RP-driven model | Completed |
| [Document Retrieval (Wallet-Driven flows)](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/80){:target="_blank"} | A planned scenario for retrieving the document to be signed from the corresponding Relying Party, instead of from the device's file system ("wallet-centric" model for rQES) | Completed |

---
### Pseudonyms

This covers utilising passkeys through the EUDI Wallet for authentication purposes. Expand to explore detailed functional specifications for the "Pseudonyms" capabilities.


| Feature | Description | Status |
| --- | --- | --- |
| [Pseudonym functionality](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/26){:target="_blank"} | Pseudonyms allow EUDI Wallet users to be identified by service provider/relying parties without revealing any personal information. | Planned |

---
### Transaction Logs

EUDI Wallet Privacy Dashboard provides a record of transactions (i.e. data exchanges) executed through the EUDI Wallet. Expand to explore detailed functional specifications for the "Transaction Logs (Privacy Dashboard)" capabilities.


| Feature | Description | Status |
| --- | --- | --- |
| [Transaction Logs (Privacy Dashboard)](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/22){:target="_blank"} | The EUDI Wallet Privacy Dashboard provides a record of transactions (i.e. data exchanges) executed through the EUDI Wallet. Transaction logs provide a higher degree of transparency, privacy and control for Users over their personal data. | Completed |


---

### Request data deletion from RPs

This covers Users requesting data deletion from Relying Parties they have previously interacted with.


| Feature | Description | Status |
| --- | --- | --- |
|[Request Data Deletion](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/31){:target="_blank"}| Users request the deletion of their personal attributes from Relying Parties with which they have interacted through their Wallet Unit. | Planned |


---

### Report unlawful or suspicious requests

Users report a Relying Party to the competent national Data Protection Authority where an allegedly unlawful or suspicious request for data is received.


| Feature | Description |Status |
| --- | --- | --- |
|[Report unlawful or suspicious requests](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/32){:target="_blank"}| Users, through the Wallet Unit, report a Relying Party to the competent national Data Protection Authority where an allegedly unlawful or suspicious request for data is received. |Planned |


---

### Attestation Revocation

This covers attestations revoked by the issuer. Expand to explore detailed functional specifications for the "Attestation Revocation" capabilities.

| Feature | Description | Status |
| --- | --- | --- |
| [Handling attestation revocation](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/4){:target="_blank"}| This provides attestation revocation support for the reference implementation including support from the issuer, verifier and wallet. | Completed |

---
### Wallet Revocation

This covers wallet instances revoked by the wallet provider. Expand to explore detailed functional specifications for the "Wallet Revocation" capabilities.


| Feature | Description | Status |
| --- | --- | --- |
| [Wallet instance revocation](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/28){:target="_blank"}| TBC | Planned |

---

### Wallet to Wallet

An EUDI Wallet User can request that another EUDI Wallet User share an attestation of attributes using their EUDI Wallet Instances when they are in close proximity. Expand to explore detailed functional specifications for "Wallet to Wallet" interaction capabilities.
 

| Feature | Description | Status |
| --- | --- | --- |
|[Wallet to Wallet Communication](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/30){:target="_blank"}| An EUDI Wallet User can request that another EUDI Wallet User share an attestation of attributes using their EUDI Wallet Instances when they are in close proximity. | Planned |


---
### Wallet Backup and Restore

This covers backing up and restoring attestations of an EUDI Wallet. Expand to explore detailed functional specifications for "Backup and Restore" interaction capabilities. 


| Feature | Description | Status |
| --- | --- | --- |
|[Wallet Backup & Restore](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/5){:target="_blank"}| This covers procedures for backing up the attestations a wallet unit contains. | Planned |

---
### Migrate to a different wallet

This covers migrating attestations to a different EUDI Wallet. Expand to explore detailed functional specifications for "Migration" capabilities.


| Feature | Description | Status |
| --- | --- | --- |
|[Migrate to a different wallet](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/33){:target="_blank"}| This covers procedures for migrating backed-up attestations of a wallet unit to a different Wallet Solution. | Planned |


---

### Support for ZKP

This enables the support of Zero-Knowledge Proofs (ZKP).


| Feature | Description | Status |
| --- | --- | --- |
|[Support for Zero-Knowledge Proof](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/56){:target="_blank"}| This enables the support of ZKPs in EUDI Wallet interactions. | Planned |


---

## Supported Attestations

The following table provides an overview of the key attestations supported by the EUDI Wallet Reference Implementation.

| Attestation | Description | Status |
| --- | --- | --- |
| [PID](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/67){:target="_blank"} | Support for the "Personal Identification Data (PID)" in alignment with the [PID Rulebook](https://github.com/eu-digital-identity-wallet/eudi-doc-attestation-rulebooks-catalog/blob/main/rulebooks/pid/pid-rulebook.md){:target="_blank"} | Completed|
| [mDL](https://eu-digital-identity-wallet.github.io/eudi-doc-architecture-and-reference-framework/latest/annexes/annex-3/annex-3.02-mDL-rulebook/){:target="_blank"} | Support for the "Mobile Driving License" in alignment with the [mDL Rulebook](https://github.com/eu-digital-identity-wallet/eudi-doc-attestation-rulebooks-catalog/blob/main/rulebooks/mdl/mdl-rulebook.md){:target="_blank"} | Completed |
| [EHIC](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/45){:target="_blank"} | Support for the "European Health Insurance Card" | Completed |
| [PDA1](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/46){:target="_blank"} | Support for the "Portable Document A1" | Completed |

For further attestations supported by the EUDI Wallet Reference Implementation you can check our [Issuer](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py){:target="_blank"}.

## Business Demos

### Business Demos

A set of demo implementations are available that mock business flows in different contexts and demonstrate the EUDI Wallet functionalities in real-life scenarios. 

| Business Scenario | Description | Status |
| --- | --- | --- |
|[Travel](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/6){:target="_blank"}| A "Travel Use Case" implementation for the EUDI Wallet that demonstrates how the EUDI Wallet works in a "Travel" business scenario. The EUDI Wallet is used for several purposes, such as presenting attestations (remotely and in proximity) and digitally signing documents. | Completed |
|[Cross-border recruitment](https://github.com/eu-digital-identity-wallet/eudi-wallet-reference-implementation-roadmap/issues/55){:target="_blank"}| A "Cross-Border Recruitment Use Case" implementation for the EUDI Wallet that demonstrates how the EUDI Wallet works in a "Cross-Border Recruitment" business scenario. The EUDI Wallet is used for several purposes, such as presenting attestations (remotely and in proximity) when applying/on-boarding for a job and digitally signing a job contract. | In Progress |

## Releases
The latest published versions of the key EUDI Wallet Reference Implementation components are summarised below:

| Component | Release |
| --- | --- |
| EUDI Wallet app (Android) | [![Latest Android Wallet UI](https://img.shields.io/github/v/release/eu-digital-identity-wallet/eudi-app-android-wallet-ui?label=Latest%20Android%20Wallet%20UI)](https://github.com/eu-digital-identity-wallet/eudi-app-android-wallet-ui/releases){:target="_blank"} |
| EUDI Wallet app (iOS) | [![Latest iOS Wallet UI](https://img.shields.io/github/v/release/eu-digital-identity-wallet/eudi-app-ios-wallet-ui?label=Latest%20iOS%20Wallet%20UI)](https://github.com/eu-digital-identity-wallet/eudi-app-ios-wallet-ui/releases){:target="_blank"} |
| Remote Verifier | [![Latest Remote Verifier](https://img.shields.io/github/v/release/eu-digital-identity-wallet/eudi-web-verifier?label=Latest%20Remote%20Verifier)](https://github.com/eu-digital-identity-wallet/eudi-web-verifier/releases){:target="_blank"} |
| Issuer (Python) | [![Latest Issuer Python](https://img.shields.io/github/v/release/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py?label=Latest%20Issuer%20Python)](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/releases){:target="_blank"} |
| Issuer (Kotlin) | [![Latest Issuer Kotlin](https://img.shields.io/github/v/release/eu-digital-identity-wallet/eudi-srv-pid-issuer?label=Latest%20Issuer%20Kotlin)](https://github.com/eu-digital-identity-wallet/eudi-srv-pid-issuer/releases){:target="_blank"} |
| Proximity Verifier | [![Latest Proximity Verifier](https://img.shields.io/github/v/release/eu-digital-identity-wallet/eudi-app-multiplatform-verifier-ui?label=Latest%20Verifier%20UI)](https://github.com/eu-digital-identity-wallet/eudi-app-multiplatform-verifier-ui/releases){:target="_blank"} |



You can refer to the [EUDI Wallet Reference Implementation Roadmap](https://github.com/orgs/eu-digital-identity-wallet/projects/24){:target="_blank"} to view further details on the release roadmap.








