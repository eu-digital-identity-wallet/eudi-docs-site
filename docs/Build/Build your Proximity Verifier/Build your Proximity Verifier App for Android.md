# Build your Proximity Verifier App for Android

The EUDI Verifier App is a cross-platform reference implementation for ISO 18013-5 proximity-based credential verification. 
Built with Kotlin Multiplatform (KMP/CMP), the app provides a unified codebase for business logic, 
leveraging platform-native libraries to ensure compliance with the latest standards and security requirements.

This guide explains how to set up, build, and run the project on Android.

### Platform and Feature Support

You can use emulators or simulators for UI and navigation testing, but completing a **full verification flow** requires a **physical device**.

| Platform   | BLE       | NFC             | Status                                  |
|------------|-----------|-----------------|-----------------------------------------|
| Android    | Supported | Not implemented | Fully operational with BLE verification |

*Features that are not yet implemented are planned for future releases.*

## Project Setup

To get started:

1. Clone the repository:
```
git clone https://github.com/eu-digital-identity-wallet/eudi-app-multiplatform-verifier-ui.git
```
2. Open the project in **Android Studio**.
3. Allow Gradle to sync and download all required dependencies.  
   The first sync may take a few minutes.

## Building the App

### Requirements
- **JDK 17 or newer**
- **Android SDK 36** installed
- Device or emulator running **Android 10 (API 29)** or higher  
  *(verification flow requires a physical device)*

### Build & Run

1. Open the project in **Android Studio** and wait for Gradle sync to complete.
2. In **Build Variants** (`Build → Select Build Variant`), choose one of:
    - **DevDebug (default)**
    - DevRelease
    - PublicDebug
    - PublicRelease  
      *(All variants are currently functionally equivalent. Use **DevDebug** unless you have a specific reason to choose another.)*
3. Select a deployment target:
    - **Emulator** for UI-only checks, or
    - **Physical device** (Android 10 or higher) to test the complete verification flow.
4. Run the app (`Run → Run 'verifierApp'`) to build, install, and launch it.

## Notes

- The shared Kotlin code and UI (Compose Multiplatform) are located under `verifierApp/commonMain`.
- You can test the UI and navigation flows on emulators.  
  For actual proximity verification, use **physical hardware**.

For a complete list of the configuration options, [see the main project README](https://github.com/eu-digital-identity-wallet/eudi-app-multiplatform-verifier-ui/blob/main/README.md){:target="_blank"}.
