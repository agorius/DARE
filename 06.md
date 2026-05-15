# Inference Model Stack — POC Plan and Deliverables

## Goal
Low-cost, demonstrable GPU inference for agentic AI + GP tasks with measurable SLAs; integrates with energy-aware scheduler.

## Core components
- Triton Inference Server (OSS) for GPU inference
- Fallback FastAPI/TorchServe for tiny models
- MinIO as model-store (S3)
- NVIDIA stack: drivers, CUDA, device plugin
- Ingress: Caddy or NGINX with HTTP/3
- Batching/queue: Triton batching + Redis (or in-process) queue
- Model-manager service (upload/version/load/unload/prewarm)
- Autoscaler: K8s HPA + GPU-aware scaler (Keda or custom)
- Monitoring: Prometheus + DCGM exporter + Grafana
- Tracing: OpenTelemetry + Jaeger
- Load generator: Locust + custom agentic scenarios

## Model strategy (demo)
- Use small/quantized models (e.g., Llama-2-7B or similarly sized models quantized to 4-bit/INT8)
- Provide 2 model classes:
  - Interactive (small, low-latency)
  - Batch (medium quality, deferred)
- Use quantization (bitsandbytes/GPTQ) and prefer models that run well on middle-tier GPUs.

## Pod & k8s config
- NodeSelector: gpu=true for inference pods
- Requests/limits: GPU, CPU, memory tuned per model
- Priority classes: inference-high (protected) vs batch-low
- Readiness/liveness: model health and GPU free memory
- Sidecar: prometheus exporter and prewarm hook

## Inference API (high-level)
- POST /infer -> sync inference; body includes model, input, options
- POST /infer-async -> accept job and return job_id
- POST /model/upload -> upload model artifact
- POST /model/warm -> pre-warm model instance
- GET /model/status -> model health and versions

(OpenAPI spec required as deliverable)

## Batching and latency controls
- Configure Triton max_batch_size and batch_timeout per model
- Front-end queue with max queue length and 429 on overload
- Implement latency-aware admission: route to smaller model or reject when SLA predicted to be violated
- Expose queue-length and predicted-wait metrics for autoscaler/scheduler

## Energy-aware hooks
- Model-manager accepts "power-priority" labels
- Scheduler can set model-modes (performance/energy-saver)
- Operator can evict batch pods and keep interactive ones running during low-power periods

## Observability metrics (required)
- inference_latency_seconds{model,quantile}
- inference_throughput_rps{model}
- gpu_utilization_percent{node}
- gpu_memory_used_bytes{model}
- model_load_time_seconds
- queue_length{model}
- power_requested_kw, power_assigned_kw

## Acceptance criteria (POC)
- Cold-start load time for small model < 10s (target)
- Steady-state p90 for small model < 300ms (adjust per GPU/model)
- p99 within acceptable demo threshold (document measured values)
- Scheduler interaction: during simulated low-power, batch jobs deferred while interactive pod p99 remains within SLA

## Deliverables for contractor
- Helm charts / manifests for Triton + model-manager + ingress + queue
- OpenAPI for inference & model management endpoints
- Example quantized models + packaging guide
- Prometheus metric list and Grafana dashboard JSON
- Load test scripts (Locust scenarios) and pass/fail criteria
- Runbook: deploy, scale, failure modes, acceptance tests
