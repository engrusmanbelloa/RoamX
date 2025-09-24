# Setup Guide: Foundry Installation and Project Setup

## Overview

This guide walks you through installing Foundry, a fast and efficient Ethereum development toolkit, and setting up the RoamX project for development. RoamX uses Foundry for smart contract development on Base, alongside React Native for the app. Follow these steps to get started.

## Prerequisites

- **Operating System**: macOS, Linux, or Windows (WSL recommended for Windows).
- **Tools**: Git, Node.js (v18+), npm, and a code editor (e.g., VS Code).
- **Internet**: Stable connection for package downloads and RPC access.

## Step-by-Step Setup

### 1. Install Foundry

- **Command**: Open your terminal and run:

  ```bash
  curl -L https://foundry.paradigm.xyz | bash
  ```

- **Update**: After installation, run:
  ```bash
  foundryup
  ```
  This ensures you have the latest version (v0.2.0+ as of Sept 2025).
- **Verify**: Check installation with:
  ```bash
  forge --version
  cast --version
  anvil --version
  ```
  Expected output: e.g., `forge 0.2.0 (abcd123...)`.

### 2. Clone the RoamX Repository

- **Command**: Navigate to your workspace and clone the repo:
  ```bash
  git clone https://github.com/yourusername/roamx.git
  cd roamx
  ```

### 3. Initialize the Foundry Project

- **Command**: Set up the basic Foundry structure:
  ```bash
  forge init --template minimal
  ```
- **Customize**: Move or create the `contracts/`, `script/`, and `test/` folders as outlined in [contract structure](contract_structure.md).

### 4. Install Dependencies

- **Smart Contracts**: Add OpenZeppelin contracts for base functionality:
  ```bash
  forge install OpenZeppelin/openzeppelin-contracts
  ```
- **App**: Install React Native dependencies:
  ```bash
  cd app && npm install
  ```
- **Note**: Ensure `foundry.toml` is configured (see below).

### 5. Configure Foundry

- **Edit `foundry.toml`**: Add the following to the project root:
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
- **Explanation**: Sets source paths, test output, and Arbitrum Sepolia RPC for testing.

### 6. Set Up Environment Variables

- **Create `.env`**: In the root, add:
  ```
  ARBITRUM_SEPOLIA_RPC=https://sepolia-rollup.arbitrum.io/rpc
  PRIVATE_KEY=your_private_key_here
  ```
- **Security**: Never commit `.env`—add it to `.gitignore`. Use a testnet key (e.g., from MetaMask).

### 7. Start Development Environment

- **Local Node**: Launch Anvil for testing:
  ```bash
  anvil
  ```
- **App**: Run the React Native app:
  ```bash
  cd app && expo start
  ```
- **Contracts**: Compile and test:
  ```bash
  forge build
  forge test
  ```

## Troubleshooting

- **Foundry Install Fails**: Ensure curl is installed (`sudo apt install curl` on Linux).
- **RPC Errors**: Verify `.env` RPC URL or use a free provider (e.g., Infura).
- **App Crashes**: Check Node.js version and clear npm cache (`npm cache clean --force`).

## Next Steps

- Explore the [contract structure](contract_structure.md) for folder details.
- Run tests with [testing guide](testing.md) to validate contracts.
- Deploy to Arbitrum with [deployment guide](deployment.md).

[Back to [developer guide index](index.md).]
