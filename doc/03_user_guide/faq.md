# RoamX FAQ

## Overview

This FAQ addresses common questions about using RoamX, during the MVP phase (Q3 2025). It covers buyer and host experiences, technical details, and general inquiries. For more, check the [buyer flow](buyer_flow.md) or [host flow](host_flow.md).

## General Questions

### What is RoamX?

RoamX is a decentralized P2P marketplace for sharing unused internet bandwidth (e.g., from Starlink) via WireGuard VPN tunnels. Buyers get affordable data; hosts earn $ROAM tokens.

### How does RoamX differ from traditional VPNs?

Unlike centralized VPNs (e.g., Surfshark), RoamX is P2P, decentralized, and rewards sharers. No subscriptions—pay per use with gasless $ROAM transactions.

### Is RoamX free to use?

The app is free. Buyers pay for data (~$0.05/GB); hosts earn from sales. 20MB seed data is free via Starlink DTC for offline users.

### Which regions does RoamX support?

MVP launches in Nigeria and Kenya (high roaming + mobile adoption). Global connections are available, with expansion to 50+ countries by 2026.

## Buyer Questions

### How do I get internet if I'm offline (no signal)?

Starlink DTC auto-activates 20MB seed data outdoors (sky view needed). It loads the marketplace; connect to a host for more.

### Can I connect to hotspots in another country?

Yes—global P2P via WireGuard. Nearby is faster (20ms latency); global may add 150ms but ensures availability.

### What if I use more data than my escrow?

Session pauses at limit → Prompt to top-up $ROAM (via card). No debt—pay exact amount post-settlement.

### What happens if the host's speed is slow?

Chainlink oracles verify uptime/speed. If <80%, auto-refund 50% + session switch. Rate hosts to build reputation.

### Are payments secure?

Yes—escrow holds $ROAM until ZK proof confirms usage. Gasless via ERC-4337; all on Arbitrum for transparency.

## Host Questions

### How much can I earn?

Depends on bandwidth/price (e.g., 50Mbps at $0.05/GB = $0.10-0.50/session). Net after 1% fee; stake $ROAM for priority.

### Do I need special hardware?

No—your smartphone + stable connection (e.g., Starlink) suffices. App embeds WireGuard; Libp2p handles NAT.

### What if a buyer disconnects early?

ZK proofs settle partial payment based on usage. Refunds go to buyer; you get fair share.

### How do I improve my rating?

Maintain >80% uptime (oracle-verified). Respond to feedback; high ratings boost visibility in marketplace.

## Technical Questions

### What is Starlink DTC?

Direct-to-Cell provides satellite seed data to unmodified LTE phones in dead zones. It's RoamX's offline magic—no QR/USSD needed.

### Why WireGuard over other VPNs?

Lightweight, secure, and fast—perfect for mobile P2P. Supports global tunnels with Libp2p for firewalls.

### What are ZK proofs?

Zero-Knowledge proofs verify usage (e.g., 2.4GB) without revealing details, ensuring privacy and trust.

### Does RoamX work behind firewalls?

Yes—Libp2p/WebRTC enables NAT traversal. Global connections use relays if needed.

## Fees and Token Questions

### What fees does RoamX charge?

1% protocol fee on trades (funds Data Bank/DAO). No gas fees for users (ERC-4337).

### How do I get $ROAM tokens?

Buy via app (fiat/crypto ramps) or earn as host. Stake for discounts/governance; 40% allocation for community rewards.

### What is the Data Bank?

Pooled seed data (20MB/user) funded by fees, providing offline access. Hosts can contribute excess for yields.

## Risks and Support

### What about regulations?

Geo-blocked in restricted regions (OFAC-compliant). Check local laws for data sharing.

### How do I get help?

In-app chat, X (@roamx_network), or Discord. For bugs, file on GitHub.

### What's next for RoamX?

Beta Q1 2026: Fiat onboarding, 10K hotspots. Global scale 2026: Telecom partnerships.

[Back to [user guide index](index.md).]
