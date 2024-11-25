As part of the test suite, we offer an issuer, that allows you to test various issuance flows of OpenID4VCI with your wallet:
- Credential Offer
- Credential Offer Pre-Authorization
- Credential Offer Deferred
- Credential Offer Dynamic
  
You can test the issuance of credentials in both mdoc and sd-jwt formats. The test stools include a variety of credential types.

| Tool    | Description |
| -------- | ------- |
| Basic issuer  |  Basic issuer that supports all issuance flows, in both mdoc and sd-jwt formats. Includes several credential types. <br><br>Available at [https://issuer.eudiw.dev/](https://issuer.eudiw.dev/). |
| Advanced issuance tester | A more comprehensive issuance tester that enables following the different steps in the issuance flow. Supports all issuance flows, in both mdoc and sd-jwt formats. Includes several credential types. <br><br> Available at [https://tester.issuer.eudiw.dev/](https://tester.issuer.eudiw.dev/). |
| Locally installed issuer | Instal the issuer locally. Allows you to add new credential types. <br> <br>See [Installation instruction](./eudi-srv-web-issuing-eudiw-py/) and instructions how to [add new credential types](https://mgiakkou.github.io/devhub/eudi-srv-web-issuing-eudiw-py/api_docs/add_credential/). |
