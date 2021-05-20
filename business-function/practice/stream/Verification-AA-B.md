---
title: Architecture Mitigation
type: stream
url: model/verification/architecture-assessment/stream-b/
business_function: Verification
business_function_url: verification
practice: Architecture Assessment
stream: B
description: Verification / Architecture Assessment
keywords: ["Business function", "Practice", "Verification", "Architecture Assessment"]

maturity_levels:
    level1:
        level: 1
        benefit: |
            Assures that the architecture protects against typical security threats.
        activity: |
            Review the architecture for typical security threats. Security-savvy technical staff conduct this analysis with input from architects, developers, managers, and business owners as needed, to ensure the architecture addresses all common threats which development teams lacking specialised security expertise may have overlooked.

            Typical threats in an architecture can relate to incorrect assumptions in, or overly reliance on, the provisioning of security mechanisms such as authentication, authorization, user and rights management, secure communication, data protection, key management and log management. Threats, on the other hand, can also relate to known limitations of, or issues in, technological components or frameworks that are part of the solution and for which insufficient mitigation has been put in place.

        question: Do you review the application architecture for mitigations of typical threats on an ad-hoc basis?
        quality_criteria:
            - You have an agreed upon model of the overall software architecture
            - Security savvy staff conduct the review
            - You consider different types of threats, including insider and data-related one

        answers:
            - "No"
            - Yes, for some applications
            - Yes, for at least half of the applications
            - Yes, for most or all of the applications

    level2:
        level: 2
        benefit: |
            All identified threats to the application are adequately handled.
        activity: |
            Systematically review each threat identified during the Threat Assessment activities and examine how the architecture mitigates them. Use a standardised process for analyzing system architectures and the flow of data within them. This is typically linked to the threat model used (e.g. STRIDE) in order to identify the relevant security objectives which address each type of threat. For each threat, identify the design-level features of the architecture which counter it and assess their effectiveness in doing so.

            Where available, review architectural decision records to understand the architectural constraints and tradeoffs made during design. Take their impact into consideration along with any security assumptions on which the safe operation of the system relies and re-evaluate them.

            Enrich your previously created threat model such that each threat and its estimated impact are linked to the corresponding counter measure. Produce a mapping document, or dashboard in a specialized tool, to make the information available and visible to the relevant stakeholders.

        question: Do you regularly evaluate the threats to your architecture?
        quality_criteria:
            - You systematically review each threat identified in the Threat Assessment
            - Trained or experienced people lead review exercise
            - You identify mitigating design-level features for each identified threat
            - You log unhandled threats as defects

        answers:
            - "No"
            - Yes, for some applications
            - Yes, for at least half of the applications
            - Yes, for most or all of the applications

    level3:
        level: 3
        benefit: |
            Continuous improvement of enterprise architecture based on architecture reviews
        activity: |
            As an organization, you can further improve your software security posture by understanding which threats remain unaddressed in the software architectures and adapting your tactics to prevent this. Formalize a process to use recurring architecture findings as a trigger to identify the causes of gaps in the security assessment and deal with them. Feed findings back to the Design phase by creating, or updating relevant reference architectures, existing security solutions, or organisation design principles and patterns.

        question: Do you regularly update your reference architectures based on architecture assessment findings?
        quality_criteria:
            - You assess your architectures in a standardized, documented manner
            - You use recurring findings to trigger a review of reference architectures
            - You independently review the quality of the architecture assessments on an ad-hoc basis
            - You use reference architecture updates to trigger reviews of relevant shared solutions, in a risk-based manner

        answers:
            - "No"
            - Yes, for some applications
            - Yes, for at least half of the applications
            - Yes, for most or all of the applications

---
