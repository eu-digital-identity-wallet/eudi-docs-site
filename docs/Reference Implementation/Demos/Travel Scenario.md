# Travel Scenario

The Reference Implementation includes the travel use case implementation to showcase the utilization of the EUDI Wallet in a ‘Travel’ scenario, where the EUDI Wallet is used for several purposes, such as presenting attestations (remotely and in proximity) as well as digitally signing documents.

## Use Case

1. **Jane is preparing for her next trip** with the help of her EUDI Wallet. Jane starts by securing her essential travel documents. She issues her Digital Identity, Mobile Driving License, and Photo-ID directly into her EUDI Wallet. Each document is safely stored, ready to be accessed whenever she needs them.
2. **Booking**: With her documents in place, Jane navigates to the travel booking portal. Here, she effortlessly presents her Digital ID and other necessary documents requested by the booking portal from her EUDI Wallet to book her car rental and hotel.
3. **Renting a car**: When it comes to renting a car, Jane is redirected to a remote signing portal to conclude the rental process. Using her EUDI Wallet, she digitally signs the car rental contract, finalizing her arrangements with security and ease.
4. **Hotel check-in**: Upon arrival at her hotel, Jane approaches the check-in counter. She presents her Digital ID and Photo-ID from her EUDI Wallet to the hotel’s proximity reader. The process is quick and secure, allowing her to start relaxing in her room in no time.

[Travel Scenario](https://github.com/eu-digital-identity-wallet/eudi-doc-developers-hub-site/blob/main/docs/assets/EUDI%20Wallet_Travel%20Demo.mp4)


## Test online or run locally

1. Download the [EUDI Wallet Reference Implementation application](../../../Test/Wallet Application/Introduction/).
2. Access the [demo booking service](https://dev.booking.demo.eudiw.dev){:target="_blank"}.

## User Journey

1. **User is preparing for a trip with the help of her EUDI Wallet.**
	1. User issues the necessary identification documents, i.e. Digital Identity, Mobile Driving License and Photo-ID
	2. User navigates to the issuance service and follows the process to complete the issuance of the needed documents
	3. Identification documents are successfully issued to the EUDI Wallet

2. **User makes a reservation**
	1. User navigates to the booking service
	2. User fills in the required data for the booking reservation:
		1. Number of Guests
		2. Number of Rooms
		3. Check In/Out dates
		4. Option to include ‘car rental’ in the reservation
	3. User is requested to present the required attestations from the EUDI Wallet (note: depending on the scenario, the user scans the rendered QR-code or selects the deep-link in cross-device or same-device flows respectively)
	4. User receives the presentation request from the booking service and consents to the presentation of the requested attestations
3. **User reviews reservation details**
	1. User can view a summary of the reservation details, based on the previously added data as well as the attestations shared from the EUDI Wallet
	2. User selects to add the reservation confirmation to the EUDI Wallet
		1. User scans the rendered QR-code
		2. Following the issuance process in the EUDI Wallet, the ‘reservation confirmation’ is added to the EUDI Wallet
4. **User selects to sign the ‘car rental contract’**
	1. User downloads a template car rental contract from the corresponding link
	2. User selects to sign the car rental contract and is navigated to the external trust service, which prompts the user to remotely sign the uploaded car rental contract
5. **User checks-in at the hotel:**
	1. User approaches the reader at the hotel check-in (note: the available proximity verifier can be utilized to mock the ‘reader’ service at a hotel)
	2. User presents the QR-code from the EUDI Wallet, which is scanned from the proximity verifier
	3. User receives the presentation request for the ‘Photo-ID’ and the ‘Reservation’ attestations
	4. User consents to present the attestations, which are successfully received by the proximity verifier
	
You can also run the booking service locally. [Instructions for this available in GitHub](https://github.com/eu-digital-identity-wallet/eudi-web-booking-service-demo){:target="_blank"}.
