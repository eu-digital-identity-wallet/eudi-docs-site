# EUDIW Issuer

## Overview

The EUDIW Issuer is an implementation of  the PID and (Q)EAA Provider service, supporting the OpenId4VCI (draft 13) protocol.

The service provides, by default, support for `mso_mdoc` and `SD-JWT-VC`formats, for the following credentials:


| Credential/Attestation | Format    |
|------------------------|-----------|
| PID                    | mso_mdoc  |
| PID(sample)            | SD-JWT-VC |
| mDL                    | mso_mdoc  | 
| mDL                    | SD-JWT-VC  | 

For authenticating the user, it requires the use of eIDAS node, OAUTH2 server or a simple form (for testing purposes).


## OpenId4VCI coverage

This version of the EUDIW Issuer supports the [OpenId for Verifiable Credential Issuance (draft 13)](https://openid.net/specs/openid-4-verifiable-credential-issuance-1_0.html){:target="_blank"} protocol with the following coverage:


| Feature                                                   | Coverage                                                        |
|-------------------------------------------------------------------|-----------------------------------------------------------------|
| [Authorization Code flow](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/tree/main/api_docs/authorization.md){:target="_blank"}              | ✅ Support for PAR, PKCE, credential configuration id, scope    |
| [Pre-authorized code flow](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/tree/main/api_docs/pre-authorized.md){:target="_blank"}            | ✅                                                              |
| Dynamic Credential Request                                        | ✅                                                              |
| mso_mdoc format                                                   | ✅                                                              |
| SD-JWT-VC format                                                  | ✅                                                              |
| W3C VC DM                                                         | ❌                                                              |
| [Token Endpoint](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/tree/main/api_docs/token.md){:target="_blank"}                               | ✅                                                              |
| [Credential Offer](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/tree/main/api_docs/credential_offer.md){:target="_blank"}                  | ✅ `authorization_code` , ✅ `pre-authorized_code`              |
| [Credential Endpoint](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/tree/main/api_docs/credential.md){:target="_blank"}                     | ✅ Including proofs and repeatable invocations                  |
| Credential Issuer MetaData                                        | ✅                                                              | 
| [Batch Endpoint](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/tree/main/api_docs/batch_credential.md){:target="_blank"}                     | ✅                                                              | 
| [Deferred Endpoint](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/tree/main/api_docs/deferred.md){:target="_blank"}                         | ✅                                                              |
| Proof                                                             | ✅ JWT, ✅ CWT                                                  |
| [Notification Endpoint](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/tree/main/api_docs/notification.md){:target="_blank"}                 | ✅                                                              |


You can use the EUDIW Issuer at [https://issuer.eudiw.dev/](https://issuer.eudiw.dev/){:target="_blank"}, or install it locally.
