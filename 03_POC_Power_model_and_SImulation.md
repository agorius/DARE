# POC Power Model and Simulation

## Production concept summary
- Target production: DC "can" fed by 1 MW of DC 800V power.
- System will be slightly overprovisioned so BESS + load balancer present constant 1 MW load to ICE genset.
- Voltage/current ripple must be within tolerances for electronic governor on genset to keep motor at efficient operating point.

## POC approach
- Emulate BESS smoothing and constant-load presentation in software rather than deploying MW-scale hardware.
- Use small power-meter devices on servers to report real draw.
- Implement a Power Emulation Service that:
  - Accepts bids/requests from scheduler (power requested to run jobs).
  - Enforces a presented-load policy (e.g., maintain constant 1 MW virtual presentation).
  - Simulates BESS discharge/charge windows and constraints.
  - Exposes Prometheus metrics and an OpenAPI for scheduler integration.

## Minimal hardware for telemetry
- 1–3 low-cost power meters (Shelly / IoTaWatt / Emporia) connected to a telemetry adapter.
- Small UPS for graceful shutdown and to test transient conditions.

## Key API surfaces (POC)
- GET /power/status -> {presented_load_kw, available_kw, bess_charge_pct, timestamp}
- POST /power/bid -> {job_id, requested_kw, duration_s, priority} -> {accepted: bool, scheduled_start}
- GET /power/history -> time series for presented_load, accepted_bids

## Demonstrable behaviors
- Show scheduler deferring or throttling hashing during simulated low power windows.
- Show BESS smoothing effect on presented_load graphs while server draw fluctuates.
- Provide per-job power accounting for billing demos.
