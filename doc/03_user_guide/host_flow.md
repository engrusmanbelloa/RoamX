# Host Flow: Step-by-Step UX

## Overview

As a host on RoamX, you can share your surplus internet bandwidth (e.g., from Starlink or unlimited plans) and earn $ROAM tokens by connecting with buyers worldwide. This flow is designed for simplicity and security, leveraging WireGuard tunnels and automated payouts. During the MVP phase, hosts benefit from gasless settlements and on-chain reputation tracking.

## Prerequisites

- Download the RoamX app (React Native + Expo) via app stores or PWA link.
- Own a high bandwidth connection (e.g., Starlink, 50-200Mbps) with stable uptime.
- Connect a wallet (ERC-4337 supported) to receive $ROAM payments.

## Step-by-Step Host Flow

### 1. Open the App and Switch to Host Mode

- **Scenario**: You’re ready to share unused bandwidth (e.g., off-peak hours).
- **What Happens**: Open the app → Tap "Switch to Host" on the homepage.
- **UX Elements**:
  - Welcome screen: "Become a host—earn $ROAM by sharing data."
  - Toggle: "Host Mode" (auto-detects connection speed via test).
- **Tip**: Ensure your device has a public IP or relay setup (Libp2p handles NAT).

### 2. Set Up and List Bandwidth

- **What Happens**: Configure your offering—bandwidth capacity, price, and availability.
- **UX Elements**:
  - Form: "Bandwidth: [50Mbps]" (auto-filled), "Price: [$0.05/GB]" (slider), "Availability: [24/7 or custom hours]."
  - Preview: "Listing: Lagos Starlink, 50Mbps, $0.05/GB, 99% uptime."
  - Submit: "List Hotspot" (saves to Ceramic/IPFS, visible to buyers).
- **Protection**: Minimum uptime (80%) required; stake $ROAM (e.g., 10 $ROAM) for credibility.
- **Note**: Starlink users can leverage DTC signal strength for bonus visibility.

### 3. Accept Connections

- **Scenario**: Buyers connect to your hotspot (nearby or global).
- **What Happens**: App notifies you of incoming requests → WireGuard tunnel establishes automatically.
- **UX Elements**:
  - Notification: "Buyer from Nairobi connected—using 0.5MB."
  - Dashboard: Active sessions (e.g., 2 buyers, total 2.1GB), speed (e.g., 40Mbps shared), and disconnect option.
- **Global Logic**: Accepts global buyers (e.g., Kenya to Nigeria) via Libp2p/WebRTC NAT traversal.
- **Protection**: ZK proofs verify usage; slashing (10% stake) for <80% uptime.

### 4. Monitor and Manage Sessions

- **What Happens**: Track usage and performance in real-time.
- **UX Elements**:
  - Live stats: "Session 1: 1.2GB, 95% uptime; Session 2: 0.9GB, 98% uptime."
  - Controls: Pause (e.g., for maintenance) or end sessions manually.
  - Alerts: "Low speed detected—check connection?" (oracle-triggered).
- **Tip**: Prioritize nearby buyers for lower latency; global adds diversity.

### 5. Earn and Settle Payments

- **What Happens**: Session ends → ZK proof submitted → Smart contract releases payment.
- **UX Elements**:
  - Summary: "Session complete: 2.1GB sold for $0.105 (net $0.10395 after 1% fee)."
  - Payout: $ROAM credited to wallet (gasless via ERC-4337).
  - Rating: Buyer feedback updates your on-chain reputation.
- **Protection**: Funds escrowed until ZK verification; disputes handled by DAO.
- **Bonus**: Stake $ROAM to increase listing priority and earn yield.

## Flow Diagram

[Insert Diagram Here]

- **Suggested Layout**: Use Draw.io or Figma:
  - **Start**: Open App → Switch to Host Mode.
  - **Middle**: Set Up Listing → Accept Connections (WireGuard).
  - **End**: Monitor → ZK Proof → Earn $ROAM.
  - **Arrows**: Show buyer requests, session data, and payout flow.
- **Example Description**: "Host lists 50Mbps → Buyer connects globally → Usage tracked → $ROAM paid."

## Tips for Hosts

- **Maximize Earnings**: Set competitive prices ($0.04-$0.07/GB) and ensure 24/7 uptime.
- **Troubleshooting**: If tunnels fail, check firewall (Libp2p auto-configures); contact support.
- **Reputation**: High ratings boost visibility—maintain quality service.

[Previous: Check the [buyer flow](buyer_flow.md) for using host data.]
[Next: Explore common [FAQs](faq.md) for more details.]
