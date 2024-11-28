# Build a Wallet

EUDI Wallet Providers are Member States or organizations that are mandated or recognized by them to make the EUDI Wallet available to end users. The terms and conditions of the mandate or recognition are for each Member State to determine. The EUDI Wallet Providers are responsible for providing the EUDI Wallet, which gives users full control over their Person Identification Data (PID) and Electronic Attestations of Attributes (QEAA, PuB-EAA or EAA). EUDI Wallet Providers are responsible for ensuring compliance with the requirements for EUDI Wallets.

The reference implementation provides tools, libraries, and test services to support and help you with building your own Wallet. Let’s get started!

## Try the ready-made Wallet application

A reference application for the Wallet is available for both Android and iOS. This allows you to familiarise yourself with the application and test the Wallet functionalities before starting the development of your own Wallet. Instructions for setting up the application can be found [here](../test-suite-wallet).

## Use the libraries to build your own Wallet

Leverage the reference implementation libraries tailored to your platform: 

- for Android developers: [Android Wallet Provider](../eudi-app-android-wallet-ui/wiki/how_to_build/)
	
- for iOS developers: [iOS Wallet Provider](../eudi-app-ios-wallet-ui/wiki/how_to_build/)

## Test your Wallet

The Test Suite offers comprehensive tools to test your own Wallet implementation. It includes both an Issuer and a Verifier, so you don’t need to build them yourself. With the Test Suite you can

- [Issue credentials to your Wallet](../tools-issuer)
- [Test your Wallet in an online service](../tools-verifier/)
- [Test your Wallet with the Verifier application](../eudi-app-android-wallet-ui/wiki/verifier_proximity/)
