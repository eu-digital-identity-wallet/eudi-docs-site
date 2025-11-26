# EUDI Wallet Reference Implementation - Repositories

The EUDI Wallet Reference Implementation uses a modular architecture with business-agnostic, reusable components that evolve incrementally and can be reused across multiple projects. This document provides an overview of the key repositories of the EUDI Reference Implementation. 

The EUDI Wallet Reference Implementation includes the following components:

- 📚 [Libraries and other software components needed by the framework](#libraries)
- 🛡️ [Verifier mobile native applications and services for proximity and remote flows](#verifier-apps-and-services)
- 📝 [Issuer applications and services](#issuing-apps-and-services)
- 📱 [EUDI Wallet mobile native applications for issuing, proximity and remote flows](#eudi-wallet-mobile-native-applications)
- ✍️ [Remote electronic signing applications and services](#signing-apps-and-services)


## Libraries

### Wallet Core (Android) and Wallet Kit (iOS) Coordinator Libraries

| Repository | Description | 
|---|---|
| [Wallet Core (Android)](https://github.com/eu-digital-identity-wallet/eudi-lib-android-wallet-core){:target="_blank"} | Implementation of the EUDI Wallet Core library for Android that serves as a coordinator layer between the Wallet UI App and the Wallet libraries. Currently, it coordinates issuing, proximity and remote presentation libraries. |
| [Wallet Kit (iOS)](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-wallet-kit){:target="_blank"} | Implementation of the EUDI Wallet Kit library for iOS that serves as a coordinator layer between the Wallet UI App and the Wallet libraries. Currently it coordinates issuing, proximity and remote presentation libraries. |

### Proximity Sharing iOS Libraries

| Repository | Description | 
|---|---|
| [mDoc Security (iOS)](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-iso18013-security){:target="_blank"} | Implementation of mDoc security mechanisms according to ISO/IEC 18013-5.|
| [mDoc Data Transfer (iOS)](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-iso18013-data-transfer){:target="_blank"} | Implementation of the mDoc data-transfer library according to ISO/IEC 18013-5.| 
| [mDoc Data Model (iOS)](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-iso18013-data-model){:target="_blank"} | Implementation of the mDoc data model according to ISO/IEC 18013-5.| 


### Proximity Sharing Android Libraries

| Repository | Description |
|---|---|
| [mDoc Data Transfer (Android)](https://github.com/eu-digital-identity-wallet/eudi-lib-android-iso18013-data-transfer){:target="_blank"} | This library provides a set of classes to manage the transfer of documents in a EUDI ISO/IEC 18013-5 Android Wallet. |

### Remote Presentation iOS Libraries

| Repository | Description |
|---|---|
| [Presentation Exchange (iOS)](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-presentation-exchange-swift){:target="_blank"} | Implementation of DIF Presentation Exchange v2 specification in Swift. | 
| [SIOPv2 & OpenID4VP protocols (iOS)](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-siop-openid4vp-swift){:target="_blank"} | Implementation of SIOPv2 and OpenID4VP protocols (wallet's role) in Swift. |
| [SD-JWT (iOS)](https://github.com/eu-digital-identity-wallet/eudi-lib-sdjwt-swift){:target="_blank"} | SD-JWT library for creating and verifying SD-JWT in Swift. | 


### Remote Presentation Android Libraries

| Repository | Description |
|---|---|
| [Presentation Exchange (Android)](https://github.com/eu-digital-identity-wallet/eudi-lib-jvm-presentation-exchange-kt){:target="_blank"} | Implementation of DIF Presentation Exchange v2 specification in Kotlin. |
| [SIOPv2 & OpenID4VP protocols (Android)](https://github.com/eu-digital-identity-wallet/eudi-lib-jvm-siop-openid4vp-kt){:target="_blank"} | Implementation of SIOPv2 and OpenID4VP protocols (wallet's role) in Kotlin. | 
| [SD-JWT (Android)](https://github.com/eu-digital-identity-wallet/eudi-lib-jvm-sdjwt-kt){:target="_blank"} | SD-JWT library for creating and verifying SD-JWT in Kotlin. | 

### Issuing iOS Libraries

| Repository | Description | 
|---|---|
| [OpenID4VCI (iOS)](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-openid4vci-swift){:target="_blank"} | Implementation of credential management supporting the OpenID4VCI protocol. | 

### Issuing Android Libraries

| Repository | Description | 
|---|---|
| [OpenID4VCI (Android)](https://github.com/eu-digital-identity-wallet/eudi-lib-jvm-openid4vci-kt){:target="_blank"} | Implementation of credential management supporting the OpenID4VCI protocol.|

### Wallet Data Storage and Cryptographic Management iOS Libraries

| Repository | Description |
|---|---|
| [mDoc Document Storage (iOS)](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-wallet-storage){:target="_blank"} | Storage for keys and wallet documents. |

### Wallet Data Storage and Cryptographic Management Android Libraries

| Repository | Description |
|---|---|
| [mDoc Document Storage (Android)](https://github.com/eu-digital-identity-wallet/eudi-lib-android-wallet-document-manager){:target="_blank"} | This library provides a set of classes to manage documents and their cryptographic keys in a EUDI Android Wallet. |


### Revocation Libraries

| Repository | Description |
|---|---|
| [Token Status List (Kotlin)](https://github.com/eu-digital-identity-wallet/eudi-lib-kmp-statium){:target="_blank"} | Statium is a Kotlin multiplatform library supporting JVM and Android platforms. It implements the Token Status List Specification and allows callers to check the status of a 'Referenced Token' as defined in the specification, effectively enabling applications to verify if tokens are valid, revoked or in other states. |
| [Token Status List (Swift)](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-statium-swift){:target="_blank"} | Statium is a Swift library for iOS and macOS. It implements the Token Status List Specification and allows callers to check the status of a 'Referenced Token' as defined in the specification, effectively enabling applications to verify if tokens are valid, revoked or in other states.|


### rQES: Low Level Libraries

| Repository | Description |
|---|---|
| [EUDI rQES CSC library (Kotlin)](https://github.com/eu-digital-identity-wallet/eudi-lib-jvm-rqes-csc-kt){:target="_blank"} | This is a Kotlin library targeting Android that supports the Cloud Signature Consortium API (version 2) protocol. |
| [EUDI rQES CSC library (Swift)](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-rqes-csc-swift){:target="_blank"} | This is a Swift library targeting iOS that supports the Cloud Signature Consortium API (version 2) protocol. |

### rQES: Core and Kit Libraries

| Repository | Description |
|---|---|
| [EUDI Remote Qualified Electronic Signature (RQES) Core library for Android](https://github.com/eu-digital-identity-wallet/eudi-lib-android-rqes-core){:target="_blank"} | This module provides the core functionality for the EUDI Wallet for Android, focusing on the Remote Qualified Electronic Signature (RQES) service. |
| [EUDI Remote Qualified Electronic Signature (RQES) Core library for iOS](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-rqes-kit){:target="_blank"} | This module provides the core functionality for the EUDI Wallet for iOS, focusing on the Remote Qualified Electronic Signature (RQES) service. |

### rQES: UI Libraries

| Repository | Description |
|---|---|
| [EUDI Remote Qualified Electronic Signature (RQES) UI library for Android](https://github.com/eu-digital-identity-wallet/eudi-lib-android-rqes-ui){:target="_blank"} | This module provides the core and UI functionality for the EUDI Wallet for Android implementation, focusing on the Remote Qualified Electronic Signature (RQES) service.|
| [EUDI Remote Qualified Electronic Signature (RQES) UI library for iOS](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-rqes-ui){:target="_blank"} | This package provides the core and UI functionality for the EUDI Wallet for iOS implementation, focusing on the Remote Qualified Electronic Signature (RQES) service.|


## EUDI Wallet mobile native applications

| Repository | Description |
|---|---|
| [Wallet UI App (Android)](https://github.com/eu-digital-identity-wallet/eudi-app-android-wallet-ui){:target="_blank"} | Implementation of Wallet UI App for Android. Currently, it includes a demo App, demonstrating the following capabilities: Proximity presentation, Same-device Online Presentation and Issuance of PID and mDL.	 |
| [Wallet UI App (iOS)](https://github.com/eu-digital-identity-wallet/eudi-app-ios-wallet-ui){:target="_blank"} | Implementation of Wallet UI App for iOS. Currently, it includes a demo App, demonstrating the following capabilities: Proximity presentation, Same-device Online Presentation and Issuance of PID and mDL.| 


## Verifier Apps and Services

| Repository | Description |
|---|---|
| [Web Verifier](https://github.com/eu-digital-identity-wallet/eudi-web-verifier){:target="_blank"} | Demo Web Verifier UI application (Frontend) that acts as a Verifier/RP trusted endpoint. Available at: [https://verifier.eudiw.dev](https://verifier.eudiw.dev) | 
| [RESTful API (web-services)](https://github.com/eu-digital-identity-wallet/eudi-srv-web-verifier-endpoint-23220-4-kt){:target="_blank"} | Demo Web Verifier application (Backend RESTful service) that acts as a Verifier/RP trusted endpoint.| 


## Issuing Apps and Services

| Repository | Description |
|---|---|
| [OpenID4VCI issuer (Python)](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py){:target="_blank"} | An implementation of a credential issuing service, according to OpenID4VCI, in Python. Available at: https://issuer.eudiw.dev/ | 
| [OpenID4VCI issuer (Kotlin)](https://github.com/eu-digital-identity-wallet/eudi-srv-pid-issuer){:target="_blank"} | An implementation of a credential issuing service, according to OpenID4VCI, in Kotlin. Available at: https://issuer-backend.eudiw.dev/ | 


## Signing Apps and Services

| Repository | Description |
|---|---|
| [TrustProvider Signer](https://github.com/eu-digital-identity-wallet/eudi-srv-web-trustprovider-signer-java){:target="_blank"} | The TrustProvider Signer is a remote signing service provider and client. The TrustProvider Signer can be accessed using the EUDI Wallet through OID4VP presentation of the PID. Available [here](https://trustprovider.signer.eudiw.dev/tester). | 
| [EUDI Wallet-driven signer QTSP](https://github.com/eu-digital-identity-wallet/eudi-srv-web-walletdriven-rpcentric-signer-qtsp-java){:target="_blank"} | Implementation of a wallet-driven QTSP for the remote Qualified Electronic Signature component of the EUDI Wallet. The QTSP provides endpoints based on the CSC API v2.0 specification and supports authentication via OpenID4VP.| 
| [EUDI Wallet-driven external SCA](https://github.com/eu-digital-identity-wallet/eudi-srv-web-walletdriven-signer-external-sca-java){:target="_blank"} | Implementation of a wallet-driven SCA for the remote Qualified Electronic Signature component of the EUDI Wallet. The SCA provides endpoints that allow the calculation of the hash value of a document and obtain the signed document given the signature value.| 
| [RP Centric rQES SCA](https://github.com/eu-digital-identity-wallet/eudi-srv-web-rpcentric-signer-sca-java){:target="_blank"} | This is a REST API server implementing the RP-centric SCA for the remote Qualified Electronic Signature (rQES) component of the EUDI Wallet.| 
