# Run with Local Services

The first step here is to have all three services running locally on your machine.
You can follow these Repositories for further instructions:

- [Issuer](https://github.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py){:target="_blank"}
- [Web Verifier UI](https://github.com/eu-digital-identity-wallet/eudi-web-verifier){:target="_blank"}
- [Web Verifier Endpoint](https://github.com/eu-digital-identity-wallet/eudi-srv-web-verifier-endpoint-23220-4-kt){:target="_blank"}


After this, and assuming you are now running everything locally,
you need to change the contents of the ConfigWalletCoreImpl file, from:
```Kotlin
override val vciConfig: List<OpenId4VciManager.Config>
    get() = listOf(
       OpenId4VciManager.Config.Builder()
      .withIssuerUrl(issuerUrl = "https://ec.dev.issuer.eudiw.dev")
      .withClientId(clientId = "wallet-dev")
      .withAuthFlowRedirectionURI(BuildConfig.ISSUE_AUTHORIZATION_DEEPLINK)
      .withParUsage(OpenId4VciManager.Config.ParUsage.IF_SUPPORTED)
      .withDPoPUsage(OpenId4VciManager.Config.DPoPUsage.IfSupported())
      .build()
)
```
with this:
```Kotlin
override val vciConfig: List<OpenId4VciManager.Config>
    get() = listOf(
       OpenId4VciManager.Config.Builder()
      .withIssuerUrl(issuerUrl = "local_IP_address_of_issuer")
      .withClientId(clientId = "wallet-dev")
      .withAuthFlowRedirectionURI(BuildConfig.ISSUE_AUTHORIZATION_DEEPLINK)
      .withParUsage(OpenId4VciManager.Config.ParUsage.IF_SUPPORTED)
      .withDPoPUsage(OpenId4VciManager.Config.DPoPUsage.IfSupported())
      .build()
)
```

for example:
```Kotlin
override val vciConfig: List<OpenId4VciManager.Config>
    get() = listOf(
       OpenId4VciManager.Config.Builder()
      .withIssuerUrl(issuerUrl = "https://10.0.2.2")
      .withClientId(clientId = "wallet-dev")
      .withAuthFlowRedirectionURI(BuildConfig.ISSUE_AUTHORIZATION_DEEPLINK)
      .withParUsage(OpenId4VciManager.Config.ParUsage.IF_SUPPORTED)
      .withDPoPUsage(OpenId4VciManager.Config.DPoPUsage.IfSupported())
      .build()
)
```
