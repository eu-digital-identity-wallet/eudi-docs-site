# Building the Reference apps to interact with issuing and verifying services.

## Overview

This guide aims to assist developers to build the EUDI Wallet application on iOS.

## Setup EUDI Wallet application on iOS

1. Download and install Xcode and its associated tools by following the official [setup guide](https://xcodereleases.com){:target="_blank"}. Using the latest stable version is recommended.
2. Clone the [iOS repository](https://github.com/eu-digital-identity-wallet/eudi-app-ios-wallet-ui){:target="_blank"} using the following command:
	```git clone git@github.com:eu-digital-identity-wallet/eudi-app-ios-wallet-ui.git ```
3. Open the project file in Xcode.
4. The application has two schemes: "EUDI Wallet Dev" and "EUDI Wallet Demo" that can be configured in the xcconfig files located under the Config folder in the project.

    The application has two product flavors:
    
        - "Dev", which communicates with the services deployed in an environment based on the latest main branch.
        - "Demo", which communicates with the services deployed in an environment based on the latest main branch.

    and two Build Types:
    
        - "Debug", which has full logging enabled, used when running the app from within Xcode.
        - "Release", which has no logging enabled, used when running the app after it has been distributed via a distribution platform, currently TestFlight.

    which, ultimately, result in the following Build Variants:

        - "devDebug", "devRelease", "demoDebug", "demoRelease"

5. The App can be executed both on a device or on an emulator:

	1. To run the app on the simulator, select your app schema and press Run.
	2. To run the app on a device, follow similar steps to running it on the simulator. Additionally, you need to supply your own provisioning profile and signing certificate in the Signing & Capabilities tab of your app target.

6. Finally, the App needs to be connected with an Issuer and a Verifier either locally, or remotely.
    1. [Follow the instructions](../Running with Remote Services) to run remotely.
    2. [Follow the instructions](../Running with Local Services) to run locally.

7. (Optional) [Follow the instructions](../Self-signed Certificates) if self-signed certificates are required.

For a complete list of all configuration options please refer to [this document](https://github.com/eu-digital-identity-wallet/eudi-app-ios-wallet-ui/blob/main/wiki/configuration.md){:target="_blank"}