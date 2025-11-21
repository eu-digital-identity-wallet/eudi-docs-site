# Remote Signature Service Provider (RSSP)

An RSSP is the entity that provides the remote electronic signature service. It operates the backend infrastructure that:

+ Stores and protects users’ signature keys.
+ Performs remote signature operations when the user requests a signature.

## Reference Implementation Signature Services

The Reference Implementation (RI) Signature services constitute a suite of supporting services within the EUDI Wallet Ecosystem that enable end-to-end testing and validation of remote electronic signature flows. These services provide controlled, standards-based environments for Wallets, Relying Parties, and QTSP-like components to interact in accordance with the EUDI Wallet specifications, and the Wallet-driven and RP-centric signature architectures.

These RI Signature services are made available exclusively as part of the EUDI Wallet Reference Implementation and are intended purely for testing, experimentation, and interoperability validation. They provide a controlled environment to explore and evaluate the different remote signing flows (including Wallet-driven and RP-centric approaches), but they do not constitute production-grade trust services, are not operated as QTSP services, and must not be used to generate real electronic signatures or seals. Their sole purpose is to support developers, integrators, and Member State teams in understanding the expected behaviour of the ecosystem and in verifying that their components interact correctly with the signing interfaces defined in the EUDI Wallet specifications.

### TrustProvider Signer

The TrustProvider Signer is a CSC-compliant Remote Signature Service Provider (RSSP) and Signature Application. It includes:

+ an RSSP backend implementing CSC API behaviours;
+ a Signature Application handling signing orchestration; and
+ a Client interface supporting account creation, OpenID4VP authentication, certificate and key-pair creation, and document signing.

It enables Wallet implementers to test non-qualified remote signing workflows.

#### TrustProvider Signer Service

For testing purposes, a hosted instance of the Reference Implementation TrustProvider Signer service is available at <https://trustprovider.signer.eudiw.dev/login>.

The complete source code, deployment instructions and configuration details for the TrustProvider Signer Reference Implementation are publicly available in the GitHub repository at [eudi-srv-web-trustprovider-signer-java](https://github.com/eu-digital-identity-wallet/eudi-srv-web-trustprovider-signer-java).

### Wallet-Driven Signer

The Wallet-Driven signature flow supports an rQES flow initiated and processed within the EUDI Wallet environment. It encompasses the following functional steps:

1. Service (QTSP) Authentication.

    Before initiating the credential listing or signing operation, the Wallet must authenticate itself to the QTSP. In this signature flow, it is assumed that the Wallet has been previously registered with the QTSP.

    To initiate user authentication with the QTSP (Service Authentication process), the SIC (Signature Activation Component) will send a request to the QTSP Authorization Server. The authentication is carried out using the OAuth2 protocol, complemented by the OpenId4VP protocol.

```mermaid
sequenceDiagram
    title Service (QTSP) Authentication

    actor U as UserAgent
    participant EW as EUDI Wallet
    participant AS as Authorization Server (QTSP)
    participant OIDV as OID4VP Verifier

    U->>+EW: Selects QTSP to use
    EW->>+AS: GET /oauth2/authorize?...&redirect_uri=wallet://oauth2/callback&...

    opt is not authenticated
        AS->>+OIDV: Authorization Request (Post dev.verifier-backend.eudiw.dev/ui/presentations?redirect_uri={oid4vp_redirect_uri})
        OIDV->>-AS: Authorization Request returns
        AS->>+AS: Generate link to Wallet
        AS->>-EW: Redirect to link in the Wallet
        EW->>-U: Request Authorization
        U->>+EW: Authorize (Shares PID)
        EW->>+AS: GET oid4vp_redirect_uri
        AS->>+OIDV: Get VP Token
        OIDV->>-AS: Send VP Token
        AS->>+AS: Validate VP Token
        AS->>+EW: Returns session token (successful authentication) & Redirects to /oauth2/authorize
        EW->>+AS: GET /oauth2/authorize?...&redirect_uri=wallet://oauth2/callback&... [Cookie JSession]
    end

    AS->>+EW: Redirect to wallet://oauth2/callback?code={code}
    EW->>+EW: GET wallet://oauth2/callback?code={code}
    EW->>+AS: /oauth2/token?code={code}
    AS->>+AS: Generate Access Token
    AS->>+EW: Return Access Token
```

2. Credential Listing,

    After the user has agreed to sign the document and selected which QTSP will be used, the Wallet shall display the available credentials from the chosen QTSP. To achieve this, the Wallet shall request the list of credentials (including certificates and additional information) from the QTSP.

```mermaid
sequenceDiagram
    title Credential Listing

    actor U as UserAgent
    participant SCC as Signature Creation Component (EUDIW)
    participant RS as Resource Server (QTSP)

    U->>+SCC: Request list of available credentials
    SCC->>+RS: /credentials/list
    opt credential list is empty
        RS->>+RS: issue credentials
    end
    RS->>-SCC: List of the credentials of the user
    SCC->>-U: Present the list of credentials

    opt is a single credential info requested
        U->>+SCC: Request the information of a single credential
        SCC->>+RS: /credentials/info
        RS->>-SCC: credential's information
        SCC->>-U: Present the credential's information
   end

```

3. Document Signing.

    The signature process is divided into two main operations: credential authorization and document signing.

    In the credential authorization flow, the Wallet sends the document to be signed, along with the certificate and the certificate chain of the credential chosen, and other relevant information required to the SCA. The SCA (Signature Creation Application) then computes the hash of the document to be signed. Following this, the Wallet requests authorization from the QTSP to use the private signing key, initiating an OAuth2 flow with OpenID for Verifiable Presentations.

    Once the Wallet receives the token granting access to the chosen credential, the document signing process proceeds. The Wallet uses the QTSP API to obtain the signature for the hash value. Finally, a request is sent to the SCA with the signature value, the document to be signed, the certificate, and any other required data.

```mermaid
sequenceDiagram
    title Document Signing

    actor U as UserAgent
    participant EW as EUDI Wallet
    participant SCA as Signature Creation Application
    participant AS as Authorization Server (QTSP)
    participant RS as Resource Server (QTSP)
    participant OIDV as OID4VP Verifier

    U->>+EW: Chooses credential to use
    U->>+EW: Request document signing
    EW->>+RS: /csc/v2/credentials/info
    RS->>-EW: credentials info

    EW->>+SCA: "calculate hash" (certificates, document to sign)
    SCA->>-EW: hash value

    EW->>+AS: /oauth2/authorize?...&redirect_uri=wallet://login/oauth2/code&...
    AS->>+OIDV: Authorization Request (Post dev.verifier-backend.eudiw.dev/ui/presentations?redirect_uri={oid4vp_redirect_uri})
    OIDV->>-AS: Authorization Request returns
    AS->>+AS: Generate link to Wallet
    AS->>-EW: Redirect to link in the Wallet
    EW->>-U: Request Authorization

    U->>+EW: Authorize (Shares PID)
    EW->>+AS: Redirect to oid4vp_redirect_uri
    AS->>+OIDV: Request VP Token
    OIDV->>-AS: Get and validate VP Token
    AS->>-EW: Returns session token (successful authentication) & Redirects to /oauth2/authorize
    EW->>+AS: GET /oauth2/authorize?...&redirect_uri=wallet://oauth2/callback&... [Cookie JSession]
    AS->>-EW: Redirect to wallet://login/oauth2/code?code={code}
    EW->>+EW: Get wallet://login/oauth2/code....
    EW->>+AS: /oauth2/token?code={code}
    AS->>-EW: access token authorizing credentials use (SAD/R)

    EW->>+RS: /signatures/signHash
    RS->>-EW: signature

    EW->>+SCA: "obtain signed document" (certificates & document & signature value)
    SCA->>-EW: signed document
```

#### Wallet-Driven Signer Service

The Wallet-Driven Signer service provides a reference implementation of a QTSP (Authorization server and Resource server components), supporting authentication and authorisation via OpenID4VP. It supports the complete rQES Wallet-Driven signature flow, including QTSP authentication, credential listing, and remote signature creation, through endpoints such as /oauth2/authorize, /oauth2/token, and /csc/v2/signatures/signHash.

For testing purposes, a hosted instance of the Reference Implementation Wallet-Driven Signer service is available at:

+ <https://walletcentric.signer.eudiw.dev> - RESTful API server implementing both the SCA and QTSP endpoints, serving as the wallet-centric backend components for the EUDI Wallet (and for any other Wallets wishing to test this flow);
+ <https://walletcentric.signer.eudiw.dev/rp/> - Relying Party web interface that allows users to test the Wallet-Driven signature flow by signing PDF, JSON, XML, and TXT documents using the EUDI Wallet (or any other Wallets wishing to test it).

The complete source code, deployment instructions and configuration details for the Wallet-Driven Signer Reference Implementation are publicly available in the GitHub repositories at:

+ [eudi-srv-web-walletdriven-rpcentric-signer-qtsp-java](https://github.com/eu-digital-identity-wallet/eudi-srv-web-walletdriven-rpcentric-signer-qtsp-java) - RESTful API server that implements a Wallet-Driven and RP-Centric QTSP.
+ [eudi-srv-web-walletdriven-signer-external-sca-java](https://github.com/eu-digital-identity-wallet/eudi-srv-web-walletdriven-signer-external-sca-java) - REST API server implementing the Wallet-driven external SCA component. It integrates with the Wallet-Driven QTSP.
+ [eudi-srv-web-walletdriven-signer-relyingparty-py](https://github.com/eu-digital-identity-wallet/eudi-srv-web-walletdriven-signer-relyingparty-py) - Relying Party (RP) Web Service that enables testing and validation of the Wallet-driven remote signature flow. This service implements an RP that interacts with the Wallet in Wallet-Driven rQES flows. It allows the user to select a sample document, triggers the Wallet signature flow, and receives the resulting signed document.

### Relying Party Centric Signer

The Relying Party-Centric (RP-Centric) signature flow supports an rQES process initiated and orchestrated within the Relying Party environment. It encompasses functional steps that mirror those described for the [Wallet-Driven signer](#wallet-driven-signer):

1. Service (QTSP) Authentication.

```mermaid
sequenceDiagram
    title Service (QTSP) Authentication

    actor U as UserAgent
    participant EW as EUDI Wallet
    participant RP as Web Page (RP)
    participant PC as Presentation Component (RP)
    participant AS as Authorization Server (QTSP)
    participant OIDV as OID4VP Verifier

    U->>+RP: Authenticate using OID4VP

    RP->>+RP: Load document
    RP->>+PC: Present document
    U->>+RP: Consent to sign document

    RP->>+AS: /oauth2/authorize
    AS->>+OIDV: Authorization Request (POST {verifier}/ui/presentations)
    OIDV-->>-AS: Authorization Request returns
    AS->>+AS: Generate link to Wallet
    AS-->>-RP: Render link as QrCode

    EW->>+RP: Scan QrCode
    EW->>+OIDV: Share requested information

    AS->>+OIDV: Request VP Token
    OIDV-->>-AS: Get and validate VP Token

    AS-->>-RP: Redirects to /oauth2/authorize (with session token)
    RP->>+AS: /oauth2/authorize [Cookie JSession]
    AS-->>-RP: Redirect to {redirect_uri}?code={code}
    RP->>+AS: /oauth2/token?code={code}
    AS-->>-RP: Access Token
```

2. Credential Listing,

```mermaid
sequenceDiagram
    title Credentials Listing

    actor U as UserAgent
    participant RP as Web Page (RP)
    participant RS as Resource Server (QTSP)

    RP->>+RS: Get credentials list (/credentials/list)
    opt is credential list empty
        RS->>+RS: Issue credential
    end
    RS-->>-RP: credentials list

    opt is a single credential info requested
        RP->>+RS: Get credential's info (/credentials/info)
        RS->>-RP: credential's information
   end
```

3. Document Signing.

```mermaid
sequenceDiagram
title Document Signing

    actor U as UserAgent
    participant EW as EUDI Wallet
    participant BR as Browser
    participant RP as Web Page (RP)
    participant SCA as Signature Creation Application (RP)
    participant AS as Authorization Server (QTSP)
    participant RS as Resource Server (QTSP)
    participant OIDV as OID4VP Verifier

    U->>+RP: Choose credential to use
    RP->>+SCA: Request document signing
    SCA->>+RS: Get certificate of the chosen credential (credentials/info)
    SCA->>+SCA: Get document's hash

    SCA->>+AS: /oauth2/authorize
    AS->>+OIDV: Authorization Request (POST {verifier}/ui/presentations)
    OIDV-->>-AS: Authorization Request returns
    AS->>+AS: Generate link to Wallet
    AS-->>-BR: Render link as QrCode

    EW->>+BR: Scan QrCode
    EW->>+OIDV: Share requested information

    AS->>+OIDV: Request VP Token
    OIDV-->>-AS: Get and validate VP Token

    AS-->>-BR: Redirects to /oauth2/authorize (with session token)
    BR->>+AS: /oauth2/authorize [Cookie JSession]
    AS-->>-BR: Redirect to {sca_redirect_uri}?code={code}

    BR->>+SCA: {sca_redirect_uri}?code={code}
    SCA->>+AS: /oauth2/token?code={code}
    AS-->>-SCA: access token authorizing credentials use (SAD/R)

    SCA->>+RS: Sign hash request (/signatures/signHash)
    RS-->>-SCA: signature

    SCA->>+SCA: generate signed document
    SCA-->>-RP: returns signed document
```

#### RP-Centric Signer Service

The RP-Centric Signer service provides a reference implementation of a QTSP (Authorization server and Resource server components), supporting authentication and authorisation via OpenID4VP. It supports the complete rQES RP-Centric signature flow, including QTSP authentication, credential listing, and remote signature creation, through endpoints such as /oauth2/authorize, /oauth2/token, and /csc/v2/signatures/signHash.

For testing purposes, a hosted instance of the Reference Implementation RP-Centric Signer service is available at:

+ <https://rpcentric.signer.eudiw.dev/tester> - Relying Party web interface that allows users to test the RP-Centric signature flow by signing PDF, JSON, XML, and TXT documents using the EUDI Wallet (or any other Wallets wishing to test it).

The complete source code, deployment instructions and configuration details for the RP-Centric Signer Reference Implementation are publicly available in the GitHub repositories at:

+ [eudi-srv-web-walletdriven-rpcentric-signer-qtsp-java](https://github.com/eu-digital-identity-wallet/eudi-srv-web-walletdriven-rpcentric-signer-qtsp-java) - RESTful API server that implements a Wallet-Driven and RP-Centric QTSP.
+ [eudi-srv-web-rpcentric-signer-sca-java](https://github.com/eu-digital-identity-wallet/eudi-srv-web-rpcentric-signer-sca-java) - REST API server implementing the RP-Centric SCA component. This implementation of the SCA serves as a component of a Relying Party (RP) web service and is used to sign documents.
+ [eudi-srv-web-rpcentric-signer-relyingparty-py](https://github.com/eu-digital-identity-wallet/eudi-srv-web-rpcentric-signer-relyingparty-py) - Relying Party (RP) Web Service that enables testing and validation of the RP-Centric remote signature flow. This service relies on the RP-Centric QTSP Service and on the RP-Centric SCA component, both operating within the RP environment. It implements an RP capable of interacting with the Wallet in RP-Centric rQES flows: it allows the user to select a sample document, initiates the Wallet’s signature process, and receives the resulting signed document.
