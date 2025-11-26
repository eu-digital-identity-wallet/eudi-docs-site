# Relying Party Registration Service

The Relying Party (RP) Registration Service (RS) is a supporting ecosystem service within the EUDI Wallet framework that enables the registration, authentication, and management of Relying Party instances. This service allows Relying Party Registrars to register new Relying Parties, automatically issue RP access certificates, and manage their lifecycle.

## Reference Implementation RPRS

The RP Registration Service Reference Implementation is provided solely as a non-production environment to enable Member State authorities, developers, and integrators to experiment with Relying Party registration, validate workflows, and test interoperability with Wallet instances. It does not constitute a production-grade service and must not be used to manage real Relying Party access certificates or other credentials.

The [RPRS](https://registry.serviceproviders.eudiw.dev/) provides the following functionalities:

- Relying Party Registration: Collects essential information from the Relying Party (country, official name, common name, registration number, contact details, intended Wallet usage, and password for key protection) and automatically issues a certificate and keypair.
- Certificate Management: Lists issued certificates and enables revocation when necessary, maintaining trust in the ecosystem.

## Supported credentials and formats

The current version of the RPRS supports the issuance of Relying Party Access Certificates (RPAC), issued in PKCS#12 (P12) format.

The RPAC is used by Wallet instances to authenticate the Relying Party in transactions where the Wallet shares user attributes. This authentication process is part of the standard presentation communication protocols, enabling secure and trusted interactions between Wallets and Relying Party instances.

### Integration with the RI Verifier

To integrate with the [RI Verifier](../build-your-remote-verifier/index.md) in order to load from a keystore the key used for JAR-signing authorisation requests ([variable `VERIFIER_JAR_SIGNING_KEY_KEYSTORE`](../build-your-remote-verifier/configure.md)), please use the following command line to convert the downloaded PKCS#12 file to a JKS file:

```shell
keytool -importkeystore -srckeystore [FileIn.p12] -srcstoretype pkcs12 -destkeystore [FileOUT.jks] -deststoretype jks -deststorepass [passwordJKS] 
```

## Reference Implementation RPRS deployment and configuration

The complete source code, deployment instructions and configuration details for the RP Registration Service Reference Implementation are publicly available in the GitHub repository at [eudi-srv-web-relyingparty-registration-py](https://github.com/eu-digital-identity-wallet/eudi-srv-web-relyingparty-registration-py).
