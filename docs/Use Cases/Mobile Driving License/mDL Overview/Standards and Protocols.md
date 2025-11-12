# :clipboard: Standards and Protocols
The [4th Driving License Directive] clarifies that the mDL Use Case target solution shall comply with the ISO/IEC 18013-5 standard on mobile driving licences and since mDL can only be issued to EUDI wallets provided in accordance with Regulation (EU) 910/2014, some of the requirements applicable to EUDI wallets are also applicable to mDL providers. The latter requirements are further detailed by the Regulation (EU) 910/2014, including its implementing acts, in some cases, further detailed by the technical Architecture and Reference Framework (ARF).

## Standards and Specifications references

The mDL Use Case target solution is based on the following standards and specifications:

- [ISO/IEC 18013-5:2021(E)] is the international standard focused on implementing a Mobile Driving Licence (mDL) application on mobile devices. The provisional second version of this standard is referenced regarding the mDL revocation capabilities.
- [ISO/IEC 18013-7] This document augments the capabilities of the mobile driving licence (mDL) standardized in ISO/IEC 18013-5 with the presentation of a mobile driving licence to a reader over the internet.
- [OpenID for Verifiable Credential Issuance (OID4VCI)](https://openid.net/specs/openid-4-verifiable-credential-issuance-1_0-final.html): is a standardized protocol defining an API for issuing Verifiable Credentials. The protocol is built on top of the OAuth 2.0 framework, where the Wallet acts as an OAuth 2.0 Client to obtain authorization to receive credentials from a Credential Issuer, which acts as a Resource Server
- [OpenID for Verifiable Presentations (OpenID4VP)](https://openid.net/specs/openid-4-verifiable-presentations-1_0.htm): ) is the mandatory protocol for presenting attributes from attestations to a Relying Party (verifier) in remote (online) scenarios. It defines the message structures and transaction flows for a Wallet to respond to a presentation request from a Verifier over the internet.
- [Architecture and Reference Framework (ARF)](https://eu-digital-identity-wallet.github.io/eudi-doc-architecture-and-reference-framework/latest/architecture-and-reference-framework-main/): An informal document that describes the architecture of the EUDI Wallet ecosystem and all of its components, as well as how these components will interact to ensure the security of the ecosystem and data protection of its Users. It also specifies the high-level requirements established in Annex 2 related to the EUDI Wallet ecosystem. While ARF is not a legal document, the Commission uses the ARF specifications for its reference implementation.

## Main Design Options

The main design options of the mDL target solution backed by the Legal and Compliance Framework are summarised as follows:

- Wallet Reference Implementation accepts attestations only via the Attestation Issuance Interface (AII), which complies with the [OpenID4VCI] standard ([ARF] “4.3.3 Wallet Unit interfaces and protocols”). The latest OpenID4VCI is v1.0.
- mDL can only be issued to EUDI Wallet ([4th Driving License Directive] Article 5.2 and Annex I, Part C (2))
- mDL shall comply with the ISO/IEC 18013-5 standard ([4th Driving License Directive] Annex I, Part C (2), [ARF] ANNEX 3.02 - mDL Rulebook ch2.1)
- mDL can only be presented using the Presentation Interface (PI), which accommodates both remote and proximity interactions ([ARF] “4.3.3 Wallet Unit interfaces and protocols” ).

### Remote Presentation Flows

For remote presentation flows for ISO/IEC 18013-5-compliant attestations the Wallet Instance and the Remote verifier web application implement the OpenID for Verifiable Presentation protocol [OpenID4VP] in combination with the [ISO/IEC 18013-7] profile ([ARF] “5.6.2 Secure data exchange using ISO/IEC 18013-5 and ISO/IEC 18013-7 ”). This flow has the following distinct variations/mechanisms supported by different standards and specifications:

- For the remote presentation flow that does not use the user agent (Digital Credentials API) mechanism, the Wallet Instance and the Remote verifier web application shall comply with Annex B (Use of OID4VP to retrieve an mdoc) of ISO/IEC 18013-7.
- For the remote presentation flow that uses the data retrieval mechanism of the user agent (Digital Credentials API), the Wallet Instance and the Remote verifier web application
    - Shall comply with the Annex C (Digital credentials API retrieval) of ISO/IEC 18013-7.
    - Implement OpenID4VP in combination with Digital Credentials API (Appendix A. OpenID4VP over the Digital Credentials API)

### Proximity Presentation Flows 
For the proximity presentation flow, the Wallet Instance and the proximity verifier mobile application (mDL Reader) implement the [ISO/IEC 18013-5] standard.

##  Digital Credentials API Optionality
It should be noted that ARF in section 5.6.2 states explicitly that __“Within the EUDI Wallet ecosystem, the second option above will be used for requesting and presenting ISO/IEC 18013-5-compliant attestations in remote transaction flows”__. This second option referenced in ARF is: __“Using [OpenID4VP], …. [ISO/IEC 18013-7] specifies a profile for this standard,”__ and it refers to “Annex B Use of OID4VP to retrieve an mdoc” of ISO 18013-7. ARF also in section 4.4.3.1 states that __“The use of this [Digital Credentials] API by Wallet Units and Relying Parties is optional “__. Therefore, the remote presentation flows using the Digital Credentials API is considered as optional for the target solution.

## Transaction Flows Summary
The table below provides the summary of the issuance and presentation transaction flows as specified in ARF that apply explicitly to the target mDL Use Case solution:

| Operation    | 	Flow     | 	Credential Format Profiles | 	Protocol                                                                                                               | 	Optionality |
|--------------|-----------|-----------------------------|-------------------------------------------------------------------------------------------------------------------------|--------------|
| Issuance     | Remote    | ISO/IEC 18013-5 (CBOR)      | OpenID4VCI, v1.0                                                                                                        | Mandatory    |
| Presentation | Remote    | ISO/IEC 18013-5 (CBOR)      | OpenID4VP v1.0 instead of OpenID4VP Draft 18 as defined in ISO/IEC 18013-7 (Annex B: Use of OID4VP to retrieve an mdoc) | Mandatory    |
| Presentation | Remote    | ISO/IEC 18013-5 (CBOR)      | ISO/IEC 18013-7 (Annex C: Digital credentials API retrieval)                                                            | Optional     |
| Presentation | Remote    | ISO/IEC 18013-5 (CBOR)      | OID4VP in combination with Digital Credentials API (OID4VP Appendix A. OpenID4VP over the Digital Credentials API)      | Optional     |
| Presentation | Proximity | ISO/IEC 18013-5 (CBOR)      | ISO/IEC 18013-5 (device retrieval)                                                                                      | Mandatory    |

## Areas for further clarification and specification 
🔎 Although the designated sources provide the vast majority of the mDL specifications, some areas still need further clarification and detailed specification to allow the development of the mDL components for these areas. These areas are summarized as follows:

- 📨 **mDL Issuance**

The first significant area requiring clarification concerns the issuance process for mDLs. This aspect is unspecified in Commission Implementing Regulation 2024/2982 and in ISO 18013-5 and ISO 18013-7 standards. ARF in section 4.3.3 specifies the use of OpenID4VCI with no specific requirements for mdoc credentials (mDL). There is a clear gap for a dedicated profile on OpenID4VCI that specifically describes how to apply it to mDL issuance, which is crucial for the consistent and secure development of mDL components.

- 📲 **Remote presentation of mDLs over HTTP**

ISO 18013-7 (mandatory for EUDI Wallets according to CIR 2024/2982) Appendix B references OpenID4VP (specifically Draft 18) while ARF refers to version 1 which introduces discrepancies. However, the additional OpenID4VP features – such as transaction_data or the combined presentation of multiple, different credential types – are not applicable to mDLs. 

- ➡️ **Remote Presentation of mDL over Digital Credentials API**

Contradictory specifications exist for remote presentation of mDLs over the optional Digital Credentials API. While ISO 18013-7 Appendix C explicitly does not use OpenID4VP, ARF in section 4.4.3.4 specifies OpenID4VP for this purpose.

Furthermore, ARF in the same section also references ISO/IEC 18013-7 Annex B, stating that it "contains a profile for OpenID4VP to be [used, implying compliance] by Relying Parties and Wallet Units when the format of the attestation complies with ISO/IEC 18013-5." This creates a direct conflict, as Annex B is typically associated with HTTP presentation, not DC API.

As ARF also states, the OpenID Foundation has not yet standardized a profile for the W3C Digital Credentials API that would define how OpenID4VP is to be used over this specific API.
