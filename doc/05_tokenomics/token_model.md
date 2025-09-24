# Token Model: $ROAM Supply, Staking, and Rewards

## Overview

The $ROAM token is the backbone of the RoamX ecosystem, powering a decentralized peer-to-peer (P2P) data exchange as of September 2025, during the MVP phase (Q3 2025). This section details the token's supply distribution, staking mechanics, and reward system, designed to incentivize participation and ensure long-term sustainability on Base.

## Token Supply

- **Total Supply**: 1,000,000,000 $ROAM (1 billion tokens).
- **Initial Mint**: Deployed via `ROAMToken.sol` with a fixed supply, non-inflatable.
- **Distribution** (as percentage of total supply):
  - **Community Rewards**: 40% (400M $ROAM) – Airdrops, staking rewards, and host incentives.
  - **Team & Advisors**: 20% (200M $ROAM) – Vested over 2 years with a 1-year cliff.
  - **Ecosystem Development**: 15% (150M $ROAM) – Funding Data Bank, partnerships, and marketing.
  - **Liquidity Pools**: 15% (150M $ROAM) – Uniswap/Base DEX for trading.
  - **Private Sale/Investors**: 10% (100M $ROAM) – Locked with 6-month cliff, 18-month vesting.
- **Circulating Supply (MVP)**: ~10% (100M $ROAM) initially, increasing with unlocks.

## Staking Mechanics

- **Purpose**: Encourages long-term commitment from buyers and hosts, reducing sell pressure.
- **Process**:
  - Users stake $ROAM in the `ROAMToken.sol` contract via the `stake` function.
  - Minimum stake: 100 $ROAM; no maximum.
  - Lock period: 30 days (flexible, extensible to 90 days for higher rewards).
- **Benefits**:
  - **Buyer Discount**: 10% off data purchases (e.g., $0.05/GB becomes $0.045/GB).
  - **Host Priority**: Staked hosts gain higher visibility in the marketplace.
  - **Yield**: 5% APY on staked amount, distributed quarterly from protocol fees.
- **Unstaking**: 7-day cooldown; penalties (1% fee) for early unstake within lock period.

## Rewards System

- **Host Rewards**: Earn $ROAM per GB sold (e.g., $0.05/GB net after 1% fee). Bonus rewards for uptime >95% (oracle-verified).
- **Community Airdrops**: 50M $ROAM allocated for early adopters (Q4 2025), distributed based on usage.
- **Referral Program**: Invite users to earn 5% of their first purchase in $ROAM.
- **DAO Governance**: Stakers vote on fee adjustments and feature proposals, with 1 $ROAM = 1 vote.
- **Data Bank Contribution**: Hosts staking >1,000 $ROAM can contribute excess bandwidth for 2% yield.

## Token Utility

- **Payments**: Gasless $ROAM used for escrow (via ERC-4337) and session settlements.
- **Governance**: Stakers influence protocol decisions (e.g., fee caps, DTC expansion).
- **Incentives**: Drives adoption by rewarding active participants.

## Security and Compliance

- **Audits**: Planned pre-mainnet (Q1 2026) via OpenZeppelin or similar.
- **Anti-Dumping**: Vesting schedules and staking locks mitigate sell-offs.
- **Regulatory**: Compliant with OFAC; geo-restrictions applied where needed.

## Future Enhancements

- **Dynamic Staking**: Adjustable lock periods and yields post-MVP.
- **Burn Mechanism**: 0.1% of transaction fees burned to reduce supply (Q2 2026).
- **Fiat Onboarding**: Integrate Stripe for $ROAM purchases (Q1 2026).

[Next: Explore the [economics](economics.md) for fee structure and DAO treasury details.]
[Back to [tokenomics index](index.md).]
