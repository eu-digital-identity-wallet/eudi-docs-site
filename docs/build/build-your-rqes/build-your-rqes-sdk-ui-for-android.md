# Build your rQES SDK UI for Android

The **EUDI RQES UI SDK** provides user interface components and integration logic for enabling **Remote Qualified Electronic Signatures (RQES)** in Android applications. It is part of the **EUDI Wallet ecosystem**, allowing integrators to embed RQES flows – including document signing and **Qualified Trust Service Provider (QTSP)** communication – within their own applications.

This document focuses on **how to integrate and use** the SDK in your Android project.

---

## Overview

The RQES UI SDK offers ready-to-use UI screens and the underlying logic to handle:

- **Signature initiation** (local or remote)
- **QTSP interactions** (authentication, signing, and timestamping)
- **User authorisation** and **OAuth redirection flows**
- **Document retrieval and validation**

The entry point is the `EudiRQESUi` object, which exposes set-up and flow-control functions.  
Runtime and visual behaviour are configured via the `EudiRQESUiConfig` interface.

## Requirements

- Android 10 (API level 29) or higher

## Installation

Add the SDK dependency to your app’s `build.gradle` file:

```gradle
dependencies {
    implementation("eu.europa.ec.eudi:eudi-lib-android-rqes-ui:<version>")
}
```

Replace `<version>` with the latest published release available on Maven Central.

## Integration Guide

### 1. Implement the SDK Configuration

Create your own implementation of `EudiRQESUiConfig` to provide all required parameters for your
integration.

```kotlin
class RQESConfigImpl(
    private val context: Context
) : EudiRQESUiConfig {

    override val qtsps: List<QtspData>
        get() = listOf(
            QtspData(
                name = "your_name",
                endpoint = "your_endpoint".toUriOrEmpty(),
                tsaUrl = "your_tsaUrl",
                clientId = "your_clientid",
                clientSecret = "your_secret",
                authFlowRedirectionURI = URI.create("your_registered_deeplink"),
                hashAlgorithm = HashAlgorithmOID.SHA_256,
            )
        )

    override val printLogs: Boolean get() = BuildConfig.DEBUG

    override val documentRetrievalConfig: DocumentRetrievalConfig
        get() = DocumentRetrievalConfig.X509Certificates(
            context = context,
            certificates = listOf(R.raw.my_certificate),
            shouldLog = should_log_option
        )
}
```

You can optionally override:

- `translations` – to provide custom localization
- `themeManager` – to adjust the UI appearance
- `printLogs` – to enable or disable SDK logging

### 2. Configure OAuth and Deep Links

#### OAuth Redirect Handling

Register the `authFlowRedirectionURI` in your app manifest.  
This allows the RQES Service to redirect the user back to your app after authentication.

```xml
<intent-filter>
    <action android:name="android.intent.action.VIEW" />

    <category android:name="android.intent.category.DEFAULT" />
    <category android:name="android.intent.category.BROWSABLE" />

    <data
        android:host="oauth"
        android:path="/callback"
        android:scheme="rqes://" />

</intent-filter>
```

Alternatively, you can use Android App Links [Google Documentation](https://developer.android.com/studio/write/app-link-indexing)

You must extract the `code` query parameter from this redirect and pass it to the SDK (see “Resuming
a Flow” below).

#### Document Retrieval (Same Device Scenario)

If your use case supports **same-device document retrieval**, register an additional deep link in
your manifest:

```xml
<intent-filter>
    <action android:name="android.intent.action.VIEW" />

    <category android:name="android.intent.category.DEFAULT" />
    <category android:name="android.intent.category.BROWSABLE" />

    <data
        android:host="your_host"
        android:scheme="your_scheme://" />

</intent-filter>
```

This enables the RQES Service to trigger your app and pass a remote URL to initialise a same-device
retrieval flow.

### 3. Initialise the SDK

Initialise the SDK in your Application class by providing your application context, configuration, and, if you are using Koin for dependency injection, the KoinApplication.

```kotlin
EudiRQESUi.setup(
    application = application_context,
    config = rqes_config,
    koinApplication = koinapplication_if_applicable
)
```

This makes the SDK ready to handle all signing and retrieval operations.

### 4. Start the Signing Process

You can start an RQES signing session in one of two ways.

##### Option A: Sign a Local File

```kotlin
EudiRQESUi.initiate(
    context = activity_context,
    documentUri = DocumentUri(file_uri)
)
```

##### Option B: Retrieve and Sign a Remote Document

```kotlin
EudiRQESUi.initiate(
    context = activity_context,
    remoteUri = RemoteUri(remote_uri)
)
```

### 5. Resume a Flow After OAuth Redirect

When the OAuth redirect deep link triggers your app, retrieve the `code` query parameter and resume
the RQES process:

```kotlin
EudiRQESUi.resume(
    context = activity_context,
    authorizationCode = code
)
```
This continues the signing flow and completes the RQES transaction with the QTSP.

---
The source code is available [in the EUDI RQES UI for Android SDK repository](https://github.com/eu-digital-identity-wallet/eudi-lib-android-rqes-ui){:target="_blank"}.
