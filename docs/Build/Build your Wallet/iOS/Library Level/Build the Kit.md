# Build the Kit

To use EUDI Wallet Kit, add the following dependency to your Package.swift:
```swift
dependencies: [
    .package(url: "https://github.com/eu-digital-identity-wallet/eudi-lib-ios-wallet-kit.git", .upToNextMajor(from: "0.6.6"))
]
```

Then add the Eudi Wallet package to your target's dependencies:
```swift
dependencies: [
    .product(name: "EudiWalletKit", package: "eudi-lib-ios-wallet-kit"),
]
```
## Reference
 For detailed documentation, please refer to the [DocC documentation](https://eu-digital-identity-wallet.github.io/eudi-lib-ios-wallet-kit/documentation/eudiwalletkit/){:target="_blank"} available in the project's repository.

## Initialization
The [library](https://eu-digital-identity-wallet.github.io/eudi-lib-ios-wallet-kit/documentation/eudiwalletkit/eudiwallet){:target="_blank"} provides a unified API for the two user attestation presentation flows. It is initialized with a document storage manager instance. For SwiftUI apps, the wallet instance can be added as an ``environmentObject`` to be accessible from all views. A KeyChain implementation of document storage is available.

The wallet developer can customize cryptographic key operations by passing `SecureArea` instances to the wallet, otherwise the wallet-kit creates 'SecureEnclave' (default) and 'Software' secure areas. The wallet developer can specify key creation options per doc-type such as curve type, secure area name, and key unlock policy.

```swift
let wallet = try! EudiWallet(serviceName: "my_wallet_app",
   trustedReaderCertificates: [Data(name: "eudi_pid_issuer_ut", ext: "der")!] )
```	
