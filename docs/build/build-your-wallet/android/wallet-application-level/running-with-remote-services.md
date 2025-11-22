# Run with Remote Services

The app is configured to use some configuration in the two ***ConfigWalletCoreImpl.kt*** files (located in the "**core-logic**" module, in either
*src\dev\java\eu\europa\ec\corelogic\config* or
*src\demo\java\eu\europa\ec\corelogic\config*,
depending on the flavor of your choice).

These are the contents of the ConfigWalletCoreImpl file (dev flavor), and you don't need to change anything:
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

