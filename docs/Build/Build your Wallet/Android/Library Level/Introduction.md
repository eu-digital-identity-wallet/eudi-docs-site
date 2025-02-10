# EUDI Wallet Core library for Android

## Overview

This [repository](https://github.com/eu-digital-identity-wallet/eudi-lib-android-wallet-core){:target="_blank"} contains the EUDI Wallet Core library for Android. The library is part
of the EUDI Wallet Reference Implementation project.

This library acts as a coordinator, orchestrating the various components that are
required to implement the EUDI Wallet functionality. Additionally, it provides a simplified API
that can be used by the application to implement the EUDI Wallet functionality.

<figure>
<img src="../../../../../assets/android_core.png"
alt="Android core libraries" />
</figure>

The library provides the following functionality:

- Document management
    - [x] Document Key creation and management with Android Keystore by default
    - [x] Support for custom SecureArea implementations
    - [x] Support for multiple SecureArea implementations
- Document issuance
    - [x] Support for OpenId4VCI Draft 14 document issuance
        - [x] Authorization Code Flow
        - [x] Pre-authorization Code Flow
        - [x] Support for mso_mdoc format
      - [x] Support for sd-jwt-vc format
        - [x] Support for credential offers
        - [x] Support for DPoP JWT in authorization
      - [x] Support for JWT proof types
      - [x] Support for deferred issuance
- Proximity document presentation
    - [x] Support for ISO-18013-5 device retrieval
        - [x] QR device engagement
        - [x] NFC device engagement
        - [x] BLE data transfer
        - [ ] NFC data transfer
        - [ ] Wifi-Aware data transfer
- Remote document presentation
    - [x] OpenId4VP document transfer
        - [x] For pre-registered verifiers
        - [x] Dynamic registration of verifiers

The library is written in Kotlin and is compatible with Java. It is distributed as a Maven package
and can be included in any Android project that uses Android 8 (API level 26) or higher.
