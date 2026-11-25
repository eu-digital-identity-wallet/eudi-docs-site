# Code Quality Assurance Overview

Below you can find all **Code Quality Assurance (QA) activities** for the **EUDI Wallet project** which ensure that the EUDI Wallet meets functional, non-functional, performance and security requirements on both **Android** and **iOS** platforms.

Each release is planned and validated according to the agreed [roadmap milestones](https://github.com/orgs/eu-digital-identity-wallet/projects/24){:target="_blank"}, ensuring traceability between development deliverables and test execution.

Releases undergo full verification and validation through a combination of **manual and automated testing**, with QA activities integrated across all development phases to detect and prevent defects early.

All testing artefacts are managed in GitHub under: 
[eu-digital-identity-wallet/eudi-doc-testing-application](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application){:target="_blank"}.

## Code Quality Controls

SonarCloud works on a set of code quality checks and analyses code for multiple quality dimensions, across all stacks (Swift, Kotlin, Java, Python). The checks conducted can be further grouped into the following categories:

- Security (protecting software from threats, attacks and unauthorised access):
    - **Security Vulnerabilities**: Flaws in code or configuration that attackers can exploit to compromise the system. Through SonarCloud, the following security vulnerabilities have been identified: SQL Injection, Deserialisation, and Command Injection vulnerabilities.
    - **Security Hotspots based on OWASP Top 10 / CWE Mappings**: [OWASP Top 10](https://owasp.org/www-project-top-ten/){:target="_blank"} refers to a list of the 10 most critical web application security risks. [CWE (Common Weakness Enumeration)](https://cwe.mitre.org/top25/){:target="_blank"} refers to a standardised catalogue of software weaknesses. Vulnerabilities and hotspots can be mapped to these categories for classification.
    - **CodeQL**: Performs semantic source code analysis to identify potential security vulnerabilities, such as injection flaws, insecure data handling and other coding weaknesses. It is integrated into the CI/CD workflow to support automated security checks during development and pull request reviews.
    - **Dependency Management with Dependabot**: Monitors project dependencies for known vulnerabilities and generates alerts when affected versions are identified. It also proposes dependency updates to help maintain secure and up-to-date third-party libraries.
    - **GitHub Secret Protection**: Detects exposed credentials, API keys, access tokens and other sensitive information in repositories. It helps prevent accidental disclosure of secrets through repository scanning and, where enabled, push protection.

- Maintainability (measures how easily code can be understood, modified and extended):
    - **Code Smells**: Patterns in code that indicate potential design or implementation issues. They are warnings that indicate potential bad coding practices. The corresponding list that is checked per type of repository is the [default list](https://www.sonarsource.com/resources/library/code-smells/){:target="_blank"} provided by SonarCloud.
    - **Cognitive Complexity**: A metric indicating how difficult code is to understand. It increases with nested logic, branching and poor readability. Details of the corresponding metric can be found [here](https://www.sonarsource.com/resources/cognitive-complexity/){:target="_blank"}.
    - **Duplications**: Repeated blocks of code. High duplication leads to more effort in applying changes and increases the risk of inconsistency.

- Reliability (reflects how consistently software functions without failures):
    - **Bugs**: Using static code analysis, it detects actual bugs that can cause runtime errors or incorrect behaviour.
    - **Unit Test Coverage**: A measure of how much of the code is exercised by automated tests. Higher coverage generally increases confidence in reliability but does not guarantee the absence of bugs.

## Test Types

Testing is organised across multiple levels to validate functionality, performance and security, ensuring comprehensive coverage throughout the development lifecycle:

| Test Type | Objective | Frequency |
| --- | --- | --- | 
| [Unit](#unit-testing) | Component-level verification | Continuous | 
| [Functional](#functional-testing) | End-to-end behaviour validation | Per release |
| [Security](#security-testing) | Confidentiality, integrity and compliance | Per release |
| [Performance](#performance-testing) | Response time, app stability, CPU and memory usage | Per release | 


### Unit Testing

- **Objectives:** Unit testing verifies the correctness of individual software components and is the first quality gate in the continuous integration (CI) pipeline. Unit testing supports early defect detection and continuous integration by ensuring each new change maintains baseline quality.
- **Usage:** Unit testing is included in each repository next to the actual code development. Tests can be executed based on the information and instructions provided in the corresponding readme files.
- **Tools:** [Unit Testing Tools](#test-tools).

---

### Functional Testing


- **Objectives:** Functional and end-to-end (E2E) testing ensures that each release behaves as expected according to defined epics and user stories.
- **Requirements:** The Functional Requirements are presented in the [Feature Map](./feature-map.md).
- **Test Specifications:** The Functional Testing Specifications can be found here:
    - [Manual Testing](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application/tree/main/src/test/resources/features){:target="_blank"}.
    - [Automated Testing](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application-internal/tree/main){:target="_blank"}.
- **Usage:** Functional testing is currently performed on the main mobile application repositories ([Android UI mobile app](https://github.com/eu-digital-identity-wallet/eudi-app-android-wallet-ui){:target="_blank"} and [iOS UI mobile app](https://github.com/eu-digital-identity-wallet/eudi-app-ios-wallet-ui){:target="_blank"}) through which the functionality of the whole application is tested. Specific information on how to execute the tests through GitHub and download the corresponding results are included in the [main testing repository readme file](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application/blob/main/README.md#running-tests-via-github-actions-and-device-farm-browserstack){:target="_blank"}.
- **Tools:** [Functional Testing Tools](#test-tools).

---

### Security Testing

- **Objectives:** Security testing aims to identify, assess and validate security vulnerabilities throughout the EUDI Wallet application lifecycle. It combines automated security checks integrated into the CI/CD pipeline with static and dynamic application security testing. The approach covers source code, compiled mobile application packages and runtime behaviour, helping identify weaknesses in application logic, data handling, configurations, dependencies and network communications. Security assessments are guided by the OWASP Mobile Application Security Verification Standard (MASVS) and Mobile Application Security Testing Guide (MASTG).
- **Requirements and Test Specifications:** The [Security Requirements and Security Test Specifications](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application/blob/main/doc/security/EUDI-Wallet-NiScy_Security_Requirements_and_Controls_Documentation.md){:target="_blank"} of the EUDI Wallet.
- **Usage:** Security testing is applied across the relevant application repositories, based on the specific programming language and technology used. Automated source code analysis, dependency monitoring and secret detection are incorporated into the CI/CD workflow. Static analysis of mobile application packages is performed using MobSF to identify insecure configurations, permissions, exposed information and other mobile-specific security weaknesses. Dynamic testing is performed using Frida to inspect application behaviour at runtime and Burp Suite to intercept and analyse network traffic, including API communications, authentication and session management. More information can be found in the corresponding readme files.
- **Tools:** [Security Testing Tools](#test-tools).

---

### Performance Testing

- **Objectives:** Tests are conducted to evaluate the performance of the EUDI Wallet application under average user load across various mobile devices. This testing focuses on central processing unit (CPU) and memory usage, as well as network activity during common scenarios.
- **Requirements:** The [Performance Requirements](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application/blob/main/doc/performance/performance_requirements.md){:target="_blank"} against which the tests are executed.
- **Test Specifications**: The [Performance Test Specifications](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application/blob/main/doc/performance/performance_specifications.md){:target="_blank"} result from relevant default metrics.
- **Usage:** Performance testing is executed on the main mobile application repositories [Android UI mobile app](https://github.com/eu-digital-identity-wallet/eudi-app-android-wallet-ui){:target="_blank"} and [iOS UI mobile app](https://github.com/eu-digital-identity-wallet/eudi-app-ios-wallet-ui){:target="_blank"}) and covers the whole application. It can be executed using the corresponding functional tests in multiple devices.
- **Tools:** [Performance Testing Tools](#test-tools).

## Test Tools

The following table summarises the tools used in the applicable test types:

| Test Type | Tools | 
| --- | --- | 
| Unit | SonarCloud |
| Functional | **Manual Testing** <br> - Supported by Serenity BDD for structured reporting and visual coverage <br> **Automation** <br> - **Appium** (for mobile automation on Android and iOS) <br> - **Java** (test scripting language) <br> - **JUnit** (test framework) <br> **Other Tools** <br> - **IntelliJ IDEA** (development and execution environment) <br> - **Maven** (dependency and build management) <br> - **Appium Inspector** (for element inspection and locator validation) <br> - **Xcode** (for building and exporting iOS .ipa files) <br> - **Android packages**: .apk packages retrieved manually from Firebase for testing). |
| Security | - **CodeQL**: Semantic source code analysis (SAST) to identify potential security vulnerabilities. <br> - **SonarCloud**: Static code analysis for security vulnerabilities and security hotspots. <br> - **GitHub Dependabot**: Monitoring of third-party dependencies for known vulnerabilities and dependency update recommendations. <br> - **GitHub Secret Protection**: Detection of exposed credentials, API keys and tokens, with push protection where enabled. <br> - **MobSF (Mobile Security Framework)**: Static analysis of Android and iOS application packages to identify insecure configurations, permissions, cryptographic weaknesses and exposed sensitive information. <br> - **Frida**: Dynamic instrumentation of running applications to inspect runtime behaviour, method calls and security mechanisms. <br> - **Burp Suite**: Interception and analysis of HTTP/HTTPS traffic for testing API communications, authentication, session management and network security. <br> - **OWASP MASVS/MASTG**: Mobile application security verification standards and testing guidelines. |
| Performance | Android: Android Studio Profiler and App Inspection and iOS: Xcode Instruments for performance monitoring, memory usage and CPU/network profiling |


## Reporting

Each release is accompanied by serenity-generated reports summarising test execution results and coverage.

### Release Test Reports

| Release | Test Types | Report Links | Status |
| --- | --- | --- | --- |
| 2025.07.28 - Demo | Functional <br/> Security <br/> Performance | - [Functional test results](https://docs.eudi.dev/testing/2025_q2/){:target="_blank"} <br/> - [Security test results](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application/raw/refs/heads/milestone/2025.Q2/doc/security/EUDI-Wallet-NiScy_Security%20Testing%20Results-Version_2025.07.28-Demo.xlsx){:target="_blank"} <br/> - [Performance test results](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application/blob/milestone/2025.Q2/doc/performance/performance_test_results.md){:target="_blank"}[^1] | ✅ Released |
| 2025.10.31 - Demo | Functional | - [Functional test results](https://docs.eudi.dev/testing/2025_q3/){:target="_blank"} | ✅ Released |
| 2025.12.34 - Demo | Functional | - [Functional test results](https://docs.eudi.dev/testing/2025_q4/){:target="_blank"} | ✅ Released |
| 2026.05.37 - Demo | Functional <br/> Performance | - [Functional test results](https://docs.eudi.dev/testing/2026_q1/){:target="_blank"} <br/> - [Performance test results](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application/blob/milestone/2026.Q1/doc/performance/performance_test_results.md){:target="_blank"}| ✅ Released |
| 2026.07.39 - Demo | Functional | - [Functional test results](https://docs.eudi.dev/testing/2026_q2/){:target="_blank"} | ✅ Released |
| 2026.08.41 - Demo | Functional | - [Functional test results](https://docs.eudi.dev/testing/2026_q3a/){:target="_blank"} | ✅ Released |
| 2026.10.43 - Demo | Functional | - [Functional test results](https://docs.eudi.dev/testing/2026_q3/){:target="_blank"} | ✅ Released |

Older releases remain available in the reports directory of the [testing repository](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application-internal/actions){:target="_blank"}.

[^1] Performance testing is only performed every time significant changes occur in the applications that might impact responsiveness
