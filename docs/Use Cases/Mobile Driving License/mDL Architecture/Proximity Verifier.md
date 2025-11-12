# Proximity Verifier mobile application (mDL Reader)
The mDL Reader is a mobile application that can request, receive, and verify the integrity and authenticity of an mDL for proximity presentation flows. It is controlled by an mDL Verifier, which is a person or organization.

The mDL reader implements the proximity presentation flow with the EUDI Wallet. ISO/IEC 18013-5 specifies the interfaces between:

- :heavy_check_mark: the mDL (wallet) and mDL reader and
- :heavy_multiplication_x: the mDL reader and the issuing authority infrastructure. 

:exclamation: The interface of the mDL reader and the issuing authority infrastructure (online/server data retrieval) is **excluded (not supported)** from the mDL target solution since it allows the issuing authority to have knowledge when the mDL holder presents the mDL to a specific mDL verifier. This is prohibited explicitly by articles 5a.16 and 5a.5(b) of [eIDAS] and [ARF] Annex 2 High level requirement “ProxId_02” that states explicitly __“Wallet Solutions, PID Providers, Attestation Providers, Wallet Providers, and Relying Parties SHALL NOT support server retrieval as specified in ISO/IEC 18013-5 for requesting and presenting PID or attestation attributes”__. Therefore, this method is excluded (not supported) from the mDL target solution
