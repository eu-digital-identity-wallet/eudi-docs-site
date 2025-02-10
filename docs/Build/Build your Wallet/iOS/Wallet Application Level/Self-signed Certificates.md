# How to work with self signed certificates on iOS

In order for the app to interact with locally running service the following changes need to be done:

1. Before running the app in the simulator add these lines of code to the top of the file WalletKitController just below the import statements. 

	```swift
	class SelfSignedDelegate: NSObject, URLSessionDelegate {
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

2. Once the above is in place, add the following line in the initializer in order for the app to interact with web services that rely on self-signed certificates:

	```swift
	wallet.urlSession = walletSession
	```
