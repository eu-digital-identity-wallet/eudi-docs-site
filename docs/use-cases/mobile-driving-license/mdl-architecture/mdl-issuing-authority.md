# mDL Issuing Authority
The components required by the mDL Issuing Authority are described below. The mDL Issuing Authority needs to integrate in its infrastructure and IT systems the mDL Issuer component that offers the main mDL issuance functionality. The specific components that comprise the mDL target solution are the following:

## Issuer Client and Backend
- The mDL Issuing Authority shall offer a service to the driving licence owner to request the issuance of the mDL.
- This service implements the “issuer initiated” issuance flow which is optional (as justified below) and consequently makes this service optional as well.
- The Issuer Client interacts with the mDL Issuer component to request the Credential Offer that will be sent to the EUDI Wallet via either a QR code (cross device) or URI (same device).

## OAuth2 Authorization Server
- This component protects the mDL Issuer which acts as a resource server using Access Tokens as defined in OAuth 2.0 specification.
- The component shall comply with the OpenID4VCI where the existing OAuth 2.0 mechanisms are extended as described in section 3.2 of OpenID4VCI.
- OAuth 2.0 Authorization Server is responsible for authenticating and authorizing the End User according to policies established in the mDL Issuing Authority.

## mDL Issuer
- This is the core component responsible for issuing the mDLs to the EUDI Wallet.
- It implements the Credential Endpoint of the OpenID4VCI specification.
- The Credential Endpoint issues one or more mDLs upon presentation of a valid Access Token representing the approval of the End User.
- The component interacts with the Driving Licence Authentic Source to retrieve the details (claims) of the mDL.

## Driving Licence Authentic Source
- This component provides to the mDL Issuer component the details (claims) of the driving licence of a holder.
- Authentic Sources are public or private repositories or systems, recognised or required by law, containing attributes about natural or legal persons (ARF 3.10). The Driving Licence Authentic Source component represents these repositories or systems for the mDL Use Case.

## Issuing Authority CA (IACA)
- Issuing Authority CA is the certificate authority operated by or on behalf of an issuing authority (\[ISO/IEC 18013-5] section 3.14).
- The IACA issues the IACA root certificate, IACA link certificate, and mDL document signer certificate.
- It serves as the root of trust for all mDL verifiers to securely validate the integrity and authenticity of mDLs issued by the respective Issuing Authority (IA).

## Revocation Lists Manager
- The mDL Issuer Organisation uses this component to manage (create and update) the revocation status list or revocation identifier list of the mDLs.
- It creates a status list and identifier list. The Manager component supports both revocation list types (status and identifier).
- When an mDL is issued, then mDL Issuer component must register it in the status list using this component’s API. It shall register its unique identifier (e.g., a serial number, a unique hash, or an index) and position in the list and then initialize it (e.g. set to “VALID” or “0”).
- When an mDL is revoked then the mDL Issuer shall invoke this component’s API to either add the unique identifier in the identifier list or set the status to “INVALID” or “1” in the status list.

## Revocation Lists Publisher
- The mDL Issuer Organisation uses this component to generate, sign, publish by making available to the public the revocation status list and/or revocation identifier list of the mDLs.
