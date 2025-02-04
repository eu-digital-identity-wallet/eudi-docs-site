# How to install the application

## Minimum device requirements

- Any device that supports iOS 16.0

## Prerequisites

To complete the flows described below you need to build and run the application with xcode. Alternatively, you can directly download the Android app onto your device.

App center download method (Android app)

In addition to building the app from the source, you can also use the Android app which you can download *[here](https://install.appcenter.ms/orgs/eu-digital-identity-wallet/apps/eudi-reference-android/distribution_groups/eudi%20wallet%20(demo)%20public)*

Run the app from the source (xcode build)

Clone this repo and make sure you have access to the dependencies below:

[iso18013-data-model](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-iso18013-data-model.git){:target="_blank"}

[iso18013-data-transfer](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-iso18013-data-transfer.git){:target="_blank"}

[iso18013-security](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-iso18013-security.git){:target="_blank"}

[wallet-storage.](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-wallet-storage.git){:target="_blank"}

[wallet-kit](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-wallet-kit){:target="_blank"}

[openid4vp-swift](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-siop-openid4vp-swift.git){:target="_blank"}

[presentation-exchange-swift](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-presentation-exchange-swift.git){:target="_blank"}

[openid4vci-swift](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-openid4vci-swift){:target="_blank"}

You will also need to download the Android Verifier app. More information can be found [here](wiki/verifier_proximity.md){:target="_blank"}

## App launch

1. Launch the application
2. You will be presented with a welcome screen where you will be asked to create a PIN for future logins.

## Issuance flow (Scoped)

Proceed to [issue an attestation](../HowTo Issue (Scoped)) beginning within the wallet. 

## Issuance flow (Credential Offer)

Proceed to [issue an attestation](../HowTo Issue (Credential Offer)) beginning from the issuer. 

## Presentation (Online authentication/Same device) flow.

Proceed to [present an attestation](../HowTo Present (Same Device)) using the same device.

## Proximity flow

Proceed to [present an attestation](../HowTo Present (Proximity)) using different devices.
