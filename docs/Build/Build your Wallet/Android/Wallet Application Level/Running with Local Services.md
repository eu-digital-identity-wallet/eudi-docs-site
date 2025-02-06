# Running with local services
The first step here is to have all three services running locally on your machine,
you can follow these Repositories for further instructions:

* [Issuer](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py)
* [Web Verifier UI](https://github.com/eu-digital-identity-wallet/eudi-web-verifier)
* [Web Verifier Endpoint](https://github.com/eu-digital-identity-wallet/eudi-srv-web-verifier-endpoint-23220-4-kt)


After this, and assuming you are now running everything locally,
you need to change the contents of the ConfigWalletCoreImpl file, from:
```Kotlin
private companion object {
        const val VCI_ISSUER_URL = "https://dev.issuer.eudiw.dev"
        const val VCI_CLIENT_ID = "wallet-dev"
        const val AUTHENTICATION_REQUIRED = false
}
```
into something like this:
```Kotlin
private companion object {
        const val VCI_ISSUER_URL = "local_IP_address_of_issuer"
        const val VCI_CLIENT_ID = "wallet-dev"
        const val AUTHENTICATION_REQUIRED = false
}
```

for example:
```Kotlin
private companion object {
        const val VCI_ISSUER_URL = "https://192.168.1.1:5000"
        const val VCI_CLIENT_ID = "wallet-dev"
        const val AUTHENTICATION_REQUIRED = false
}
```

Finally, you have to also change the content of ***network_security_config.xml*** file and allow HTTP traffic, to this:
```Xml
<network-security-config>
    <base-config cleartextTrafficPermitted="true" />
</network-security-config>
```