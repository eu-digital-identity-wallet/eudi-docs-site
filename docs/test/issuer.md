# Issuer

As part of the testing tools, we offer an issuer, that allows you to test various issuance flows of OpenID4VCI with your wallet:

- Credential Offer
- Credential Offer Pre-Authorization
- Credential Offer Deferred
- Credential Offer Dynamic
  
You can test the issuance of credentials in both mDoc and SD-JWT formats. The test tools include a variety of credential types.

| Tool    | Description |
| --- | --- |
| Basic issuer  |  Basic issuer that supports all issuance flows, in both mDoc and SD-JWT formats. Includes several credential types. <br><br>Available at [https://issuer.eudiw.dev/](https://issuer.eudiw.dev/){:target="_blank"}. |
| Advanced issuance tester | A more comprehensive issuance tester that enables following the different steps in the issuance flow. Supports all issuance flows, in both mDoc and SD-JWT formats. Includes several credential types. <br><br> Available at [https://tester.issuer.eudiw.dev/](https://tester.issuer.eudiw.dev/){:target="_blank"}. |
| Locally installed Issuer | Install the issuer locally. Allows you to add new credential types. <br> <br>See [Installation instructions](../build/build-your-issuer/steps-to-build.md) and instructions on how to [add new credential types](../build/build-your-issuer/new-attestation.md). |
