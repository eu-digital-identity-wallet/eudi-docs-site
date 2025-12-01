# Revocation Lists Manager and Publisher Specifications
The following are considered necessary capabilities of the Revocation Lists components for the mDL Use Case:

|Specification |Optionality |Description and Reference |
|---|---|---|
| :open_file_folder: **Revocation List Management** | | |
| Set up (create) a status list or identifier list | Mandatory | The system sets up a new status list or identifier list to support the mDLs revocation functionality. |
| Register Request handling (Associate an mDL with a pointer in the status list) | Mandatory | When an mDL is issued, the system must receive and process requests to register its unique identifier (e.g., a serial number, a unique hash) with a status list pointer. Upon issuance, the mDL's status is initialised to "valid" (or equivalent, e.g. a "0" bit in a bitstring) to the corresponding position in the status list. This method applies only for the status list. |
| Revocation Request handling | Mandatory | The system must receive and process requests via API calls to revoke an mDL by the Authentic Source or related component. Upon revocation, the system updates the status of the specific mDL in its internal database (e.g. changing a bit from 0 to 1, or marking an entry as revoked) or adds the identifier to the identifier list. |
| Manual mDL Revocation | Optional | The system shall allow administrative controls to manually change an mDL's status in the status list or add the identifier in the identifier list. The component offers an endpoint for the mDL revocation that needs to be modified accordingly to support this feature. |
| mDL Revocation by mDL subjects | Optional | The system shall allow the mDL holder to revoke their own mDL by presenting the mDL to be revoked as authentication mechanism. |
| Search mDL | Excluded / not supported | The system does not store mDL claims (data elements) and therefore cannot support the search and view mDL status operations. This is responsibility of the Authentic Source. |
| View mDL Status | Excluded / not supported | As above |
| Audit Logging | Mandatory | The system shall keep logging of all status changes, API requester and when they were initiated. |
| :open_file_folder: **Revocation List Generation/Publication** | | |
| Generate revocation list | Mandatory | Periodically or upon changes, the system aggregates the status of all issued mDLs into the status list format (e.g., a bitstring) or identifier list. |
| Encode MSO revocation list as status list | Mandatory | According to ISO 18013-5 2<sup>nd</sup> version section 9.1.2.6: "Two mechanisms can be used to encode the revocation information: as an identifier list or as a status list" |
| Encode MSO revocation list as identifier list | Mandatory | As above |
| COSE_Sign1 structure | Mandatory | According to ISO 18013-5 2<sup>nd</sup> version section 9.1.2.6 "The MSO revocation list is a COSE_Sign1 structure that indicates whether a particular MSO is revoked or not." |
| Cryptographic Signing | Mandatory | The generated revocation list must be digitally signed by the mDL Issuing Authority to ensure its authenticity and integrity for Verifiers. |
| Revocation List Publication | Mandatory | The signed revocation list is published to a publicly accessible endpoint at the URL referenced within the issued mDLs |
| Version/History Management | Mandatory | The system manages different versions of the revocation list, ensuring that Verifiers can access the correct, up-to-date list. The component keeps a history of changes. |
| Revocation List monitoring | Optional | Monitoring to ensure revocation lists are being published successfully and are accessible. |
| Error Reporting | Optional | Alerts for failures in updates, list generation, or publication of the revocation list. |
