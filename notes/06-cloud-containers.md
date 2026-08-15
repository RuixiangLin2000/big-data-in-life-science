# 云计算、容器与编排（Cloud Computing, Containers, and Orchestration）

## 云模型（Cloud model）

云计算按需提供异地基础设施和服务，虚拟化允许多个隔离系统共享物理硬件。（Cloud computing provides off-premises infrastructure and services on demand. Virtualization allows multiple isolated systems to share physical hardware.）

### 常见服务层级（Common service layers）

- 基础设施即服务：虚拟机、网络和存储（Infrastructure as a Service: virtual machines, networks, and storage）
- 平台即服务：托管运行环境和数据平台（Platform as a Service: managed runtimes and data platforms）
- 软件即服务：完整应用（Software as a Service: complete applications）

## HPC 与云（HPC versus cloud）

HPC 通常提供带调度器和集中管理软件的共享集群；云平台提供隔离、可编程、弹性扩展并按使用计费的资源。两者没有绝对优劣。（HPC commonly offers a shared cluster with a scheduler and centrally managed software. Cloud platforms offer isolated, programmable resources with elastic scaling and usage-based cost. Neither is universally better.）

## 虚拟机与容器（Virtual machines and containers）

虚拟机包含客户操作系统；容器打包应用和用户空间依赖，同时共享宿主机内核。（A virtual machine includes a guest operating system. A container packages an application and its user-space dependencies while sharing the host kernel.）

容器提高可移植性和可复现性，但镜像标签本身不是完整来源记录，应尽量固定不可变镜像摘要。（Containers improve portability and reproducibility, but an image tag alone is not a complete provenance record. Pin immutable image digests where possible.）

## Docker 风格流程（Docker-style workflow）

```bash
docker build -t analysis:1.0 .
docker run --rm -v "$PWD/data:/data:ro" -v "$PWD/results:/results" analysis:1.0
```

原始数据应只读挂载，输出应写入独立位置。（Mount raw data read-only and write outputs to a separate location.）

## Kubernetes（Kubernetes）

Kubernetes 在集群上协调容器工作负载，核心概念包括 Pod、Deployment、Service、配置、Secret、调度和持久存储。它适合服务和弹性任务，但会增加运维复杂度。（Kubernetes coordinates containerized workloads across a cluster. Core ideas include pods, deployments, services, configuration, secrets, scheduling, and persistent storage. It is powerful for services and elastic workloads but adds operational complexity.）

## 生命科学中的权衡（Life-science tradeoffs）

优势包括按需扩展、标准化环境、更方便的协作部署，以及托管服务和加速器。（Advantages: on-demand scale; standardized environments; easier collaboration and deployment; and access to managed services and accelerators.）

挑战包括数据传输与出口费用、隐私和司法管辖、访问控制、成本监控、托管服务变化导致的复现问题，以及安全运维所需的专业能力。（Challenges: data transfer time and egress cost; privacy, jurisdiction, and access control; cost monitoring; reproducibility across changing managed services; and specialized skills required for secure operation.）
