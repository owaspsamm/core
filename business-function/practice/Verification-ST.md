---
title: Security Testing
url: ./model/verification/security-testing/
business_function: "Verification"
business_function_url: "verification"
keywords: ["Business function", "Practice", "Security Testing"]
type: practice

practice_maturity_1_description: Perform security testing (both manual and tool based) to discover security defects.
practice_maturity_2_description: Make security testing during development more complete and efficient through automation complemented with regular manual security penetration tests.
practice_maturity_3_description: Embed security testing as part of the development and deployment processes.

stream_a: Scalable Baseline

stream_a_maturity_1_activity: Utilize automated security testing tools
stream_a_maturity_2_activity: Employ application-specific security testing automation
stream_a_maturity_3_activity: Integrate automated security testing into the build and deploy process

stream_b: Deep Understanding

stream_b_maturity_1_activity: Perform manual security testing of high-risk components
stream_b_maturity_2_activity: Conduct manual penetration testing
stream_b_maturity_3_activity: Integrate security testing into development process
---

The Security Testing (ST) practice leverages the fact that, while automated security testing is fast and scales well to numerous applications, in-depth testing based on good knowledge of an application and its business logic is often only possible via slower, manual expert security testing. Each stream therefore has one approach at its core.

The first stream focuses on establishing a common security baseline to automatically detect so-called "low hanging fruit". Progressively customize the automated tests for each application and increase their frequency of execution to detect more bugs and regressions earlier, as close as possible to their inception. The more bugs the automated processes can detect, the more time experts have to use their knowledge and creativity to focus on more complex attack vectors and ensure in-depth application testing in the second stream. As manual review is slow and hard to scale, reviewers prioritize testing components based on their risk, recent relevant changes, or upcoming major releases. Organizations can also access external expertise by participating in bug bounty programs, for example.

Unlike the Requirements-driven testing practice which focuses on verifying that applications correctly implement their requirements, the goal of this practice is to uncover technical and business-logic weaknesses in application and make them visible to management and business stakeholders, irrespective of requirements.

