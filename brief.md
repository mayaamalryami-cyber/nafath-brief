## Networking
BGP routers trust route announcements from neighbours, so a network can mis-announce a prefix it does not hold and pull the owner's traffic towards itself. With RPKI, the holder publishes signed Route Origin Authorizations (ROAs) naming which AS may originate the prefix. Routers mark each route Valid, Invalid or NotFound and can block Invalid ones. RPKI checks only the origin AS, not the path, so a forged path ending in the valid AS still succeeds.
Resource: RFC 6811 - BGP Prefix Origin Validation - https://www.rfc-editor.org/rfc/rfc6811

## Cybersecurity
Log4Shell (CVE-2021-44228) was a flaw in log4j-core, part of the Apache Log4j 2 Java logging library. Its JNDI features did not protect against attacker-controlled LDAP endpoints, so anyone controlling a log message could make the server load and run arbitrary code. It scored 10.0 Critical: attackable over the network, low complexity, no privileges or user interaction needed. Apache fixed it in 2.15.0 for Java 8, 2.12.2 for Java 7 and 2.3.1 for Java 6.
Resource: Security - Apache Logging Services - https://logging.apache.org/security.html

## Data
An SBOM is a nested inventory, a list of ingredients that make up software. The 2026 CISA Minimum Elements, which replace the NTIA 2021 list, set two groups of data fields. SBOM Metadata: author, author signature, data format name and version, generation context, timestamp, tool name and version, and SBOM version. Component Data: producer, name, version, identifiers, hash value and hash algorithm, license, and dependency relationship. An SBOM should cover all components, including transitive dependencies.
Resource: 2026 Minimum Elements for a Software Bill of Materials (SBOM) - https://www.cisa.gov/sites/default/files/2026-07/2026_cisa_sbom_minimum_elements_508c.pdf
