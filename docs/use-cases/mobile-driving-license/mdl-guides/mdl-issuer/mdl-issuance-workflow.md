# Technical Deep Dive – mDL Issuance Workflow
## Development pre-requisites

Τhis section outlines essential integration dependencies and prerequisite procedures for a national authority or organisation (acting as the mDL Issuer) to successfully launch its mDL issuance solution using the EUDI Wallet Reference Implementation.

For the technical team to successfully deploy the mDL Issuer, integration with the following external national infrastructure components is required. 

- **Authentic Source Integration for Claims Acquisition**
 
The mDL Issuing Authority is required to issue mDLs containing accurate claims about the subject. The ability to verify attributes typically relies on establishing an interface with the relevant Authentic Sources (public or private repositories containing person mDL attributes).

Your implementation must ensure the mDL Issuer component is configured to retrieve the authenticated data needed for the mDL claims from your designated Authentic Source. 

- **OAuth 2.0 Authorization Server Set-up (for OpenID4VCI)**

The mDL Issuer supports authenticating the end user via an OAuth2 server. The OAuth2 server handles the initial authentication and consent flows, notably supporting the Authorization Code Flow.

You must integrate your existing national OAuth2 server (or deploy a compliant one) to handle user identification and access controls before the issuance process begins. 


- **Access Certificate provision**

To ensure the Wallet Unit can trust the mDL Issuer, the Issuer must obtain and manage an Access Certificate from a designated Access Certificate Authority (CA). This certificate serves as proof of the Issuer's authenticity and validity, which is presented to the Wallet Unit during the mDL issuance process. 
 
You must establish the procedures for obtaining and integrating this certificate into your operational environment.

- **Becoming a Trust mDL Issuer**

For successful cross-border operation, your national mDL Issuance Authority must be recognised as a trusted entity within the EUDI ecosystem. This status is achieved by registering with a national Registrar (Trusted List Provider). Upon successful registration, the Issuing Authority's trust anchors (public keys) are included in the relevant Trusted List/VICAL(Verified Issuer Certificate Authority List). Wallet Units across the EU use these published trust anchors to validate the authenticity of the mDLs you issue.

 You shall complete the registration and notification process to establish the Issuer's identity and trust anchors within the EUDI framework. This is described in #Becoming trust issuer section below.
 

## Issuance of an mDL

The issuance process reuses the underlying protocols supported by the EUDI Wallet Reference Implementation Issuer, notably OpenID for Verifiable Credential Issuance (OpenID4VCI).

- **Preparation and Configuration** 

Follow the documented steps to configure your Issuer and define the mDL schema and data models. The Issuer supports the necessary format for mDL: mso_mdoc (ISO/IEC 18013-5 compliant).

- **User Authorization Flow** 

Implement the required OpenID4VCI flow, typically the Authorization Code flow (recommended for high assurance, incorporating PKCE/PAR) or the Pre-authorized Code flow. This flow verifies the user's identity via the integrated OAuth2 Server.

- **Credential Data Integration** 

Ensure the system retrieves required claims about the user (e.g. data points such as name, date of birth, driving privileges) from the Authentic Source.

- **Proof of Possession (Binding)** 

The issuance process incorporates proof of possession, cryptographically binding the issued mDL to the user's Wallet Secure Cryptographic Device (WSCD) key. The Issuer verifies that the key pair is genuinely protected by the WSCD.

- **Delivery** 

The authenticated and cryptographically bound mDL is delivered as a Verifiable Credential via the Credential Endpoint. The Issuer handles specialised features like batch issuance or deferred issuance if required.

## Revocation of an mDL

Revocation is an essential component of the trust model. The mDL Issuing Authority is the sole party responsible for executing the revocation of an mDL.

- **Revocation Mechanism Implementation** 

Since mDLs are attestations valid for longer than 24 hours, the Issuer SHALL use either a Status List or a Revocation Identifier List mechanism. You can use the provided Revocation Lists Manager component to manage (create and update) the revocation status list or revocation identifier list.

If you decide to implement the Status List mechanism then when an mDL is issued, the mDL Issuer component must register it in the status list using this component’s API. It shall register its unique identifier (e.g. serial number, unique hash, or index) and position, and initialise it (e.g. set to `VALID` or `0`). 

If you decide to implement either mechanism, then when an mDL is revoked the mDL Issuer shall invoke this component’s API to either add the unique identifier to the identifier list or set the status to 'INVALID' or '1' in the status list.

- **Embedding Revocation Information** 

Ensure that the issued mDL includes revocation information (a URL pointing to the status/revocation list and an identifier/index for that specific attestation).

- **The mDL Issuer SHALL revoke an mDL when:**

  - the security of the mDL or the mDL Issuing Authority infrastructure has been compromised;
  - the value of one or more attributes in the mDL changes (triggering re-issuance and revocation of the old mDL);
  - upon explicit request from the mDL subject (recommended action).
 
- **Revocation Publication**

You can use the provided Revocation Lists Publisher to publish and make available the chosen revocation mechanism which is either the Status List or the Revocation Identifier List so that Relying Parties and Wallets can verify the mDL's validity prior to presentation.

## Becoming trust issuer

The process of establishing trust is formalised through registration and transparency in the ecosystem.

- **Registration** 

The nationally appointed mDL Provider shall be added to the national Registrar (Trusted List Provider). This step may include specifying the types of attestations (e.g. mDL) that the provider intends to issue.

- **Access Certificate Acquisition** 

Obtain the necessary Access Certificate from the designated Access Certificate Authority (CA). This certificate is used to authenticate the mDL Issuer's actions to the Wallet.

- **Notification and Publication** 

The Member State is responsible for notifying the mDL Provider and its trust anchors to the European Commission. These trust anchors are subsequently included in a Trusted List or/and Verified Issuer Certificate Authority List (VICAL).

- **Relying Party Verification** 

The inclusion of your trust anchors in the Trusted List/VICAL enables Relying Parties to perform signature validation on the mDLs you issue, confirming their authenticity. Wallet Units also rely on the Access Certificate Authority Trusted List to authenticate you during the issuance request.
 
## Libraries & SDKs

The EUDI Wallet Reference Implementation provides key reusable components to accelerate deployment. Please refer to the relevant section for detailed instructions on how to [build](https://eu-digital-identity-wallet.github.io/Build/Build%20your%20Issuer/) and [test](https://eu-digital-identity-wallet.github.io/Test/Issuer/) the mDL Issuer and Revocation List Manager and Publisher.
