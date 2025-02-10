# Manage Documents

The library provides a set of methods to work with documents.

```kotlin
val documents = wallet.getDocuments()
```

You can also retrieve documents based on a predicate. The following snippet shows how to retrieve
documents of mso_mdoc format of a specific docType:

```kotlin
val documents = wallet.getDocuments { document ->
    (document.format as MsoMdocFormat).docType == "eu.europa.ec.eudi.pid.1"
}
```

The following snippet shows how to retrieve a document by its id:

```kotlin
val documentId = "some_document_id"
val document: Document? = wallet.getDocumentById(documentId)
```

To delete a document, use the following code snippet:

```kotlin
try {
    val documentId = "some_document_id"
    val deleteResult = wallet.deleteDocumentById(documentId)
    deleteResult.getOrThrow()
} catch (e: Throwable) {
    // Handle the exception
}
```

## Creating and storing a new document

Adding a new document to the wallet is a two-step process. First, a new document must be
created using the `createDocument` method. The method returns an `UnsignedDocument` object that
contains the keys that will be used for signing the proof of possession for the issuer. Creating a
new document requires the document format and the create key settings. The create key settings can
be used to specify the way the keys are created.

When using the built-in `AndroidKeystoreSecureArea` implementation of the library, the
`wallet.getDefaultCreateDocumentSettings()` extension can be used to create an instance of the
appropriate `CreateDocumentSettings` class.

After the document is created, the user must retrieve the document's data from the issuer and store
it in the wallet using the storeIssuedDocument method.

The following snippet demonstrates how to create a new document for the mso_mdoc format, using
library's default implementation of CreateDocumentSettings.

```kotlin
try {
    // create a new document
    // Construct the CreateDocumentSettings object
    val createSettings = wallet.getDefaultCreateDocumentSettings()

    val createDocumentResult = wallet.createDocument(
        format = MsoMdocFormat(docType = "eu.europa.ec.eudi.pid.1"),
        createSettings = createSettings
    )
    val unsignedDocument = createDocumentResult.getOrThrow()
    val publicKeyBytes = unsignedDocument.publicKeyCoseBytes

    // prepare keyUnlockData to unlock the key
    // here we use the default key unlock data for the document
    // provided by the library
    val keyUnlockData = unsignedDocument.DefaultKeyUnlockData
    // proof of key possession
    // Sign the documents public key with the private key
    // before sending it to the issuer
    val signatureResult =
        unsignedDocument.sign(publicKeyBytes, keyUnlockData = keyUnlockData)
    val signature = signatureResult.getOrThrow().toCoseEncoded()

    // send the public key and the signature to the issuer
    // and get the document data
    val documentData = sendToIssuer(
        publicKeyCoseBytes = publicKeyBytes,
        signatureCoseBytes = signature
    )

    // store the issued document with the document data received from the issuer
    val storeResult =
        wallet.storeIssuedDocument(unsignedDocument, documentData)

    // get the issued document
    val issuedDocument = storeResult.getOrThrow()
} catch (e: Throwable) {
    // Handle the exception
}

// ...

fun sendToIssuer(publicKeyCoseBytes: ByteArray, signatureCoseBytes: ByteArray): ByteArray {
    TODO("Send publicKey and proof of possession signature to issuer and retrieve document's data")
}
```

**Important!:** In the case of `DocumentFormat.MsoMdoc`, the `DocumentManager.storeIssuedDocument()` 
method expects the document's data to be in CBOR bytes and have the IssuerSigned structure according to
ISO 23220-4.

Currently, the library does not support IssuerSigned structure without the `nameSpaces` field.

The following CDDL schema describes the structure of the IssuerSigned structure:

```cddl
IssuerSigned = {
 ?"nameSpaces" : IssuerNameSpaces, ; Returned data elements
 "issuerAuth" : IssuerAuth ; Contains the mobile security object (MSO) for issuer data authentication
}
IssuerNameSpaces = { ; Returned data elements for each namespace
 + NameSpace => [ + IssuerSignedItemBytes ]
}
IssuerSignedItemBytes = #6.24(bstr .cbor IssuerSignedItem)
IssuerSignedItem = {
 "digestID" : uint, ; Digest ID for issuer data authentication
 "random" : bstr, ; Random value for issuer data authentication
 "elementIdentifier" : DataElementIdentifier, ; Data element identifier
 "elementValue" : DataElementValue ; Data element value
}
IssuerAuth = COSE_Sign1 ; The payload is MobileSecurityObjectBytes
```

### Working with sample documents

The wallet-core library provides a method to load sample documents easily. This feature is useful
for demonstration or testing purposes.

Currently, the library supports loading sample documents in MsoMdoc format.

The following code snippet shows how to load sample documents:

```kotlin
val sampleMdocDocuments: ByteArray = readFileWithSampleData()

val createSettings = wallet.getDefaultCreateDocumentSettings()
val loadResult = wallet.loadMdocSampleDocuments(
    sampleData = sampleMdocDocuments,
    createSettings = createSettings,
    documentNamesMap = mapOf(
        "eu.europa.ec.eudi.pid.1" to "EU PID",
        "org.iso.18013.5.1.mDL" to "mDL"
    )
)

val documentIds: List<DocumentId> = loadResult.getOrThrow()

// ...

fun readFileWithSampleData(): ByteArray = TODO("Reads the bytes from file with sample documents")
```

Sample documents must be in CBOR format with the following structure:

```
Data = {
 "documents" : [+Document] ; Sample documents
}
Document = {
 "docType" : DocType, ; Document type returned
 "issuerSigned" : IssuerSigned ; Data elements
}
IssuerSigned = {
 "nameSpaces" : IssuerNameSpaces, ; Returned data elements
}
IssuerNameSpaces = { ; Returned data elements for each namespace
 + NameSpace => [ + IssuerSignedItemBytes ]
}
IssuerSignedItem = {
 "digestID" : uint, ; Digest ID for issuer data authentication
 "random" : bstr, ; Random value for issuer data authentication
 "elementIdentifier" : DataElementIdentifier, ; Data element identifier
 "elementValue" : DataElementValue ; Data element value
}
```