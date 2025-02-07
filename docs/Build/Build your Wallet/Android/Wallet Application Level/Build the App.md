# Building the Reference apps to interact with issuing and verifying services.

## Overview
This guide aims to assist developers build the EUDI Wallet application on Android.

## Setup EUDI Wallet application on Android

To build the application using the source code and connect it with the issuer and verifier, please follow the next steps:

1. Download and install Android Studio and its associated tools following the instuctions that can be found [here](https://developer.android.com/studio){:target="_blank"}. We recommend the latest stable version.
2. Clone the [Android repository](https://github.com/eu-digital-identity-wallet/eudi-app-android-wallet-ui){:target="_blank"} using the following command:
	```git clone git@github.com:eu-digital-identity-wallet/eudi-app-android-wallet-ui.git ```
3. Open the project in Android Studio.
4. Configure the Build Variant by navigating to Build -> Select Build Variant and from the tool window you can click on the "Active Build Variant" of the module ":app" and select the one you prefer. It will automatically apply it for the other modules as well.

    The application has two product flavors:
    
        - "Dev", which communicates with the services deployed in an environment based on the latest main branch.
        - "Demo", which communicates with the services deployed in an environment based on the latest main branch.

    and two Build Types:
    
        - "Debug", which has full logging enabled.
        - "Release", which has no logging enabled.

    which, ultimately, result in the following Build Variants:

        - "devDebug", "devRelease", "demoDebug", "demoRelease"

5. The App can be executed both on a device or on an emulator:

    1. To run the App on a device, firstly you must connect your device with the Android Studio, and then go to Run -> Run 'app'.
    2. To run the App on an emulator, simply go to Run -> Run 'app'.

6. Finally, the App needs to be connected with an Issuer and a Verifier either locally, or remotely.
    1. [Follow the instructions](../Running with Remote Services) to run remotely.
    2. [Follow the instructions](../Running with Local Services) to run locally.

7. (Optional) [Follow the instructions](../Self-signed Certificates) if self-signed certificates are required.

[Check the full list of configuration options](https://github.com/eu-digital-identity-wallet/eudi-app-android-wallet-ui/blob/main/wiki/configuration.md){:target="_blank"}