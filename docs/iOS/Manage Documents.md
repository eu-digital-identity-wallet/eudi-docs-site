# Manage documents

The [EudiWallet](https://eu-digital-identity-wallet.github.io/eudi-lib-ios-wallet-kit/documentation/eudiwalletkit/eudiwallet){:target="_blank"} class provides a set of methods to work with documents.

## Loading documents

The `loadDocuments` method returns documents with a specific status from storage.

The following example shows how to retrieve issued documents:

```swift
 public func loadDocuments() async throws {
    let documents = try await wallet.loadDocuments(status: .issued)
  }
```

To retrieve documents of all statuses use the `loadAllDocuments` method.

```swift
let documents = try await wallet.loadAllDocuments()
```

The `loadDocument(id:status:)` method returns a document with a given id and status. 

The following example shows how to retrieve a document:

```swift
let document = try await wallet.loadDocument(id: documentId, status: .issued)
```

## Storage manager
The read-only property ``storage`` is an instance of a [StorageManager](https://eu-digital-identity-wallet.github.io/eudi-lib-ios-wallet-kit/documentation/eudiwalletkit/storagemanager) class.
Currently the keychain implementation is used. It provides document management functionality using the iOS KeyChain.

The storage model provides the following models for the supported well-known document types:

|DocType|Model|
|-------|-----|
|eu.europa.ec.eudiw.pid.1|[EuPidModel](https://eu-digital-identity-wallet.github.io/eudi-lib-ios-iso18013-data-model/documentation/mdocdatamodel18013/eupidmodel){:target="_blank"}|
|org.iso.18013.5.1.mDL|[IsoMdlModel](https://eu-digital-identity-wallet.github.io/eudi-lib-ios-iso18013-data-model/documentation/mdocdatamodel18013/isomdlmodel){:target="_blank"}|

Since the issued mDoc documents retrieved expose only basic metadata and the raw data, they must be decoded to the corresponding CBOR models. The library provides the ``StorageManager\toClaimsModel`` function to decode document raw CBOR data to strongly-typed models conforming to [DocClaimsDecodable](https://eu-digital-identity-wallet.github.io/eudi-lib-ios-iso18013-data-model/documentation/mdocdatamodel18013/DocClaimsDecodable) protocol. 

The loading functions automatically update the ``StorageManager`` members. The decoded issued documents are available in the ``docModels`` property. The deferred and pending documents are available in the ``StorageManager\deferredDocuments`` and ``StorageManager\pendingDocuments`` properties respectively.

For other document types the [GenericMdocModel](https://eu-digital-identity-wallet.github.io/eudi-lib-ios-iso18013-data-model/documentation/mdocdatamodel18013/genericmdocmodel){:target="_blank"} is provided.


## Deleting a document

The `deleteDocument(id:)` method that deletes a document with the given id.

The following example shows how to delete a document:

```swift
try await wallet.deleteDocument(id: documentId)
```