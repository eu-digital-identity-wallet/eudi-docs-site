# Configure your Verifier

## Configuration

The Verifier Endpoint application can be configured using the following *environment* variables:

Variable: `SPRING_PROFILES_ACTIVE`  
Description: Comma separated list of Spring Profiles to activate  
Available profiles:

- `self-signed`: Configures a Ktor HttpClient that trusts self-signed certificates and performs no hostname verification.

Variable: `SPRING_WEBFLUX_BASEPATH`  
Description: Context path for the Verifier Endpoint application.  
Default value: `/`

Variable: `SERVER_PORT`  
Description: Port for the HTTP listener of the Verifier Endpoint application.
Default value: `8080`

Variable: `VERIFIER_ORIGINALCLIENTID`  
Description: Client Id of the Verifier Endpoint application **without** the Client Id prefix.<br>
Default value: `Verifier`

Variable: `VERIFIER_CLIENTIDPREFIX`  
Description: Client Id Prefix used by the Verifier Endpoint application.<br>
Possible values: `pre-registered`, `x509_san_dns`, `x509_hash`  
Default value: `pre-registered`

Variable: `VERIFIER_JAR_SIGNING_ALGORITHM`  
Description: Algorithm used to sign Authorization Request.   
Possible values: Any `Algorithm Name` of an IANA registered asymmetric signature algorithm (i.e. Usage is `alg`):
https://www.iana.org/assignments/jose/jose.xhtml#web-signature-encryption-algorithms   
Note: The configured signing algorithm must be compatible with the configured signing key.  
Default value: `ES256`

Variable: `VERIFIER_JAR_SIGNING_KEY`  
Description: Key to use for Authorization Request signing.  
Possible values: `GenerateRandom`, `LoadFromKeystore`  
Setting this value to `GenerateRandom` will result in the generation of a random `EC` key using the curve `P-256`.   
Note: The configured signing key must be compatible with the configured signing algorithm  
Default value: `GenerateRandom`

Variable: `VERIFIER_PUBLICURL`  
Description: Public URL of the Verifier Endpoint application.  
Default value: `http://localhost:${SERVER_PORT}`

Variable: `VERIFIER_REQUESTJWT_EMBED`  
Description: How Authorization Requests will be provided.    
Possible values: `ByValue`, `ByReference`  
Default value: `ByReference`

Variable: `VERIFIER_REQUESTJWT_REQUESTURIMETHOD`  
Description: Default `request_uri_method` to use for a Presentation when one is not provided during its initialization. Applicable when `VERIFIER_REQUESTJWT_EMBED` is `ByReference`.          
Possible values: `Get`, `Post`  
Default value: `Get`  

Variable: `VERIFIER_RESPONSE_MODE`  
Description: How Authorization Responses are expected.    
Possible values: `DirectPost`, `DirectPostJwt`  
Default value: `DirectPostJwt`

Variable: `VERIFIER_MAXAGE`  
Description: TTL of an Authorization Request.  
Notes: Provide a value using Java Duration syntax.  
Example: `PT6400M`  
Default value: `PT6400M`

Variable: `VERIFIER_PRESENTATIONS_CLEANUP_MAXAGE`  
Description: Age of Authorization Requests. Authorization Requests older than this, are deleted.     
Notes: Provide a value using Java Duration syntax.
Example: `P10D`  
Default value: `P10D`

Variable: `VERIFIER_AUTHORIZATIONREQUESTURI`  
Description: The Authorization Request Uri to be used when generating an Authorization Request.      
Example: `haip-vp://`  
Default value: `haip-vp://`

Variable: `VERIFIER_ALLOWEDREDIRECTURISCHEMES`  
Description: Comma-separated list of schemes allowed to be used in the `wallet_response_redirect_uri_template`. 
When Verifier Endpoint is used by a native mobile application, `wallet_response_redirect_uri_template` might contain a URI with a custom scheme (i.e., a deep-link). 
In such cases the custom scheme must be added to `VERIFIER_ALLOWEDREDIRECTURISCHEMES`.  
Default value: `https`

Variable: `VERIFIER_CLIENTMETADATA_RESPONSEENCRYPTION_ALGORITHM`  
Description: Algorithm that verifier is advertising and supports for authorization response encryption.    
Possible values: `ECDH-ES`, `ECDH-ES+A128KW`, `ECDH-ES+A192KW`, `ECDH-ES+A256KW`  
Default value: `ECDH-ES`

Variable: `VERIFIER_CLIENTMETADATA_RESPONSEENCRYPTION_METHOD`  
Description: Method that verifier is advertising and supports for authorization response encryption.   
Possible values: `A128CBC-HS256`, `A192CBC-HS384`, `A256CBC-HS512`, `A128GCM`, `A192GCM`, `256GCM`, `XC20P`  
Default value: `A128GCM`  

Variable: `VERIFIER_CLIENTMETADATA_VPFORMATS_SDJWTVC_ENABLED`  
Description: Enables support for SD-JWT VC.   
Default value: `true`  

Variable: `VERIFIER_CLIENTMETADATA_VPFORMATS_SDJWTVC_SDJWTALGORITHMS`  
Description: Comma separated list of signature algorithms the Issuer Signed JWT of an SD-JWT VC can be signed with.     
Possible values: Any `Algorithm Name` of an IANA registered asymmetric signature algorithm (i.e. Usage is `alg`):
https://www.iana.org/assignments/jose/jose.xhtml#web-signature-encryption-algorithms.
Default value: `ES256`

Variable: `VERIFIER_CLIENTMETADATA_VPFORMATS_SDJWTVC_KBJWTALGORITHMS`  
Description: Comma separated list of signature algorithms the Key Binding JWT of an SD-JWT VC can be signed with.     
Possible values: Any `Algorithm Name` of an IANA registered asymmetric signature algorithm (i.e. Usage is `alg`):
https://www.iana.org/assignments/jose/jose.xhtml#web-signature-encryption-algorithms.
Default value: `ES256`

Variable: `VERIFIER_CLIENTMETADATA_VPFORMATS_MSOMDOC_ENABLED`  
Description: Enable support for MSO MDoc.    
Default value: `true`  

Variable: `VERIFIER_VALIDATION_SDJWTVC_STATUSCHECK_ENABLED`  
Description: Enables status check validation for sd-jwt-vc attestations shared.  
Default value: `true`  

Variable: `VERIFIER_TRANSACTIONDATA_HASHALGORITHM`  
Description: Hash algorithm to communicate in the `transaction_data_hashes_alg` claim of transaction data.  
Default value: `sha-256`  
Supported values: `sha-256`, `sha-384`, `sha-512`, `sha3-224`, `sha3-256`, `sha3-384`, `sha3-512`  

Variable: `CORS_ORIGINS`  
Description: Comma separated list of allowed Origins for cross-origin requests.  
Default value: `*`

Variable: `CORS_ORIGINPATTERNS`  
Description: Comma separated list of patterns used for more fine grained matching of allowed Origins for cross-origin requests.  
Default value: `*`

Variable: `CORS_METHODS`  
Description: Comma separated list of HTTP methods allowed for cross-origin requests.  
Default value: `*`

Variable: `CORS_HEADERS`  
Description: Comma separated list of allowed and exposed HTTP Headers for cross-origin requests.  
Default value: `*`

Variable: `CORS_CREDENTIALS`  
Description: Whether credentials (i.e. Cookies or Authorization Header) are allowed for cross-origin requests.<br>
Default value: `false`

Variable: `CORS_MAXAGE`  
Description: Time in seconds of how long pre-flight request responses can be cached by clients.  
Default value: `3600`

### Setting `VERIFIER_JAR_SIGNING_KEY` to `LoadFromKeystore`

When `VERIFIER_JAR_SIGNING_KEY` is set to `LoadFromKeystore` the following environment variables must also be configured.

Variable: `VERIFIER_JAR_SIGNING_KEY_KEYSTORE`  
Description: URL of the Keystore from which to load the Key to use for JAR signing.  
Examples: `classpath:keystore.jks`, `file:///keystore.jks`

Variable: `VERIFIER_JAR_SIGNING_KEY_KEYSTORE_TYPE`  
Description: Type of the Keystore from which to load the Key to use for JAR signing.  
Examples: `jks`, `pkcs12`

Variable: `VERIFIER_JAR_SIGNING_KEY_KEYSTORE_PASSWORD`  
Description: Password of the Keystore from which to load the Key to use for JAR signing.

Variable: `VERIFIER_JAR_SIGNING_KEY_ALIAS`  
Description: Alias of the Key to use for JAR signing, in the configured Keystore.

Variable: `VERIFIER_JAR_SIGNING_KEY_PASSWORD`  
Description: Password of the Key to use for JAR signing, in the configured Keystore.

### Configuring Trust Sources

The verifier supports the configuration of multiple trust sources, that will be used to trust the issuers of presented credentials.  
Each trust source is associated with a regex pattern, that will be used to match the trust source to an issuer, based on a credential's docType/vct.
Each trust source can be configured with a List of Trusted Lists, a Keystore or both.
The trust sources are configured using the environment variable `VERIFIER_TRUSTSOURCES` and are indexed starting from `0`. You can define multiple trust sources by incrementing the index (e.g., VERIFIER_TRUSTSOURCES_0_*, VERIFIER_TRUSTSOURCES_1_*, etc.)

Variable: `VERIFIER_TRUSTSOURCES_0_PATTERN`<br>
Description: The regex pattern used to match the trust source to an issuer, based on a credential's docType/vct.<br>
Example: `eu.europa.ec.eudi.pid.*|urn:eu.europa.ec.eudi:pid:.*`<br>

Variable: `VERIFIER_TRUSTSOURCES_0_LOTL_LOCATION`<br>
Description: If present, the URL of the List of Trusted Lists from which to load the X509 Certificates for this trust source.<br>

Variable: `VERIFIER_TRUSTSOURCES_0_LOTL_REFRESHINTERVAL`<br>
Description: If present, a cron expression with the refresh interval of the List of Trusted Lists in seconds. If not present, the default value is `0 0 * * * * ` (every hour).<br>
Example: `0 0 */4 * * *`

Variable: `VERIFIER_TRUSTSOURCES_0_LOTL_SERVICETYPEFILTER`<br>
Description: If present, the service type filter to be used when loading the List of Trusted Lists. If not present, all service types are loaded. Valid values are `PIDProvider`, `QEEAProvider` and `PubEAAProvider`.<br>
Example: `PIDProvider`

Variable: `VERIFIER_TRUSTSOURCES_0_LOTL_KEYSTORE_PATH`<br>
Description: If present, the URL of the Keystore which contains the public key that was used to sign the List of Trusted Lists.<br>
Examples: `classpath:lotl-key.jks`, `file:///lotl-key.jks`

Variable: `VERIFIER_TRUSTSOURCES_0_LOTL_KEYSTORE_TYPE`<br>
Description: Type of the Keystore which contains the public key that was used to sign the List of Trusted Lists.<br>
Examples: `jks`, `pkcs12`

Variable: `VERIFIER_TRUSTSOURCES_0_LOTL_KEYSTORE_PASSWORD`<br>
Description: If present and non-blank, the password of the Keystore which contains the public key that was used to sign the List of Trusted Lists.<br>

Variable: `VERIFIER_TRUSTSOURCES_0_KEYSTORE_PATH`<br>
Description: If present, the URL of the Keystore from which to load the X509 Certificates for this trust source. <br>
Examples: `classpath:trusted-issuers.jks`, `file:///trusted-issuers.jks`

Variable: `VERIFIER_TRUSTSOURCES_0_KEYSTORE_TYPE`<br>
Description: Type of the Keystore from which to load the X509 Certificates for this trust source.<br>
Examples: `jks`, `pkcs12`

Variable: `VERIFIER_TRUSTSOURCES_0_KEYSTORE_PASSWORD`<br>
Description: If present and non-blank, the password of the Keystore from which to load the X509 Certificates for this trust source.<br>

### Proxy Configuration  

Variable: `VERIFIER_HTTP_PROXY_URL`  
Description: Optional HTTP proxy server to use.  
Example: `http://exmaple.com`

Variable: `VERIFIER_HTTP_PROXY_USERNAME`  
Description: Username to authenticate against the proxy.  
Example: `username`

Variable: `VERIFIER_HTTP_PROXY_PASSWORD`  
Description: Password to authenticate against the proxy.  
Example: `passwd`

### SD-JWT-VC Type Metadata Policy

Variable: `VERIFIER_VALIDATION_SDJWTVC_TYPEMETADATA_POLICY`  
Description: Choose SD-JWT VC Type Metadata policy. Information about the available policies can be found [here](https://github.com/eu-digital-identity-wallet/eudi-lib-jvm-sdjwt-kt?tab=readme-ov-file#type-metadata-resolution){:target="_blank"}.
Accepted values: `not_used`,`optional`,`always_required`,`required_for`  
Default value: `not_used`  

Variable: `VERIFIER_VALIDATION_SDJWTVC_TYPEMETADATA_POLICY_REQUIREDFOR`  
Description: Comma separated list of VCTs for which Type Metadata are required for. Required when `VERIFIER_VALIDATION_SDJWTVC_TYPEMETADATA_POLICY` is set to `required_for`.  
Example: `urn:eudi:pid:1`  

#### SD-JWT-VC Type Metadata Resolution

Required when `VERIFIER_VALIDATION_SDJWTVC_TYPEMETADATA_POLICY` is not set to `not_used`.  

Variable: `VERIFIER_VALIDATION_SDJWTVC_TYPEMETADATA_RESOLUTION_VCTS_XX_VCT` (e.g. `VERIFIER_VALIDATION_SDJWTVC_TYPEMETADATA_RESOLUTION_VCTS_0_VCT`)   
Description: VCT for which Type Metadata resolution is enabled.  
Example: `urn:eudi:pid:1`  

Variable: `VERIFIER_VALIDATION_SDJWTVC_TYPEMETADATA_RESOLUTION_VCTS_XX_URL` (e.g. `VERIFIER_VALIDATION_SDJWTVC_TYPEMETADATA_RESOLUTION_VCTS_0_URL`)  
Description: Url from which Type Metadata can be fetched from for `VERIFIER_VALIDATION_SDJWTVC_TYPEMETADATA_RESOLUTION_VCTS_XX_VCT`.  
Example: `http://localhost:8080/type-metadata/urn:eudi:pid:1`  

Variable: `VERIFIER_VALIDATION_SDJWTVC_TYPEMETADATA_RESOLUTION_CACHE_TTL`  
Description: Cache TTL for resolved Type Metadata.  
Notes: Provide a value using Java Duration syntax.
Default value: `PT1H`  

Variable: `VERIFIER_VALIDATION_SDJWTVC_TYPEMETADATA_RESOLUTION_CACHE_MAXENTRIES`  
Description: Cache maximum entries for resolved Type Metadata.  
Default value: `10`  

Variable: `VERIFIER_VALIDATION_SDJWTVC_TYPEMETADATA_RESOLUTION_INTEGRITY_ENABLED`  
Description: Enables sub-resource integrity validation for SD-JWT VC Type Metadata and JSON schemas.  
Default value: `false`

Variable: `VERIFIER_VALIDATION_SDJWTVC_TYPEMETADATA_RESOLUTION_INTEGRITY_ALLOWEDALGORITHMS`    
Description: Comma-separated list of allowed sub-resource integrity hash algorithms.  
Allowed values: `sha256`, `sha384`, `sha512`  
Default value: `sha256,sha384,sha512`  

Variable: `VERIFIER_VALIDATION_SDJWTVC_TYPEMETADATA_JSONSCHEMA_VALIDATION_ENABLED`  
Description: Whether Json Schema validation should be enabled or not.    
Default value: `true`   
