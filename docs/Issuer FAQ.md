# Frequently Asked Questions

## A. How to make your local EUDIW Issuer available on the Internet?

Please see detailed instructions in [install.md](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/blob/main/install.md#4-make-your-local-eudiw-issuer-available-on-the-internet-optional){:target="_blank"}.

## B. How to add a new credential to the issuer ?

Please see detailed instructions in [api_docs/add_credential.md](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/blob/main/api_docs/add_credential.md){:target="_blank"}.

## C. Can I use my IACA certificate with the EUDIW Issuer?

Yes. You must copy your IACA trusted certificate(s) (in PEM format) to the `trusted_CAs_path` folder. If you don't have an IACA certificate, we provide an example test IACA certificate for the country Utopia (UT).

See more information in [api_docs/configuration.md](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/blob/main/api_docs/configuration.md#1-service-configuration){:target="_blank"}.

## D. Can I use my Document Signer private key and certificate with the EUDIW Issuer?

Yes. Please follow the instructions in [api_docs/configuration.md](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/blob/main/api_docs/configuration.md#2-configuration-of-countries){:target="_blank"}. If you don't have Document Signer private key and certificate, we provide  test private DS keys and certificates, for country Utopia (UT).

## E. How can I create a credential offer to issue a credential?

Please see detailed instructions in [api_docs/credential_offer.md](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/blob/main/api_docs/credential_offer.md){:target="_blank"}.

## F. Can I test the pre-authorized flow?

Yes. Please see how in [api_docs/pre-authorized.md](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/blob/main/api_docs/pre-authorized.md){:target="_blank"}.

## H. Can I run the issuer in a Docker container?

Yes. Please see how in [Install Docker](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/blob/main/install.md#6-docker){:target="_blank"}.

