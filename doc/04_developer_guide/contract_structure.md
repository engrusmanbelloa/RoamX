# Contract Structure

## Overview

This guide details the folder structure for RoamX's smart contracts, designed for development with Foundry on Base. During the MVP phase (Q3 2025), this structure supports the core functionality escrow, $ROAM token management, usage tracking with ZK proofs, and admin controls—while ensuring modularity and scalability for the decentralized P2P data exchange.

## Contract Folder Structure

The structure is organized within the `contracts/` directory of the RoamX repository, adhering to Foundry conventions. Below is the recommended layout:

```

roamx/
├── contracts/
│ ├── interfaces/ # Interface definitions for modularity
│ │ ├── IEscrow.sol # Escrow contract interface
│ │ ├── IROAMToken.sol # $ROAM token interface
│ │ ├── IUsageTracker.sol # Usage tracking interface
│ │ └── IAdmin.sol # Admin controls interface
│ ├── core/ # Core business logic contracts
│ │ ├── Escrow.sol # Manages payment escrow and ZK proof release
│ │ ├── ROAMToken.sol # ERC-20 $ROAM token with staking
│ │ ├── UsageTracker.sol # Tracks session usage with ZK integration
│ │ └── Admin.sol # Platform fee/hosting fee controls
│ ├── mocks/ # Mock contracts for testing
│ │ ├── MockOracle.sol # Mock Chainlink oracle for testing
│ │ ├── MockERC4337.sol # Mock account abstraction for gasless tx
│ │ └── MockZKProof.sol # Mock ZK proof generator
│ ├── libraries/ # Reusable utility code
│ │ ├── SafeMath.sol # Safe arithmetic operations
│ │ └── ZKUtils.sol # ZK proof helper functions (e.g., Semaphore)
│ └── utils/ # Helper contracts/tools
│ ├── Initializable.sol # Upgradeable contract base
│ └── Ownable.sol # Ownership management
├── script/ # Deployment and interaction scripts
│ ├── DeployEscrow.s.sol # Deploy escrow contract
│ ├── DeployROAMToken.s.sol # Deploy $ROAM token
│ └── FundTestWallets.s.sol # Fund test wallets with $ROAM
├── test/ # Unit and integration tests
│ ├── Escrow.t.sol # Tests for escrow logic
│ ├── ROAMToken.t.sol # Tests for token functionality
│ ├── UsageTracker.t.sol # Tests for usage tracking
│ └── Integration.t.sol # End-to-end tests
├── foundry.toml # Foundry configuration file
└── README.md # Project overview

```

## Detailed Breakdown

### `interfaces/`

- Contains abstract contract definitions for external interactions.
- Example: `IEscrow.sol` defines functions like `createSession` and `settleSession` for modular testing.

### `core/`

- Houses the main business logic:

  - **Escrow.sol**: Escrows $ROAM, releases on ZK proof (Chainlink-verified).
  - **ROAMToken.sol**: ERC-20 with staking logic.
  - **UsageTracker.sol**: Processes tcpdump data into ZK proofs.
  - **Admin.sol**: Manages fees and emergency stops.

### `mocks/`

- Mock contracts for testing (e.g., `MockERC4337` simulates gasless txs).

### `libraries/`

- Reusable code (e.g., `ZKUtils` for Semaphore integration).

### `utils/`

- Base contracts (e.g., `Initializable.sol` for upgrades).

### `script/`

- Deployment scripts (e.g., `DeployEscrow.s.sol` uses `forge script`).

### `test/`

- Comprehensive tests (e.g., `Integration.t.sol` for end-to-end flows).

## Setup Instructions

1. **Create Folders**: Manually set up `interfaces/`, `core/`, etc., in `contracts/`.
2. **Add Contracts**: Start with `core/Escrow.sol` and expand.
3. **Install Dependencies**: `forge install OpenZeppelin/openzeppelin-contracts`.
4. **Configure**: Update `foundry.toml` as per [setup guide](setup.md).

## Best Practices

- **Modularity**: Use interfaces for external calls.
- **Testing**: Cover all edge cases (e.g., ZK proof failures).
- **Security**: Audit contracts pre-deployment (e.g., via OpenZeppelin Defender).

[Previous: Check the [setup guide](setup.md) for installation.]
[Next: Learn [testing](testing.md) with Forge.]
