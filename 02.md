# Software BOM and Cost (Demo-focused, Low Cost)

## Open-source components (POC)
- Orchestration: k3s
- IaC/provisioning: Terraform, Ansible
- Container runtime: containerd / Docker
- NVIDIA stack: drivers, CUDA, NVIDIA Container Toolkit, device plugin
- Inference: Triton Inference Server, TorchServe / FastAPI (fallback)
- Model store / object: MinIO (S3)
- CDN cache: NGINX or Varnish, OpenResty (optional)
- Hashing: custom miner container or adapted open-source benchmark
- WAN: TCP/QUIC tuning, Caddy/NGINX with HTTP/3
- Observability: Prometheus, Grafana, Loki, OpenTelemetry, Jaeger
- Logging: Promtail / EFK alternative (Loki)
- Load testing: k6, Locust, wrk
- Secrets/Auth: Vault OSS, cert-manager, Keycloak (optional)
- Remote ops: WireGuard / autossh

## Minimal commercial/trial items
- Starlink Business terminal + 1 month: ~$2,500 + ~$200/mo
- Optional SD-WAN trial: $0–$500
- Cloud control-plane VM: $50–200/mo

## Hardware (POC)
- GPU server: $2,000–8,000 (used/new depending)
- App server: $800–2,000
- Control-plane server/cloud VM: $300–800 or $50–150/mo
- UPS / PDU / misc: $500–1,000
- Power meters: $100–300 each
- Misc switch/cables: $200–500

## Rough estimated total (one-time + 1 month)
- Typical: ~$9,000 (mid-range GPU used, Starlink, devices)
- Lower-cost variant: $4k–6k if using cheaper GPU / cloud control-plane / cheaper backhaul
