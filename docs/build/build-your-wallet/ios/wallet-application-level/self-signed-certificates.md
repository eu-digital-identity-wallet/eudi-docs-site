# Self-signed Certificates

In addition to the change below, to enable the app to interact with a locally running service, a minor code change is required for successful interaction.

Before running the app in the simulator, add these lines of code to the top of the file WalletKitController just below the import statements.

```swift
final class SelfSignedDelegate: NSObject, URLSessionDelegate {
  func urlSession(
    _ session: URLSession,
    didReceive challenge: URLAuthenticationChallenge,
    completionHandler: @escaping (URLSession.AuthChallengeDisposition, URLCredential?) -> Void
  ) {
    // Check if the challenge is for a self-signed certificate
    if challenge.protectionSpace.authenticationMethod == NSURLAuthenticationMethodServerTrust,
       let trust = challenge.protectionSpace.serverTrust {
      // Create a URLCredential with the self-signed certificate
      let credential = URLCredential(trust: trust)
      // Call the completion handler with the credential to accept the self-signed certificate
      completionHandler(.useCredential, credential)
    } else {
      // For other authentication methods, call the completion handler with a nil credential to reject the request
      completionHandler(.cancelAuthenticationChallenge, nil)
    }
  }
}

let walletSession: URLSession = {
  let delegate = SelfSignedDelegate()
  let configuration = URLSessionConfiguration.default
  return URLSession(
    configuration: configuration,
    delegate: delegate,
    delegateQueue: nil
  )
}()
```

Once the above is in place, adjust the initialiser:

```swift
guard let walletKit = try? EudiWallet(serviceName: configLogic.documentStorageServiceName, networking: walletSession) else {
  fatalError("Unable to Initialize WalletKit")
}
```

This change will allow the app to interact with web services that rely on self-signed certificates.

