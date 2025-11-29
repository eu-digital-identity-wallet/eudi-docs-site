# mDL Issuing Authority
The components required by the mDL Issuing Authority are described below. The mDL Issuing Authority needs to integrate the mDL Issuer into its infrastructure and IT systems, as this component provides the main mDL issuance functionality. The specific components comprising the mDL target solution are as follows.

## Issuer Client and Backend
- The mDL Issuing Authority shall offer a service for driving licence holders to request the issuance of an mDL.
- This service implements the "issuer-initiated" issuance flow, which is optional (as justified below), and consequently, makes this service optional as well.
- The Issuer Client interacts with the mDL Issuer component to request the Credential Offer, which is delivered to the EUDI Wallet via either a QR code (cross device) or URI (same device).

## OAuth2 Authorization Server
- This component protects the mDL Issuer, which acts as a resource server, using Access Tokens as defined in the OAuth 2.0 specification.
- The component shall comply with the OpenID4VCI, where the existing OAuth 2.0 mechanisms are extended as described in section 3.2 of OpenID4VCI.
- OAuth 2.0 Authorization Server is responsible for authenticating and authorising the End User according to policies established in the mDL Issuing Authority.

## mDL Issuer
- This is the core component responsible for issuing mDLs to the EUDI Wallet.
- It implements the Credential Endpoint of the OpenID4VCI specification.
- The Credential Endpoint issues one or more mDLs upon presentation of a valid Access Token representing the End User's approval.
- The component interacts with the Driving Licence Authentic Source to retrieve the details (claims) of the mDL.

## Driving Licence Authentic Source
- This component provides the mDL Issuer with the driving license holder's details (claims).
- Authentic Sources are public or private repositories or systems, recognised or required by law, containing attributes about natural or legal persons (ARF 3.10). For the mDL Use Case, the Driving Licence Authentic Source represents these systems.

## Issuing Authority CA (IACA)
- Issuing Authority CA is the certificate authority operated by or on behalf of an issuing authority (\[ISO/IEC 18013-5] section 3.14).
- The IACA issues the IACA root certificate, IACA link certificate, and mDL document signer certificate.
- It serves as the root of trust, enabling all mDL verifiers to securely validate the integrity and authenticity of mDLs issued by the respective IA.

## Revocation Lists Manager
- The mDL Issuer Organisation uses this component to manage (create and update) the revocation status list or revocation identifier list for mDLs.
- It creates a status list and identifier list. The Manager component supports both revocation list types (status and identifier).
- When an mDL is issued, the mDL Issuer must register it in the status list through this component's API, recording its unique identifier (e.g. serial number, unique hash or index) and position, and initialising its status (e.g. set to `VALID` or `0`).
- When an mDL is revoked, the mDL Issuer invokes this component’s API to either add the unique identifier to the identifier list or set the status to `INVALID` or `1` in the status list.

## Revocation Lists Publisher
- The mDL Issuer Organisation uses this component to generate, sign and publish the revocation status list and/or revocation identifier list by making them available to the public.
