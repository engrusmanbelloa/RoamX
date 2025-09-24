# RoamX Tech Stack

## Overview

RoamX is built on a robust, decentralized tech stack designed to deliver a seamless, secure, and scalable P2P data exchange. This section outlines the tools, frameworks, and protocols powering the platform, enabling global connectivity, offline bootstrapping, and trustless transactions as of September 18, 2025.

## Core Technologies

### Blockchain and Smart Contracts

- **Foundry**: Our development and testing framework, chosen for its speed (parallel testing via Forge), gas optimization, and EVM compatibility. Foundry powers contract development, deployment, and testing on Base.
- **Base**: The Layer 2 scaling solution for Ethereum, providing low-cost, high-throughput transactions. Used for deploying $ROAM token, escrow, and usage tracking contracts.
- **ERC-4337 (Account Abstraction)**: Enables gasless user experiences by abstracting transaction signing. Integrated via a relayer for seamless $ROAM payments.
- **Solidity/Vyper**: Primary languages for writing smart contracts, ensuring security and efficiency (e.g., `Escrow.sol` for session settlements).
- **Chainlink Oracles**: Verifies off-chain data (e.g., usage stats, host uptime) for ZK proof validation and refunds.

### Networking and VPN

- **WireGuard**: A lightweight, high-performance VPN protocol embedded in the app for P2P tunnels. Supports global connections with minimal overhead, optimized for mobile devices.
- **Libp2p/WebRTC**: Facilitates NAT traversal and peer discovery, enabling connections across firewalls and regions. WebRTC's QUIC protocol enhances UDP performance for long-distance links.
- **tcpdump + ZK Proofs**: Captures session usage data, processed into Zero-Knowledge proofs (e.g., via Semaphore) for privacy-preserving verification on-chain.

### Application Layer

- **React Native + Expo**: Cross-platform mobile app development with Progressive Web App (PWA) support for offline caching and installation via pre-shared links.
- **Redux/Wagmi**: Manages app state and wallet interactions, integrating with Arbitrum for $ROAM transactions.
- **Ceramic/IPFS**: Decentralized storage for marketplace data (e.g., hotspot listings) and offline caches, ensuring resilience and censorship resistance.
- **Node.js Relayer**: Handles meta-transactions for ERC-4337, bridging app and blockchain layers.

### Offline Bootstrapping

- **Starlink Direct-to-Cell (DTC)**: Provides 20MB seed data in dead zones via satellite, auto activating on app open. Leverages unmodified LTE devices for seamless connectivity in remote areas (e.g., rural Nigeria, Kenyan safaris).
- **Service Workers**: Cache marketplace UI and hotspot data offline, enhancing PWA functionality with Workbox.

### Token and Incentives

- **$ROAM Token (ERC-20)**: Fuels the ecosystem with staking (10% buyer discounts), governance, and rewards. Minted and managed via Foundry deployed contracts.
- **Data Bank**: A pooled resource (funded by 1% protocol fees) delivering seed data, transitioning users to token-based usage.

## Integration Points

- **App to Blockchain**: Wagmi connects React Native to Base contracts, with relayer handling gasless txs.
- **Networking to Contracts**: ZK proofs from tcpdump are submitted to `UsageTracker.sol`, triggering escrow releases in `Escrow.sol`.
- **Offline to Online**: Starlink DTC hands off to WireGuard tunnels post-seed, syncing with Ceramic/IPFS for real-time updates.

## Why This Stack?

- **Speed**: Foundry and Base optimize development and transaction costs.
- **Scalability**: WireGuard and Libp2p support global P2P, while DTC extends reach to unserved regions.
- **Security**: ZK proofs and ERC-4337 ensure trust and privacy.
- **User-Centric**: Mobile-first design with offline bootstrapping reduces barriers.

## Future Enhancements

- **Tor Integration**: For enhanced censorship resistance (Q1 2026).
- **Fiat Onboarding**: Stripe integration for $ROAM top-ups (Q1 2026).
- **AI Pricing**: Dynamic pricing models via Chainlink oracles (post-MVP).

[Next: Explore our [system design](system_design.md) for a visual breakdown of components.]
