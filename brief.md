Version: NAFATH-V4
Track: Software

## Overview
A national service provider depends on code, AI models and internet routes that it did not fully build, and an attacker needs to compromise only one link. The six fields protect different links of this chain. In Software, credentials kept outside the code cannot leak when the code is shared. In AI, training data and supplied models can be poisoned before they reach production. In Mobile, MASVS gives a standard way to verify the apps that citizens install. In Networking, RPKI blocks some false route announcements, but not all of them. In Cybersecurity, Log4Shell showed how one hidden logging library let attackers run code remotely. In Data, an SBOM lists every component, so a vulnerable one is found quickly. My own track is Software, so my focus is where the Twelve-Factor App says configuration and secrets belong.

## Software
The Twelve-Factor App defines config as everything likely to vary between deploys, such as database handles and credentials for external services. It must be stored in environment variables, not as constants in the code, because the methodology requires strict separation of config from code. The test: could the codebase be made open source at any moment without compromising any credentials? Environment variables are also easy to change per deploy and rarely committed by accident.
Resource: III. Config - The Twelve-Factor App - https://12factor.net/config

## AI
NIST classifies attacks by lifecycle stage and by goal: availability, integrity or privacy. Evasion happens after deployment: the attacker slightly changes an input to create an adversarial example that the model misclassifies. Poisoning happens during training: the attacker inserts or modifies training data, or controls the model's parameters, for example a supplier's poisoned model. Privacy attacks, such as membership inference, try to learn about the training data or the model.
Resource: NIST AI 100-2e2025 - Adversarial Machine Learning: A Taxonomy and Terminology of Attacks and Mitigations - https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-2e2025.pdf

## Mobile
MASVS is OWASP's security standard for mobile apps, used as a metric, guidance and baseline for security verification, including during procurement. Its controls sit in eight groups: STORAGE, CRYPTO, AUTH, NETWORK, PLATFORM, CODE, RESILIENCE and PRIVACY, numbered like MASVS-CODE-3. Testers assess the app against these controls with MASTG test cases, using a MAS testing profile chosen by risk with business owners. Backend servers are checked separately with OWASP ASVS.
Resource: The Mobile Application Security Verification Standard - OWASP Mobile Application Security - https://mas.owasp.org/MASVS/03-Using_the_MASVS/

## Networking
BGP routers trust route announcements from neighbours, so a network can mis-announce a prefix it does not hold and pull the owner's traffic towards itself. With RPKI, the holder publishes signed Route Origin Authorizations (ROAs) naming which AS may originate the prefix. Routers mark each route Valid, Invalid or NotFound and can block Invalid ones. RPKI checks only the origin AS, not the path, so a forged path ending in the valid AS still succeeds.
Resource: RFC 6811 - BGP Prefix Origin Validation - https://www.rfc-editor.org/rfc/rfc6811

## Cybersecurity
Log4Shell (CVE-2021-44228) was a flaw in log4j-core, part of the Apache Log4j 2 Java logging library. Its JNDI features did not protect against attacker-controlled LDAP endpoints, so anyone controlling a log message could make the server load and run arbitrary code. It scored 10.0 Critical: attackable over the network, low complexity, no privileges or user interaction needed. Apache fixed it in 2.15.0 for Java 8, 2.12.2 for Java 7 and 2.3.1 for Java 6.
Resource: Security - Apache Logging Services - https://logging.apache.org/security.html

## Data
An SBOM is a nested inventory, a list of ingredients that make up software. The 2026 CISA Minimum Elements, which replace the NTIA 2021 list, set two groups of data fields. SBOM Metadata: author, author signature, data format name and version, generation context, timestamp, tool name and version, and SBOM version. Component Data: producer, name, version, identifiers, hash value and hash algorithm, license, and dependency relationship. An SBOM should cover all components, including transitive dependencies.
Resource: 2026 Minimum Elements for a Software Bill of Materials (SBOM) - https://www.cisa.gov/sites/default/files/2026-07/2026_cisa_sbom_minimum_elements_508c.pdf

## Misconception in My Track
A common wrong belief is that passwords and API keys are safe inside the code, or inside a config file committed to the repository, as long as the repository is private. The Twelve-Factor App says the opposite: storing config as constants in code is a violation, and even config files kept outside Git are easy to check in by mistake. Its litmus test, in the section "III. Config", is: "A litmus test for whether an app has all config correctly factored out of the code is whether the codebase could be made open source at any moment, without compromising any credentials."

## Open Question
How can the provider check, before deployment, that a pre-trained AI model from an outside supplier has not been poisoned? I would learn which extra SBOM elements CISA expects for AI systems, since the 2026 guidance says AI software may need more than the minimum.

