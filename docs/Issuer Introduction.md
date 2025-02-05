# EUDIW Issuer

## Overview

The EUDIW Issuer is an implementation of  the PID and (Q)EAA Provider service, supporting the OpenId4VCI (draft 13) protocol.

The service provides, by default, support for `mso_mdoc` and `SD-JWT-VC`formats, for the following credentials:


| Credential/Attestation | Format    |
|------------------------|-----------|
| PID                    | mso_mdoc  |
| PID                    | SD-JWT-VC |
| mDL                    | mso_mdoc  | 
| mDL                    | SD-JWT-VC  | 
| (Q)EAA age-over-18 pseudonym | mso_mdoc |
| (Q)EAA loyalty card | mso_mdoc |

For authenticating the user, it requires the use of eIDAS node, OAUTH2 server or a simple form (for testing purposes).


## OpenId4VCI coverage

This version of the EUDIW Issuer supports the [OpenId for Verifiable Credential Issuance (draft 13)](https://openid.net/specs/openid-4-verifiable-credential-issuance-1_0.html){:target="_blank"} protocol with the following coverage:


| Feature                                                   | Coverage                                                        |
|-------------------------------------------------------------------|-----------------------------------------------------------------|
| [Authorization Code flow](api_docs/authorization.md)              | ✅ Support for PAR, PKCE, credential configuration id, scope    |
| [Pre-authorized code flow](api_docs/pre-authorized.md)            | ✅                                                              |
| Dynamic Credential Request                                        | ✅                                                              |
| mso_mdoc format                                                   | ✅                                                              |
| SD-JWT-VC format                                                  | ✅                                                              |
| W3C VC DM                                                         | ❌                                                              |
| [Token Endpoint](api_docs/token.md)                               | ✅                                                              |
| [Credential Offer](api_docs/credential_offer.md)                  | ✅ `authorization_code` , ✅ `pre-authorized_code`              |
| [Credential Endpoint](api_docs/credential.md)                     | ✅ Including proofs and repeatable invocations                  |
| Credential Issuer MetaData                                        | ✅                                                              | 
| [Batch Endpoint](api_docs/batch_credential.md)                     | ✅                                                              | 
| [Deferred Endpoint](api_docs/deferred.md)                         | ✅                                                              |
| Proof                                                             | ✅ JWT, ✅ CWT                                                  |
| [Notification Endpoint](api_docs/notification.md)                 | ✅                                                              |


You can use the EUDIW Issuer at https://issuer.eudiw.dev/, or install it locally.


## Disclaimer

The released software is a initial development release version:

-   The initial development release is an early endeavor reflecting the efforts of a short timeboxed
    period, and by no means can be considered as the final product.
-   The initial development release may be changed substantially over time, might introduce new
    features but also may change or remove existing ones, potentially breaking compatibility with your
    existing code.
-   The initial development release is limited in functional scope.
-   The initial development release may contain errors or design flaws and other problems that could
    cause system or other failures and data loss.
-   The initial development release has reduced security, privacy, availability, and reliability
    standards relative to future releases. This could make the software slower, less reliable, or more
    vulnerable to attacks than mature software.
-   The initial development release is not yet comprehensively documented.
-   Users of the software must perform sufficient engineering and additional testing in order to
    properly evaluate their application and determine whether any of the open-sourced components is
    suitable for use in that application.
-   We strongly recommend not putting this version of the software into production use.
-   Only the latest version of the software will be supported
