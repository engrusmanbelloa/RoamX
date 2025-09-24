# Contribution Guidelines

## Overview

RoamX welcomes contributions from the community to build a decentralized P2P data exchange. During the MVP phase (Q3 2025), this guide outlines the process for submitting pull requests (PRs), reporting issues, and collaborating on GitHub. All contributions must align with our code of conduct and technical standards.

## Code of Conduct

- Be respectful, inclusive, and collaborative.
- No harassment, discrimination, or offensive language.
- Follow the Contributor Covenant (see CODE_OF_CONDUCT.md).

## How to Contribute

### 1. Report Issues

- **Use GitHub Issues**: Open an issue for bugs, features, or questions.
- **Template**: Use the provided templates (e.g., Bug Report, Feature Request).
- **Details**: Include:
  - Description: Clear summary.
  - Steps to Reproduce: For bugs.
  - Expected vs. Actual: Behavior.
  - Environment: OS, Foundry version, Arbitrum network.
- **Labels**: Add labels (e.g., "bug", "enhancement", "MVP").

### 2. Submit Pull Requests (PRs)

- **Fork the Repo**: Fork https://github.com/yourusername/roamx on GitHub.
- **Branching**: Create a feature branch (e.g., `feature/add-zk-utils`).
- **Development**:
  - Follow [contract structure](contract_structure.md) for contracts.
  - Use Foundry for testing (see [testing guide](testing.md)).
  - App changes: React Native standards, test with Expo.
- **Commit Guidelines**: Use conventional commits (e.g., "feat: add escrow contract", "fix: latency alert").
- **PR Process**:
  - Open PR against `main` branch.
  - Title: Descriptive (e.g., "feat: integrate Starlink DTC bootstrap").
  - Description: Explain changes, reference issues (e.g., "Closes #123").
  - Add screenshots/diagrams for UX changes.
- **Review**: PRs require 1+ approvals; CI tests (Forge, npm) must pass.

### 3. Contribution Types

- **Code**: Contracts (Solidity), app (React Native), relayer (Node.js).
- **Docs**: Update this guide or add tutorials.
- **Testing**: Add Forge tests or app unit tests.
- **Features**: Propose via issues; align with roadmap (e.g., AI pricing).

## Tools and Standards

- **Foundry**: For contracts—build/test with `forge build`, `forge test`.
- **Linting**: Solidity: Solhint; JS: ESLint (run `npm run lint`).
- **Commit Hooks**: Use Husky for pre-commit checks.
- **Security**: All PRs scanned for vulnerabilities (e.g., Mythril).

## Review Process

- **Time**: Reviews within 48 hours; major changes may take longer.
- **Feedback**: Constructive; address comments before re-request.
- **Merge**: Maintainers merge once approved and tests pass.

## Rewards for Contributors

- **$ROAM Airdrops**: Eligible for community rewards (40% allocation) based on impact.
- **Recognition**: Featured in release notes and community.md.

## Questions?

- Open an issue or join X (@roamx_network) / Discord.

[Next: Learn [community engagement](community.md).]
[Back to [contributing index](index.md).]
