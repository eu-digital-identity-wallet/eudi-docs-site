# Technical Deep Dive – mDL Verifier Workflow

This guide is a technical deep dive into how an organisation, acting as an mDL Verifier (Relying Party), launches an mDL verification solution using the EUDI Wallet Reference Implementation. It covers the development prerequisites and the remote and proximity verification flows.

## Development prerequisites

The reference implementation's preconditions listed in the relevant section on the implementer's hub do apply to the mDL Verifier. Nevertheless, this section outlines the essential integration dependencies and prerequisite procedures for organisations (acting as mDL Verifiers/Relying Parties) to successfully launch their mDL verification solution using the EUDI Wallet Reference Implementation.

For the technical team to successfully deploy the mDL Verifier, integration with the following external infrastructure components is required.

### Trust anchor configuration

The mDL Verifier must be configured to access and validate trust anchors from relevant Trusted Lists to verify the authenticity of mDL attestations. This includes:

- Integration with ETSI Trusted Lists (via the List of Trusted Lists, LOTL), which contains the trust anchors for all recognised mDL Issuers;
- VICAL (Verified Issuer Certificate Authority List) integration for third-country recognition (optional, but recommended);
- Certificate Revocation List (CRL) access for certificate status validation of the Issuing Authority's key.

Your implementation must ensure the mDL Verifier component can retrieve and validate these trust relationships during the verification process.

### Relying Party registration and authorisation

To interact with EUDI Wallet Units, your organisation must register as a Relying Party with the designated national Registrar. This process confirms the RP identity and requires a formal declaration of the "intended use": the specific user attributes you are authorised to request.

- **RP Registration Certificate:** after registering, the RP receives a Registration Certificate (a data object) that specifies the scope of attributes the RP is permitted to request from Wallet Users. The Wallet Unit checks this during presentation to enforce data minimisation.

### Access Certificate and Trust List inclusion

Your organisation needs to obtain an Access Certificate to prove its identity during interactions with the Wallet Unit.

- **Access Certificate (X.509):** this certificate is issued by the designated Access Certificate Authority. It is used to digitally sign presentation requests.

The Trust List inclusion is linked to this mechanism: the public key of the Access Certificate Authority is reflected in the relevant national/EU Trust Lists. This allows every EUDI Wallet Unit across the EU to cryptographically verify that the RP's Access Certificate is legitimate.

### Revocation status checking infrastructure

Your mDL Verifier must be capable of checking the revocation status of presented mDLs by accessing the Status Lists or Revocation Identifier Lists published by mDL Issuers.

## Verification of an mDL

The verification process supports both proximity and remote presentation flows, implementing the protocols specified in ISO/IEC 18013-5 and OpenID4VP respectively.

### Remote verification architecture

#### (Remote) mDL Verifier Client

- Runs in the web browser and provides the user interface for initiating and managing the presentation flow.
- Renders and submits the presentation requests to the Wallet.
- Interacts with the Digital Credentials API of the web browser to manage the presentation requests and responses.

#### (Remote) mDL Verifier Backend

- The server-side component of the mDL Verifier application that directly interacts with the Wallet via the frontend.
- Sends presentation requests, compliant with the OpenID4VP specification, to the Wallet via the browser's Digital Credentials API.
- Receives the encrypted presentation response containing the requested attributes from the Wallet (forwarded by the browser).
- Performs the trust relationship checks.
- Integrates with the mDL Verifier organisation's backend systems to provide information about the requested mDL claims and verification checks.

#### mDL Verifier organisation backend systems

- Requests the mDL Verifier Backend to initiate the mDL remote presentation flow.
- Receives from the mDL Verifier Backend the requested mDL attributes and the validation and verification checks.

### Data retrieval methods

- **Non-Digital Credentials API:** uses ISO/IEC 18013-5 (CBOR) and the OpenID4VP v1.0 specification.
- **Digital Credentials API based:** uses ISO/IEC 18013-5 (CBOR) with ISO/IEC 18013-7 Annex C, or OpenID4VP in combination with the Digital Credentials API.

### Proximity verification flow (mDL Reader)

The mDL Reader is a mobile application that can request, receive, and verify the integrity and authenticity of an mDL for proximity presentation flows. It is controlled by an mDL Verifier, which is a person or an organisation. This section focuses explicitly on the mDL Reader.

The mDL Reader implements the proximity presentation flow with the EUDI Wallet. ISO/IEC 18013-5 specifies the interfaces between:

- the mDL (Wallet) and the mDL Reader;
- the mDL Reader and the issuing authority infrastructure.

The interface between the mDL Reader and the issuing authority infrastructure (online/server data retrieval) is excluded (not supported) from the mDL target solution, since it would allow the issuing authority to know when the mDL holder presents the mDL to a specific mDL Verifier. This is prohibited explicitly by articles 5a.16 and 5a.5(b) of [eIDAS] and by [ARF] Annex 2 high-level requirement "ProxId_02", which states explicitly that "Wallet Solutions, PID Providers, Attestation Providers, Wallet Providers, and Relying Parties SHALL NOT support server retrieval as specified in ISO/IEC 18013-5 for requesting and presenting PID or attestation attributes". Therefore, this method is excluded (not supported) from the mDL target solution.

## Libraries & SDKs

The EUDI Wallet Reference Implementation provides key reusable components to accelerate deployment. Please refer to the relevant section for detailed instructions on how to [build](https://eu-digital-identity-wallet.github.io/Build/Build%20your%20Verifier/) and [test](https://eu-digital-identity-wallet.github.io/Test/Online%20Verifier/) the mDL Verifier.
