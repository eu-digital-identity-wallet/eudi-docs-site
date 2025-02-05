# Building the Reference apps to interact with issuing and verifying services.

## Overview

This guide aims to assist developers to build the iOS application.

# Setup EUDI iOS Wallet reference application

1. You need [xcode](https://xcodereleases.com/){:target="_blank"} and its associated tools installed on your machine. We recommend the latest non-beta version. 
2. Clone the [iOS repository](https://github.com/eu-digital-identity-wallet/eudi-app-ios-wallet-ui) using the following command:
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

5. The aApp can be executed both on a device or on an emulator:

	1. To run the app on the simulator, select your app schema and press Run.
	2. To run the app on a device, follow similar steps to running it on the simulator. Additionally, you need to supply your own provisioning profile and signing certificate in the Signing & Capabilities tab of your app target.

6. Finally, the App needs to be connected with an Issuer and a Verifier either locally, or remotely.
    1. To run remotely, please follow the instructions [here](../running with Remote Services)
    2. To run locally, please follow the instructions [here](../running with Local Services)

7. (Optional) In case self-signed certificates are required, please follow the instructions [here](../Self-signed Certificates)

For a complete list of all configuration options please refer to [this document](https://github.com/eu-digital-identity-wallet/eudi-app-ios-wallet-ui/blob/main/wiki/configuration.md){:target="_blank"}