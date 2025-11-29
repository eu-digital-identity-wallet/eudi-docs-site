# Remote Verifier web application
The components required by the (Remote) mDL Verifier Organization are described below. The mDL Verifier Organization needs to integrate in its infrastructure and IT systems the mDL Verifier component that offers the main remote mDL verification functionality. The specific components that comprise the mDL target solution are as follows. 

## (Remote) mDL Verifier Client
- This runs in the web browser and provides the user interface for initiating and managing the presentation flow. 
- It renders and submits the presentation requests to the wallet. 
- It interacts with the Digital Credential API of the web browser to manage the presentation requests and responses. 

## (Remote) mDL Verifier Backend
- This is the server-side component of the mDL Verifier application that directly interacts with the Wallet via the front end. 
- It sends presentation requests, compliant with the OpenID4VP specification, to the Wallet via the browser's Digital Credentials API. 
- It receives the encrypted presentation response containing the requested attributes from the Wallet (forwarded by the browser). 
- It performs the trust relationship checks. 
- It integrates with the mDL Verifier Organization backend systems to provide information about the requested mDL claims and verification checks. 

## mDL Verifier Organization backend systems
- They request the mDL Verifier Backend to initiate the mDL remote presentation flow. 
- They receive the requested mDL attributes and the results of validation and verification checks from the mDL Verifier Backend. 
