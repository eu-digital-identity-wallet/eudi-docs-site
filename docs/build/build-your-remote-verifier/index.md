# Build your Remote Verifier

## Overview

This is a Web application (Backend Restful service) that acts as a Verifier/RP trusted end-point that implements [OpenId4VP (1.0)](https://openid.net/specs/openid-4-verifiable-presentations-1_0-final.html){:target="_blank"} protocol. 
This backend service is accompanied by a [Web UI application](https://github.com/eu-digital-identity-wallet/eudi-web-verifier){:target="_blank"}.

Application exposes two APIs:

- [Verifier API](https://github.com/eu-digital-identity-wallet/eudi-srv-web-verifier-endpoint-23220-4-kt/blob/main/src/main/kotlin/eu/europa/ec/eudi/verifier/endpoint/adapter/input/web/VerifierApi.kt){:target="_blank"}.
- [Wallet API](https://github.com/eu-digital-identity-wallet/eudi-srv-web-verifier-endpoint-23220-4-kt/blob/main/src/main/kotlin/eu/europa/ec/eudi/verifier/endpoint/adapter/input/web/WalletApi.kt){:target="_blank"}.

The Verifier API, supports two operations:

- [Initialise Transaction](https://github.com/eu-digital-identity-wallet/eudi-srv-web-verifier-endpoint-23220-4-kt/blob/main/src/main/kotlin/eu/europa/ec/eudi/verifier/endpoint/port/input/InitTransaction.kt){:target="_blank"}, where Verifier may define whether it wants to request a SIOP or OpenID4VP or combined request.
- [Get Wallet response](https://github.com/eu-digital-identity-wallet/eudi-srv-web-verifier-endpoint-23220-4-kt/blob/main/src/main/kotlin/eu/europa/ec/eudi/verifier/endpoint/port/input/GetWalletResponse.kt){:target="_blank"}, where Verifier receives a `vp_token`, or an error.

These operations are specified in an [Open API v3 specification](https://github.com/eu-digital-identity-wallet/eudi-srv-web-verifier-endpoint-23220-4-kt/blob/main/src/main/resources/public/openapi.json){:target="_blank"}.

The Wallet API, provides the following main operations:

- [Get Request Object](https://github.com/eu-digital-identity-wallet/eudi-srv-web-verifier-endpoint-23220-4-kt/blob/main/src/main/kotlin/eu/europa/ec/eudi/verifier/endpoint/port/input/RetrieveRequestObject.kt){:target="_blank"} according JWT Secured Authorization Request.
- [Direct Post](https://github.com/eu-digital-identity-wallet/eudi-srv-web-verifier-endpoint-23220-4-kt/blob/main/src/main/kotlin/eu/europa/ec/eudi/verifier/endpoint/port/input/PostWalletResponse.kt){:target="_blank"} according to OpenID4VP `direct_post`.

Please note that:

- Both APIs need to be exposed over HTTPS.  
- Verifier API needs to be protected to allow only authorized access. 

Both of those concerns have not been tackled by the current version of the application, since in its current version is merely a development tool, rather a production application.
