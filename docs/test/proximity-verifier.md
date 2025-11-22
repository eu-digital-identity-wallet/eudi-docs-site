# Proximity Verifier

The Proximity Verifier (also referred as mDoc Verifier) is an Android application based on the `appverifier` from the [Google Identity Credential library](https://github.com/openwallet-foundation-labs/identity-credential){:target="_blank"}, implementing ISO/IEC 18013-5:2021.

## Purpose

The Proximity Verifier app is provided to help developers test and validate their wallet implementations.

## Modifications

Starting from the original code of the `appverifier` [here](https://github.com/openwallet-foundation-labs/identity-credential/commit/0b9b31ef63047762e10300e23a22f6d7dcfb6d15){:target="_blank"}, the following modifications have been made (the code is not currently publicly available):

 - Support for requesting EU Documents:
   - Personal Identification Data (PID) document, according to the ARF PID RuleBook.
   - Age Verification (Pseudonym) document.
 - IACA Certificates: Updated to support EUDI Wallet IACAs as trusted certificates.
 - Reader Authentication Certificate.

## Install the Verifier

The app is available for download from the App Center, [here](https://install.appcenter.ms/orgs/eu-digital-identity-wallet/apps/mdoc-verifier-testing/distribution_groups/eudi%20verifier%20(testing)%20public){:target="_blank"}.

## Important Note
The Proximity Verifier app is a testing tool for developers to validate their wallet implementations. 
It is not intended for production use. 
The app may contain bugs or other issues that affect its functionality on different mobile devices or Android versions.
These issues will be addressed in the upcoming open-source library, which will be available for developers to build their own verifier applications.
