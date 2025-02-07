# Build the Core

## Requirements

- Android 8 (API level 26) or higher

### Dependencies

To use snapshot versions add the following to your project's settings.gradle file:

```groovy

dependencyResolutionManagement {
    repositories {
        // ...
        maven {
            url = uri("https://s01.oss.sonatype.org/content/repositories/snapshots/")
            mavenContent { snapshotsOnly() }
        }
        // ...
    }
}
```

To include the library in your project, add the following dependencies to your app's build.gradle
file.

```groovy
dependencies {
    implementation "eu.europa.ec.eudi:eudi-lib-android-wallet-core:0.14.0"
    // required when using the built-in AndroidKeystoreSecureArea implementation provided by the library
    // for user authentication with biometrics
    implementation "androidx.biometric:biometric-ktx:1.2.0-alpha05"
}
```

## How to Use

### Initialize the library

To instantiate a `EudiWallet` use the `EudiWallet.Builder` class or the `EudiWallet.invoke` method,
from the EudiWallet companion object.

The minimum requirements to initialize the library is to provide a `EudiWalletConfit` object that
will be used to configure the library's built-in components.

The built-in components are:

- `AndroidKeystoreSecureArea` for storing and managing the documents' keys
- `AndroidStorageEngine` for storing the documents' data
- `ReaderTrustStore` implementation for validating the reader's certificates
- `PresentationManager` implementation for managing both proximity and remote presentation of
  documents
- `Logger` implementation for logging

The following example demonstrates how to initialize the library for using the built-in components:

```kotlin
// configuring the wallet
val config = EudiWalletConfig()
    // configure the document storage
    // the noBackupFilesDir is used to store the documents by default
    .configureDocumentManager(context.noBackupFilesDir)
    // configure the built-in logger
    .configureLogging(
        // set log level to info
        level = Logger.LEVEL_INFO
    )
    // configure the built-in key creation settings
    .configureDocumentKeyCreation(
        // set userAuthenticationRequired to true to require user authentication
        userAuthenticationRequired = true,
        // set userAuthenticationTimeout to 30 seconds
        userAuthenticationTimeout = 30_000L,
        // set useStrongBoxForKeys to true to use the the device's StrongBox if available
        // to store the keys
        useStrongBoxForKeys = true
    )
    .configureReaderTrustStore(
        // set the reader trusted certificates for the reader trust store
        listOf(readerCertificate)
    )
    // mandatory configuration for OpenId4Vci if you want to issue documents
    .configureOpenId4Vci {
        withIssuerUrl("https://issuer.com")
        withClientId("client-id")
        withAuthFlowRedirectionURI("eudi-openid4ci://authorize")
    }
    // configuration for proximity presentation
    // the values below are the default values
    .configureProximityPresentation(
        // ble mode: peripheral and/or central
        enableBlePeripheralMode = true,
        enableBleCentralMode = false,
        clearBleCache = true,
        // registered application service for handling NFC device engagement
        nfcEngagementServiceClass = MyNfcEngagementService::class.java
    )
    // mandatory configuration for OpenId4Vp if you want to enable
    // remote presentation of documents with OpenId4Vp
    .configureOpenId4Vp {
        withEncryptionAlgorithms(
            EncryptionAlgorithm.ECDH_ES
        )
        withEncryptionMethods(
            EncryptionMethod.A128CBC_HS256,
            EncryptionMethod.A256GCM
        )
        withClientIdSchemes(
            ClientIdScheme.X509SanDns
        )
        withSchemes(
            "openid4vp",
            "eudi-openid4vp",
            "mdoc-openid4vp"
        )
        withFormats(
            Format.MsoMdoc, 
            Format.SdJwtVc.ES256
        )
    }

val wallet = EudiWallet(context, config)
```

`EuidWallet.Builder` allows to configure the library with custom implementations of the built-in
components.

The following example demonstrates how to initialize the library with custom implementations for
StorageEngine, SecureArea, ReaderTrustStore, and Logger:

```kotlin
val wallet = EudiWallet(context, config) {
    // custom StorageEngine to store documents' data
    withStorageEngine(myStorageEngine)
    // a list of SecureArea implementations to be used
    withSecureAreas(listOf(deviceSecureArea, cloudSecureArea))
    // ReaderTrustStore to be used for reader authentication
    withReaderTrustStore(myReaderTrustStore)
    // custom logger to be used
    withLogger(myLogger)
}
```

See the [CustomizeSecureArea.md](https://github.com/eu-digital-identity-wallet/eudi-lib-android-wallet-core/blob/main/CustomizeSecureArea.md){:target="_blank"} for more information on how to use the
wallet-core library with custom SecureArea implementations.