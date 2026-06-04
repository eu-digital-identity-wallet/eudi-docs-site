# Proximity Verifier

The EUDI Verifier App is a cross-platform (iOS and Android) reference implementation for ISO 18013-5 proximity-based credential verification. Built with Kotlin Multiplatform (KMP/CMP), the app provides a unified codebase for business logic, leveraging platform-native libraries to ensure compliance with the latest standards and security requirements.

The EUDI Verifier App enables organizations and relying parties to:

1. Read and verify ISO 18013-5 compliant mobile credentials (mDL, PID, etc.) over proximity channels (NFC/BLE).
2. Support secure, privacy-preserving credential presentation flows, both for in-person and potentially remote scenarios.
3. Demonstrate modular, reusable architecture by utilizing platform-specific low-level libraries, orchestrated by a shared multiplatform business logic layer.
4. Provide an accessible, extensible codebase for pilots, research, and real-world integration projects targeting digital identity verification.

This repository contains the source code for the multi-platform app, while credential-handling libraries are used as external dependencies.

## Purpose

The Proximity Verifier app is provided to help developers test and validate their wallet implementations.

## Minimum device requirements

- API level 29 (Android 10) or higher.
- iOS 18.6 or higher

## Install the Verifier

The application (APK file) is available for download through [GitHub releases](https://github.com/eu-digital-identity-wallet/eudi-app-multiplatform-verifier-ui/releases){:target="_blank"}.


## Important Note
The Proximity Verifier app is a testing tool for developers to validate their wallet implementations. 
It is not intended for production use. 
Currently, the project supports building both Android and iOS applications. However, only the Android version is fully operational. The iOS version builds the user interface, but no actions are functional, as the ISO 18013-5 library has not yet been implemented. Support for this functionality is planned for a future release.

