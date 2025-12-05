# Wallet Provider Specifications

The following are considered necessary capabilities of the EUDI Wallet reference implementation for the mDL Use Case:

## mDL Verifiable Credentials
|Specification |Optionality |Description and Reference |
|---|---|---|
| ISO/IEC 18013-5 (CBOR) | Mandatory | [4th Driving License Directive] Annex I, Part C <br/>[ARF], High Level Requirement:  mDL_01 <br/>[ARF] "Annex 3.02 - mDL Rulebook" |
| mDL Data Model | Mandatory | As above |

## Attestation Issuance Interface (AII)

|Specification |Optionality |Description and Reference |
|---|---|---|
| Credential Issuance API according to OpenID4VCI v1.0 specification | Mandatory | Refer to Issuer relevant specification |

Issuance Initiation

|Specification |Optionality |Description and Reference |
|---|---|---|
| Issuer-initiated | Optional | Refer to Issuer relevant specification |
| Wallet-initiated | Mandatory | Refer to Issuer relevant specification |

Issuer Authorization

|Specification |Optionality |Description and Reference |
|---|---|---|
| Pre-Authorized Code Flow | Optional | Refer to Issuer relevant specification |
| Authorization Code Flow | Mandatory | Refer to Issuer relevant specification |

Number of VCs per issuance request

|Specification |Optionality |Description and Reference |
|---|---|---|
| One verifiable credential per issuance request | Mandatory | Refer to Issuer relevant specification |
| Multiple same verifiable credentials per issuance request (Batch Issuance) | Mandatory | Refer to Issuer relevant specification |

## Time of Issuance
|Specification |Optionality |Description and Reference |
|---|---|---|
| Immediate Issuance | Optional [^1] | Refer to Issuer relevant specification |
| Deferred Issuance | Optional [^1] | Refer to Issuer relevant specification |

## Additional issuance flows

|Specification |Optionality |Description and Reference |
|---|---|---|
| Dynamic Issuance (synchronous or just-in-time) | Optional | Refer to Issuer relevant specification |
| Re-issuance | Mandatory | Refer to Issuer relevant specification |

## Topology for Issuance (issuer-initiated) flows

|Specification |Optionality |Description and Reference |
|---|---|---|
| Same device | Optional | Refer to Issuer relevant specification |
| Cross device | Optional | Refer to Issuer relevant specification |

## Issuance Trust Relationships

|Specification |Optionality |Description and Reference |
|---|---|---|
| Authenticate mDL Issuer using the access certificate (IACA) | Mandatory | ARF section 6.6.2.1 point 1 and section 6.6.2.2 |
| Verify authenticity of mDL | Mandatory | ARF section 6.6.2.1 point 5 and section 6.6.2.5 |
| Download the mDL Issuer Access CA Trusted List(s) from the relevant Trusted List Provider(s) | Mandatory | ARF section 6.6.2.2 |
| Checks registration certificate or the online service of the Registrar indicated in the access certificate | Mandatory | ARF section 6.6.2.2 specifies that "Wallet Unit checks the registration information contained in the registration certificate (if available in the Issuer metadata) or in the online service of the Registrar indicated in the access certificate." |

## mDL Presentation Policy

|Specification |Optionality |Description and Reference |
|---|---|---|
| Store locally the mDL presentation policy | Mandatory | ARF section 6.6.2.1 point 7 and section 6.6.2.7 |

## Presentation Interface (PI)

|Specification |Optionality |Description and Reference |
|---|---|---|
| Proximity Flow: Presentation Request (of verifiable credentials according to ISO/IEC 18013-5 standard) | Mandatory | Refer to Proximity Verifier relevant specification |
| Remote Flow: Presentation Request (of verifiable credentials) according to ISO 18013 -7 Annex B (OpenID4VP specification) | Mandatory | Refer to Remote Verifier relevant specification<br/> OpenID4VP version 1.0 will be supported instead of Draft 18 which is specified in ISO 18013-5 Annex B. |
| Remote Flow: Presentation Request (of verifiable credentials) according to ISO 18013 -7 Annex C | Optional | Refer to Remote Verifier relevant specification <br/>ARF section 4.4.3.1 states that "The use of this API by Wallet Units and Relying Parties is optional." |
| Remote Flow: Presentation Request (of verifiable credentials) according to OpenID4VP specification in combination with the Digital Credentials API | Optional | Refer to Remote Verifier relevant specification <br/>ARF section 4.4.3.1 states that "The use of this API by Wallet Units and Relying Parties is optional." |

## Topology for Presentation Flow

|Specification |Optionality |Description and Reference |
|---|---|---|
| Cross device (for proximity and remote flows) | Mandatory | Refer to Remote Verifier relevant specification <br/>Refer to Proximity Verifier relevant specification |
| Same device (for remote flow) | Mandatory | Refer to Remote Verifier relevant specification |

## Presentation Flows

|Specification |Optionality |Description and Reference |
|---|---|---|
| Remote | Mandatory | Refer to Remote Verifier relevant specification |
| Proximity | Mandatory | Refer to Proximity Verifier relevant specification |

## Initialization for Proximity Presentation Flow

|Specification |Optionality |Description and Reference |
|---|---|---|
| mDL reader using NFC | Optional | Refer to Proximity Verifier relevant specification |

## Device Engagement Technologies for Proximity Presentation Flow

|Specification |Optionality |Description and Reference |
|---|---|---|
| NFC | Conditional [^1] | According to Table 1 in ISO/IEC 18013-5 |
| QR Code | Conditional [^1] | According to Table 1 in ISO/IEC 18013-5 |

## NFC Device engagement technology support for Proximity Presentation Flow

|Specification |Optionality |Description and Reference |
|---|---|---|
| Static Handover | Conditional [^2] | According to section 6.3.2.3 in ISO/IEC 18013-5, if the EUDI Wallet supports NFC for device engagement then it shall support Static Handover, Negotiated Handover, or both. |
| Negotiated Handover | Conditional [^2] | As above |

## Data Retrieval Methods for Proximity Presentation Flow

|Specification |Optionality |Description and Reference |
|---|---|---|
| Offline (device) retrieval | Mandatory | Refer to Proximity Verifier relevant specification |
| Online (server) retrieval | N/A | This method does not apply to the EUDI Wallet. |

## Message Encoding for Proximity Presentation Flow

|Specification |Optionality |Description and Reference |
|---|---|---|
| mdoc Request/Response messages encoded with CBOR | Mandatory | Refer to Proximity Verifier relevant specification |

## Data Transmission/ Device Retrieval for Proximity Presentation Flow

|Specification |Optionality |Description and Reference |
|---|---|---|
| NFC | Conditional [^1] | According to Table 2 in ISO/IEC 18013-5 |
| BLE | Conditional [^1] | According to Table 2 in ISO/IEC 18013-5 |
| Wi-Fi Aware | Optional | According to Table 2 in ISO/IEC 18013-5 |

## Data Device Retrieval using BLE for Proximity Presentation Flow

|Specification |Optionality |Description and Reference |
|---|---|---|
| mdoc central client mode | Optional | Section 8.3.3.1.1.1 in ISO/IEC 18013-5 implies that this mode is optional. |
| mdoc peripheral server mode | Optional | As above |
| BLE L2CAP | Optional | Refer to Proximity Verifier relevant specification |

## Security Mechanism and Trust Relationships for Device Retrieval for Proximity/Remote (DC API) Presentation Flow

|Specification |Optionality |Description and Reference |
|---|---|---|
| Session Encryption | Mandatory (assumed) for proximity <br/>Conditional for remote | For offline interactions, a session-based encryption mechanism directly encrypts the mDL response. |
| Issuer data authentication | Mandatory | According to ISO/IEC 18013-5, section 9.1.2, the purpose of issuer data authentication is to confirm that the mdoc data is issued by the issuing authority and that it has not changed since issuance. Section 9.3.1 also applies, specifying this as a mandatory capability. <br/>Issuer data authentication is implemented by way of a digital signature over mDL data, using a public-private (asymmetric) key pair. |
| mdoc authentication (device binding) | Mandatory | According to section 9.1.3 in ISO/IEC 18013-5 the security objective of mDL authentication is to prevent cloning of the mDL and to mitigate man in the middle attacks. |
| mdoc Reader authentication | Mandatory for proximity <br/>Optional for remote | According to section 9.1.4 in ISO/IEC 18013-5, mDL Reader authentication uses information stored in the mDL Reader to confirm that the mDL Reader and the mDL Reader Request are authenticated. <br/>Section 7.1.2 states that "An mDL may require mdoc reader authentication (see 9.1.4) before releasing data elements not marked as mandatory in Table 5. An mDL shall not require mdoc reader authentication as a precondition for the release of any of the mandatory data elements. An mDL may offer functionality to the mDL holder to pre-authorise the release of mandatory data elements selected by the mDL holder to mDL readers using mdoc reader authentication." |

## Disclosure Options

|Specification |Optionality |Description and Reference |
|---|---|---|
| Selective Disclosure | Mandatory | Refer to Proximity Verifier relevant specification |
| Digital Credentials Query Language (DCQL) | Mandatory | OpenID4VP v1.0 chapter 6 specifies a JSON-encoded query language that allows the Verifier to request Presentations that match the query. <br/>OpenID4VP introduced DCQL in Draft 22. Therefore, DCQL is not supported in Draft 18. |

## Authorization Response for Remote Presentation Flow

|Specification |Optionality |Description and Reference |
|---|---|---|
| Support encrypted Authorization Response | Mandatory | Refer to Remote Verifier relevant specification |
| End-User authentication using SIOP v2 | Excluded / Not Supported | Refer to Remote Verifier relevant specification |

## Policy-based Checks

|Specification |Optionality |Description and Reference |
|---|---|---|
| Revocation (of mDL) | Mandatory | ARF in Annex 2 VCR_19 states that "A Wallet Unit SHOULD regularly check the revocation status of its PIDs, attestations, and WUAs, and notify the User if a PID, attestation, or WUA (i.e. the Wallet Unit itself), is revoked." |

## Digital Credentials API for Remote Presentation Flow

|Specification |Optionality |Description and Reference |
|---|---|---|
| Device Request | Optional | Refer to Remote Verifier relevant specification DC API is optional according to ARF section 4.4.3.1 |
| Device Response | Optional | Refer to Remote Verifier relevant specification <br/>Refer above for optionality |
| HPKE single shot encryption /decryption | Optional | Refer to Remote Verifier relevant specification <br/>Refer above for optionality |
| Session Transcript | Optional | Refer to Remote Verifier relevant specification <br/>Refer above for optionality |
| SerializedOrigin in Session Transcript | Optional | Refer above for optionality <br/>Annex C.5 in ISO/IEC 18013-57 states that the mdoc (wallet) shall use the origin received from the user agent to determine the SerializedOrigin value. If the mdoc (wallet) does not receive the origin from the user agent, it shall abort the transaction. |

[^1]: Support for at least one of these methods is mandatory.

[^2]: Support for one of the handover methods or both.
