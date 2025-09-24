# Economics: Fee Structure and DAO Treasury

## Overview

The RoamX economic model ensures sustainability and community governance 2025, during the MVP phase (Q3 2025). This section details the fee structure that funds the ecosystem and the DAO treasury's role in managing resources, aligning with the decentralized P2P data exchange vision on Arbitrum.

## Fee Structure

- **Protocol Fee**: 1% of each transaction (e.g., $0.001 on a $0.10 sale) deducted from host earnings.
  - **Purpose**: Funds the Data Bank (20MB seed data), relayer operations, and DAO initiatives.
  - **Calculation**: Fee = Transaction Amount × 0.01; applied post-escrow settlement.
  - **Example**: Host sells 2GB at $0.05/GB ($0.10 total) → $0.001 fee → Host nets $0.099.
- **Staking Penalty**: 1% fee on early unstaking within lock period (e.g., 1 $ROAM penalty on 100 $ROAM unstake).
  - **Purpose**: Discourages short-term dumping; funds treasury.
- **No Gas Fees**: ERC-4337 relayer absorbs gas costs, funded by protocol fees.
- **Future Adjustments**: DAO can vote on fee caps (max 5%) post-MVP.

## DAO Treasury

- **Composition**: Treasury holds accumulated protocol fees, staking penalties, and 15% ecosystem allocation (150M $ROAM).
- **Management**: Governed by $ROAM stakers (1 token = 1 vote) via smart contracts (e.g., `Admin.sol`).
- **Allocation**:
  - **Data Bank**: 50% of fees (e.g., $0.0005 of $0.001) for seed data distribution.
  - **Development**: 30% for upgrades, audits, and partnerships (e.g., Starlink DTC expansion).
  - **Community Grants**: 20% for airdrops and host rewards (e.g., uptime bonuses).
- **Transparency**: Allocations tracked on-chain; quarterly reports via IPFS.
- **Voting Process**:
  - Proposals submitted with 1,000 $ROAM stake.
  - Quorum: 5% of staked $ROAM; majority wins.
  - Example: Vote to increase Data Bank funding (passed Sept 2025).

## Economic Incentives

- **Host Motivation**: Net earnings (e.g., $0.099/GB) incentivize bandwidth sharing; staking boosts visibility.
- **Buyer Savings**: 10% discount with $ROAM staking reduces costs (e.g., $0.045/GB).
- **Sustainability**: Fees cover operational costs; treasury grows with adoption (target: 10K hotspots by Q1 2026).

## Security and Compliance

- **Audits**: Treasury logic audited pre-mainnet (Q1 2026).
- **Risk Mitigation**: Multi-sig wallet (e.g., Gnosis Safe) for treasury access; 2/3 approval required.
- **Regulatory**: Fees compliant with local tax laws; geo-restrictions applied (OFAC-compliant).

## Future Enhancements

- **Dynamic Fees**: AI-driven adjustments based on demand (post-MVP).
- **Burn Mechanism**: 0.1% of fees burned to reduce $ROAM supply (Q2 2026).
- **Treasury Diversification**: Invest in stablecoins or liquidity pools (Q3 2026).

[Previous: Review the [token model](token_model.md) for supply and staking.]
[Back to [tokenomics index](index.md).]
