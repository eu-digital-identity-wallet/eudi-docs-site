# Building the Reference apps to interact with issuing and verifying services.

## Overview

This guide aims to assist developers to build the iOS application.

# Setup EUDI iOS Wallet reference application

You need [xcode](https://xcodereleases.com/) and its associated tools installed on your machine. We recommend the latest non-beta version. 

Clone the [iOS repository](https://github.com/eu-digital-identity-wallet/eudi-app-ios-wallet-ui)

Open the project file in Xcode. The application has two schemes: "EUDI Wallet Dev" and "EUDI Wallet Demo".

- EUDI Wallet Dev: This target communicates with the services deployed in an environment based on the latest main branch.
- EUDI Wallet Demo: This target communicates with the services deployed in the latest stable environment.


Each scheme has two configurations: Debug and Release.

- Debug: Used when running the app from within Xcode.
- Release: Used when running the app after it has been distributed via a distribution platform, currently TestFlight.

This setup results in a total of four configurations. All four configurations are defined in the xcconfig files located under the Config folder in the project.

To run the app on the simulator, select your app schema and press Run.

To run the app on a device, follow similar steps to running it on the simulator. Additionally, you need to supply your own provisioning profile and signing certificate in the Signing & Capabilities tab of your app target.

6. Finally, the App needs to be connected with an Issuer and a Verifier either locally, or remotely.
    1. To run remotely, please follow the instructions [here](../running with Remote Services)
    2. To run locally, please follow the instructions [here](../running with Local Services)

7. (Optional) In case serlf-signed certificates are required, please follow the instructions [here](../Self-signed Certificates)

For a complete list of all configuration options please refer to [this document](https://github.com/eu-digital-identity-wallet/eudi-app-ios-wallet-ui/blob/main/wiki/configuration.md){:target="_blank"}