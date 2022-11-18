---
title: Secret Management
type: stream
url: model/implementation/secure-deployment/stream-b/
business_function: Implementation
business_function_url: implementation
practice: Secure Deployment
stream: B
description: Implementation / Secure Deployment
keywords: ["Business function", "Practice", "Implementation", "Secure Deployment"]

maturity_levels:
    level1:
        level: 1
        benefit: |
            Defined and limited access to your production secrets
        activity: |
            Developers should not have access to secrets or credentials for production environments. Have a mechanism in place to adequately protect production secrets, for instance by (i) having specific persons adding them to relevant configuration files upon deployment (the separation of duty principle) or (ii) by encrypting the production secrets contained in the configuration files upfront.

            Do not use production secrets in configuration files for development or testing environments, as such environments may have a significantly lower security posture. Similarly, do not keep secrets unprotected in configuration files stored in code repositories.

            Store sensitive credentials and secrets for production systems with encryption-at-rest at all times. Consider using a purpose-built tool for this. Handle key management carefully so only personnel with responsibility for production deployments are able to access this data.

        question: Do you limit access to application secrets according to the least privilege principle?
        quality_criteria:
            - You store production secrets protected in a secured location
            - Developers do not have access to production secrets
            - Production secrets are not available in non-production environments

        answers:
            - "No"
            - Yes, for some applications
            - Yes, for at least half of the applications
            - Yes, for most or all of the applications

    level2:
        level: 2
        benefit: |
            Detection of potential leakage of production secrets
        activity: |
            Have an automated process to add credentials and secrets to configuration files during the deployment process to respective stages. This way, developers and deployers do not see or handle those sensitive values.

            Implement checks that detect the presence of secrets in code repositories and files, and run them periodically. Configure tools to look for known strings and unknown high entropy strings. In systems such as code repositories, where there is a history, include the versions in the checks. Mark potential secrets you discover as sensitive values, and remove them where appropriate. If you cannot remove them from a historic file in a code repository, for example, you may need to refresh the value on the system that consumes the secret. This way, if an attacker discovers the secret, it will not be useful to them.

            Make the system used to store and process the secrets and credentials robust from a security perspective. Encrypt all secrets at rest and in transit. Users who configure this system and the secrets it contains are subject to the principle of least privilege. For example, a developer might need to manage the secrets for a development environment, but not a user acceptance test or production environment.

        question: Do you inject production secrets into configuration files during deployment?
        quality_criteria:
            - Source code files no longer contain active application secrets
            - Under normal circumstances, no humans access secrets during deployment procedures
            - You log and alert to any abnormal access to secrets

        answers:
            - "No"
            - Yes, for some applications
            - Yes, for at least half of the applications
            - Yes, for most or all of the applications

    level3:
        level: 3
        benefit: |
            Minimized possibility and timely detection of production secret abuse
        activity: |
            Implement lifecycle management for production secrets, and ensure the generation of new secrets as much as possible, and for every application instance. The use of secrets per application instance ensures that unexpected application behavior can be traced back and properly analyzed. Tools can help in automatically and seemlessly updating the secrets in all relevant places upon change.

            Ensure that all access to secrets (both reading and writing) is logged in a central infrastructure. Review these logs regularly to identify unexpected behavior and perform proper analysis to understand why this happened. Feed issues and root causes into the defect management practice to make sure that the organization will resolve any unacceptable situations.

        question: Do you practice proper lifecycle management for application secrets?
        quality_criteria:
            - You generate and synchronize secrets using a vetted solution
            - Secrets are different between different application instances
            - Secrets are regularly updated

        answers:
            - "No"
            - Yes, for some applications
            - Yes, for at least half of the applications
            - Yes, for most or all of the applications

---
