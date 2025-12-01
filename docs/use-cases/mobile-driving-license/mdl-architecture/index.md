# High-level Architecture of the mDL Target Solution

The design options for the mDL Use Case target solution are implemented by the software components shown in the following figure. These components are organised according to the roles defined in Chapter 3 of the Architecture and Reference Framework [ARF]. 

![img.png](mdl-logical-components.png)

The components are categorised as follows, based on their provider. 

- Green components represent software libraries and modules provided by the Commission as part of the EUDI Wallet Reference Implementation. This implementation follows a modular architecture composed of business agnostic, reusable components. 
- White components are prerequisites required for the target solution to function. These are provided by organisations or entities acting as service providers, such as mDL Issuers and mDL Verifiers.
- Grey components are part of the services provided by the Commission's eIDAS Dashboard. 
