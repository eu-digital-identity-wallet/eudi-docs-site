# Technical Deep Dive - mDL Verifier Workflow
## Development pre-requisites

The reference implementation's preconditions listed in the relevant section on the implementer's hub do apply to the mDL Verifier.
Nevertheless, this section outlines essential integration dependencies and pre-requisites procedures for organisations (acting as mDL Verifiers/Relying Parties) to successfully launch their mDL verification solution using the EUDI Wallet Reference Implementation.

For the technical team to successfully deploy the mDL Verifier, integration with the following external infrastructure components is required:

**Trust Anchor Configuration**

The mDL Verifier must be configured to access and validate trust anchors from relevant Trusted Lists to verify the authenticity of mDL attestations. This includes:

- Integration with ETSI Trusted Lists (via the List of Trusted Lists - LOTL), which contains the trust anchors for all recognised mDL Issuers
- VICAL (Verified Issuer Certificate Authority List) integration for third-country recognition (optional, but recommended)
- Certificate Revocation List (CRL) access for certificate status validation of the Issuing Authority's key

Your implementation must ensure the mDL Verifier component can retrieve and validate these trust relationships during the verification process.

**Relying Party Registration and Access Certificate**

To interact with EUDI Wallet Units, your organisation must register as a Relying Party with the national Registrar. Successful registration ensures your organisation's status is reflected in the relevant national/EU Trust Lists. Your organisation then obtains an Access Certificate from the designated Access Certificate Authority. This certificate enables:

- Authentication to Wallet Units during presentation requests (the verifier proves its identity).
- Verification of your organisation's legitimacy by the Wallet Unit (the wallet checks the verifier's certificate chain against the national/EU Trust Lists).

**Revocation Status Checking Infrastructure**

Your mDL Verifier must be capable of checking the revocation status of presented mDLs by:

- Accessing Status Lists or Revocation Identifier Lists published by mDL Issuers

## Verification of mDL

The verification process supports both proximity and remote presentation flows, implementing the protocols specified in ISO/IEC 18013-5 and OpenID4VP respectively.

**Remote Verification Architecture:**

**(Remote) mDL Verifier Client:**

- runs in the web browser and provides the user interface for initiating and managing the presentation flow. 
- renders and submits the presentation requests to the wallet. 
- interacts with the Digital Credential API of the web browser to manage the presentation requests and responses. 

**(Remote) mDL Verifier Backend:**

- is the server-side component of the mDL Verifier application that directly interacts with the Wallet via the frontend. 
- sends presentation requests, compliant with the OpenID4VP specification, to the Wallet via the browser's Digital Credentials API 
- receives the encrypted presentation response containing the requested attributes from the Wallet (forwarded by the browser) 
- performs the trust relationships checks. 
- integrates with the mDL Verifier Organisation backend systems to inform about the requested mDLs claims and verification checks. 

**mDL Verifier organisation backend systems:** 

- It requests from the mDL Verifier Backend to initiate the mDL remote presentation flow, 
- It receives from the mDL Verifier Backend the requested mDL attributes and validation and verification checks. 

**Data Retrieval Methods:**

- **Non-Digital Credentials API**: Uses ISO/IEC 18013-5 (CBOR) and OpenID4VP v1.0 specification
- **Digital Credentials API based**: Uses ISO/IEC 18013-5 (CBOR) with ISO/IEC 18013-7 Annex C, or OpenID4VP in combination with Digital Credentials API

**Proximity Verification Flow (mDL Reader):**
The mDL Reader is a mobile application that can request, receive, and verify the integrity and authenticity of an mDL for proximity presentation flows. It is controlled by an mDL Verifier, which is a person or organisation. This section focuses explicitly on the mDL Reader.
The mDL reader implements the proximity presentation flow with the EUDI Wallet. ISO/IEC 18013-5 specifies the interfaces between:

- the mDL (wallet) and mDL reader
- the mDL reader and the issuing authority infrastructure.

The interface of the mDL reader and the issuing authority infrastructure (online/server data retrieval) is excluded (not supported) from the mDL target solution since it allows the issuing authority to have knowledge when the mDL holder presents the mDL to a specific mDL verifier. This is prohibited explicitly by articles 5a.16 and 5a.5(b) of [eIDAS] and [ARF] Annex 2 High level requirement “ProxId_02” that states explicitly “Wallet Solutions, PID Providers, Attestation Providers, Wallet Providers, and Relying Parties SHALL NOT support server retrieval as specified in ISO/IEC 18013-5 for requesting and presenting PID or attestation attributes”. Therefore, this method is excluded (not supported) from the mDL target solution.

## Libraries & SDKs

The EUDI Wallet Reference Implementation provides key reusable components to accelerate deployment. Please refer to the relevant section in the implementers' hub for detailed instructions on how to build and test the mDL Verifier components.
