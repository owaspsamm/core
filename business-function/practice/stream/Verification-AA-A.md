---
title: Architecture Validation
type: stream
url: model/verification/architecture-assessment/stream-a/
business_function: Verification
business_function_url: verification
practice: Architecture Assessment
stream: A
description: Verification / Architecture Assessment
keywords: ["Business function", "Practice", "Verification", "Architecture Assessment"]

maturity_levels:
    level1:
        level: 1
        benefit: |
            Understanding of high-level architecture and sensible security measures
        activity: |
            Create a view of the overall architecture and examine it for the correct provision of general security mechanisms such as authentication, authorization, user and rights management, secure communication, data protection, key management and log management. Also consider the support for privacy. Do this based on project artifacts such as architecture or design documents, or interviews with business owners and technical staff. Also consider the infrastructure components - these are all the systems, components and libraries (including SDKs) that are not specific to the application, but provide direct support to use or manage the application(s) in the organisation.

            Note any security-related functionality in the architecture and review its correct provision. Do this in an ad-hoc manner, from the point of view of anonymous users, authorized users, and specific application roles.

        question: Do you review the application architecture for key security objectives on an ad-hoc basis?
        quality_criteria:
            - You have an agreed upon model of the overall software architecture
            - You include components, interfaces, and integrations in the architecture model
            - You verify the correct provision of general security mechanisms
            - You log missing security controls as defects

        answers:
            - "No"
            - Yes, for some applications
            - Yes, for at least half of the applications
            - Yes, for most or all of the applications

    level2:
        level: 2
        benefit: |
            Consistent architecture review process across your organization
        activity: |
            Verify that the solution architecture addresses all identified security and compliance requirements. For each interface in the application, iterate through the list of security and compliance requirements and analyze the architecture for their provision. Also perform an interaction or data flow analysis to ensure that the requirements are adequately addressed over different components. Elaborate the analysis to show the design-level features that address each requirement.

            Perform this type of analysis on both internal interfaces, e.g. between tiers, as well as external ones, e.g. those comprising the attack surface. Also identify and validate important design decisions made as part of the architecture, in particular when they deviate from the available shared security solutions in the organization. Finally, update the findings based on changes made during the development cycle, and note any requirements that are not clearly provided at the design level as assessment findings.

        question: Do you regularly review the security mechanisms of your architecture?
        quality_criteria:
            - You review compliance with internal and external requirements
            - You systematically review each interface in the system
            - You use a formalized review method and structured validation
            - You log missing security mechanisms as defects

        answers:
            - "No"
            - Yes, for some applications
            - Yes, for at least half of the applications
            - Yes, for most or all of the applications

    level3:
        level: 3
        benefit: |
            Assurance of effectiveness of architecture controls
        activity: |
            Review the effectiveness of the architecture components and their provided security mechanisms in terms of alignment with the overall strategy of the organization, and scrutinize the degree of availability, scalability and enterprise-readiness of the chosen security solutions. While tactical choices for a particular application can make sense in specific contexts, it is important to keep an eye on the bigger picture and ensure future readiness of the designed solution.

            Feed any findings back into defect management to trigger further improvements to the architecture.

        question: Do you regularly review the effectiveness of the security controls?
        quality_criteria:
            - You evaluate the preventive, detective, and response capabilities of security controls
            - You evaluate the strategy alignment, appropriate support, and scalability of security controls
            - You evaluate the effectiveness at least yearly
            - You log identified shortcomings as defects

        answers:
            - "No"
            - Yes, for some applications
            - Yes, for at least half of the applications
            - Yes, for most or all of the applications

---
