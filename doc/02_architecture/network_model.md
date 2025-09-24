# RoamX Network Model

## Overview

The RoamX network model defines how users connect to hotspots either nearby or globally within a decentralized peer-to-peer (P2P) framework. This model supports the MVP's goal of seamless connectivity, leveraging Starlink Direct-to-Cell (DTC) for offline bootstrapping and WireGuard for secure tunnels. This section explores the logic, performance considerations, and optimization strategies for hotspot selection.

## Core Network Components

- **WireGuard VPN**: Provides the backbone for P2P tunnels, enabling secure data exchange between buyers and hosts.
- **Libp2p/WebRTC**: Facilitates peer discovery and NAT traversal, ensuring connectivity across diverse network conditions.
- **Starlink DTC**: Delivers 20MB seed data in offline scenarios, serving as the entry point for remote users.
- **Ceramic/IPFS**: Caches hotspot listings for offline browsing and syncs real-time updates post-connection.

## Global vs. Nearby Hotspot Logic

RoamX supports connections to hotspots anywhere—nearby (same region/state) or globally (different state/country)—with the following model:

### 1. Global Hotspot Connections

- **Feasibility**: Users can connect to hosts worldwide, as WireGuard tunnels operate over public IPs or relayed via WebRTC's STUN/TURN servers. For example, a buyer in Lagos, Nigeria, can link to a host in Nairobi, Kenya, or New York, USA.
- **Use Case**: Ideal for users in censored regions (e.g., China, Iran) or areas with few local hosts, ensuring availability.
- **Performance**: Latency varies (e.g., 200-400ms international vs. 3-50ms local), potentially reducing speeds (e.g., 50Mbps to 10-20Mbps). QUIC enhances UDP efficiency for long-distance links.
- **Discovery**: Libp2p's Distributed Hash Table (DHT) locates global peers, updated via Ceramic/IPFS.

### 2. Nearby Hotspot Connections

- **Feasibility**: Prioritizes hosts within the same geographic area (e.g., same city or state), detected via device GPS and ping tests.
- **Use Case**: Optimal for low-latency needs (e.g., streaming, gaming) or users with stable local options.
- **Performance**: Offers lower latency (3-50ms) and higher throughput (up to host capacity, e.g., 50Mbps), enhancing user experience.
- **Discovery**: App filters hotspots by proximity, leveraging cached IPFS data and real-time sync.

### Connection Process

1. **Bootstrap**: User opens app offline → Starlink DTC provides 20MB → Cached IPFS data loads marketplace.
2. **Selection**: App displays hotspots with distance, latency estimates, and pricing (e.g., "Lagos Host, 10km, 20ms, $0.05/GB").
3. **Connection**: User taps "Connect" → WireGuard tunnel establishes → Libp2p/WebRTC handles NAT traversal.
4. **Optimization**: App auto-prioritizes nearby hosts unless global is selected (e.g., for censorship bypass).

## Performance Considerations

- **Latency**: Nearby connections minimize RTT (round-trip time), while global links may introduce delays. WireGuard's lightweight design mitigates overhead.
- **Bandwidth**: Host capacity (e.g., Starlink's 50-200Mbps) dictates speed, shared across connected buyers.
- **Reliability**: Global connections may face packet loss; WebRTC's error correction and DTC fallback improve stability.
- **Censorship**: Global relays (e.g., Tor, planned for Q1 2026) ensure access in restricted areas.

## Optimization Strategies

- **Geo-Filtering**: Default to nearby hotspots based on GPS, with a "Global" toggle for flexibility.
- **Ping Testing**: Pre-connect handshake measures latency, sorting options in the app.
- **Dynamic Pricing**: AI-driven adjustments (post-MVP) reflect distance/latency (e.g., +10% for global).
- **Fallbacks**: If nearby fails, switch to global; if both fail, DTC sustains seed data.

## Network Diagram

[Insert Diagram Here]

- **Suggested Layout**: Use Draw.io or Figma to show:
  - **Center**: User device with Starlink DTC (20MB seed).
  - **Left**: Nearby hotspot (e.g., Lagos) with WireGuard tunnel.
  - **Right**: Global hotspot (e.g., Nairobi) with Libp2p/WebRTC relay.
  - **Arrows**: Data flow from DTC to P2P, with latency indicators.
- **Example Description**: "User in rural Nigeria → DTC connects → Chooses Lagos host (low latency) or Nairobi host (global access)."

## Edge Cases

- **No Nearby Hosts**: Global discovery via DHT ensures availability.
- **High Latency**: App notifies users (e.g., "Global: +150ms expected") and offers pause/resume.
- **Censorship**: Tor fallback routes traffic through unrestricted nodes.

## Future Enhancements

- **Multi-Path Routing**: Combine nearby/global paths for redundancy (post-MVP).
- **Satellite Mesh**: Expand DTC coverage with host contributions (Q1 2026).

[Previous: See our [tech stack](tech_stack.md) for component details.]
