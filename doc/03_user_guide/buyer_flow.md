# Buyer Flow: Step-by-Step UX

## Overview

As a buyer on RoamX, you can access affordable internet data from hosts worldwide—nearby or global—without the hassle of high roaming fees or complex setups. This flow is designed for maximum simplicity, starting from offline scenarios (e.g., remote tourist spots) and ending with secure settlement. As of September 18, 2025, the MVP supports gasless payments, real-time monitoring, and protections like escrow refunds.

## Prerequisites

- Download the RoamX app (React Native PWA) via a pre-shared link or app store.
- Optional: Connect a wallet (ERC-4337 supported for gasless txs) and load $ROAM tokens for discounts.

## Step-by-Step Buyer Flow

### 1. Open the App (Offline Bootstrap)

- **Scenario**: You're in a dead zone (e.g., rural Nigeria or Kenyan safari) with no signal.
- **What Happens**: The app auto-detects offline mode and activates Starlink Direct-to-Cell (DTC) for 20MB seed data—no QR scans or USSD required. Your device connects to satellites (sky view needed), loading a cached marketplace via IPFS.
- **UX**: Splash screen: "Connecting via Starlink... Welcome! Browse hotspots offline." (Takes 10-30 seconds.)
- **Tip**: If indoors, move outdoors for DTC signal.

### 2. Browse and Estimate Hotspots

- **What Happens**: View a list of available hotspots (cached for offline; syncs once online). Filters include nearby (low latency), global (for availability), price, and speed.
- **UX Examples**:
  - "Lagos Starlink Host: 50Mbps, $0.05/GB, 10km away (20ms latency)."
  - "Nairobi Global Host: 100Mbps, $0.07/GB, 500km away (150ms latency)."
- **Estimate Session**: Use a slider for time/MB (e.g., 1hr ~$0.30). App shows escrow amount and host rating (on-chain rep).
- **Protection**: See uptime guarantees (oracle-verified); low-rated hosts flagged.

### 3. Connect and Start Session

- **What Happens**: Tap "Connect" → App escrows estimated $ROAM (gasless via ERC-4337) in the smart contract. WireGuard VPN tunnel establishes automatically (Libp2p/WebRTC for NAT traversal).
- **UX**: Notification: "Escrow locked ($0.30). Tunnel active—using 0.1MB." Dashboard shows real-time usage ticker, pause/resume, and speed test.
- **Global/Nearby Logic**: App prioritizes nearby for speed; global for censorship bypass (e.g., Tor fallback).
- **Protection**: If speed <80% (Chainlink-verified), auto-pause and partial refund.

### 4. Consume Data

- **What Happens**: Route your traffic through the host's bandwidth (e.g., browsing, streaming). tcpdump logs usage in the background.
- **UX**: Minimal interruptions—full internet access. Alerts for low balance: "20% left—top-up $ROAM via card?"
- **Overage Handling**: Session pauses at escrow limit → Prompt: "Add $0.05 to continue?" (Auto-topup via Ramp/Stripe integration).
- **Tip**: Use seed data (20MB) for initial browsing; it transitions seamlessly to paid session.

### 5. Disconnect and Settle

- **What Happens**: Auto-disconnect on timer/end or manual tap. ZK proof generates from logs → Smart contract settles: Release exact payment to host (minus 1% fee), refund excess to you.
- **UX**: Summary screen: "Session complete: Used 2.4GB for $0.12. Refund: $0.18 issued. Rate host? [Thumbs up/down]." $ROAM credits update instantly.
- **Protection**: Full audit trail on-chain; disputes resolved via DAO governance if needed.

## Visual Flow Diagram

[Insert Diagram Here]

- **Suggested Layout**: Use Draw.io or Figma:
  - **Start**: Offline App Open → Starlink DTC (20MB).
  - **Middle**: Browse → Connect (Escrow) → Consume (WireGuard Tunnel).
  - **End**: Disconnect → ZK Proof → Settle (Payment/Refund).
  - **Branches**: Nearby vs. Global; Overage Pause.
- **Example Description**: "Offline user → DTC seed → Marketplace → Global tunnel to Nairobi host → Settle with $ROAM."

## Tips for Buyers

- **Maximize Savings**: Stake $ROAM for 10% discounts; choose nearby for streaming.
- **Troubleshooting**: If DTC fails, retry outdoors; contact support via app chat.
- **Privacy**: ZK proofs hide usage details—only totals are verified.

[Previous: Dive into our [network model](network_model.md) for global vs. nearby hotspot logic.]
[Next: See our [host flow](host_flow.md) for sharing data as a host.]
