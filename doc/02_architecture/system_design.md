# RoamX System Design

## Overview

This section outlines the architectural design of RoamX, a decentralized peer-to-peer (P2P) data exchange platform. As of September, 2025, the system is structured to support offline bootstrapping, global hotspot connectivity, and trustless transactions, aligning with the MVP goals for Q3 2025. The design integrates blockchain, networking, and application layers into a cohesive ecosystem.

## Component Breakdown

### 1. Blockchain Layer

- **Foundry Contracts**: Deploys and tests smart contracts on Base using Solidity/Vyper.
  - **Escrow**: Manages $ROAM escrow for sessions, releasing funds upon ZK proof verification.
  - **ROAMX**: ERC-20 token for payments, staking, and governance.
  - **UsageTracker**: Logs session usage (tcpdump → ZK proofs) and triggers payouts.
  - **Admin**: Controls fees (1%) and emergency functions.
- **Base**: Layer 2 solution for low-cost, high-throughput transactions.
- **ERC-4337**: Enables gasless payments via a Node.js relayer.
- **Chainlink Oracles**: Verifies off-chain data (e.g., usage, host uptime).

### 2. Networking Layer

- **WireGuard VPN**: Embedded in the app, creates secure P2P tunnels between buyers and hosts.
- **Libp2p/WebRTC**: Handles peer discovery and NAT traversal, supporting global connections.
- **tcpdump + ZK Proofs**: Captures usage data, processed into privacy-preserving proofs (e.g., Semaphore).
- **Starlink Direct-to-Cell (DTC)**: Provides 20MB seed data in offline scenarios, handing off to WireGuard tunnels.

### 3. Application Layer

- **React Native + Expo**: Mobile app with PWA support for offline caching and installation.
- **Redux/Wagmi**: Manages state and wallet interactions with Base.
- **Ceramic/IPFS**: Stores marketplace data (hotspot listings) and caches for offline use.
- **Node.js Relayer**: Facilitates meta-transactions for ERC-4337.

### 4. Data Bank and Offline Bootstrap

- **Data Bank**: A pooled resource (funded by 1% protocol fees) delivering seed data via Starlink DTC.
- **Service Workers**: Cache marketplace UI and hotspot data offline using Workbox.

## System Diagram

[Insert Diagram Here]

- **Suggested Layout**: Use Draw.io or Figma to create a flowchart:
  - **Top Level**: Blockchain Layer (Base, Foundry contracts).
  - **Middle Left**: Networking Layer (WireGuard, Libp2p, DTC).
  - **Middle Right**: Application Layer (React Native, Ceramic/IPFS).
  - **Bottom**: Data Bank feeding into DTC, connecting all layers.
  - **Arrows**: Show data flow (e.g., ZK proofs to Escrow, DTC to WireGuard).
- **Example Description**: "A user opens the app offline → Starlink DTC provides 20MB → Cached IPFS data loads marketplace → WireGuard connects to a host → UsageTracker submits ZK proof → Escrow settles payment on Base."

## Data Flow

1. **Offline Bootstrap**: User in a dead zone (e.g., rural Nigeria) opens the app → Starlink DTC auto activates 20MB → PWA loads cached hotspot listings.
2. **Connection**: User selects a host (nearby or global) → WireGuard tunnel establishes → Libp2p/WebRTC ensures NAT traversal.
3. **Usage Tracking**: tcpdump logs session data → ZK proof generated → Submitted to UsageTracker.
4. **Settlement**: Escrow releases $ROAM to host (minus 1% fee) → Refund excess to buyer → Chainlink verifies uptime.
5. **Sync**: Ceramic/IPFS updates marketplace; Relayer handles gasless txs.

## Key Interactions

- **Buyer-Host**: P2P tunnel via WireGuard, mediated by smart contracts.
- **App-Blockchain**: Wagmi relays user actions to Base; Relayer processes meta-tx.
- **Offline-Online**: DTC hands off to P2P network post-seed, syncing via IPFS.

## Design Considerations

- **Scalability**: Global hotspots supported by Libp2p; DTC extends reach to unserved areas.
- **Security**: ZK proofs ensure privacy; ERC-4337 mitigates gas costs.
- **Performance**: Nearby hotspots prioritized for low latency; global fallback uses QUIC for UDP efficiency.
- **Resilience**: DTC and cached data handle offline scenarios; Tor integration planned for censorship resistance.

## Future Enhancements

- **AI Pricing**: Integrate dynamic pricing via Chainlink (post-MVP).
- **Fiat Onboarding**: Add Stripe for $ROAM top-ups (Q1 2026).
- **Multi-Chain**: Explore Polygon/ZK-Rollups for broader adoption.

[Next: Dive into our [network model](network_model.md) for global vs. nearby hotspot logic.]
