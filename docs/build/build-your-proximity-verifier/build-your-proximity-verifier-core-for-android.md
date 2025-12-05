# Build your Proximity Verifier Core for Android

The EUDI Verifier Core Library for Android is designed to enable Android applications to act as conformant verifiers of mobile identity documents (mDocs), in alignment with the ISO 18013-5 specification. It provides a streamlined API to orchestrate device engagement, transfer management and document status resolution, making it possible for developers to integrate proximity and remote-based verification workflows within their Android apps.
 
This guide walks you through the essential steps to configure and integrate the library into your development environment.


## Prerequisites

- Android version 8 or higher (API level 26+).

## Permissions

The following permissions must be declared in the `AndroidManifest.md` file and requested at runtime:

```xml
<uses-permission android:name="android.permission.CAMERA" />
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH_CONNECT" />
<uses-permission android:name="android.permission.BLUETOOTH_SCAN" />
<uses-permission android:name="android.permission.BLUETOOTH_ADVERTISE" />
```

## Dependencies

To utilise snapshot versions, include the Sonatype Snapshots repository in the `settings.gradle` file as follows:

```gradle
dependencyResolutionManagement {
  repositories {
    maven {
      url = uri("https://central.sonatype.com/repository/maven-snapshots/")
      mavenContent { snapshotsOnly() }
    }
  }
}
```

Subsequently, add the library dependency to the application module:

```gradle
dependencies {
  implementation("eu.europa.ec.eudi:eudi-lib-android-verifier-core:0.1.0")
}
```

## Set-up

### Library Initialisation

To create an instance of `EudiVerifier`, use the `EudiVerifier.Builder` class or invoke the `EudiVerifier.invoke` method from the companion object. This requires providing an `EudiVerifierConfig` object that specifies the verifier's configuration.

### Document Transfer

Currently, the library supports document transfer via:

- offline transfer between devices over Bluetooth Low Energy (BLE), compliant with ISO 18013-5.
- device engagement through QR code scanning.

To instantiate a `TransferManager`, use the method `EudiVerifier.createTransferManager`.

### Event Handling

The transfer process operates asynchronously, emitting events that reflect the current state of the transfer. These events are encapsulated in the sealed class `TransferEvent`. To receive these events, a `TransferEvent.Listener` must be attached to the `TransferManager`, with appropriate handling implemented.

The available events include:

1. `TransferEvent.DeviceEngagementCompleted`: Signifies successful device engagement.
2. `TransferEvent.Connecting`: Indicates an ongoing connection attempt.
3. `TransferEvent.Connected`: Confirms that a connection has been established; this is when `transferManager.sendRequest(DeviceRequest)` should be called.
4. `TransferEvent.RequestSent`: A request has been dispatched to the holder device.
5. `TransferEvent.ResponseReceived`: A response has been received from the holder device, accessible via `transferEvent.response`.
6. `TransferEvent.Disconnected`: Denotes that the devices have been disconnected.
7. `TransferEvent.Error`: An error has occurred; the associated `Throwable` can be retrieved from `transferEvent.error`.

