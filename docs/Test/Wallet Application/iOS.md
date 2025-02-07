# How to install the application

## Minimum device requirements

- Any device that supports iOS 16.0

## Prerequisites

1. You need [xcode](https://xcodereleases.com/){:target="_blank"} and its associated tools installed on your machine. We recommend the latest non-beta version. 
2. Clone the [iOS repository](https://github.com/eu-digital-identity-wallet/eudi-app-ios-wallet-ui){:target="_blank"} using the following command:
	```git clone git@github.com:eu-digital-identity-wallet/eudi-app-ios-wallet-ui.git ```
3. Make sure you have access to the dependencies below:

	- [iso18013-data-model](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-iso18013-data-model.git){:target="_blank"}
	- [iso18013-data-transfer](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-iso18013-data-transfer.git){:target="_blank"}
	- [iso18013-security](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-iso18013-security.git){:target="_blank"}
	- [wallet-storage](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-wallet-storage.git){:target="_blank"}
	- [wallet-kit](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-wallet-kit){:target="_blank"}
	- [openid4vp-swift](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-siop-openid4vp-swift.git){:target="_blank"}
	- [presentation-exchange-swift](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-presentation-exchange-swift.git){:target="_blank"}
	- [openid4vci-swift](https://github.com/eu-digital-identity-wallet/eudi-lib-ios-openid4vci-swift){:target="_blank"}

4. To run the app on a device, select your app schema and press Run. Additionally, you need to supply your own provisioning profile and signing certificate in the Signing & Capabilities tab of your app target.

You will also need to download the Android Verifier app. More information can be found [here](../../Verifier Application)

## App launch

1. Launch the application
2. You will be presented with a welcome screen where you will be asked to create a PIN for future logins.

