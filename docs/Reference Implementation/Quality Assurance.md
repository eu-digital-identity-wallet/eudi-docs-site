# Code Quality Assurance Overview

## Purpose and Approach

This page describes the **Code Quality Assurance (QA) activities** for the **EUDI Wallet project**, providing transparency on testing practices, environments, and outcomes across all releases.

The QA process ensures that the EUDI Wallet meets functional, non-functional, performance, and security requirements on both **Android** and **iOS** platforms. Each release is planned and validated according to the agreed [roadmap milestones](https://github.com/orgs/eu-digital-identity-wallet/projects/24), ensuring traceability between development deliverables and test execution.

Releases undergo full verification and validation through a combination of **manual and automated testing**, with QA activities integrated across all development phases to detect and prevent defects early.

All testing artefacts are managed in GitHub under:  
[eu-digital-identity-wallet/eudi-doc-testing-application-internal](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application-internal)

## Test Scope and Test Cases

The scope of testing covers all features and functionalities defined for each release of the **EUDI Wallet** application.

#### Structure of Test Cases &lt;Can be a link&gt;

Test cases are defined, version-controlled, and executed within the project's dedicated testing repository:  
[eu-digital-identity-wallet/eudi-doc-testing-application-internal](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application-internal).

The repository follows a hierarchical structure:

- **Features:**
    - android/ and ios/ folders separate platform-specific tests.
    - Under each OS, **epic folders** contain **user story subfolders**.
    - Each user story folder includes .feature files written in **Gherkin syntax**, describing test scenarios and acceptance criteria.
- Test cases are tagged with:
    - Execution status (@passed, @failed, @pending)
    - Type (manual or automated)
    - Direct links to related GitHub issues and user stories.

#### Traceability and Coverage &lt;Can be a link&gt;

Every test case is linked to:

- A **user story** in GitHub (functional or non-functional requirement).
- A **Serenity Report entry**, showing detailed execution steps, screenshots (for UI tests), and results.

## Test Levels and Types

Testing is organised across multiple levels to validate functionality, performance, and security, ensuring comprehensive coverage throughout the development lifecycle

| Test Type | Objective | Frequency | Tooling |
| -------- | ------- | -------- | ------- |
| [**Unit**](#_Unit_Testing) | Component-level verification | Continuous | SonarCloud |
| [Functional](#_Functional_Testing) | End-to-end behaviour validation | Per release | Manual, Serenity BDD |
| [Security](#_Security_Testing) | Confidentiality, integrity, and compliance | Ad hoc per major release | OWASP MASVS/MASTG |
| [Performance](#_Performance_Testing) | Response time, load, and scalability validation. | Ad hoc per major release | CI / Device tests |
| [Regression](#_Regression_Testing) | Frequent automated validation of prior functionality. | Continuous | CI pipelines |

### Unit Testing

Unit testing verifies the correctness of individual software components and is the first quality gate in the CI pipeline.

Unit tests run automatically on every commit through GitHub Actions.

Unit testing supports early defect detection and continuous integration by ensuring each new change maintains baseline quality.

### Functional Testing

Functional and end-to-end (E2E) testing ensures that each release behaves as expected according to defined epics and user stories.

The Functional Requirements can be found at &lt;link&gt;

- **Scope:** Manual and automated tests (written in Gherkin) executed on both Android and iOS.
- **Coverage:** UI, and usability aspects of the mobile application mapped to user stories.
- **Traceability:** All test artefacts are linked to GitHub issues.
- **Tools:** Serenity BDD for structured reports and coverage indicators.

Functional testing results are published automatically through GitHub Actions and visible in the reports.

### Performance Testing

Performance tests validate responsiveness, stability, and resource usage under expected conditions.

- **Scope**: CPU, memory, and network activity under realistic workloads.
- **Test Devices:** Android POCO X5 Pro 5G and iPhone 14 Plus.
- **Approach**: Measurement of resource consumption and response time per feature.
- **Reporting**: Results integrated into GitHub CI pipelines; full report available in  
    _&lt; link&gt;_

Performance testing outcomes confirm that the application remains stable and responsive under normal operating conditions.

### Security Testing

The Security Requirements can be found at &lt;link&gt;

- .

Full security observations are recorded in &lt;link&gt;  

#### OWASP Mobile Application Security Verification Standard (MASVS)

- Why is this important to be done
- Process - high level: e.g., static analysis, pen test
- Tools: SAST - Sonar , Dependency Check , Git Leaks , Legitify, Defect Dojo (central)

##### Mobile Security Testing based on MSTG

- How is this connected with MASVS
- Why is it essential to be done
- Reference Security Requirements and Controls (Antonis)

#### Vulnerability Management

- Why is this important to be done
- Process - high level

### Regression Testing

Regression testing ensures that previous functionality remains stable after new features are added. Automated regression tests are planned to be part of the CI workflow.

## Test Environments

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

## Test Management and Tools

## \--> we could skip from the overview since we have the tools in the test levels and add a link to what we have in github read

Testing activities are planned and tracked in **GitHub Issues** and **Projects**, with execution and reporting automated through **GitHub Actions** and **Serenity Reports**.

**Main tools and frameworks:**

- _Serenity BDD_ for structured reporting and visual coverage.
- _OWASP Dependency-Check_ for third-party library analysis.
- _OWASP MASVS/MASTG_ for mobile security verification.
- _SQLCipher_ and _Android Keystore_ for data protection.
- _Burp Suite_ and _MobSF_ for dynamic testing and static analysis.

Each epic and user story in GitHub is linked to corresponding test artefacts, ensuring **full traceability** from requirement to validation outcome.

## Reporting

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
