# RoamX: Decentralized Mobile Data Exchange

Roam Freely, Pay Less, Own the Network.

## Overview

RoamX is a peer-to-peer (P2P) marketplace that empowers users with surplus internet bandwidth such as those on Starlink or unlimited broadband plans to share or sell their unused data to travelers, digital nomads, and people in low-connectivity regions. Unlike traditional roaming services or centralized VPNs, RoamX leverages Web3 principles, tokenized incentives ($ROAM), cryptographic verification (Zero-Knowledge proofs), and decentralized infrastructure to deliver a scalable, censorship-resistant solution for global data access. Built with a mobile first approach, it aims to disrupt the $1.7T telecommunications industry by making bandwidth a community owned asset.

### Goals

- **Primary**: Monetize excess bandwidth from unlimited plans (e.g., Starlink, fixed broadband) to provide affordable global connectivity.
- **Secondary**: Enable mobile users to resell unused capped data before expiry, maximizing value and flexibility.
- **Key Outcomes**: Reduce roaming costs by 90%+, reach 10,000+ hotspots by Q1 2026, and empower underserved regions.

## Why RoamX?

- **Problem**: Millions waste bandwidth monthly (e.g., Starlink users), while travelers face high roaming fees ($10/GB) and remote areas lack affordable access.
- **Solution**: A trustless P2P data marketplace with AI-driven dynamic pricing, gasless payments, and censorship resistance.
- **Edge**: Mobile-only (no hardware needed), seamless offline bootstrap via Starlink Direct-to-Cell (DTC), and ZK-verified usage.

## Tech Stack

- **Blockchain**: Base (Solidity, ERC-4337 for gasless UX, Chainlink Oracles for verification).
- **Networking**: WireGuard VPN (embedded), Libp2p/WebRTC for NAT traversal, tcpdump + ZK proofs for trustless logging.
- **App**: React Native + Expo (PWA for offline), Redux/Wagmi for state/wallet, Ceramic/IPFS for data storage, Node.js relayer.
- **Token**: $ROAM (ERC-20) for staking, governance, and discounts.

## User Flows

### Buyer Flow

1. **Open App**: Load with existing data or offline via Starlink DTC seed (20MB auto-activated).
2. **Browse**: View nearby/global hotspots (e.g., "Lagos Starlink, $0.05/GB, est. 1hr: $0.30").
3. **Connect**: Escrow $0.30 (gasless via ERC-4337), start WireGuard VPN.
4. **Consume**: Use data (e.g., 2.4GB), monitor real-time usage.
5. **Settle**: Pay $0.12 post-disconnect, refund $0.18, rate host.

### Host Flow

1. **Setup**: List bandwidth and price in app (e.g., $0.05/GB).
2. **Share**: Accept buyer connections via VPN.
3. **Earn**: Receive $0.12 (net $0.1188 after 1% fee) per session, auto-payout via smart contract.

## Getting Started (For Devs)

- Clone repo: `git clone https://github.com/yourusername/roamx`.
- Install Foundry: `curl -L https://foundry.paradigm.xyz | bash && foundryup`.
- Setup: `forge install` (contracts), `npm install` (React Native).
- Run MVP: `expo start` for app, `anvil` for local testnet, `forge test` for contracts.
- Test offline: Simulate DTC with local Starlink API mock.

## Roadmap

- **Q3 2025**: MVP testnet launch (gasless P2P trades, DTC bootstrap).
- **Q1 2026**: Beta with fiat onboarding (Stripe), 10,000+ hotspots.
- **2026**: Global scale (50+ countries), telecom partnerships, anti-censorship mode.

## Data Bank & Offline Magic

RoamX uses a Data Bank to provide 20MB seed data via Starlink Direct-to-Cell (DTC), enabling offline users (e.g., remote areas, tourist spots) to access the marketplace instantly—no QR scans or USSD required. Funded by protocol fees and host contributions, this ensures seamless connectivity from the first app open.

## Contributing

Fork the repo, submit PRs, or join our community on X (@roamx_network) and Discord for feedback.

## License & Contact

MIT License. Questions? hello@roamx.io | @roamx_network on X.

[Taglines: "Your passport to the decentralized web."]

# RoamX

# RoamX: Decentralized Mobile Data Exchange

Roam Freely, Pay Less, Own the Network.

## Overview

RoamX is a peer-to-peer (P2P) marketplace that empowers users with surplus internet bandwidth such as those on Starlink or unlimited broadband plans to share or sell their unused data to travelers, digital nomads, and people in low-connectivity regions. Unlike traditional roaming services or centralized VPNs, RoamX leverages Web3 principles, tokenized incentives ($ROAM), cryptographic verification (Zero-Knowledge proofs), and decentralized infrastructure to deliver a scalable, censorship-resistant solution for global data access. Built with a mobile first approach, it aims to disrupt the $1.7T telecommunications industry by making bandwidth a community owned asset.

### Goals

- **Primary**: Monetize excess bandwidth from unlimited plans (e.g., Starlink, fixed broadband) to provide affordable global connectivity.
- **Secondary**: Enable mobile users to resell unused capped data before expiry, maximizing value and flexibility.
- **Key Outcomes**: Reduce roaming costs by 90%+, reach 10,000+ hotspots by Q1 2026, and empower underserved regions.

## Why RoamX?

- **Problem**: Millions waste bandwidth monthly (e.g., Starlink users), while travelers face high roaming fees ($10/GB) and remote areas lack affordable access.
- **Solution**: A trustless P2P data marketplace with AI-driven dynamic pricing, gasless payments, and censorship resistance.
- **Edge**: Mobile-only (no hardware needed), seamless offline bootstrap via Starlink Direct-to-Cell (DTC), and ZK-verified usage.

## Tech Stack

- **Blockchain**: Base (Solidity, ERC-4337 for gasless UX, Chainlink Oracles for verification).
- **Networking**: WireGuard VPN (embedded), Libp2p/WebRTC for NAT traversal, tcpdump + ZK proofs for trustless logging.
- **App**: React Native + Expo (PWA for offline), Redux/Wagmi for state/wallet, Ceramic/IPFS for data storage, Node.js relayer.
- **Token**: $ROAM (ERC-20) for staking, governance, and discounts.

## User Flows

### Buyer Flow

1. **Open App**: Load with existing data or offline via Starlink DTC seed (20MB auto-activated).
2. **Browse**: View nearby/global hotspots (e.g., "Lagos Starlink, $0.05/GB, est. 1hr: $0.30").
3. **Connect**: Escrow $0.30 (gasless via ERC-4337), start WireGuard VPN.
4. **Consume**: Use data (e.g., 2.4GB), monitor real-time usage.
5. **Settle**: Pay $0.12 post-disconnect, refund $0.18, rate host.

### Host Flow

1. **Setup**: List bandwidth and price in app (e.g., $0.05/GB).
2. **Share**: Accept buyer connections via VPN.
3. **Earn**: Receive $0.12 (net $0.1188 after 1% fee) per session, auto-payout via smart contract.

## Getting Started (For Devs)

- Clone repo: `git clone https://github.com/yourusername/roamx`.
- Install Foundry: `curl -L https://foundry.paradigm.xyz | bash && foundryup`.
- Setup: `forge install` (contracts), `npm install` (React Native).
- Run MVP: `expo start` for app, `anvil` for local testnet, `forge test` for contracts.
- Test offline: Simulate DTC with local Starlink API mock.

## Roadmap

- **Q3 2025**: MVP testnet launch (gasless P2P trades, DTC bootstrap).
- **Q1 2026**: Beta with fiat onboarding (Stripe), 10,000+ hotspots.
- **2026**: Global scale (50+ countries), telecom partnerships, anti-censorship mode.

## Data Bank & Offline Magic

RoamX uses a Data Bank to provide 20MB seed data via Starlink Direct-to-Cell (DTC), enabling offline users (e.g., remote areas, tourist spots) to access the marketplace instantly—no QR scans or USSD required. Funded by protocol fees and host contributions, this ensures seamless connectivity from the first app open.

## Contributing

Fork the repo, submit PRs, or join our community on X (@roamx_network) and Discord for feedback.

## License & Contact

MIT License. Questions? hello@roamx.io | @roamx_network on X.

[Taglines: "Your passport to the decentralized web."]
