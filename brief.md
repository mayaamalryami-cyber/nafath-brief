## Misconception in My Track
A common wrong belief is that passwords and API keys are safe inside the code, or inside a config file committed to the repository, as long as the repository is private. The Twelve-Factor App says the opposite: storing config as constants in code is a violation, and even config files kept outside Git are easy to check in by mistake. Its litmus test, in the section "III. Config", is: "A litmus test for whether an app has all config correctly factored out of the code is whether the codebase could be made open source at any moment, without compromising any credentials."

## Open Question
How can the provider check, before deployment, that a pre-trained AI model from an outside supplier has not been poisoned? I would learn which extra SBOM elements CISA expects for AI systems, since the 2026 guidance says AI software may need more than the minimum.
