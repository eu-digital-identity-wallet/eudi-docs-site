# High-level Architecture of the mDL Target Solution

The design options form the mDL Use Case target solution are implemented by the software components presented in the following figure. The components of the target solution are presented by role of the EUDI Wallet ecosystem as laid out by chapter 3 of the [ARF]. 

![img.png](mdl-logical-components.png)

The components are distinguished in the following types based on the provider of each component: 

- The components depicted in green colour are the target solution software libraries/components provided by the Commission as part of the EUDI Wallet Reference Implementation which is based on a modular architecture composed of a set of business agnostic, re-usable components. 
- The components depicted in white colour are considered prerequisites to the target solution to function and they are provided by the organizations/entities acting as service providers such as mDL Issuers and mDL Verifiers.
- Finally, the components in grey colour are part of services provided by the Commission’s eIDAS Dashboard. 
