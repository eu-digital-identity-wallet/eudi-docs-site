# Running with remote services

The app is configured to use some configuration in the two ***ConfigWalletCoreImpl.kt*** files (located in the "**core-logic**" module, in either

`src\dev\java\eu\europa\ec\corelogic\config` or
`src\demo\java\eu\europa\ec\corelogic\config`,

depending on the flavor of your choice).

These are the contents of the ConfigWalletCoreImpl file (dev flavor) and you don't need to change anything:

```Kotlin
private companion object {
        const val VCI_ISSUER_URL = "https://dev.issuer.eudiw.dev"
        const val VCI_CLIENT_ID = "wallet-dev"
        const val AUTHENTICATION_REQUIRED = false
}
```
