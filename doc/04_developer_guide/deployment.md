# Deployment Guide: Deploying to Base Testnet

## Overview

This guide walks you through deploying RoamX smart contracts to the Base Sepolia testnet using Foundry. Deployment covers key contracts like `Escrow`, `ROAMToken`, and `UsageTracker`, ensuring a functional P2P data exchange on Arbitrum's Layer 2 network.

## Prerequisites

- Foundry installed and project set up (see [setup guide](setup.md)).
- Contracts tested (see [testing guide](testing.md)).
- A Base Sepolia RPC URL and a funded testnet wallet (e.g., via Sepolia faucet).
- Environment variables configured in `.env` (see below).

## Step-by-Step Deployment

### 1. Prepare Environment Variables

- **Create `.env`**: In the project root, add:

  BASE_SEPOLIA_RPC=https://sepolia-rollup.arbitrum.io/rpc
  PRIVATE_KEY=your_private_key_here

- **Fund Wallet**: Use a Sepolia faucet (e.g., https://sepoliafaucet.com/) to get test ETH for gas.
- **Security**: Never commit `.env`—add to `.gitignore`.

### 2. Write Deployment Scripts

- **Location**: Create scripts in `script/` (e.g., `DeployEscrow.s.sol`).
- **Example: `script/DeployEscrow.s.sol`**
- **Additional Scripts**:
  - `DeployROAMToken.s.sol`: Deploys `ROAMToken.sol` with initial supply.
  - `FundTestWallets.s.sol`: Transfers test $ROAM to addresses.

### 3. Configure Foundry for Deployment

- **Update `foundry.toml`**: Ensure RPC endpoint is set:

  ```toml
  [profile.default]
  src = "contracts"
  test = "test"
  out = "out"
  libs = ["lib"]
  rpc_endpoints = { arbitrum_sepolia = "https://sepolia-rollup.arbitrum.io/rpc" }
  optimizer = true
  optimizer_runs = 200
  ```

- **Verify**: Run `forge config` to confirm settings.

### 4. Deploy Contracts

- **Command**: Deploy a single contract:
  ```bash
  forge script script/DeployEscrow.s.sol --rpc-url $ARBITRUM_SEPOLIA_RPC --private-key $PRIVATE_KEY --broadcast
  ```
- **Multi-Contract Deployment**: Use a combined script or chain commands:
  ```bash
  forge script script/DeployEscrow.s.sol script/DeployROAMToken.s.sol --rpc-url $ARBITRUM_SEPOLIA_RPC --private-key $PRIVATE_KEY --broadcast
  ```
- **Verify Deployment**: Check transaction on Arbiscan (e.g., https://sepolia.arbiscan.io/) using the returned address.
- **Output**: Logs contract addresses (e.g., "Escrow deployed at: 0x...").

### 5. Verify Contracts on Arbiscan

- **Command**: Verify source code:
  ```bash
  forge verify-contract --chain-id 421614 --constructor-args $(cast abi-encode "constructor()" "") 0xYourContractAddress Escrow
  ```
- **Note**: Replace `0xYourContractAddress` with the deployed address and adjust constructor args if needed.

### 6. Post-Deployment Checks

- **Test Interactions**: Use `cast` to call functions:
  ```bash
  cast call 0xYourEscrowAddress "sessions(uint256)(address,address,uint256,uint256,bool,bytes)" 1
  ```
- **Update App**: Configure React Native app with deployed addresses (via Wagmi).

## Best Practices

- **Gas Optimization**: Use `forge snapshot` pre-deployment to minimize costs.
- **Multi-Sig**: Consider a Gnosis Safe for production deployment (post-MVP).
- **Logging**: Add events in contracts for tracking (e.g., `SessionCreated`).
- **Rollback**: Save deployment scripts for redeployment if needed.

## Troubleshooting

- **RPC Errors**: Ensure `.env` URL is valid; try a free provider (e.g., Infura).
- **Out of Gas**: Increase gas limit with `--gas-limit 10000000`.
- **Contract Not Found**: Verify address and chain ID (421614 for Arbitrum Sepolia).

## Next Steps

- Integrate with [API endpoints](api_endpoints.md) for app interactions.
- Explore advanced deployments (e.g., upgrades) post-MVP.

[Previous: Learn [testing](testing.md) with Forge.]
[Back to [developer guide index](index.md).]
