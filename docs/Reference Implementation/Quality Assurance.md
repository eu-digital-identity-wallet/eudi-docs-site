# Code Quality Assurance Overview

## Table of Contents
1. [Purpose and Approach](#-purpose-and-approach)
2. [Test Levels and Types](#-test-levels-and-types)
3. [Test Management and Tools ](#-test-management-and-tools)
4. [Test Environments](#-test-environments)
5. [Reporting](#-reporting)

## 🎯 Purpose and Approach

This page describes the **Code Quality Assurance (QA) activities** for the **EUDI Wallet project**, providing transparency on testing practices, environments, and outcomes across all releases.

The QA process ensures that the EUDI Wallet meets functional, non-functional, performance, and security requirements on both **Android** and **iOS** platforms. Each release is planned and validated according to the agreed [roadmap milestones](https://github.com/orgs/eu-digital-identity-wallet/projects/24), ensuring traceability between development deliverables and test execution.

Releases undergo full verification and validation through a combination of **manual and automated testing**, with QA activities integrated across all development phases to detect and prevent defects early.

All testing artefacts are managed in GitHub under:  
[eu-digital-identity-wallet/eudi-doc-testing-application-internal](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application-internal)


## 🧩 Test Levels and Types

Testing is organised across multiple levels to validate functionality, performance, and security, ensuring comprehensive coverage throughout the development lifecycle

| Test Type | Objective | Frequency |
| -------- | ------- | -------- | 
| [Unit](#unit-testing) | Component-level verification | Continuous | 
| [Functional](#functional-testing) | End-to-end behaviour validation | Per release |
| [Security](#security-testing) | Confidentiality, integrity, and compliance | Ad hoc per major release |
| [Performance](#performance-testing) | Response time, and App Stability, CPU and Memory Usage | Ad hoc per major release | 
| [Regression](#regression-testing) | Automated End to end behaviour validation | Continuous | 


### Unit Testing

- **Objectives:** Unit testing verifies the correctness of individual software components and is the first quality gate in the CI pipeline.
- **Requirements:** The requirements of the Unit testing can be found [here]().
- **Scope:** Unit testing supports early defect detection and continuous integration by ensuring each new change maintains baseline quality.
- **Tools:** [Unit testing tools](#-test-management-and-tools).

---
### Functional Testing


- **Objectives:** Functional and end-to-end (E2E) testing ensures that each release behaves as expected according to defined epics and user stories.
- **Requirements:** The Functional Requirements can be found [here](https://github.com/eu-digital-identity-wallet/eudi-wallet-product-roadmap/blob/main/EUDI%20Wallet%20Reference%20Implementation%20-%20Feature%20Map.md).
- **Scecifications:** Functional Requirements, UI, and usability aspects of the mobile application based and mapped to the respective user stories.
- **Tools:** [Functional testing tools](#-test-management-and-tools).

Functional testing results are published automatically through GitHub Actions and are visible in the reports.

---

### Security Testing

- **Objectives:** Security testing ensures the continuous security, integrity, and resilience of the EUDI Wallet applications throughout their lifecycle. By integrating automated and manual security testing within a Secure Software Development Life Cycle (SDLC) and aligning with OWASP MASVS and MASTG standards, the framework enables early detection and remediation of vulnerabilities. It combines code analysis, penetration testing, and vulnerability management using tools such as SonarQube, OWASP Dependency-Check, and DefectDojo to maintain compliance with recognized security standards and safeguard user trust in the EUDI Wallet ecosystem.
- **Requirements:** The Security Requirements can be found [here](https://github.com/eu-digital-identity-wallet/eudi-doc-reference-implementation-architecture/blob/main/security-requirements.md).
- **Specifications:** The security test specifications can be found [here]().
- **Tools:** [Security testing tools](#-test-management-and-tools).

---

### Performance Testing

- **Objectives:** Performance tests validate responsiveness, stability, and resource usage under expected conditions. Measurement of resource consumption and response time per feature in order to confirm that the application remains stable and responsive under normal operating conditions.
- **Requirements:** WIP
- **Specifications**: The performance test specifications can be found [here]()
- **Tools:** [Performance testing tools](#-test-management-and-tools).

## 💼 Test Management and Tools

Testing activities are planned and tracked in **GitHub Issues** and **Projects.**

The following table summarises the key tools utilised in the applicable test types:
| Test Type | Tools | 
| -------- | ------- | 
| Unit |  _SonarCloud_ |
| Functional |  _Manual_, _Serenity BDD_ for structured reporting and visual coverage, _Android Studio_ for Android wallet application testing |
| Security |  _OWASP MASVS/MASTG_ for mobile security verification <br> _OWASP Dependency-Check_ for third-party library analysis <br> _SQLCipher_ and _Android Keystore_ for data protection <br> _Burp Suite_ and _MobSF_ for dynamic testing and static analysis|
| Performance | CI / Device tests |
| Regression | CI pipelines |

Further details about the Test Management and the Testing tools can be found [here](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application-internal/blob/main/README.md).

## 💻 Test Environments
All testing activities are performed within two controlled environments that support continuous integration, verification, and release readiness activities for the EUDI Wallet:
- Development (DEV)
- Production (PROD)


| Component | DEV | PROD |
| -------- | ------- | ------- | 
| EUDI Wallet App (Android) |TBC |TBC|
| EUDI Wallet App (iOS) |TBC |TBC|
| Issuer | [DEV Issuer](https://dev.issuer.eudiw.dev/credential_offer_choice)|[PROD Issuer](https://issuer.eudiw.dev/credential_offer_choice)|
| Web Verifier |[DEV version](https://dev.verifier.eudiw.dev/home) |[PROD version](https://verifier.eudiw.dev/home)|



## 📊 Reporting

The QA process is continuously refined based on findings, coverage metrics, and stakeholder feedback.

**Reporting**:

- Serenity-generated reports summarising test execution and coverage.
- Per-release links to reports and workflows (see below).

**Metrics monitored**:

- Pass/fail ratio per story and epic.
- Test coverage percentage.

### Release Test Reports

Each release includes detailed artefacts and automated reports accessible via GitHub Actions.

| Release | Report Links | Status |
| --- | --- | --- |
| 2025.07.28 - Demo | GitHub Action Report | ✅ Released |
| 2025.09.30 - xxx | GitHub Action Report | 🔄 In progress |
| 2025.12.xx - xxx | (to be added) | ⏳ Planned |

Older releases remain available in the /reports directory of the testing repository.

At present, reports cover manual testing, while automation and performance reporting are being implemented.
