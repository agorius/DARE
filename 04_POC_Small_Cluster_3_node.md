# POC Small Cluster (3-node) — Design and Ops

## Node roles
- GPU node
  - Purpose: inference + occasional GPU hashing
  - Suggested spec: 1 modern GPU (A30/T4/RTX6000 class), 64–128 GB RAM, NVMe
- App/cache node
  - Purpose: CDN cache (NGINX/Varnish), MinIO, CPU-based hashing microservice, WAN optimizer
  - Suggested spec: 8–16 CPU cores, 64–128 GB RAM, NVMe
- Control-plane node (on-site or cloud)
  - Purpose: k3s server, Prometheus, Grafana, logging, management portal
  - Suggested spec: 4–8 cores, 16–32 GB RAM or a small cloud VM

## Deployment choices
- k3s cluster on-site with control-plane either local or cloud (cloud reduces on-site load and improves availability).
- Use WireGuard for secure site-to-cloud operations.
- Use nodeSelectors and taints/tolerations to isolate inference workloads on GPU node.

## Key k8s settings
- Enable NVIDIA device plugin on GPU node.
- Use priorityClass: inference-high, batch-low, control-medium.
- HPA / custom GPU-aware autoscaler (use Keda or custom metrics).
- Pod resource requests/limits tuned and Liveness/Readiness probes set.

## Ops & runbook highlights
- Bootstrap via Terraform + Ansible.
- Provide easy manifests/helm charts for Triton, MinIO, NGINX/Varnish, model-manager, scheduler operator, and power-emulator.
- CI smoke tests: cluster healthy, GPU visible, Triton serving test prompt, power API responding.
