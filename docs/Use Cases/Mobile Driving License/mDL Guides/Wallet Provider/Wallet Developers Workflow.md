# Technical Deep Dive - Wallet Developers Workflow

According to Article 5.2 of the 4th Driving License Directive, mDL shall be issued to the European Digital Identity Wallets as electronic attestations of attributes. Therefore, mDL can only be issued to an active EUDI Wallet instance, which has to comply with all requirements in the eIDAS 2 Regulation.

All baseline requirements outlined in the ARF are applicable to EUDI Wallets. The mDL use case introduces specific technical requirements (defined in the mDL Rulebook, Annex 3.2 of the ARF) regarding the attribute schema, encoding, and supported protocols.

## Development pre-requisites

The reference implementation's preconditions listed in the relevant section on the implementer's hub do apply to the Wallet Provider.

Nevertheless, this section outlines essential integration dependencies and pre-requisites for Member State organisations or entities mandated or recognized by Member States to successfully launch their EUDI Wallet Provider solution using the EUDI Wallet Reference Implementation for mDL support.

**Platform Requirements**

Your EUDI Wallet implementation must support the following platform specifications:

**Android Implementation**
- Target Operating Systems: Android 8.0+ (API 26+)
- Programming Language: Kotlin
- Development Framework: Native Android

**iOS Implementation**
- Target Operating Systems: iOS 17+
- Programming Language: Swift
- Development Framework: Native iOS

## mDL Core Functionalities

The mDL Use Case target solution for the EUDI Wallet shall support the following core functionalities. 

**mDL Attestation Issuance**

Your EUDI Wallet implementation must support issuance of the mDL according to the OpenID4VCI v1.0 specification based on ARF and ISO/IEC 18013-5 (CBOR) standard for remote flows based on specifications from the 4th Driving License Directive.

**Remote Presentation Flow Implementation**

Your EUDI Wallet must support remote presentation flow with requirements as follows:

**Data retrieval not based on user agent (Digital Credentials API)**
- Shall be according to ISO/IEC 18013-5 (CBOR), OpenID4VP v1.0 specification instead of ISO/IEC 18013-7 (Annex B) where Draft 18 of OpenID4VP is used

**Data retrieval based on user agent (Digital Credentials API) - Optional**
- According to ISO/IEC 18013-5 (CBOR), ISO/IEC 18013-7 (Annex C – Digital credentials API retrieval)
- According to OpenID4VP (Appendix A. OpenID4VP over the Digital Credentials API)

**Proximity Presentation Flow Implementation**

Your EUDI Wallet must support proximity presentation flow of the mDL according to ISO/IEC 18013-5 (CBOR) standard.


## Trust and Security Implementation

Your EUDI Wallet implementation must include the following trust and security mechanisms:

**Trust Relationships**
- Authenticate mDL Issuer using the access certificate (IACA)
- Verify authenticity of mDL attestations
- Download mDL Issuer Access CA Trusted Lists from relevant Trusted List Providers
- Check registration certificates or online services of Registrars

**Security Mechanisms**
- Implement session encryption (mandatory for proximity flows)
- Support mDL issuer data authentication
- Enable mdoc authentication (device binding) to prevent cloning of the mDL
- Implement mdoc Reader authentication for proximity flows (mandatory) and remote flows (optional)

## Wallet Provider Registration

To operate as a trusted Wallet Provider within the EUDI Wallet ecosystem, your organisation must complete the registration and notification process as specified in the ARF.

**Registration Process**

Register your organisation as a Wallet Provider with the national authorities in your Member State, ensuring compliance with all certification requirements for Wallet Solutions (see ARF section 7 - Certification and Risk Management).

**Notification and Publication**

The Member State is responsible for notifying the Wallet Provider to the European Commission, enabling cross-border recognition and interoperability within the EUDI Wallet ecosystem.

## Libraries & SDKs

The EUDI Wallet Reference Implementation provides key reusable components to accelerate deployment. Please refer to the relevant section in the implementers' hub for detailed instructions on how to build and test the Wallet Provider components.
