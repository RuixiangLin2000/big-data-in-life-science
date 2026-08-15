# Cloud Computing, Containers, and Orchestration

## Cloud model

Cloud computing provides off-premises infrastructure and services on demand. Virtualization allows multiple isolated systems to share physical hardware.

### Common service layers

- Infrastructure as a Service: virtual machines, networks, and storage
- Platform as a Service: managed runtimes and data platforms
- Software as a Service: complete applications

## HPC versus cloud

HPC commonly offers a shared cluster with a scheduler and centrally managed software. Cloud platforms offer isolated, programmable resources with elastic scaling and usage-based cost. Neither is universally better.

## Virtual machines and containers

A virtual machine includes a guest operating system. A container packages an application and its user-space dependencies while sharing the host kernel.

Containers improve portability and reproducibility, but an image tag alone is not a complete provenance record. Pin immutable image digests where possible.

## Docker-style workflow

```bash
docker build -t analysis:1.0 .
docker run --rm -v "$PWD/data:/data:ro" -v "$PWD/results:/results" analysis:1.0
```

Mount raw data read-only and write outputs to a separate location.

## Kubernetes

Kubernetes coordinates containerized workloads across a cluster. Core ideas include pods, deployments, services, configuration, secrets, scheduling, and persistent storage. It is powerful for services and elastic workloads but adds operational complexity.

## Life-science tradeoffs

Advantages:

- On-demand scale
- Standardized environments
- Easier collaboration and deployment
- Access to managed services and accelerators

Challenges:

- Data transfer time and egress cost
- Privacy, jurisdiction, and access control
- Cost monitoring
- Reproducibility across changing managed services
- Specialized skills required for secure operation
