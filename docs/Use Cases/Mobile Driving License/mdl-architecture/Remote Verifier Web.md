# Remote Verifier web application
The components required by the (Remote) mDL Verifier Organization are described below. The mDL Verifier Organization needs to integrate in its infrastructure and IT systems the mDL Verifier component that offers the main remote mDL verification functionality. The specific components that comprise the mDL target solution are the following: 

## (Remote) mDL Verifier Client: 
- runs in the web browser and provides the user interface for initiating and managing the presentation flow. 
- renders and submits the presentation requests to the wallet. 
- interacts with the Digital Credential API of the web browser to manage the presentation requests and responses. 

## (Remote) mDL Verifier Backend: 
- is the server-side component of the mDL Verifier application that directly interacts with the Wallet via the frontend. 
- sends presentation requests, compliant with the OpenID4VP specification, to the Wallet via the browser's Digital Credentials API 
- receives the encrypted presentation response containing the requested attributes from the Wallet (forwarded by the browser) 
- performs the trust relationships checks. 
- integrates with the mDL Verifier Organization backend systems to inform about the requested mDLs claims and verification checks. 

## mDL Verifier Organization backend systems: 
- It requests from the mDL Verifier Backend to initiate the mDL remote presentation flow, 
- It receives from the mDL Verifier Backend the requested mDL attributes and validation and verification checks. 
