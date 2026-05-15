# Task Partitioning for Contractors

Split into discrete packages with clear inputs/outputs, API contracts, metric names, test vectors, and acceptance criteria.

## Suggested packages
1. Cluster & infra ops (k3s setup, drivers, WireGuard)
2. Energy emulator & telemetry service (OpenAPI, Prometheus metrics)
3. Energy-aware scheduler operator (CRDs, operator, e2e tests)
4. Inference & model-serving stack (Triton, model-manager, load tests)
5. CDN edge & cache service (NGINX/Varnish, MinIO integration)
6. Crypto-hash microservice (configurable intensity, telemetry)
7. Observability & dashboards (Prometheus, Grafana, Loki, dashboards)
8. Load/test harness & user-simulation (Locust, k6, netem profiles)
9. Management portal & billing demo (React + backend, stripe sandbox)
10. Security & provisioning (Vault, cert-manager, RBAC)

## Packaging work for jobbers
- Provide one-page spec + checklist per package
  - Inputs: APIs, metrics, existing infra
  - Outputs: artifacts, container images, manifests, tests
  - Acceptance tests and CI job
- Use a monorepo with per-package directories and top-level CI
- Share OpenAPI/CRD specs, metric names, dashboard JSONs in advance

## Prioritization
- Phase 1 (2–4 weeks): 1, 4, 2, 3, 8, 7
- Phase 2: 5, 6, 9, 10

## Coordination
- Single product owner to approve PRs
- Weekly sync, Kanban board, acceptance-test-driven payments
