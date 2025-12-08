# Build the App

## Overview
This guide assists developers in building the EUDI Wallet application on Android.

## Set up EUDI Wallet application on Android

To build the application using the source code and connect it with the issuer and verifier, follow these steps:

1. Download and install Android Studio and its associated tools by following the official [setup guide](https://developer.android.com/studio){:target="_blank"}. Using the latest stable version is recommended.
2. Clone the [Android repository](https://github.com/eu-digital-identity-wallet/eudi-app-android-wallet-ui){:target="_blank"} using the following command:
	```bash
        git clone git@github.com:eu-digital-identity-wallet/eudi-app-android-wallet-ui.git 
    ```
3. Open the project in Android Studio.
4. Configure the Build Variant by navigating to Build -> Select Build Variant and from the tool window you can click on the "Active Build Variant" of the module ":app" and select the one you prefer. It will automatically apply to the other modules as well.

     The application has two product flavors:
    
     - "Dev", which communicates with the services deployed in an environment based on the latest main branch.
     - "Demo", which communicates with the services deployed in an environment based on the latest main branch.

     and two Build Types:
    
     - "Debug", which has full logging enabled.
     - "Release", which has no logging enabled.

     which, ultimately, result in the following Build Variants:

     - "devDebug", "devRelease", "demoDebug", "demoRelease"

5. The App can be executed both on a device or on an emulator:

    1. To run the App on a device, firstly you must connect your device to Android Studio, and then go to Run -> Run 'app'.
    2. To run the App on an emulator, simply go to Run -> Run 'app'.

6. Finally, the App needs to be connected to an Issuer and a Verifier either locally or remotely.
    1. [Follow the instructions](./running-with-remote-services.md) to run remotely.
    2. [Follow the instructions](./running-with-local-services.md) to run locally.

7. (Optional) [Follow the instructions](./self-signed-certificates.md) if self-signed certificates are required.

[Check the full list of configuration options](https://github.com/eu-digital-identity-wallet/eudi-app-android-wallet-ui/blob/main/wiki/configuration.md){:target="_blank"}.
