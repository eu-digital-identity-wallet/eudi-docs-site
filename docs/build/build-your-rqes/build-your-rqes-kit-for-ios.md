# Build your rQES Core for iOS

## Overview

The EUDI rQES Kit for iOS provides the essential functionality needed to enable Remote Qualified Electronic Signatures (rQES) within iOS applications. It offers a unified interface for retrieving authorisation URLs, authorising both the service and user credentials, and performing secure document signing operations. 

## Requirements

- iOS 16 or higher.

## Installation

To integrate RQES Kit using Swift Package Manager, add the following to your Package.swift file.

First, add the package repository to your dependencies:

```swift
dependencies: [
    .package(url: "https://github.com/niscy-eudiw/eudi-lib-ios-rqes-kit", exact: "0.6.4")
]
```

Then add the `RqesKit` product to your app target's dependencies:

```swift
dependencies: [
    .product(name: "RqesKit", package: "eudi-lib-ios-rqes-kit"),
]
```

## Integration guide

### Document signing flow

```mermaid
sequenceDiagram
    participant Client
    participant rQESService
    participant rQESServiceAuthorized
    participant rQESServiceCredentialAuthorized
    Client ->>+ rQESService: getServiceAuthorizationUrl()
    rQESService -->>- Client: URL
    Client ->>+ rQESService: authorizeService(authorizationCode)
    rQESService -->>- Client: RQESServiceAuthorized
    Client ->>+ rQESServiceAuthorized: getCredentialsList(request)
    rQESServiceAuthorized -->>- Client: List<CredentialInfo>
    Client ->>+ rQESServiceAuthorized: getCredentialAuthorizationUrl(credential, documents)
    rQESServiceAuthorized -->>- Client: URL
    Client ->>+ rQESServiceAuthorized: authorizeCredential(authorizationCode)
    rQESServiceAuthorized -->>- Client: RQESServiceCredentialAuthorized
    Client ->>+ rQESServiceCredentialAuthorized: signDocuments(algorithmOID)
    rQESServiceCredentialAuthorized -->>- Client: SignedDocuments
```

### 1. Create an rQES Service instance

```swift
let cscClientConfig = CSCClientConfig(
        OAuth2Client: CSCClientConfig.OAuth2Client(
                clientId: "wallet-client",
                clientSecret: "somesecret2"
        ),
        authFlowRedirectionURI: "https://oauthdebugger.com/debug", rsspId: "")
var rqesService = rQESService(
    clientConfig: cscClientConfig,
    defaultHashAlgorithmOID: .SHA256
)
```

### 2. Authorise the service

To authorise the service, you need to get the authorisation URL and open it in a browser. After the user has authorised the service, the browser will be redirected to the `redirectUri`,
that is configured in the `CSCClientConfig`, with a query parameter named `code` containing the authorisation code. You can then authorise the service by calling the `authorizeService` method:

1. Get the authorisation URL

```swift
let authorizationUrl = try await rqesService.getServiceAuthorizationUrl()
``` 
2. Open the `authorizationUrl` in a browser.
3. After the user has authorised the service, the browser will be redirected to the `redirectUri` with a query parameter named "code" containing the authorisation code

```swift
let authorizedService = try await rqesService.authorizeService(authorizationCode)
```
### 3. Select the credential 

With the authorised service, you can list the available credentials by calling the `getCredentialsList` method and choose the credential you want to use.

```swift
let credentials = try await authorizedService.getCredentialsList()
// Choose the credential you want to use
let credential = credentials.first!
```

### 4. Prepare documents to be signed

Create an array of Document objects pointing to the local files you wish to have signed.

```swift
let unsignedDocuments = [
Document(
label: "Document to sign",
fileURL: Bundle.main.url(
forResource: "document",
withExtension:"pdf")
)
]
```

### 5. Authorise the chosen credential

Next step is to get user consent to use the credential for this specific transaction, which also involves a browser redirect.

1. Get the credential authorisation URL:
```swift
let credentialAuthorizationUrl = try await authorizedService.getCredentialAuthorizationUrl(
    credentialInfo: credential,
    documents: unsignedDocuments,
)
```
2. Use the `credentialAuthorizationUrl` to open a browser and let the user authorise the credential
3. After redirect, read the code parameter and authorise the credential.
```swift
let authorizedCredential = try await authorizedService.authorizeCredential(authorizationCode)
```
### 6. Sign the documents
```swift
let signAlgorithm = SigningAlgorithmOID.ECDSA_SHA256
let signedDocuments = try await authorizedCredential.signDocuments(signAlgorithmOID: signAlgorithm)
```
## Source code
[Build your rQES SDK UI for iOS](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-rqes-kit).

