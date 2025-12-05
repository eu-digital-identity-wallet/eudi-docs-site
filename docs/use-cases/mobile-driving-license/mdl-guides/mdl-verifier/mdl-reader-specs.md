# mDL Reader Specifications

The specifications of the mDL reader are summarised in the table below.

## mDL Verifiable Credentials

|Specification |Optionality |Description and Reference |
|---|---|---|
| ISO/IEC 18013-5 (CBOR) | Mandatory | - [ARF], High Level Requirement:  mDL_01 <br/>- [ARF] "Annex 3.02 - mDL Rulebook" <br/>- [4th Driving License Directive] Annex I, Part C |
| mDL Data Model | Mandatory | As above |

## Presentation Interface (PI)

|Specification |Optionality |Description and Reference |
|---|---|---|
| Presentation Request (of verifiable credentials according to ISO/IEC 18013-5 standard) | Mandatory | [CIR 2024/2982](https://eur-lex.europa.eu/eli/reg_impl/2024/2982/oj){:target="_blank"} |

## Topology

|Specification |Optionality |Description and Reference |
|---|---|---|
| Cross device | Mandatory | ARF section 4.4.1 defines that proximity flow is when the User Device is physically near the Relying Part Instance. This implies that the flow occurs in different devices therefore the mDL reader can interact with the EUDI Wallet only in cross device scenario for the proximity flow (supervised or unsupervised). The mDL Reader implements only ARF section "4.4.2 Proximity presentation flows". |
| Same device | N/A | The same device flow is not applicable for the mDL Reader on the proximity flows as justified above. |

## Presentation Flows

|Specification |Optionality |Description and Reference |
|---|---|---|
| Remote | N/A | The remote flow is not applicable for the mDL Reader since only the proximity flow is supported. |
| Proximity | Mandatory | The mDL Reader implements only ARF section "4.4.2 Proximity presentation flows". |

## Initialization

|Specification |Optionality |Description and Reference |
|---|---|---|
| mDL reader using NFC | Optional | The EUDI Wallet can be activated either by the mDL Holder (user) or it can be triggered by the mDL Reader using NFC according to ISO/IEC 18013-5 section 6.3.2.2. The standard does not specify if this is mandatory for the mDL Reader. Therefore, it is considered optional. |

## Device Engagement Technologies

|Specification |Optionality |Description and Reference |
|---|---|---|
| NFC | Mandatory | According to Table 1 in ISO/IEC 18013-5 |
| QR Code | Mandatory | According to Table 1 in ISO/IEC 18013-5 |

## NFC Device Engagement Technology Support

|Specification |Optionality |Description and Reference |
|---|---|---|
| Static Handover | Mandatory | The mDL reader shall support both handover methods according to the last sentence of section 6.3.2.3 of ISO/IEC 18013-5. |
| Negotiated Handover | Mandatory | As above |

## Data Retrieval Methods

|Specification |Optionality |Description and Reference |
|---|---|---|
| Offline (device) retrieval | Mandatory | According to Table 2 in ISO/IEC 18013-5 |
| Online (server) retrieval | Excluded / Not Supported | The server data retrieval method allows the issuing authority to have knowledge when the mDL holder presents the mDL to a specific mDL verifier. This is prohibited explicitly by articles 5a.16 and 5a.5(b) of [eIDAS] and [ARF] Annex 2 High level requirement "ProxId_02". Therefore, this method is excluded (not supported) from the mDL target solution. |

## Message Encoding

|Specification |Optionality |Description and Reference |
|---|---|---|
| mdoc Request/Response messages encoded with CBOR | Mandatory | According to section 6.3.2.4 of in ISO/IEC 18013-5 "When using device retrieval, the mDL and mDL reader communicate using mdoc request and mdoc response messages encoded with CBOR". |

## Data Transmission/ Device Retrieval

|Specification |Optionality |Description and Reference |
|---|---|---|
| NFC | Mandatory | According to Table 2 in ISO/IEC 18013-5 |
| BLE | Mandatory | According to Table 2 in ISO/IEC 18013-5 |
| Wi-Fi Aware | Recommended | According to Table 2 in ISO/IEC 18013-5 |

## Data Device Retrieval using BLE

|Specification |Optionality |Description and Reference |
|---|---|---|
| mdoc central client mode | Mandatory | According to section 6.3.2.5 of  ISO/IEC 18013-5 "For device retrieval using BLE, the mDL reader shall support the mdoc central client mode and mdoc peripheral server mode". |
| mdoc peripheral server mode | Mandatory | As above |
| BLE L2CAP | Optional | According to section 6.3.2.5 of ISO/IEC 18013-5 that states "…The mDL and mDL reader may support the BLE 2CAP transmission profile..." |

## Data Server Retrieval

|Specification |Optionality |Description and Reference |
|---|---|---|
| WebAPI | Excluded / Not Supported | As per "Online (server) retrieval" above |
| OIDC | Excluded / Not Supported | As per "Online (server) retrieval" above |

## Security Mechanism and Trust Relationships for Device Retrieval

|Specification |Optionality |Description and Reference |
|---|---|---|
| Session Encryption | Mandatory (assumed) | Section 9.1.1 in ISO/IEC 18013-5 specifies that the session encryption applies to the device retrieval method. It does not specify explicitly it as mandatory. It is assumed that it is mandatory. Table 2 in ISO/IEC 18013-7 applies to remote presentation to an mDL reader over the internet and therefore is not applicable to the proximity flow. |
| Issuer data authentication | Mandatory | As above for section 9.1.2 in ISO/IEC 18013-5. Section 9.3.1 applies also specifying as a mandatory capability. |
| The verifier shall verify that the mDL Issuer did not revoke the mDL (Revocation of mDL) | Mandatory | ARF section 6.6.3.1, point 6 (and 6.3.6.7) The specification for mDL revocation via a status list or reference list is expected to be introduced in a future version of ISO/IEC 18013-5. Consequently, mDL Verifiers shall be capable to verify the validity status of the mDL by retrieving the status list or identifier list. ARF section 6.6.3.7 specifies that "Attestation Provider includes revocation information in the PID or attestation, if it is valid for longer than 24 hours." |
| mdoc authentication (device binding) | Mandatory (assumed) | As above for section 9.1.3 in ISO/IEC 18013-5 |
| mdoc Reader authentication | Mandatory (assumed) | As above for section 9.1.4 in ISO/IEC 18013-5 |

## Security Mechanism for Server Retrieval

|Specification |Optionality |Description and Reference |
|---|---|---|
| TLS 1.2 or higher | Excluded / Not Supported | As per "Online (server) retrieval" above. |
| JSON Web Signature (JWS). | Excluded / Not Supported | As per "Online (server) retrieval" above |

## Disclosure Options

|Specification |Optionality |Description and Reference |
|---|---|---|
| Selective Disclosure | Mandatory | The interface between the mDL and the mDL Reader shall support the selective release of mDL data to an mDL Reader as per ISO/IEC 18013-5 section 6.2 point (d) Additionally, ARF in High Level Requirements OIA_07 specify the support of selective disclosure of attributes from PIDs and attestations. |

## Policy-based Checks

|Specification |Optionality |Description and Reference |
|---|---|---|
| Certificate Revocation list | Mandatory | Section 9.3.3 in ISO/IEC 18013-5 specifies that "mdoc reader shall have access to certificate revocation information". An mDL reader needs access to the issuing authority's certificate authority (IACA) root certificate to verify issuer data authentication. It checks the status of the Document Signing certificate and the IACA certificate against the published CRLs. It confirms that the issuer's IACA certificate is present, and that it is listed as an issuer of the doctype "org.iso.18013.5.1.mDL". |
| ETSI LOTL support | Mandatory | The Reference Implementation supports ETSI trusted lists because of other use cases, see e.g. ARF Annex 2 requirement PuBPNot_03: "The format of the PuB-EAA Provider Trusted List SHALL comply with ETSI TS 119 612 v2.1.1 or with a suitable profile similarly derived from ETSI TS 102 231". |
| IACA retrieval via VICAL | Mandatory | [4<sup>th</sup> Driving License Directive] in Art. 5.7 mandates that the Commission shall adopt implementing acts [among others] for recognition of those driving licences by third country authorities. Annex C in ISO/IEC 18013-5 specifies the VICAL mechanism. It does not explicitly specify this mechanism as mandatory and therefore it is considered optional. This mechanism applies to the third countries. |
