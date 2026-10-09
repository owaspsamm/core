# OWASP SAMM: Guidance for AI-Assisted Development

This document provides additional guidance on applying OWASP SAMM when software is developed with AI assistance, i.e., when code, tests, configuration, and other artifacts may be produced by AI coding assistants, agents, or other generators. It does not change the core model: for each stream, it describes what changes with AI-assisted development and, per maturity level, how the corresponding activity is affected.

## Contents

- **Governance**
  - Strategy and Metrics
    - [G-SM-A: Create and Promote](#g-sm-a-create-and-promote)
    - [G-SM-B: Measure and Improve](#g-sm-b-measure-and-improve)
  - Policy and Compliance
    - [G-PC-A: Policy and Standards](#g-pc-a-policy-and-standards)
    - [G-PC-B: Compliance Management](#g-pc-b-compliance-management)
  - Education and Guidance
    - [G-EG-A: Training and Awareness](#g-eg-a-training-and-awareness)
    - [G-EG-B: Organization and Culture](#g-eg-b-organization-and-culture)
- **Design**
  - Threat Assessment
    - [D-TA-A: Application Risk Profile](#d-ta-a-application-risk-profile)
    - [D-TA-B: Threat Modeling](#d-ta-b-threat-modeling)
  - Security Requirements
    - [D-SR-A: Software Requirements](#d-sr-a-software-requirements)
    - [D-SR-B: Supplier Security](#d-sr-b-supplier-security)
  - Secure Architecture
    - [D-SA-A: Architecture Design](#d-sa-a-architecture-design)
    - [D-SA-B: Technology Management](#d-sa-b-technology-management)
- **Implementation**
  - Secure Build
    - [I-SB-A: Build Process](#i-sb-a-build-process)
    - [I-SB-B: Software Dependencies](#i-sb-b-software-dependencies)
  - Secure Deployment
    - [I-SD-A: Deployment Process](#i-sd-a-deployment-process)
    - [I-SD-B: Secret Management](#i-sd-b-secret-management)
  - Defect Management
    - [I-DM-A: Defect Tracking](#i-dm-a-defect-tracking)
    - [I-DM-B: Metrics and Feedback](#i-dm-b-metrics-and-feedback)
- **Verification**
  - Architecture Assessment
    - [V-AA-A: Architecture Validation](#v-aa-a-architecture-validation)
    - [V-AA-B: Architecture Mitigation](#v-aa-b-architecture-mitigation)
  - Requirements-driven Testing
    - [V-RT-A: Control Verification](#v-rt-a-control-verification)
    - [V-RT-B: Misuse/Abuse Testing](#v-rt-b-misuseabuse-testing)
  - Security Testing
    - [V-ST-A: Scalable Baseline](#v-st-a-scalable-baseline)
    - [V-ST-B: Deep Understanding](#v-st-b-deep-understanding)
- **Operations**
  - Incident Management
    - [O-IM-A: Incident Detection](#o-im-a-incident-detection)
    - [O-IM-B: Incident Response](#o-im-b-incident-response)
  - Environment Management
    - [O-EM-A: Configuration Hardening](#o-em-a-configuration-hardening)
    - [O-EM-B: Patching and Updating](#o-em-b-patching-and-updating)
  - Operational Management
    - [O-OM-A: Data Protection](#o-om-a-data-protection)
    - [O-OM-B: System Decommissioning / Legacy Management](#o-om-b-system-decommissioning--legacy-management)

## Governance

### Strategy and Metrics

#### G-SM-A: Create and Promote

AI-assisted development changes both the risk landscape and the opportunities an application security program must address. Code, tests, configuration, and infrastructure definitions may be produced by AI assistants, autonomous coding agents, or other generators, at a volume and speed that existing processes were not designed for. The organization's strategy must be explicit about the use of AI. It should at least cover where AI is allowed to be used in the software development process. It should also specify the guardrails required for every permitted AI use. Finally, there should be a feedback loop in place to measure which strategic AI decisions are working and which are not.

**Level 1: Identify the organization's risk appetite**

Extend the risk appetite discussion with executive leadership to cover AI-assisted development explicitly. Identify the main AI-related risks for the organization, such as disclosure of source code, secrets, or personal data to AI providers; insecure or unmaintainable generated code; hallucinated or malicious dependencies suggested by AI tools; autonomous agents acting with excessive privileges on repositories, pipelines, or environments; intellectual property and licensing uncertainty of generated code; and regulatory obligations related to AI. Also capture the opportunities, such as faster remediation, broader test coverage, and AI-supported security review.

Document where leadership draws the line. Typical decisions include which application risk profiles may use AI assistance, which data may be shared with which AI providers, and what level of autonomy is acceptable (e.g., suggestions only, AI-generated changes subject to review, or agents that act independently). Make clear that accountability for software remains with the organization and its teams regardless of what generated the code.

Publish the resulting AI risk appetite alongside the other risk factors so that development teams know what is allowed before they adopt AI tools, rather than discovering the boundaries afterwards.

**Level 2: Define the security strategy**

Include AI-assisted development as an explicit theme in the application security strategy and roadmap. Define the target state for the planning horizon: which AI tools and models are sanctioned, which autonomy levels are allowed for which application risk classes, and which guardrails must be in place before autonomy is extended.

For every permitted AI use, define the required guardrails (e.g., mandatory independent review, automated security checks, restricted permissions for agents, approved data flows) and how the organization verifies that they are actually applied. Define upfront which signals will show whether each strategic AI decision is working, for example the root cause analysis of security defects (see Metrics and Feedback).

Plan the supporting initiatives as roadmap milestones. These typically include establishing a list of approved AI tools and providers, translating security standards into a form that AI code generation tools and agent harnesses can consume (e.g., shared instruction files, rules, and policies), scaling automated security verification to keep pace with the increased volume of change, and adapting training.

Balance the expected productivity gains against verification capacity. When the rate of change grows faster than the organization's ability to verify it, risk accumulates silently. Offer sanctioned, well-configured AI tools to development teams early in the roadmap to reduce the use of unsanctioned tools, and obtain buy-in from development teams on the guardrails.

**Level 3: Align security and business strategies**

AI capabilities, tools, and the related threat landscape change considerably faster than most other technologies. Review the AI aspects of the strategy more frequently than the annual cycle where needed, and re-evaluate the AI risk appetite whenever the organization's business strategy for AI, available tool capabilities, or applicable regulation changes significantly.

Evaluate each milestone that extends AI usage or autonomy before proceeding to the next one. Assess not only security outcomes but also cultural effects, such as erosion of in-depth system knowledge within teams, unclear ownership of generated code, or pressure to bypass verification to retain speed. Adjust the roadmap when the evidence shows that guardrails lag behind adoption.

#### G-SM-B: Measure and Improve

_No AI-specific guidance for this stream yet._

### Policy and Compliance

#### G-PC-A: Policy and Standards

At the policy level, the organization needs new high-level positions stating how AI may be used in development and under which conditions. At the standards level, these policies, as well as existing ones, must be translated into concrete, technology-specific rules that guide not only people but also AI coding assistants and agents. Agent instruction files (e.g., AGENTS.md, CLAUDE.md, .github/copilot-instructions.md, Cursor rules) therefore become part of the distribution surface for standards, next to wikis, documents, and training.

AI tools may ignore, misinterpret, or be manipulated into overriding them. This makes the existing practice of translating policies and standards into test scripts and run-books even more important. The organization needs ways to verify key policy requirements, independently of whether the AI followed its instructions. Ideally this verification is deterministic, for example through static analysis rules, policy-as-code checks, automated tests, or tool permission configurations, so that it produces the same result every time and cannot be talked out of a finding. Verification that itself relies on AI can complement, but not replace, deterministic checks.

**Level 1: Define policies and standards**

Extend the policy library with explicit positions on AI-assisted development, consistent with the AI risk appetite and strategy. At a minimum, cover:
* Acceptable use of AI coding assistants and agents: which development activities and application risk profiles they may be used for, which data and source code may be shared with which providers, and what autonomy agents may have (e.g., read-only, propose changes, commit, run commands, access environments).
* License and intellectual property posture on AI-generated code: whether and how generated code may be included in products, how the risk of reproducing licensed code is handled, and whether AI involvement must be disclosed.
* Approved tools: only approved AI tools and integrations may be used in development, and unapproved tools are treated as unauthorized software.

Derive standards from these policies. For example, the approved tools policy translates into a standard containing the maintained list of approved AI coding agents, models, IDE plugins, MCP servers, and other tool integrations, including their permitted configuration and permissions. Standards may also need to cover other AI-specific topics, such as handling of AI-suggested dependencies and secure configuration of agent harnesses.

**Level 2: Develop test procedures**

Prepare the test scripts and run-books for interpretation by AI tools as well as by development teams. Where teams were previously briefed on key policies, now also capture them in AI-consumable formats, such as agent instruction files (e.g., AGENTS.md, CLAUDE.md, .github/copilot-instructions.md, Cursor rules) and prompts. Publish these in a central location where teams can easily find them and add them to their projects. Version them with change logs, link each rule to its source policy, and protect them with adequate change control, since tampered instructions silently weaken every change an AI tool produces.

Structure the AI-consumable formats in two layers. The policy layer states what must be done (e.g., protect against injection attacks). The standard layer states how to do it for a specific technology or development methodology (e.g., which query APIs to use and which constructs are forbidden for a given stack). Teams would typically use the standard layer that matches their technologies.

For each rule, define how compliance is verified independently of the AI tool, preferably deterministically (e.g., static analysis rules, policy-as-code, automated tests, pipeline gates). AI tools may use these checks on their own output, but this does not replace independent verification.

**Level 3: Measure compliance to policies and standards**

Use AI tools to build and maintain the automated procedures that generate compliance reports. AI tools can help map each policy and standard requirement to existing evidence (e.g., code, test results, static analysis findings), write the scripts or policy-as-code rules that collect this evidence for every application version, and identify requirements that have no automated check yet. Ensure the resulting procedures are deterministic and do not depend on AI interpretation at reporting time.

Where AI tools assess compliance directly, keep in mind that their conclusions are sensitive to how they are asked: a prompt to "find gaps" tends to produce gaps, while a prompt to "confirm compliance" tends to produce reassurance. Use neutral instructions and define explicit pass/fail criteria per requirement, require a verdict with cited evidence for each one, and validate the setup against samples with known compliance status. A gap must be unambiguous, not a matter of interpretation.

AI tools can also summarize compliance status per team or application and create reports for stakeholders identifying areas for improvement. Ensure every statement in these summaries is traceable to the underlying verdicts and evidence.

#### G-PC-B: Compliance Management

The use of AI in development introduces new external compliance obligations, most notably AI-specific regulation. Once identified, these obligations are handled in the same way as described for the Policy and Standards stream: translated into requirements and test scripts.

**Level 1: Identify compliance requirements**

Include AI regulation in the list of compliance requirements, for example the EU AI Act, including its AI literacy obligations for staff using AI systems.
Revisit existing obligations and controls in place to meet them, as AI-assisted development changes how they apply. For example, under data protection regulation such as GDPR, AI providers may become processors or sub-processors, and personal data may reach them through new channels such as prompts, code context, test data, or agents accessing environments.

**Level 2: Standardize policy and compliance requirements**

Include compliance-specific requirements and test scripts in the AI-consumable formats published for the Policy and Standards stream, so that AI tools take them into account during development. Verify compliance independently of the AI tools, preferably deterministically.

**Level 3: Measure compliance to external requirements**

Use AI tools to build automated procedures that measure and report compliance with external requirements, applying the same safeguards as for the Policy and Standards stream: deterministic procedures, neutral instructions, explicit pass/fail criteria, and verdicts traceable to evidence. As AI regulation evolves quickly, re-assess applicable AI-related obligations more frequently than other compliance drivers.

### Education and Guidance

#### G-EG-A: Training and Awareness

Training remains focused on people. With AI-assisted development, people increasingly specify, review, and approve work rather than write it themselves. Training must therefore cover the risks of AI-assisted development and the skills needed to direct and critically assess AI output.

**Level 1: Train all stakeholders for awareness**

Extend awareness training with the risks of AI-assisted development, using resources such as the OWASP Top 10 for LLM Applications and the OWASP Top 10 for Agentic Applications. Relevant topics include:
* Over-reliance on AI output: generated code, tests, and designs that look correct on the first attempt are not necessarily secure or correct. Whoever accepts AI output remains accountable for it.
* Sensitive data exposure: source code, secrets, and personal data shared with AI tools through prompts or context.
* Prompt injection: instructions hidden in content that AI tools read, such as issues, documentation, dependencies, or web pages.
* Excessive agency: risks of granting agents broad permissions, and of approving agent actions without understanding them.
* Supply chain risks: hallucinated or malicious dependencies suggested by AI, and untrusted plugins or MCP servers.
* The organization's AI policies, such as acceptable use and approved tools.

**Level 2: Customize security training**

Customize training for each role with AI-specific content, including demonstrations of the AI tooling, configurations, and guardrails developed in-house:
* Developers train on directing AI tools towards the organization's established architectural patterns, shared security services, and reference components. They are also trained on recognizing AI-generated changes that reinvent the reference patterns and components or dilute the architecture (e.g., unnecessary abstractions, overly complex solutions).
* Security Champions train on building and tuning deterministic guardrails for AI-generated code, such as custom static analysis rules, architectural boundary checks, and pipeline gates, to catch anti-patterns as early as possible before they reach code review.

Keep fundamental secure development skills in the curriculum, as people can only review AI output effectively if they understand what secure code looks like.

**Level 3: Standardize security guidance**

Consider making access to AI coding tools, or to higher levels of agent autonomy, conditional on completion of the relevant training, in the same way as access to other development systems.

#### G-EG-B: Organization and Culture

AI tools and practices evolve faster than central teams can follow alone. The existing organizational structures, such as Security Champions, the Secure Software Center of Excellence, and the security community, are well suited to spread secure AI-assisted development practices and to collect feedback on what works.

**Level 1: Identify security champions**

Security Champions embed security knowledge into the team's AI tools. They do this together with the developers, keeping them in the loop on what is added and why. Together, they create and maintain the deterministic guardrails (e.g., static analysis rules) that ensure AI-generated code meets the organization's security standards.

**Level 2: Implement centers of excellence**

Have the Secure Software Center of Excellence define best practices for AI-assisted development, such as reference configurations for approved AI tools, shared agent instruction files, and guardrail rulesets. It helps evaluate new AI tools and integrations for both security and compatibility with how teams develop. Product Champions assist teams in adopting the approved AI tools and guardrails, and the practices of teams that use AI effectively and securely are replicated to other teams.

**Level 3: Establish a security community**

Use the security community and portal to share effective practices for AI-assisted development, such as instruction files and guardrail rules. Use the portal as the central location for the organization's AI-consumable standards (see Policy and Standards).

## Design

### Threat Assessment

#### D-TA-A: Application Risk Profile

Applications that contain AI functionality, such as LLM integrations, agents, or MCP servers, introduce risks that traditional risk profiles do not capture. In addition, AI tools can assist in performing risk assessments in various ways.

**Level 1: Perform application risk assessments**

The basic risk assessment should explicitly take into account whether the application contains AI functionality, such as an LLM integration or an MCP server. Include in the risk profile the potential attack surface that this functionality may create. For instance, a read-only MCP server opens a much smaller attack surface than a full-blown LLM integration with write access.

**Level 2: Inventory risk profiles**

Extend the standardized risk evaluation with AI-specific risk factors for applications containing AI functionality, such as:
* Autonomy: whether the AI component can take actions (e.g., call tools, modify data, trigger transactions) or only produces output for people.
* Access: which data, tools, and other applications the AI component can reach, including through MCP or other integrations.
* Exposure to untrusted input: whether content from users or external sources reaches the model, enabling prompt injection.
* Use of output: whether AI output is used for decisions or processed by other systems without human verification.
* Data shared with AI providers, and dependency on third-party models.
* Regulatory classification of the AI functionality (see Compliance Management).
Record the AI components of each application (e.g., models, providers, exposed tools) in the risk profile inventory.

AI can assist risk owners with the risk assessment itself, while they remain responsible for its outcome:
* Exploring risk scenarios: AI can act as a sparring partner to develop a more thorough understanding of risk scenarios and their business impact. For example by surfacing dependencies between assets and business processes, and the cascading impact an incident may have through them.
* Quantifying risk: when a quantitative risk methodology is used (e.g., FAIR), AI can help structure estimates, perform the calculations, and analyze how sensitive the outcome is to individual assumptions. The input estimates and assumptions remain owned and documented by the risk owners.

**Level 3: Periodic review of risk profiles**

Review risk profiles of applications with AI functionality more frequently, as their risk can change without changes to the application's own code. Changes that should trigger a re-evaluation include a new model or provider, new tools or integrations available to the AI component, or increased autonomy.

#### D-TA-B: Threat Modeling

Threat modeling analyzes how risk scenarios can materialize through architectural and design-level weaknesses. AI functionality in a product does not change this conceptually: models, agents, and their tools are components in the architecture like any other, with their own data flows and trust boundaries.

Using AI to assist threat modeling is a double-edged sword. AI tools readily produce convincing but shallow threat analyses (e.g., generic STRIDE reports), which turns threat modeling into a checkbox exercise. The primary value of threat modeling is a shared understanding of the architecture among the people who build it, and that cannot be delegated to an AI tool. AI can add value by assisting people, provided it is given sufficient context, and that context lives in the architecture and the intent of the system rather than in its code.

**Level 1: Perform basic threat modeling**

Focus on establishing the architecture and data flow diagrams. Architects, senior developers, and security champions sit together and agree on the architecture, including any AI components and the data flows to and from them. Ideally, this happens before the code is written. When the code already exists, the team still agrees on the architecture and data flows as intended, rather than just deriving them from the code. Data flow diagrams generated by AI from the source code have no value unless the technical team reviews them and agrees that they represent the architecture at the right level of abstraction in order to facilitate threat elicitation.

**Level 2: Standardize and scale threat modeling**

Use AI as an assistant to validate the threats elicited by the team, for example by challenging their completeness or by suggesting mitigations. AI can also propose additional threats, but only when provided with sufficient context: the agreed architecture and data flow diagrams, the intent of the system and its business context, the application risk profile, and the assumptions made. Deriving architectural threats solely based on the source code is highly discouraged as it tends to end up in noise. Intent is very hard to derive from a working system, document it explicitly.

For applications containing AI functionality, use resources such as the OWASP Top 10 for LLM Applications and the OWASP Top 10 for Agentic Applications as aids to guide the brainstorming. They are not threats in themselves: the team still identifies threats specific to how the AI components are used in the given architecture.

**Level 3: Optimize threat modeling**

As part of improving the methodology, critically assess whether AI adds value to the threat modeling sessions. For example, track how many threats proposed by AI were accepted as relevant and led to meaningful mitigations, compared to those rejected as generic or irrelevant. Watch for signs that threat modeling is degrading into a checkbox exercise, such as generic threats, threat models that are not discussed by the team, or few resulting mitigations.

### Security Requirements

#### D-SR-A: Software Requirements

Requirements elicitation remains a human activity: people specify the functionality that needs to be developed. AI can assist by augmenting functional requirements with security requirements, so that security is in the driver's seat from the start rather than an afterthought. This matters even more with AI-assisted development, as requirements and user stories become direct input for AI coding tools. Security requirements have to be explicit.

**Level 1: Identify security requirements**

When reviewing functional requirements, the team can ask an AI assistant on a best-effort basis how the functionality could be misused and which high-level security objectives apply. The team keeps the suggestions that are specific and relevant to the application.

**Level 2: Standardize and integrate security requirements**

Make AI assistance a systematic part of backlog refinement and sprint planning from a security requirements perspective. Provide the AI with the organization's sources of security requirements, such as policies and standards, the application risk profile, and known security defects, so that it consistently brings the relevant security requirements in as regular requirements.

**Level 3: Develop a security requirements framework**

Use AI to help create and maintain the security requirements framework, derived from standards such as OWASP ASVS and MASVS and customized for specific components, applications, or the portfolio. Include the organizational policies and standards as an input as well. AI can help tailor requirements to the technologies in use and keep the framework aligned with new versions of the underlying standards.

#### D-SR-B: Supplier Security

Suppliers increasingly use AI in their development, often without this being visible to their clients. This affects the organization in two ways. First, data shared with suppliers, such as source code, specifications, test data, or credentials, may end up in AI tools and with AI providers, effectively creating additional parties that process the organization's data. Second, AI-assisted development changes the quality profile of delivered software: more code is delivered faster, and it may contain insecure patterns, unnecessary complexity, hallucinated dependencies, or code with unclear licensing. The organization must therefore make supplier AI usage explicit, contractually bounded, and verified.

**Level 1: Perform vendor assessments**

Add AI-related questions to the vendor assessment. For example:
* Does the supplier use AI tools in development, and which tools and providers?
* Which of the organization's data could reach these tools, and is it retained or used for training by the providers?
* Does the supplier have a policy on AI-assisted development, such as acceptable use and approved tools?
* How does the supplier verify AI-generated code before delivery, and how does it handle licensing of generated code?

**Level 2: Discuss security responsibilities with suppliers**

Include AI-related responsibilities in supplier agreements, such as:
* Disclosure of AI use in development, and notification when it changes significantly.
* Restrictions on sharing the organization's data and code with AI tools, for example limiting it to approved providers that do not retain the data or use it for training.
* The supplier remains fully accountable for the security and quality of delivered software, regardless of whether it was produced with AI assistance.
* Warranties on intellectual property and licensing of AI-generated code.

**Level 3: Align security methodology with suppliers**

Align AI-assisted development practices with key suppliers. Provide them with the organization's standards in AI-consumable formats (see Policy and Standards), and have their contributions pass the same deterministic guardrails and verification as internally developed AI-generated code, for example through shared pipelines.

Where suppliers cannot meet these expectations, strengthen verification at intake as a compensating control, for example through stricter static analysis, dependency analysis, architectural conformity checks, and review of high-risk components.

### Secure Architecture

#### D-SA-A: Architecture Design

AI tools that write code are notorious for causing architectural drift. In other words, they tend to ignore the architectural context and either come up with new architectural patterns or generate functionality without any meaningful architecture as a backbone. To counter this, at the very least the organization's security principles, preferred security solutions, and reference architectures need to be available in a format that AI tools can consume.

**Level 1: Adhere to basic security principles**

Make the security principles available to AI tools in a form they can relate to. AI tools are poor at translating abstract principles into concrete code on their own, so pair each principle with how it materializes in the codebase. For instance, rather than only stating "apply proper sanitization and output encoding", state that user-provided content is stored as-is in the database and encoded at output, except for rich text editor content, which is sanitized, and point to where this is done in the code. Include these principles in the agent instruction files.

**Level 2: Provide preferred security solutions**

Describe the shared security services and design patterns in an AI-consumable format: what each one is for, when to use it, and how to integrate with it, including concrete examples. Explicitly instruct AI tools to use these solutions instead of implementing their own security functionality, such as authentication, authorization, or cryptography.

More importantly, focus on creating deterministic guardrails that reliably detect re-implementations of functionality covered by the shared solutions.

**Level 3: Build reference architectures**

Make reference architectures available to AI tools in an AI-consumable format. Note that an architecture is much more than a structure of where code lives (e.g., services in one folder, entities in another). Architecture covers components, dependencies, data flows, security controls etc. Capturing all of this in a form AI tools reliably follow is still an open challenge.

Therefore, focus on detecting when AI-generated changes break out of the reference architectures and reusable services, using a combination of measures:
* Code quality metrics: assess every pull request on metrics such as cyclomatic complexity, coupling, cohesion, and duplication, against agreed thresholds. Degrading metrics are an early signal of architectural dilution. AI can then be used to propose a solution that improves the metrics, which is reviewed like any other change.
* Static analysis rules: specify anti-patterns that break the architecture as rules, for example forbidden dependencies between layers or components, or bypassing a shared security service by accessing the underlying resource directly.
* Code review guidelines: give human reviewers explicit architectural review criteria, for example whether the change reuses existing components and services, introduces new patterns or components, or crosses component boundaries.

When AI tools repeatedly deviate from the reference architecture, treat this as input for improving the way reference architecture is made available to AI tools, or the rules above.

#### D-SA-B: Technology Management

AI affects technology management in two ways. First, AI development tools (e.g., coding agents, models, IDE plugins, MCP servers) are themselves technologies that need to be identified, evaluated, and managed like any other development tooling. Second, AI tools take the path of least resistance even more than people do: they readily introduce new frameworks and libraries into an application, which may be outdated, unmaintained, or not recommended by the organization.

**Level 1: Identify tools and technologies**

Include the AI development tools and integrations used by the teams, as well as AI components used in the applications (e.g., models, providers, AI frameworks), in the identification of technologies. Evaluate them for their security quality, for example how they handle data, which permissions they require, and how trustworthy their source is.

**Level 2: Promote preferred tools and technologies**

Include AI development tools and integrations in the list of recommended technologies; this list forms the basis of the approved AI tools standard (see Policy and Standards). Make the list of recommended technologies available in an AI-consumable format, so that AI tools choose recommended frameworks and libraries by default. Review AI tools more frequently than other technologies, as they evolve quickly.

**Level 3: Enforce the use of recommended technologies**

Enforce the use of recommended technologies deterministically, for example by failing the build when a change introduces a framework or library that is not on the recommended list. Enforce the use of approved AI tools and their configuration through centrally managed settings where the tools support it (e.g., allowed MCP servers and permissions), and detect the use of unapproved AI tools.

## Implementation

### Secure Build

#### I-SB-A: Build Process

AI changes little about the build process itself. AI can help create build pipeline definitions, but AI tools should not have access to the build system, its secrets, or signing keys. The build is the place where the deterministic guardrails for AI-generated code become mandatory.

**Level 1: Define a consistent build process**

AI can assist in proofreading the formal build process definition, for example to identify missing or ambiguous steps, and in suggesting hardening measures for the build tools in use.

**Level 2: Automate the build process**

AI can assist in creating build pipeline definitions as well as suggesting hardening measures for the build tools in use. Do not give AI tools access to the build system, its secrets, or signing keys. Treat changes to pipeline definitions as security-sensitive: they require human review, also when proposed by an AI tool.

**Level 3: Enforce a security baseline during build**

Add the deterministic guardrails for AI-generated code (e.g., custom static analysis rules, architectural rules, code quality metrics) to the automated security checks in the pipeline.

If the pipeline includes AI-based steps, such as automated AI code review, treat them as processing untrusted input, since pull requests may contain prompt injection. Run such steps without access to secrets or write permissions.

#### I-SB-B: Software Dependencies

AI tools may suggest packages that do not exist. Attackers exploit this by publishing malicious packages under those names (so-called slopsquatting). AI tools may also suggest outdated versions, as their knowledge is limited to their training data. At the same time, AI offers clear opportunities for this practice: it can help keep dependencies lean, build and maintain the curated list of approved dependencies, and analyze third-party code for security issues.

Good practice is that no dependency enters an application only because an AI tool suggested it, while AI is used to make dependency management more thorough than manual effort alone allows.

**Level 1: Identify application dependencies**

Verify every dependency suggested by an AI tool before adding it. Make sure the dependency is the intended one, it is maintained and included in an up-to-date version.

**Level 2: Review application dependencies for security**

Use AI to help detect and remove unnecessary dependencies. AI can also assist in creating and maintaining the curated list of approved dependencies. It can help flag dependencies that are risky, such as unmaintained packages or packages with suspicious recent changes.

Point the AI tools to the list with approved dependencies so that it is aware which ones should be used.

**Level 3: Test application dependencies**

Use AI to help analyze the code of third-party dependencies for vulnerabilities and malicious code, such as backdoors, complementing established analysis tools. This makes the in-depth verification of dependencies expected at this level feasible at a larger scale. Pay attention to the eagerness of AI tools to find something. They should be configured to look for something major rather than every possible vulnerability with unclear risk.

### Secure Deployment

#### I-SD-A: Deployment Process

As with the build, AI changes little about the deployment process itself. AI can help define and automate deployments, but AI tools should not have access to production environments, deployment credentials, or the deployment system. Decisions in the deployment process, such as approvals and exceptions, remain with people.

**Level 1: Use a repeatable deployment process**

AI can assist in proofreading the formal deployment process definition and in suggesting hardening measures for the deployment tools in use. The separation between development and production also applies to AI tools. AI tools used in development must not have access to the production environment.

**Level 2: Automate deployment and integrate security checks**

AI can assist in creating deployment pipeline definitions. Do not give AI tools access to the deployment system or its credentials. Treat changes to deployment pipeline definitions as security-sensitive.

**Level 3: Verify the integrity of deployment artifacts**

AI doesn't change anything for this activity.

#### I-SD-B: Secret Management

AI does not change how secrets should be managed, but it massively increases the risk of getting it wrong. AI tools read files, process context, and execute commands, and anything they can access may be sent to an AI provider. Least privilege principle is key here and AI tools should be treated as potentially malicious from the secrets management perspective. At the same time, AI can help find secrets where they should not be and keep the inventory of secrets clean.

**Level 1: Protect application secrets in configuration and code**

Handle AI tools as a potential attacker. AI tools must never have access to secrets other than development-grade secrets, whether through code, configuration files, environment variables, or prompts. Secrets pasted in prompts should be considered as compromised.

**Level 2: Include application secrets during deployment**

Use AI to complement static secret detection tools. Such tools may lack context and produce false positives. AI tools that have access to the codebase can better judge whether a value is an actual secret and whether it is sensitive. This is even more important for the local secrets detection as developers may keep production-grade secrets on their machines that are not checked-in into the repository. If AI tools are already running on such a machine, AI already has access to them. So use AI to find such secrets and raise the alarm. Treat every production secret found this way as compromised, and rotate it.

**Level 3: Enforce lifecycle management of application secrets**

Lifecycle management of secrets remains an activity performed by people. AI can help create and maintain an inventory of secrets. Provide AI tools with the names and metadata of secrets only, never with their values.

### Defect Management

#### I-DM-A: Defect Tracking

With AI-assisted development, most changes are produced with AI assistance, so recording whether a defect came from AI says little. Instead, defect tracking should capture enough information to understand why a defect occurred, as input for root cause analysis (see Metrics and Feedback), while keeping ownership of every defect clearly with people. AI can also assist with triaging defects and tracking SLAs.

**Level 1: Track security defects centrally**

Record for each security defect the information needed to later understand why it occurred, such as the related requirements, the affected components, and the context in which the change was made. This is the basis for root cause analysis and allows focusing on prevention, although, given the non-deterministic nature of AI, prevention might not always work.

Ensure every security defect has a clear owner, regardless of whether AI was involved in producing the change. The team that accepted a change owns its defects, and an AI tool is never the owner of a defect, even when it is used to fix it.

AI can assist with triaging defects, for example by identifying duplicates and likely false positives. Treat its conclusions as proposals that people confirm.

**Level 2: Rate and track security defects**

AI can assist in rating security defects. However keep in mind that AI is susceptible to suggestion, and context implying that a defect is less severe than it seems can lead to an underrated defect. Apply the rating methodology with explicit criteria, require the AI to justify its rating with evidence, and keep the final rating with people.

AI can help create dashboards and monitoring for tracking SLA compliance.

**Level 3: Enforce an SLA for defect management**

AI can help build the automated SLA alerting and the integration of the defect management system with build, deployment, and monitoring tooling. Be careful with the autonomy AI gets over these tools. It is okay to let AI help create the integrations, but do not give AI tools the permissions to operate them, for example to change build or deployment outcomes or to sign off exceptions.

#### I-DM-B: Metrics and Feedback

When code is written with AI assistance, root cause analysis of security defects remains just as relevant. Whether the defect's root cause is coming from the context given to AI tools, the architecture, or the requirements specifications (or their absence) helps to improve and to prevent similar defects. This data should then feed into the AI-assisted AppSec strategy at the level of the team, the business unit, and even the organization.

**Level 1: Define basic defect metrics**

When periodically going over recorded security defects, make a best-effort attempt to identify the root cause of the most relevant ones. No formal categorization is needed at this level. Typical root causes in AI-assisted development include:
* Specifications: security requirements were missing, ambiguous, or not explicit.
* Architecture: the reference architecture or shared security solutions were missing, unclear, or not followed.
* Context: the AI tool lacked or misinterpreted relevant instructions, standards, or information about the codebase.
Where evident, also note why the defect was not caught earlier, such as a missing guardrail, test, or review. Derive quick wins from these insights, for example updating the agent instruction files, clarifying a security requirement, or adding a deterministic guardrail (e.g., a static analysis rule).

**Level 2: Define advanced defect metrics**

Add the root cause categories and the reasons defects were not caught earlier as dimensions of the unified metrics across the organization. This allows comparing, for example, time to resolve, regressions, and reopened defects between products, teams, or business units that use AI differently. Share the lessons learned across teams, including the resulting changes to instructions, specifications, and guardrails.

**Level 3: Use metrics to improve the security strategy**

Regularly evaluate whether the root cause metrics show where AI adds value and where it is a burden. Use these as input for the decisions in the AI-assisted AppSec strategy, such as investing in better context, architecture, or specifications, or extending or restricting AI use for certain applications, technologies, and/or teams.

## Verification

### Architecture Assessment

#### V-AA-A: Architecture Validation

Architecture assessment is where AI can be of substantial benefit. As systems evolve the dev team may start losing track of the entire scope of the project. AI can help keep the complete picture in view. However AI needs proper context to do this well. AI also tends to report code-level issues as architectural problems. Teams also tend to use AI for a quick architectural analysis as a checkbox exercise. This may be acceptable at the first maturity level, but higher levels require teams to maintain a human-readable representation of the architecture: its components, their interactions, and the security controls. This representation is maintained by and for people, not for the sake of AI, and serves as the basis for AI-assisted reviews.

**Level 1: Assess application architecture**

AI can perform an ad-hoc assessment of the architecture for the provision of general security mechanisms, based on the available architecture or design documents and the code. Review the findings and keep those that are actually architectural, rather than code-level issues.

**Level 2: Verify the application architecture for security methodically**

Regularly review whether the architecture provides the required security mechanisms, such as authentication, authorization, secure communication, data protection, and logging. To this end, create and maintain a catalog of security controls: which controls exist, which requirements they address, and in which architectural components and interfaces they are provided. The architecture and data flow diagrams from threat modeling are a natural starting point (see Threat Modeling).

Cataloging is a human activity that AI can assist, for example by proposing candidate controls from documentation and code, or by pointing out requirements without a corresponding control. People validate the catalog, as it serves as the context for all further reviews.

**Level 3: Verify the effectiveness of security components**

Use AI to scrutinize the controls in the catalog in detail, including at the code level. This is where AI can go deep, but context is everything: provide the catalog of controls, the architecture representation, the security requirements, and the relevant reference architectures and shared security solutions. People verify the findings and log confirmed shortcomings as defects. The judgement on strategic alignment, scalability, and enterprise-readiness of the security solutions remains with people.

#### V-AA-B: Architecture Mitigation

As for Architecture Validation, AI can be of benefit in reviewing whether the architecture mitigates threats. However AI needs proper context to do this well. AI also tends to report code-level issues as architectural problems. Teams also tend to use AI for a quick architectural mitigation review as a checkbox exercise. From the second maturity level onwards, AI-assisted reviews are based on the human-readable representation of the architecture and threat models maintained by the team.

**Level 1: Evaluate architecture for typical threats**

AI can perform an ad-hoc review of the architecture for typical threats, based on the available architecture or design documents and the code. Review the findings and keep those that are actually architectural, rather than code-level issues.

**Level 2: Structurally verify the architecture for identified threats**

Ensure that the mitigations for the threats identified in the threat model are correctly implemented in the code. For each identified threat, use AI to check whether its mitigations are properly implemented, and whether anything remains unmitigated, for example an abuse path that bypasses the intended controls. Make sure to provide the threat model and the catalog of controls as context. People validate the results and maintain the mapping between threats and their implemented mitigations.

**Level 3: Feed review results back to improve reference architectures**

Aside from helping with the reference architecture updates, AI does not seem to bring much value to this activity.

### Requirements-driven Testing

#### V-RT-A: Control Verification

Control verification is where AI can help substantially, as it makes writing and running security tests much cheaper. The maturity levels differ in rigour: AI is used ad hoc at the first level, systematically at the second, and at the third level as many security requirements as possible are translated into automated test cases. People remain responsible for defining what needs to be tested, and for checking that AI-generated tests verify the intended behavior rather than the implementation.

**Level 1: Test the effectiveness of security controls**

Use AI to verify that the standard security controls work correctly, for example authentication, access control, input validation, encoding, and encryption. People specify which standard security controls are in scope and what their expected behavior is.

The verification can be performed ad hoc, for example when the application changes its use of the controls, but each run should be well prepared. Provide the AI with the controls in scope and their expected behavior as context, and reuse the same prompts across runs, rather than just asking the AI to "verify that the standard security controls work correctly".

**Level 2: Define and run security test cases from requirements**

Developers use AI to write unit and integration test cases derived from the security requirements, to automatically verify the correct working of the security controls. Review the generated tests for meaningful assertions, as AI-generated tests may confirm the implementation rather than the requirement.

**Level 3: Automate security requirements testing**

Translate as many security requirements as possible into automated test cases, and include them in your build pipeline to run as a regression test suite for every run. Once again focus on making sure you are verifying the intent (i.e., the security requirements) and not the implementation.

#### V-RT-B: Misuse/Abuse Testing

Misuse and abuse testing is the counterpart of Control Verification: rather than confirming that controls work as intended, it tries to make them fail. AI can help write negative and abuse test cases and find choking points in the application, but only when given a meaningful description of the functionality under test.

**Level 1: Perform fuzz testing**

Use established fuzzing tools to generate and send the inputs, as they are far cheaper and faster at this than AI. Use AI where it adds value around them: identifying the main input parameters of the application, writing fuzzing harnesses and seed inputs, and triaging crashes for their security impact.

**Level 2: Define and run security abuse cases from requirements**

Use AI to write negative test cases for the security requirements, as well as more elaborate abuse test cases for key features, such as business logic attacks. Simply asking AI to write abuse cases does not produce meaningful results: provide a description of the feature, its business rules, and the security requirements that apply, and review the resulting test cases for relevance.

**Level 3: Perform security stress testing**

Stress testing is not only about network load, but about choking points in the application. Use AI to investigate the codebase for such choking points. Use AI to write test cases targeting these choking points, and to verify that rate limiting and other resource controls work as intended.

### Security Testing

#### V-ST-A: Scalable Baseline

Teams are often overwhelmed by the sheer amount of findings produced by automated security testing tools. AI can help with triaging and understanding findings, and with fixing them, as long as people stay on top of the fixes. Most importantly, AI can help customize static analysis tools into deterministic guardrails, which is essential now that massive amounts of code are written by AI.

**Level 1: Perform automated security testing**

Use AI to help triage the findings of automated security testing tools and to help development teams understand them, for example by explaining a finding in the context of their code. Be aware that AI is susceptible to suggestion and may dismiss true findings as false positives.

AI can also propose fixes for findings. Automated fixes by AI are a double-edged sword, as AI cannot guarantee a correct fix. People review every AI-proposed fix, and the fix is verified by re-running the tool and the relevant tests.

**Level 2: Develop application-specific security test cases**

Use AI to help customize static analysis tools, for example by writing custom rules for the organization's technologies, frameworks, and standards, or by tuning rules to reduce false positives and false negatives. These custom rules are the deterministic guardrails that ensure AI-generated code meets the organization's security standards (see Policy and Standards). Validate each rule against code samples that should and should not trigger it before rolling it out.

**Level 3: Integrate security testing tools in the delivery pipeline**

AI adds little to the integration of security testing tools into the delivery pipeline.

#### V-ST-B: Deep Understanding

In-depth security testing has always been limited by its cost: manual expert review is slow and hard to scale. This is where AI shines. AI is good at finding potential vulnerabilities at speed, making in-depth testing feasible for many more components and changes. Experts remain essential as they direct the AI with the right context, validate its findings, and judge their impact. Without that, AI-driven testing produces both missed issues and convincing false findings.

**Level 1: Test high risk application components manually**

Use AI to perform in-depth security reviews of high-risk components, such as authentication, access control enforcement, session management, external interfaces, and input parsers. Provide the AI with the context it needs, such as the relevant requirements, the catalog of controls, and the threat model, and focus it on how the component handles untrusted input. A qualified reviewer directs the review, validates each finding, for example by reproducing it, and discards false positives before findings are triaged.

**Level 2: Establish a penetration testing process**

Use AI to support penetration testing, for example by deriving application-specific test cases, exploring attack chains that combine several weaknesses, analyzing application responses, and writing proof-of-concept exploits. Penetration testers remain in control of the scope and the conclusions. Run AI-driven testing only against authorized targets and in non-production environments. Beware that AI testing agents may perform destructive actions.

Expect an increasing number of AI-generated reports in bug bounty programs, many of which are low quality. Define how such reports are triaged without overwhelming the team, for example by requiring a reproducible proof of concept.

**Level 3: Establish continuous, scalable security verification**

Make the results of in-depth testing scale by translating recurring issue types into deterministic guardrails, such as custom static analysis rules, so that they are caught early and consistently from then on. Also feed them back into the context of AI coding tools, such as the agent instruction files, to prevent the issues from being introduced in the first place.

## Operations

### Incident Management

#### O-IM-A: Incident Detection

In many organizations, the link between product teams and operations teams is weak, and operations teams look for generic attack patterns. AI offers a major opportunity to bridge this gap. You can leverage AI to derive application-specific attack patterns from the source code, help analyze logs for suspicious events, and help determine whether suspicious activity is an incident or legitimate behavior. However, log data may contain personal and other sensitive information. Giving AI access to it must comply with the organization's data protection policies and the AI-related data risks identified in its policies.

**Level 1: Use best-effort incident detection**

Use AI to help analyze available log data for anything suspicious, and to help determine whether suspicious activity is legitimate or a possible security incident. Only use approved AI tools that are allowed to process the data contained in the logs. Use personal data masking if possible.

**Level 2: Define an incident detection process**

Use AI to help create the checklist of expected attack vectors and known kill chains. Make the checklist application-specific by having AI derive possible attack patterns from the application's source code, for example which functionality is security-sensitive, and what its abuse would look like in the logs. This does not replace involving the product teams: they vet the AI-generated attack patterns before these are added to the checklist.

Use AI to help triage potential incidents. People decide on the escalation.

**Level 3: Improve the incident detection process**

Use AI to keep the checklist of suspicious events aligned with changes in the applications, for example by deriving new attack patterns when new functionality is released. AI can also compare the attack patterns with the log data the application actually produces, to identify missing log data needed for detection, which is then handled as a defect.

#### O-IM-B: Incident Response

AI can support incident responders, most notably in root cause analysis, and also in reconstructing timelines, documenting the response, and preparing playbooks and exercises. Decisions and response actions remain with people.
AI-assisted development introduces new types of incidents the organization must be prepared to respond to, such as secrets exposed to an AI provider or an AI agent performing unintended actions.

**Level 1: Create an incident response plan**

AI can help document the actions taken during an incident and reconstruct the timeline of events. Only share incident data with approved AI tools that are allowed to process it.

**Level 2: Define an incident response process**

Include incident scenarios related to AI-assisted development in the response process, for example secrets or sensitive data exposed to an AI provider, a compromised AI tool, plugin, or MCP server, an AI agent performing unintended or destructive actions, or prompt injection steering an AI tool. Define how to respond to them, for example how to quickly revoke the access and credentials of AI tools, using the inventory of AI tools and their permissions.

Use AI to support root cause analysis, for example by correlating log data and code changes to identify how an incident could happen. Make sure AI cannot modify any of the original evidence related to the incident. People verify the root cause before acting on it.

**Level 3: Establish an incident response team**

Use AI to generate realistic, application-specific scenarios for incident and emergency exercises, including scenarios related to AI-assisted development. AI can help automate response procedures, but do not let AI tools autonomously execute response actions, such as containment, in production environments.

### Environment Management

#### O-EM-A: Configuration Hardening

AI can help create hardening baselines, verify that configurations conform to them, and translate them into deterministic guardrails. At the same time, configuration itself is increasingly written by AI, for example infrastructure-as-code, container definitions, and deployment manifests, which makes enforcing the baselines automatically all the more important. Baselines remain owned by people.

**Level 1: Use best-effort hardening**

Use AI to help apply secure configurations to the elements of the technology stack. Verify AI suggestions against current vendor documentation or established benchmarks, as AI may propose outdated or insecure settings.
For applications with AI functionality, include its components in the stack to be hardened, such as model servers, AI gateways, and MCP servers.

**Level 2: Establish hardening baselines**

Use AI to help create hardening baselines and configuration guides for the components in each technology stack. Each baseline has an owner who is responsible for it; an AI tool cannot be the owner of a baseline. Make the baselines available in an AI-consumable format, so that AI tools generating configuration apply them (see Policy and Standards).

Use AI to help translate the baselines into deterministic guardrails, for example by creating or tuning the configuration of infrastructure-as-code scanners, static and dynamic analysis tools, or policy-as-code rules, so that configurations are checked against the baselines automatically.

**Level 3: Perform continuous configuration monitoring**

Use AI to help verify that deployed configurations conform to the baselines, complementing the deterministic checks, for example for components or settings the checks do not cover. AI can also help the baseline owners keep the baselines up to date, for example by identifying changes in vendor guidance or new component versions that affect them.

#### O-EM-B: Patching and Updating

The inventory of technology stack components and their versions, such as operating systems and their packages, runtimes, application servers, container base images, and frameworks, should be based on deterministic tools, such as host and package inventory tools, container image scanners, and cloud asset inventories. AI can complement them by filling gaps, by assessing whether a vulnerability is actually relevant to the application, and by reducing the effort of upgrading components, which makes timely patching more feasible.

**Level 1: Practice best-effort patching**

Use deterministic tools to determine the versions of components in use. AI can help identify components these tools miss, such as manually installed binaries or components referenced only in configuration. When notified of a vulnerability, AI can help assess whether the application is actually affected, for example whether it uses the vulnerable functionality.

**Level 2: Formalize patch management**

Use AI to reduce the effort of applying updates, for example by adapting the code to breaking changes in new component versions, so that regular releases including patches remain feasible. Such changes go through the same review and verification as any other change.

**Level 3: Enforce timely patch management**

Feed AI with external threat intelligence sources, such as security advisories, mailing lists, and researcher publications, and let it help determine how the reported vulnerabilities may affect the organization's applications and components. People verify the results before acting on them.

### Operational Management

#### O-OM-A: Data Protection

AI introduces major risks to data protection. Every AI tool is a potential channel through which data leaves the organization: through prompts, through the context AI tools read, through agents accessing files, databases, and environments, and through unapproved AI tools used outside the organization's control (shadow AI). Data stored locally on a single person's machine can propagate to an AI provider without anyone noticing. This calls for a much stricter approach to data governance.

At the same time, AI can help create and maintain the data catalog and build the deterministic and automated controls that enforce the data protection policy.

**Level 1: Organize basic data protections**

Include AI tools and providers in the understanding of where data ends up, in the same way as sharing with external partners. Do not share sensitive data with AI tools unless they are explicitly approved for it. Revisit any possible paths that production data can make it outside the production environment (such as database exports, logs, or test data in lower environments and on developers' machines) as AI tools working there can access them directly.

**Level 2: Establish a data catalog**

Use AI to help create and maintain the data catalog, for example by identifying data elements from database schemas, code, and data flows, and proposing their type and sensitivity classification. Avoid giving actual data to AI, use schemas and metadata instead. People validate the classification.

Record in the data catalog which data may be processed by which approved AI tools and providers, and include rules for AI use in the data protection policy (see Policy and Standards). Use AI to help create deterministic checks for data retention, so that retention requirements are enforced automatically.

**Level 3: Respond to data breaches**

Extend the technical controls enforcing the data protection policy to AI channels, for example by monitoring data sent to AI providers and detecting the use of unapproved AI tools.
Use AI to help create scripts for automated mechanisms, for example to audit backups and record deletions, or to review the data catalog against the data protection policy. People review the outcome and decide on updates.

#### O-OM-B: System Decommissioning / Legacy Management

AI can help identify unused systems and the resources associated with them, and reduce the effort of migrating away from legacy versions and end-of-life dependencies. Decommissioning must also cover AI-related resources, such as AI provider credentials and agent permissions.

**Level 1: Identify unused applications**

AI can help identify unused applications and services, for example by analyzing usage logs or references in code and configuration. People decide on decommissioning.

**Level 2: Formalize decommissioning process**

Use AI to help find all resources associated with a system being decommissioned, for example in infrastructure-as-code, configuration files, and access management, so that no accounts, firewall rules, secrets, or data are left behind. Include AI-related resources, such as AI provider credentials, service accounts and permissions of AI agents, and integrations such as MCP servers.

**Level 3: Review application lifecycle state regularly**

For applications with AI functionality, include the models and AI services they rely on in the lifecycle review, as AI providers deprecate models and change their services on short schedules. AI can help gather the support status and end-of-life information of software assets and components across the portfolio, which people verify.
