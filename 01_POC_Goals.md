# POC Goals and Hardware

## Goals
- Prove latency, throughput, reliability for target services (Agentic AI, crypto hashing, CDN, GP processing).
- Demonstrate remote deployment feasibility (stranded power, satellite backhaul).
- Validate customer willingness via trials, metrics, and pricing experiments.
- Emulate production 1 MW DC can behavior for scheduler and billing demos.

## High-level Hardware (POC scale)
- GPU server: 1 modern GPU (e.g., NVIDIA A30/T4/A100/RTX6000).
- App/cache server: 1 x86 server (8–16 cores, 64–128 GB RAM, NVMe).
- Control-plane server: 1 small server or cloud VM (4–8 cores, 16–32 GB).
- Networking: small managed switch, Starlink terminal (backhaul), cables.
- Power telemetry: Shelly/IoTaWatt/Emporia or similar meters.
- UPS / PDUs (demo-grade) for graceful shutdown and telemetry.

## Key POC Demonstrations
- Remote deploy and Starlink backhaul with measured RTT/jitter.
- Energy-aware scheduling: keep interactive inference responsive while deferring hashing during power windows.
- CDN edge caching with MinIO + NGINX/Varnish and measured cache-hit latency.
- Power emulation (BESS smoothing) presenting constant load to genset controller (simulated).
- Observability: p50/p90/p99 latency, throughput, power-per-inference/hash, scheduler decisions.
