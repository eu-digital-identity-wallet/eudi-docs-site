# Build your rQES SDK UI for iOS

## Overview

The **EUDI RQES UI SDK for iOS** provides user interface components and integration logic for enabling **Remote Qualified Electronic Signatures (RQES)** in iOS applications. It is part of the **EUDI Wallet ecosystem**, allowing integrators to embed RQES flows — including document signing and Qualified Trust Service Provider (QTSP) communication — within their own apps.

The entry point is the `EudiRQESUi` actor, which defines methods for configuring, initializing, and using the SDK. Runtime and visual behavior can be customized through the `EudiRQESUiConfig` protocol.

## Requirements

- **iOS 16** or higher

## Installation

### Swift Package Manager

Open `Xcode`, go to `File -> Swift Packages -> Add Package Dependency`, and enter 
```
https://github.com/eu-digital-identity-wallet/eudi-lib-ios-rqes-ui.git
```

You can also add `EudiRQESUi` as a dependency to your `Package.swift`:
```swift
dependencies: [
  .package(url: "https://github.com/eu-digital-identity-wallet/eudi-lib-ios-rqes-ui.git", from: "LATEST_RELEASE")
]
```

```swift
 targets: [
    .target(
      dependencies: [
        .product(
          name: "EudiRQESUi",
          package: "eudi-lib-ios-rqes-ui"
        )
      ]
    )
```

## How to use

### Configuration

Implement the `EudiRQESUiConfig` protocol and supply all the necessary options for the SDK.

```swift
final class RQESConfigImpl: EudiRQESUiConfig {

  var rssps: [QTSPData]

  // Optional. Default is false.
  var printLogs: Bool

  // Optional. Default English translations will be used if not set.
  var translations: [String : [LocalizableKey : String]]

  // Optional. Default theme will be used if not set.
  var theme: ThemeProtocol
}
```

Example:

```swift
final class RQESConfigImpl: EudiRQESUiConfig {

  var rssps: [QTSPData] {
    return .init(
            name: "your_dev_name",
            rsspId: "your_dev_rssp",
            tsaUrl: "your_dev_tsa",
            clientId: "your_dev_clientid",
            clientSecret: "your_dev_secret",
            authFlowRedirectionURI: "your_registered_deeplink",
            hashAlgorithm: .SHA256,
            includeRevocationInfo: false
        )
  }

  var printLogs: Bool {
    true
  }
}
```

### Setup

Register the `authFlowRedirectionURI` in your application's plist to ensure the RQES Service can trigger your application.
It is the application's responsibility to retrieve the `code` query parameter from the deep link and pass it to the SDK to continue the flow.

```xml
<array>
    <dict>
        <key>CFBundleTypeRole</key>
        <string>Editor</string>
        <key>CFBundleURLName</key>
        <string>$(PRODUCT_BUNDLE_IDENTIFIER)</string>
        <key>CFBundleURLSchemes</key>
        <array>
            <string>rqes</string>
        </array>
    </dict>
</array>
```

Alternatively, you can use universal app links with associated domains [Apple Documentation](https://developer.apple.com/documentation/xcode/supporting-associated-domains)

Initialize the SDK by providing your configuration. You must first ensure instance availability before performing any actions

```swift
let eudiRQESUi: EudiRQESUi
do {
  eudiRQESUi = try EudiRQESUi.instance()
} catch {
  eudiRQESUi = await EudiRQESUi.init(config: rqes_config)
}
```

### Initialization

Start the signing process by providing your TopViewController and the URL of the selected file.

```swift
try await EudiRQESUi.instance().initiate(
  on: view_controller,
  fileUrl: file_url
)
```

Resume the signing process once the `authFlowRedirectionURI` triggers your application following the PID presentation process.
Provide your TopViewController and the extracted code from the `authFlowRedirectionURI` deep link.

```swift
try await EudiRQESUi.instance().resume(
  on: view_controller,
  authorizationCode: code
)
```

If you are using SwiftUI, you can retrieve the TopViewController using the bundled SDK's UIApplication extension function.
Please note that if the application is transitioning from the background to the foreground, this function may return nil for the first ~500 milliseconds.

```swift
let controller = await UIApplication.shared.topViewController()
```

---
The source code is available [in the EUDI RQES UI for iOS SDK repository](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-rqes-ui){:target="_blank"}.
