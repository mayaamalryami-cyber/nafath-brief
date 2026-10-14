## Software
The Twelve-Factor App defines config as everything likely to vary between deploys, such as database handles and credentials for external services. It must be stored in environment variables, not as constants in the code, because the methodology requires strict separation of config from code. The test: could the codebase be made open source at any moment without compromising any credentials? Environment variables are also easy to change per deploy and rarely committed by accident.
Resource: III. Config - The Twelve-Factor App - https://12factor.net/config

## AI
NIST classifies attacks by lifecycle stage and by goal: availability, integrity or privacy. Evasion happens after deployment: the attacker slightly changes an input to create an adversarial example that the model misclassifies. Poisoning happens during training: the attacker inserts or modifies training data, or controls the model's parameters, for example a supplier's poisoned model. Privacy attacks, such as membership inference, try to learn about the training data or the model.
Resource: NIST AI 100-2e2025 - Adversarial Machine Learning: A Taxonomy and Terminology of Attacks and Mitigations - https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-2e2025.pdf

## Mobile
MASVS is OWASP's security standard for mobile apps, used as a metric, guidance and baseline for security verification, including during procurement. Its controls sit in eight groups: STORAGE, CRYPTO, AUTH, NETWORK, PLATFORM, CODE, RESILIENCE and PRIVACY, numbered like MASVS-CODE-3. Testers assess the app against these controls with MASTG test cases, using a MAS testing profile chosen by risk with business owners. Backend servers are checked separately with OWASP ASVS.
Resource: The Mobile Application Security Verification Standard - OWASP Mobile Application Security - https://mas.owasp.org/MASVS/03-Using_the_MASVS/

