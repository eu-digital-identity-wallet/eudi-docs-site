# Code Quality Assurance Overview

## Table of Contents
1. [Purpose and Approach](#-purpose-and-approach)
2. [Test Types](#-test-types)
3. [Test Tools ](#-test-tools)
4. [Reporting](#-reporting)

## 🎯 Purpose and Approach

This page describes the **Code Quality Assurance (QA) activities** for the **EUDI Wallet project**, providing transparency on testing practices, environments, and outcomes across all releases.

The QA process ensures that the EUDI Wallet meets functional, non-functional, performance, and security requirements on both **Android** and **iOS** platforms. Each release is planned and validated according to the agreed [roadmap milestones](https://github.com/orgs/eu-digital-identity-wallet/projects/24), ensuring traceability between development deliverables and test execution.

Releases undergo full verification and validation through a combination of **manual and automated testing**, with QA activities integrated across all development phases to detect and prevent defects early.

All testing artefacts are managed in GitHub under:  
[eu-digital-identity-wallet/eudi-doc-testing-application-internal](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application-internal)


## 🧩 Test Types

Testing is organised across multiple levels to validate functionality, performance, and security, ensuring comprehensive coverage throughout the development lifecycle:

| Test Type | Objective | Frequency |
| -------- | ------- | -------- | 
| [Unit](#unit-testing) | Component-level verification | Continuous | 
| [Functional](#functional-testing) | End-to-end behaviour validation | Per release |
| [Security](#security-testing) | Confidentiality, integrity, and compliance | Per release |
| [Performance](#performance-testing) | Response time, and App Stability, CPU and Memory Usage | Per release | 


### Unit Testing

- **Objectives:** Unit testing verifies the correctness of individual software components and is the first quality gate in the CI pipeline. Unit testing supports early defect detection and continuous integration by ensuring each new change maintains baseline quality.
- **Tools:** [Unit Testing Tools](#-test-management-and-tools).

---

### Functional Testing


- **Objectives:** Functional and end-to-end (E2E) testing ensures that each release behaves as expected according to defined epics and user stories.
- **Requirements:** The Functional Requirements can be found [here](https://github.com/eu-digital-identity-wallet/eudi-wallet-product-roadmap/blob/main/EUDI%20Wallet%20Reference%20Implementation%20-%20Feature%20Map.md).
- **Specifications:** The Functional Testing Specifications can be found here:
    - [Manual Testing](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application-internal/tree/main/src/test/resources/features).
    - [Automated Testing](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application-internal/tree/main/src/test/java/eu/europa/eudi).
- **Tools:** [Functional Testing Tools](#-test-management-and-tools).

---

### Security Testing

- **Objectives:** Security testing ensures the continuous security, integrity, and resilience of the EUDI Wallet applications throughout their lifecycle. By integrating automated and manual security testing within a Secure Software Development Life Cycle (SDLC) and aligning with OWASP MASVS and MASTG standards, the framework enables early detection and remediation of vulnerabilities. It combines code analysis, penetration testing, and vulnerability management using tools such as SonarQube, OWASP Dependency-Check, and DefectDojo to maintain compliance with recognized security standards and safeguard user trust in the EUDI Wallet ecosystem.
- **Requirements:** The Security Requirements can be found [here](https://github.com/eu-digital-identity-wallet/eudi-doc-reference-implementation-architecture/blob/main/security-requirements.md).
- **Specifications:** The Security Test Specifications can be found [here](#).
- **Tools:** [Security Testing Tools](#-test-management-and-tools).

---

### Performance Testing

- **Objectives:** Performance tests measure resource consumption and response time per feature in order to confirm that the application remains stable and responsive under normal operating conditions.
- **Requirements:** The Performance Requirements can be found [here](#).
- **Specifications**: The Performance Test Specifications can be found [here](#)
- **Tools:** [Performance Testing Tools](#-test-management-and-tools).

## 💼 Test Tools

The following table summarises the tools utilised in the applicable test types:
| Test Type | Tools | 
| -------- | ------- | 
| Unit |  _SonarCloud_ |
| Functional |  _Manual_, _Serenity BDD_ for structured reporting and visual coverage, _Android Studio_ for Android wallet application testing |
| Security |  _OWASP MASVS/MASTG_ for mobile security verification <br> _OWASP Dependency-Check_ for third-party library analysis <br> _SQLCipher_ and _Android Keystore_ for data protection <br> _Burp Suite_ and _MobSF_ for dynamic testing and static analysis|
| Performance | CI / Device tests |


## 📊 Reporting

Each release is accompanied with serenity-generated reports summarising test execution results and coverage.

### Release Test Reports

| Release | Report Links | Status |
| --- | --- | --- |
| 2025.07.28 - Demo | GitHub Action Report | ✅ Released |
| 2025.10.31 - Demo | GitHub Action Report | 🔄 In progress |
| 2025.12.xx - xxx | (to be added) | ⏳ Planned |

Older releases remain available in the reports directory of the [testing repository](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application-internal/actions).

