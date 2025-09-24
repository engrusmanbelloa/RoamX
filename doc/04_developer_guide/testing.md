# Testing Guide: Testing with Forge

## Overview

This guide explains how to test RoamX smart contracts using Forge, Foundry's testing framework, as of September 23, 2025, during the MVP phase (Q3 2025). Forge enables fast, parallel unit and integration testing for contracts like `Escrow`, `ROAMToken`, and `UsageTracker` on Arbitrum. Follow these steps to ensure robustness and security.

## Prerequisites

- Foundry installed and project set up (see [setup guide](setup.md)).
- Contracts structured as per [contract structure](contract_structure.md).
- Anvil running locally: `anvil` (default port 8545).

## Testing Structure

Tests reside in the `test/` directory, with files ending in `.t.sol` (e.g., `Escrow.t.sol`). Use Solidity for test scripts, leveraging Forge's DSL.

## Step-by-Step Testing

### 1. Write Unit Tests

- **Purpose**: Test individual contract functions (e.g., `createSession` in `Escrow.sol`).
- **Example: `test/Escrow.t.sol`**
- **Notes**: Use `vm.prank` for sender simulation, `vm.deal` for ETH, and mocks for dependencies.

### 2. Write Integration Tests

- **Purpose**: Test contract interactions (e.g., `Escrow` with `UsageTracker`).
- **Example: `test/Integration.t.sol`**
- **Notes**: Simulate full flows; use mocks for external calls (e.g., Chainlink).

### 3. Run Tests

- **Command**: In the project root:
  ```bash
  forge test
  ```
- **Options**:
  - Filter tests: `forge test --match-test testCreateSession`
  - Debug: `forge test --match-test testSettleSession -vv`
  - Fuzz: `forge test --match-contract EscrowTest -vvvv` (runs 256 inputs).
- **Output**: Displays pass/fail, gas usage, and logs.

### 4. Test Coverage

- **Command**: Generate coverage report:
  ```bash
  forge coverage
  ```
- **Analyze**: Check `coverage.json` for uncovered lines; aim for >90% coverage.
- **Tool**: Use `forge coverage --report lcov` and import into a viewer (e.g., lcov.info).

## Best Practices

- **Isolation**: Test each function independently with mocks.
- **Edge Cases**: Cover ZK proof failures, low balances, and <80% uptime.
- **Gas Optimization**: Use `forge snapshot` to track gas costs.
- **CI/CD**: Integrate with GitHub Actions (e.g., `forge test` on push).

## Troubleshooting

- **Test Fails**: Check `vm.prank` sender; ensure Anvil is running.
- **Gas Issues**: Adjust `foundry.toml` optimizer settings.
- **Coverage Low**: Add tests for untested branches (e.g., `withdrawFees`).

## Next Steps

- Deploy tested contracts with the [deployment guide](deployment.md).
- Explore [API endpoints](api_endpoints.md) for app integration.

[Previous: Review the [contract structure](contract_structure.md).]
[Back to [developer guide index](index.md).]
