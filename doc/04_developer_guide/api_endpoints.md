# API Endpoints: Relayer and App Contract Interactions

## Overview

This guide details the API endpoints and interactions for RoamX's relayer (Node.js-based for ERC-4337 gasless payments) and smart contract calls (via Wagmi in the React Native app). These enable seamless app-blockchain integration for escrow, $ROAM transfers, and ZK proof submissions on Arbitrum. The relayer handles meta-transactions, while Wagmi hooks facilitate direct contract reads/writes.

## Relayer API (ERC-4337 Meta-Transactions)

The Node.js relayer acts as a bundler/relayer for gasless UserOperations, submitting bundles to the EntryPoint contract (e.g., 0x5FF137D4b0FDCD49DcA30c7CF57E578a026d2789 on Arbitrum Sepolia). It exposes REST endpoints for app integration, using Express.js. Deployed at `https://relayer.roamx.network` (or local: `http://localhost:3001`).

### Key Endpoints

### Implementation Notes

- **Security**: Rate-limit requests (e.g., via express-rate-limit); validate UserOps with signature checks.
- **Integration**: App calls relayer for gasless ops (e.g., createSession without ETH).

## App Contract Interactions (Wagmi Hooks)

### Key Hooks and Examples

## Best Practices

- **Error Handling**: Use `useWaitForTransactionReceipt` for confirmations; fallback to relayer for gasless.
- **Offline Support**: Cache reads in Redux; sync on Starlink DTC bootstrap.
- **Security**: Validate ZK proofs client-side before submission.

## Next Steps

- Implement relayer in Node.js (see examples from eth-infinitism/bundler).
- Test interactions with Wagmi in app simulator.

[Previous: Review [deployment](deployment.md).]
[Back to [developer guide index](index.md).]
