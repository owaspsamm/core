---
title: Requirements-driven Testing
url: ./model/verification/requirements-driven-testing/
business_function: "Verification"
business_function_url: "verification"
keywords: ["Business function", "Practice", "Requirements-driven Testing"]
type: practice

practice_maturity_1_description: Opportunistically find basic vulnerabilities and other security issues.
practice_maturity_2_description: Perform implementation review to discover application-specific risks against the security requirements.
practice_maturity_3_description: Maintain the application security level after bug fixes, changes or during maintenance.

stream_a: Control Verification

stream_a_maturity_1_activity: Test for software security controls
stream_a_maturity_2_activity: Derive test cases from known security requirements
stream_a_maturity_3_activity: Perform regression testing (with security unit tests)

stream_b: Misuse/Abuse Testing

stream_b_maturity_1_activity: Perform security fuzzing testing
stream_b_maturity_2_activity: Create and test abuse cases and business logic flaw test
stream_b_maturity_3_activity: Denial of service and security stress testing
---

The goal of the Requirements-driven Testing (RT) practice is to ensure that the implemented security controls operate as expected and satisfy the project's stated security requirements. It does so by incrementally building a set of security test and regression cases and executing them regularly.

A key aspect of this practice is its attention to both positive and negative testing. The former verifies that the application's security controls satisfy stated security requirements and validates their correct functioning. These requirements are typically functional in nature. Negative testing addresses the quality of the implementation of the security controls and aims to detect unexpected design flaws and implementation bugs through misuse and abuse testing. In its more advanced forms, the practice promotes security stress testing, such as denial of service, and strives to continuously improve application security by consistently automating security unit tests and creating security regression tests for all bugs identified and fixed.

Although both the Requirements-driven Testing and Security Testing practices are concerned with security testing, the former focuses on verifying the correct implementation of security requirements, while the latter aims to uncover technical implementation weaknesses in an application, irrespective of requirements.

