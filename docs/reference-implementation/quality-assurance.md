# Code Quality Assurance Overview

Below you can find all **Code Quality Assurance (QA) activities** for the **EUDI Wallet project**, which ensure that the EUDI Wallet meets functional, non-functional, performance, and security requirements on both **Android** and **iOS** platforms.

Each release is planned and validated according to the agreed [roadmap milestones](https://github.com/orgs/eu-digital-identity-wallet/projects/24), ensuring traceability between development deliverables and test execution.

Releases undergo full verification and validation through a combination of **manual and automated testing**, with QA activities integrated across all development phases to detect and prevent defects early.

All testing artefacts are managed in GitHub under: 
[eu-digital-identity-wallet/eudi-doc-testing-application-internal](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application-internal)

## Code Quality Controls

SonarCloud works on a set of code quality checks and analyzes code for multiple quality dimensions, across all stacks (Swift, Kotlin, Java, Python). The checks conducted can be further grouped into the following categories:

- Security (protecting software from threats, attacks, and unauthorized access):
 - Security Vulnerabilities: Flaws in code or configuration that attackers can exploit to compromise the system. Through SonarCloud the following security vulnerabilities are identified: SQL Injection, Deserialization, and Command Injection vulnerabilities.
 - Security Hotspots based on OWASP Top 10 / CWE Mappings: OWASP Top 10 refers to a list of the ten most critical web application security risks (e.g., injection, broken authentication) that can be found [here](https://owasp.org/www-project-top-ten/). CWE (Common Weakness Enumeration) refers to a standardized catalog of software weakness types. Vulnerabilities and hotspots can be mapped to these categories for classification. The relevant information can be found [here](https://cwe.mitre.org/top25/).

- Maintainability (measures how easily code can be understood, modified, and extended):
 - Code Smells: Patterns in code that indicate potential design or implementation issues. They are warning indicators that arise due to potential bad coding practices. The corresponding list that is checked per type of repository is the default provided by SonarCloud and can be found [here](https://rules.sonarsource.com/?_gl=1*7ng3p*_gcl_aw*R0NMLjE3NjMzODYzMTMuRUFJYUlRb2JDaE1Jd29LcTlLWDVrQU1WUEtXREJ4MUdXQ0dHRUFBWUFTQUFFZ0tNaWZEX0J3RQ..*_gcl_au*MTkzNjEwODQ0My4xNzYyNDM4OTc3*_ga*MjEyNzQ5NjI2MS4xNzYyNDM4OTM4*_ga_9JZ0GZ5TC6*czE3NjMzODYyNjYkbzYkZzEkdDE3NjMzODY1NzQkajQ1JGwwJGgw).
 - Cognitive Complexity: A metric indicating how difficult code is to understand. It increases with nested logic, branching, and poor readability. Details of the corresponding metric can be found [here](https://www.sonarsource.com/resources/cognitive-complexity/)
 - Duplications: Repeated blocks of code. High duplication leads to more effort in applying changes and increases the risk of inconsistency.

- Reliability (reflects how consistently software functions without failures):
 - Bugs: Using static code analysis, it detects actual bugs that can cause runtime errors or incorrect behavior.
 - Unit Test Coverage: A measure of how much of the code is exercised by automated tests. Higher coverage generally increases confidence in reliability but doesn’t guarantee the absence of bugs.

## Test Types

Testing is organised across multiple levels to validate functionality, performance, and security, ensuring comprehensive coverage throughout the development lifecycle:

| Test Type | Objective | Frequency |
| --- | --- | --- | 
| [Unit](#unit-testing) | Component-level verification | Continuous | 
| [Functional](#functional-testing) | End-to-end behaviour validation | Per release |
| [Security](#security-testing) | Confidentiality, integrity, and compliance | Per release |
| [Performance](#performance-testing) | Response time, and App Stability, CPU and Memory Usage | Per release | 


### Unit Testing

- **Objectives:** Unit testing verifies the correctness of individual software components and is the first quality gate in the CI pipeline. Unit testing supports early defect detection and continuous integration by ensuring each new change maintains baseline quality.
- **Tools:** [Unit Testing Tools](#test-tools).

---

### Functional Testing


- **Objectives:** Functional and end-to-end (E2E) testing ensures that each release behaves as expected according to defined epics and user stories.
- **Requirements:** The Functional Requirements can be found [here](https://github.com/eu-digital-identity-wallet/eudi-wallet-product-roadmap/blob/main/EUDI%20Wallet%20Reference%20Implementation%20-%20Feature%20Map.md).
- **Test Specifications:** The Functional Testing Specifications can be found here:
 - [Manual Testing](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application-internal/tree/main/src/test/resources/features).
 - [Automated Testing](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application-internal/tree/main).
- **Tools:** [Functional Testing Tools](#test-tools).

---

### Security Testing

- **Objectives:** Security testing ensures the continuous security, integrity, and resilience of the EUDI Wallet applications throughout their lifecycle. By integrating automated and manual security testing within a Secure Software Development Life Cycle (SDLC) and aligning with OWASP MASVS and MASTG standards, the framework enables early detection and remediation of vulnerabilities. It combines code analysis, penetration testing, and vulnerability management using tools such as SonarQube, OWASP Dependency-Check, and DefectDojo to maintain compliance with recognized security standards and safeguard user trust in the EUDI Wallet ecosystem.
- **Requirements and Test Specifications:** The Security Requirements and Security Test Specifications can be found [here](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application/blob/milestone/2025.Q4/doc/security/EUDI-Wallet-NiScy_Security_Requirements_and_Controls_Documentation.md).
- **Tools:** [Security Testing Tools](#test-tools).

---

### Performance Testing

- **Objectives:** Performance tests to evaluate the performance of the EUDI Wallet application under average user load across various mobile devices. This testing focuses on CPU and memory usage, as well as network activity during common scenarios.
- **Requirements:** The Performance Requirements can be found [here](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application/blob/milestone/2025.Q4/doc/performance/performance_requirements.md).
- **Test Specifications**: The Performance Test Specifications can be found [here](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application/blob/milestone/2025.Q4/doc/performance/performance_specifications.md).
- **Tools:** [Performance Testing Tools](#test-tools).

## Test Tools

The following table summarises the tools utilised in the applicable test types:
| Test Type | Tools | 
| --- | --- | 
| Unit | _SonarCloud_ |
| Functional | _Manual_, _Serenity BDD_ for structured reporting and visual coverage, Automation: Appium (for mobile automation on Android and iOS), Java (test scripting language), JUnit (test framework), IntelliJ IDEA (development and execution environment), Maven (dependency and build management), Appium Inspector (for element inspection and locator validation), Xcode (for building and exporting iOS .ipa files and Android .apk packages retrieved manually from Firebase for testing). |
| Security | _OWASP MASVS/MASTG_ for mobile security verification <br> _OWASP Dependency-Check_ for third-party library analysis <br> _SQLCipher_ and _Android Keystore_ for data protection <br> _Burp Suite_ and _MobSF_ for dynamic testing and static analysis|
| Performance | Android: Android Studio Profiler and App Inspection and iOS: Xcode Instruments for performance monitoring, memory usage, and CPU/network profiling |


## Reporting

Each release is accompanied with serenity-generated reports summarising test execution results and coverage.

### Release Test Reports

| Release | Test Types | Report Links | Status |
| --- | --- | --- | --- |
| 2025.07.28 - Demo | Functional <br/> Security <br/> Performance | [Functional test results](https://mgiakkou.github.io/testing/2025_q3/) <br/> [Security test results](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application/raw/refs/heads/milestone/2025.Q4/doc/security/EUDI-Wallet-NiScy_Security%20Testing%20Results-Version_2025.07.28-Demo.xlsx) <br/> [Performance test results](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application/blob/milestone/2025.Q4/doc/performance/preformance_test_results.md)| ✅ Released |
| 2025.10.31 - Demo | Functional | [Functional test results](https://mgiakkou.github.io/testing/2025_q4/) | ✅ Released |
| 2025.12.xx - xxx | (to be added) | (to be added) | 🔄 In progress |

Older releases remain available in the reports directory of the [testing repository](https://github.com/eu-digital-identity-wallet/eudi-doc-testing-application-internal/actions).

