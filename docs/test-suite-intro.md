# Test Suite

The test suite allows you to validate whether your wallet application meets the functional requirements. It provides a comprehensive set of test cases to assess both credential issuance and verification in your wallet implementation.

## Issuance

Test whether your wallet supports various issuance flows:
- Credential Offer
- Credential Offer Pre-Authorization
- Credential Offer Deferred
- Credential Offer Dynamic
  
You can test the issuance of credentials in both mdoc and sd-jwt formats. The test service includes a variety of credential types.

[Access the test service for issuance](https://issuer.eudiw.dev/)

## Verification

Test how your wallet implementation responds to a credential request from a verifier.

The test service provides extensive capabilities to test various credentials, including PID. You can also create custom credential requests tailored to your specific needs.

Test service supports both mDoc and sd-jwt formats.

There are two options available:
- [https://verifier.eudiw.dev/](https://verifier.eudiw.dev/)
- [https://tester.relyingparty.eudiw.dev/](https://tester.relyingparty.eudiw.dev/)
