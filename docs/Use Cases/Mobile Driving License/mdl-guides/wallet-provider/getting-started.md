# Wallet Provider Getting Started

This guide provides the technical framework, requirements and detailed instructions necessary for implementing EUDI Wallet Provider solutions within the European Digital Identity (EUDI) Wallet ecosystem to support Mobile Driving Licence (mDL) use cases.

The foundation for this implementation is the Architecture and Reference Framework (ARF), which is intended to create uniform conditions for the implementation of the eIDAS 2 Regulation. The provided reference implementation acts as the Wallet Unit, supporting all compliant mDL flows.

This guide details the steps required to configure and operate a Wallet Unit using the reference implementation to ensure interoperability, security, and privacy across the European Union, with specific focus on supporting the mDL attestation requirements.

## Who is this guide for

This guide is primarily targeted at technical professionals responsible for designing and building EUDI Wallet Provider solutions that support mDL use cases. This includes developers, solution architects, and engineers from Member State organisations or entities mandated or recognized by Member States to provide Wallet Solutions to Users.

The target audience could also expand to other stakeholders who require a deep technical understanding of Wallet Provider responsibilities within the EUDI Wallet ecosystem. 

## How to use this guide

No new requirements are imposed by the mDL use case on EUDI wallets. However, for an overview, this guide is structured to mirror the implementers' hub sections, providing similar navigation. The main body of this guide focuses on the lifecycle and technical implementation details relevant to EUDI Wallet Provider operations for mDL support, by including:

- the foundational technical and organisational steps required before beginning implementation
- mDL support implementation, including attestation issuance and presentation flows
- the process of registering and notifying your entity as a Wallet Provider
- where to get the reference implementation libraries and SDKs
- tools and procedures necessary for conformance testing and validation of the implemented Wallet Solution

## Links to essential resources

To ensure seamless operation and mutual recognition across the Union, all compliant Wallet Providers implemented using this guide SHALL support the [Wallet Provider Specs](./wallet-provider-specs.md).
