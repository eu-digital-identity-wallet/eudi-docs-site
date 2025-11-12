# mDL Issuer Getting Started
This guide provides the technical framework, requirements and detailed instructions necessary for implementing national Mobile Driving Licence (mDL) issuance solutions within the European Digital Identity (EUDI) Wallet ecosystem. 

The foundation for this implementation is the Architecture and Reference Framework (ARF), which is intended to create uniform conditions for the implementation of the eIDAS 2 Regulation. The provided reference implementation acts as the Attestation Issuer (or mDL Issuer), supporting all compliant attestation issuance flows.

This guide details the steps required to configure and operate an mDL Issuer (Attestation Provider) using the reference implementation to ensure interoperability, security, and privacy across the European Union.


## Who is this guide for
This guide is primarily targeted at technical professionals responsible for designing and building national mDL issuance solutions. This includes developers, solution architects, and engineers from Member State organizations or mandated bodies undertaking the role of a PuB-EAA Provider (Electronic attestation of attributes issued by or on behalf of a public sector body responsible for an authentic source) or an Attestation Provider, since the mDL may be issued in this capacity.

The target audience could also expand to other stakeholders who require a deep technical understanding of the mDL solution within the EUDI Wallet ecosystem. Specifically, anyone wishing to understand how the requirements for mDL issuance align with real-world mDL use cases will find this information relevant.

## How to use this guide
This guide is structured to mirror the implementers' hub sections providing similar navigation. The main body of this guide focuses on the lifecycle and technical implementation details relevant to the Mobile Driving Licence (mDL) Issuance, by including 

- the foundational technical and organizational steps required before beginning implementation
- the detail implementation guide on how to issue an mDL to a Wallet Unit
- the mechanisms and how to revoke an mDL
- the process of registering and notifying your entity as an mDL Issuer
- where to get the reference implementation libraries and SDKs 
- tools and procedures necessary for conformance testing and validation of the implemented mDL Issuer solution

## Links to essential resources
To ensure seamless operation and mutual recognition across the Union, all compliant mDL issuance solutions implemented using this guide SHALL support the [mDL Issuance](./mDL Issuer Specs.md) and [mDL Revocation](./mDL Revocation Specs.md) core technical specifications.

