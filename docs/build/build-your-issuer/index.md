# Build your Issuer

## Overview

The Issuer is an implementation of  the PID and (Q)EAA Provider service, supporting the OpenID4VCI (draft 15) protocol.

The service provides, by default, support for `mso_mdoc` and `SD-JWT-VC`formats, for the following credentials:


| Credential/Attestation | Format    |
|---|---|
| PID                    | mso_mdoc  |
| PID(sample)            | SD-JWT-VC |
| mDL                    | mso_mdoc  | 
| mDL                    | SD-JWT-VC  | 

For authenticating the user, it requires the use of an eIDAS node, an OAUTH2 server or a simple form (for testing purposes).


## OpenId4VCI Coverage

This version of the Issuer supports the [OpenId for Verifiable Credential Issuance (draft 15)](https://openid.net/specs/openid-4-verifiable-credential-issuance-1_0-15.html){:target="_blank"} protocol with the following coverage:


| Feature                                                   | Coverage                                                        |
|---|---|
| [Authorization Code flow draft](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/tree/main/api_docs/authorization.md)              | ✅ Support for credential configuration id, scope, (draft 15)               |
| [Pre-authorized code flow](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/tree/main/api_docs/pre-authorized.md)            | ✅ (draft 15)                                                       |
| [Credential Offer](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/tree/main/api_docs/credential_offer.md)                  | ✅ `authorization_code` , ✅ `pre-authorized_code`    (draft 15)          |
| Dynamic Credential Request                                        | ✅ (draft 15)                                                             |
| mso_mdoc format                                                   | ✅                                                              |
| SD-JWT-VC format                                                  | ✅                                                              |
| W3C VC DM                                                         | ❌                                                              |
| [Token Endpoint](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/tree/main/api_docs/token.md)                               | ✅ (draft 15)                                                             |
| [Credential Endpoint](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/tree/main/api_docs/credential.md)                     | ✅ Including proofs and repeatable invocations, (draft 15)               |
| Credential Issuer MetaData                                        | ✅ Unsigned metadata, (draft 15)                                            | 
| [Nonce endpoint](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/tree/main/api_docs/nonce_endpoint.md)                    | ✅ (draft 15)                                                             | 
| [Deferred Endpoint](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/tree/main/api_docs/deferred.md)                         | ✅ (draft 15)                                                              |
| Proof                                                             | ✅ JWT                                                 |
| Credential response encryption                                    | ✅ (draft 15)                                                             |
| [Notification Endpoint](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/tree/main/api_docs/notification.md)                 | ✅                                                              |
| Pushed authorization request                                      | ✅                                                              |
| Wallet authentication                                             | ✅ public client                                                |
| Demonstrating Proof of Possession (DPoP)                          | ❌                                                              |
| PKCE                                                              | ✅                                                              |


You can use the Issuer at [https://issuer.eudiw.dev/](https://issuer.eudiw.dev/){:target="_blank"}, or [install it locally](./steps-to-build.md).
