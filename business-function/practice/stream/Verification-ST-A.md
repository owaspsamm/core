---
title: Scalable Baseline
type: stream
url: model/verification/security-testing/stream-a/
business_function: Verification
business_function_url: verification
practice: Security Testing
stream: A
description: Verification / Security Testing
keywords: ["Business function", "Practice", "Verification", "Security Testing"]

maturity_levels:
    level1:
        level: 1
        benefit: |
            Detection of common easy-to-find vulnerabilities
        activity: |
            Use automated static and dynamic security test tools for software, resulting in more efficient security testing and higher quality results. Progressively increase the frequency of security tests and extend code coverage.

            Application security testing can be performed statically, by inspecting an application's source code without running it, or dynamically by simply observing the application's behavior in response to various input conditions. The former approach is often referred to as Static Application Security Testing (SAST), the latter as Dynamic Application Security Testing (DAST). A hybrid approach, known as Interactive Application Security Testing (IAST), combines the strengths of both approaches (at the cost of additional overhead) by dynamically testing automatically instrumented applications, allowing accurate monitoring of the application's internal state in response to external input.

            Many security vulnerabilties are very hard to detect without carefully inspecting the source code. While this is ideally performed by expert or peer review, it is a slow and expensive task. Although "noisier" and frequently less accurate than expert-led reviews, automated SAST tools are cheaper, much faster, and more consistent than humans. A number of commercial and free tools are able to efficiently detect sufficiently important bugs and vulnerabilities in large code bases.

            Dynamic testing does not require application source code, making it ideal for cases where source code is not available. It also identifies concrete instances of vulnerabilities. Due to its "black-box" approach , without instrumentation, it is more likely to uncover shallow bugs. Dynamic testing tools need a large source of test data whose manual test generation is prohibitive. Many tools exist which generate suitable test data automatically, leading to more efficient security testing and higher quality results.

            Select appropriate tools based on several factors, including depth and accuracy of inspection, robustness and accuracy of security test cases, available integrations with other tools, usage and cost model, etc. When selecting tools, use input from security-savvy technical staff as well as developers and development managers and review results with stakeholders.

        question: Do you scan applications with automated security testing tools?
        quality_criteria:
            - You dynamically generate inputs for security tests using automated tools
            - You choose the security testing tools to fit the organization's architecture and technology stack, and balance depth and accuracy of inspection with usability of findings to the organization

        answers:
            - "No"
            - Yes, some of them
            - Yes, at least half of them
            - Yes, most or all of them

    level2:
        level: 2
        benefit: |
            Detection of organization-specific easy-to-find vulnerabilites
        activity: |
            Increase the effectiveness of automated security testing tools by tuning and customizing them for your particular technology stacks and applications. Automated security testing tools have 2 important characteristics: Their false positive rate, i.e. the non-existent bugs and vulnerabilities they incorrectly report; their false negative rate, i.e. actual bugs and vulnerabilities which they fail to detect. As you mature in your use of automated testing tools, you strive to minimize their false positive and false negative rates. This maximizes the time development teams spend reviewing and addressing real security issues in their applications, and reduces the friction typically associated with using untuned automated security analysis tools.

            Start by disabling tool support for technologies and frameworks you do not use and target specific versions where possible. This will increase execution speed and reduce the number spurious results reported. Rely on security tool champions or shared security teams to pilot the tools in coordination with a select group of motivated development teams. This will identify likely false positive findings to ignore or remove from the tools' output. Identify specific security issues and anti-patterns and favor the best tool for detecting them.

            Leverage available tool features to take application-specific and organizational coding styles, as well as technical standards into account. Many automated static analysis tools allow users to write their own rules or customize default analysis rules to the specific software interfaces in the project under test for improved accuracy and depth of coverage. For example, potentially dangerous input (aka tainted) can be marked as safe after it flows through a designated custom sanitization method.

            Strategically, it is better to reliably detect a limited subset of security issues via automated tooling, and incrementally extend coverage than attempting to detect all known issues immediately. Once the tools have been sufficiently tuned, they can be made available to a more development teams. It is important to continuously monitor their perceived efficacy among development teams. In more advanced forms, machine learning techniques can be adopted to identify and automatically filter out likely false positives at scale.

        question: Do you customize the automated security tools to your applications and technology stacks?
        quality_criteria:
            - You tune and select tool features which match your application or technology stack
            - You minimize false positives by silencing or automatically filter irrelevant warnings or low probability findings
            - You minimize false negatives by leverage tool extensions or DSLs to customize tools for your application or organizational standards

        answers:
            - "No"
            - Yes, some of them
            - Yes, at least half of them
            - Yes, most or all of them

    level3:
        level: 3
        benefit: |
            Identification of automatically identifiable vulnerabilities in earliest possible stages
        activity: |
            Projects within the organization routinely run automated security tests and review results during development. Configure security testing tools to automatically run as part of the build and deploy process to make this scalable with low overhead. Inspect findings as they occur.

            Conducting security tests as early as the requirements or design phases can be beneficial. While traditionally used for functional test cases, this type of test-driven development approach involves identifying and running relevant security test cases early in the development cycle. With the automatic execution of security test cases, projects enter the implementation phase with a number of failing tests for the non-existent functionality. Implementation is complete when all the tests pass. This provides a clear, upfront goal for developers early in the development cycle, lowering risk of release delays due to security concerns or forced acceptance of risk to meet project deadlines.

            Make the results of automated and manual security tests visible via dashboards, and routinely present them to management and business stakeholders (e.g. before each release) for review. If there are unaddressed findings that remain as accepted risks for the release, stakeholders and development managers work together to establish a concrete timeframe for addressing them. Continuously review and improve the quality of the security tests.

            Consider and implement security test correlation tools to automate the matching and merging of test results from dynamic, static, and interactive application scanners into one central dashboard, providing direct input towards Defect Management. Spread the knowledge of the created security tests and the results across the development team to improve security knowledge and awareness inside the organization.

        question: Do you integrate automated security testing into the build and deploy process?
        quality_criteria:
            - Management and business stakeholders track and review test results throughout the development cycle
            - You merge test results into a central dashboard and feed them into defect management

        answers:
            - "No"
            - Yes, some of it
            - Yes, at least half of it
            - Yes, most or all of it

---
