# Code Quality Assurance Overview

## Table of Contents
1. [Purpose and Approach](#-purpose-and-approach)
2. [Test Levels and Types](#-test-levels-and-types)
3. [Test Environments](#-test-environments)
4. [Test Management and Tools ](#-test-management-and-tools)
5. [Reporting](#-reporting)

## 🎯 Purpose and Approach

This page describes the **Code Quality Assurance (QA) activities** for the **EUDI Wallet project**, providing transparency on testing practices, environments, and outcomes across all releases.

The QA process ensures that the EUDI Wallet meets functional, non-functional, performance, and security requirements on both **Android** and **iOS** platforms. Each release is planned and validated according to the agreed [roadmap milestones](https://github.com/orgs/eu-digital-identity-wallet/projects/24), ensuring traceability between development deliverables and test execution.

Releases undergo full verification and validation through a combination of **manual and automated testing**, with QA activities integrated across all development phases to detect and prevent defects early.

All testing artefacts are managed in GitHub under:  
[eu-digital-identity-wallet/eudi-doc-testing-application-internal](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application-internal)


## 🧩 Test Levels and Types

Testing is organised across multiple levels to validate functionality, performance, and security, ensuring comprehensive coverage throughout the development lifecycle

| Test Type | Objective | Frequency | Tooling |
| -------- | ------- | -------- | ------- |
| [**Unit**](#unit-testing) | Component-level verification | Continuous | SonarCloud |
| [Functional](#functional-testing) | End-to-end behaviour validation | Per release | Manual, Serenity BDD |
| [Security](#security-testing) | Confidentiality, integrity, and compliance | Ad hoc per major release | OWASP MASVS/MASTG |
| [Performance](#performance-testing) | Response time, and App Stability, CPU and Memory Usage | Ad hoc per major release | CI / Device tests |
| [Regression](#regression-testing) | Automated End to end behaviour validation | Continuous | CI pipelines |

### Unit Testing

Unit testing verifies the correctness of individual software components and is the first quality gate in the CI pipeline.

Unit tests run automatically on every commit through GitHub Actions.

Unit testing supports early defect detection and continuous integration by ensuring each new change maintains baseline quality.

---
### Functional Testing

Functional and end-to-end (E2E) testing ensures that each release behaves as expected according to defined epics and user stories.

The Functional Requirements can be found [here](https://github.com/eu-digital-identity-wallet/eudi-wallet-product-roadmap/blob/main/EUDI%20Wallet%20Reference%20Implementation%20-%20Feature%20Map.md).

- **Scope:** Manual and automated tests (written in Gherkin) executed on both Android and iOS.
- **Coverage:** Functional Requirements, UI, and usability aspects of the mobile application based and mapped to the respective user stories.
- **Traceability:** All test artefacts are linked to the respective GitHub issues (User Stories).
- **Tools:** Serenity BDD for structured reports and coverage indicators.

Functional testing results are published automatically through GitHub Actions and are visible in the reports.

---

### Security Testing

Ensuring the security and integrity of the EUDI Wallet applications requires a continuous, lifecycle-wide testing approach. The framework combines **automated verification** within the SDLC (Software Development Life Cycle) with **periodic manual security assessments**, ensuring that vulnerabilities are identified early, while complex logic and implementation flaws are addressed through in-depth manual analysis. The following subsections describe how standardized methodologies, defined security requirements, and integrated tooling work together to maintain assurance and resilience across all stages of the EUDI Wallet's lifecycle

#### OWASP Mobile Application Security Verification Standard (MASVS)

The **OWASP Mobile Application Security Verification Standard (MASVS)** defines a structured set of security requirements that serve as the foundation for the secure design, development, and verification of mobile applications.

Alignment with the MASVS ensures that EUDI Wallet applications consistently meets recognized security standards, thereby reducing the likelihood of vulnerabilities.

A multi-layered verification process is applied, combining both manual and automated techniques to ensure depth and coverage:

- **Manual Source Code Review**: Targeted reviews of the application's source code to identify logic flaws, insecure data handling, cryptographic weaknesses, and other vulnerabilities that may not be identified through automation;
- **Dynamic Testing and Penetration Testing**: The compiled application is analysed in a runtime environment to validate its behaviour, data flow, and communication security;

#### Mobile Security Testing based on MΑSTG

The **Security Requirements and Controls** defined by the relevant protocols and specifications (e.g., OpenID4VC, OpenID4VP, ISO/IEC 18013-5) are identified and documented as part of the secure design process. These requirements establish the baseline for the protection mechanisms implemented within the EUDI Wallet application, ensuring alignment with recognized standards and best practices.

Verification of the security requirements is conducted through testing activities based on the Mobile Application Security Testing Guide (MASTG). Each defined control is validated using the corresponding MASTG test cases to confirm that the implementation effectively enforces the intended security objectives.

The Security Requirements can be found at &lt;link&gt;

The **OWASP Mobile Application Security Testing Guide (MASTG)** complements MASVS by providing the practical techniques and test cases used to verify each MASVS requirement.

While MASVS defines "_what"_ must be secure", MASTG defines "_how"_ to test and validate it through structured, and repeatable techniques.

Mobile security testing activities are guided by MASTG principles and are structured to address both MASVS verification requirements and organization-specific security objectives. This approach ensures that each test confirms compliance with recognized industry standards while also validating that the EUDI Wallet application satisfies unique technical and business security needs.

MASTG-based testing establishes a consistent and evidence-driven process that enables the identification of vulnerabilities and maintains continuous assurance throughout the EUDI Wallet application's lifecycle.

#### Secure SDLC (Software Development Life Cycle)

An effective **Secure SDLC process** is essential for maintaining the integrity and resilience of the EUDI Wallet applications.

Through this process, vulnerabilities detected by automated tools and manual testing are identified, prioritized, and remediated. The vulnerability management process integrates both automated tools and centralized coordination to provide complete visibility across the development and security lifecycle:

- **SonarQube (SAST)**: Performs static code analysis to identify potential security and quality issues early in development.
- **OWASP Dependency-Check**: Detects known vulnerabilities in open-source libraries and third-party dependencies.
- **GitLeaks**: Scans repositories for hardcoded secrets or exposed credentials
- **Legitify**: Audits GitHub repositories and organizational configurations to detect potential misconfigurations.
- **DefectDojo**: Serves as a centralized vulnerability management platform, aggregating findings from all tools and assessments for triage, remediation, and reporting.

This integrated approach promotes consistent vulnerability tracking and continuous improvement of the overall security posture.

---

### Performance Testing

Performance tests validate responsiveness, stability, and resource usage under expected conditions.

- **Scope**: CPU, memory, and network activity under realistic workloads.
- **Test Devices:** Android POCO X5 Pro 5G and iPhone 14 Plus.
- **Approach**: Measurement of resource consumption and response time per feature.
- **Reporting**: The Performance Test Report include the Performance Test Strategy, the scope and the results. are provided in a separate report  
    **_&lt; link&gt;_**

Performance testing outcomes confirm that the application remains stable and responsive under normal operating conditions.

---
### Regression Testing

Regression testing is automated and ensures that previous functionality remains stable after new features are added. Automated regression tests are planned to be part of the CI workflow.

## 💻 Test Environments
All testing activities are performed within two controlled environments - Development (DEV) and Production (PROD) - that together support continuous integration, verification, and release readiness activities for the EUDI Wallet.

Main components:

- **EUDI Wallet Application:** Android and iOS test builds configured to interact with DEV services. &lt;links&gt;
- **Issuer Services:**  
    Used for issuing test credentials to the Wallet.  
    Example endpoints:  
    <https://issuer.eudiw.dev/credential_offer_choice>  
    <https://issuer-backend.eudiw.dev/issuer/credentialsOffer/generate>
- **Verifier Portal:**  
    <https://verifier.eudiw.dev/home> - used to validate credentials during presentation flows.

## 💼 Test Management and Tools

Testing activities are planned and tracked in **GitHub Issues** and **Projects.**

Details about the Test Management and the Testing tools can be found [here](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application-internal/blob/main/README.md)

**Main tools and frameworks:**

- _Serenity BDD_ for structured reporting and visual coverage.
- _OWASP Dependency-Check_ for third-party library analysis.
- _OWASP MASVS/MASTG_ for mobile security verification.
- _SQLCipher_ and _Android Keystore_ for data protection.
- _Burp Suite_ and _MobSF_ for dynamic testing and static analysis.

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
