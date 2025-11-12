# mDL Verifier getting started

This guide provides the technical framework, requirements and detailed instructions necessary for implementing Mobile Driving Licence (mDL) verification solutions within the European Digital Identity (EUDI) Wallet ecosystem.

The foundation for this implementation is the Architecture and Reference Framework (ARF), which is intended to create uniform conditions for the implementation of the eIDAS 2 Regulation. The provided reference implementation supports both proximity and remote mDL verification scenarios, acting as Relying Party Instances that can verify mDL attestations presented by EUDI Wallet Units.

This guide details the steps required to configure and operate an mDL Verifier (Relying Party) using the reference implementation to ensure interoperability, security, and privacy across the European Union.

## Who is this guide for

This guide is primarily targeted at technical professionals responsible for designing and building mDL verification solutions. This includes developers, solution architects, and engineers from both public and private sector organizations implementing Relying Party services that need to verify mobile Driving Licences.

The target audience could also expand to other stakeholders who require a deep technical understanding of the mDL verification solution within the EUDI Wallet ecosystem. Specifically, anyone wishing to understand how the requirements for mDL verification align with real-world mDL use cases will find this information relevant.

## How to use this guide

This guide is structured to mirror the implementers' hub sections providing similar navigation. The main body of this guide focuses on the lifecycle and technical implementation details relevant to Mobile Driving Licence (mDL) verification, by including:

- the foundational technical and organizational steps required before beginning implementation
- the detailed implementation guide on how to verify an mDL presented by a Wallet Unit
- proximity and remote verification flow implementations
- where to get the reference implementation libraries and SDKs
- tools and procedures necessary for conformance testing and validation of the implemented mDL Verifier solution

## Links to essential resources

To ensure seamless operation and mutual recognition across the Union, all compliant mDL verification solutions implemented using this guide SHALL support the [mDL Verifier](./mDL Reader Specs.md) and [mDL Verifier](./mDL Remote Verifier Specs.md)  core technical specifications.
