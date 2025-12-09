# Run with Remote Services

The app is configured to the type (debug/release) and variant (dev/demo) in the four xcconfig files. These are the contents of the xcconfig file. You don't need to change anything if you don't want to:

```
BUILD_TYPE = RELEASE
BUILD_VARIANT = DEMO
```

The values defined in the `.xcconfig` files are utilised within instances of `WalletKitConfig` and `RQESConfig` to assign the appropriate configurations. These configurations are selected based on the specified build type and build variant defined in the `.xcconfig` files.

Instances of `ConfigLogic` are responsible for interpreting the raw string values extracted from the `.xcconfig` files and converting them into appropriate data types.

```swift
/**
 * Build type.
 */
var appBuildType: AppBuildType { get }

/**
 * Build variant.
 */
var appBuildVariant: AppBuildVariant { get }
```

Using this parsed information, instances such as `WalletKitConfig` and `RQESConfig` can determine and assign their specific configurations based on the defined build type and variant.

For instance, here's how `WalletKitConfig` resolves its configuration for OpenID4VCI remote services based on the build variant:

```swift
var vciConfig: [String: OpenId4VciConfiguration] {
  let openId4VciConfigurations: [OpenId4VciConfiguration] = {
    switch configLogic.appBuildVariant {
    case .DEMO:
      return [
        .init(
          credentialIssuerURL: "https://ec.issuer.eudiw.dev",
          client: .public(id: "wallet-dev"),
          authFlowRedirectionURI: URL(string: "eu.europa.ec.euidi://authorization")!,
          usePAR: true,
          useDpopIfSupported: true,
          cacheIssuerMetadata: true
        )
    case .DEV:
      return [
        .init(
          credentialIssuerURL: "https://ec.dev.issuer.eudiw.dev",
          client: .public(id: "wallet-dev"),
          authFlowRedirectionURI: URL(string: "eu.europa.ec.euidi://authorization")!,
          usePAR: true,
          useDpopIfSupported: true,
          cacheIssuerMetadata: true
        )
      ]
    }
  }()

  // ...
}
```

In this example, the `vciConfig` property dynamically assigns configurations, such as `issuerUrl`, `clientId`, `redirectUri`, `usePAR`, `useDPoP`, and `metadataCache`, based on the current `appBuildVariant`. This ensures that the appropriate settings are applied for each variant (e.g., `.DEMO` or `.DEV`).

