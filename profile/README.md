<p align="center">
  <img src="https://raw.githubusercontent.com/kubeply/.github/main/assets/banner-hero.svg" alt="Kubeply" width="100%"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/kubernetes-1.29%2B-326CE5?style=flat-square&logo=kubernetes&logoColor=white" alt="Kubernetes"/>
  <img src="https://img.shields.io/badge/terraform-1.7%2B-7B42BC?style=flat-square&logo=terraform&logoColor=white" alt="Terraform"/>
  <img src="https://img.shields.io/badge/argocd-2.10%2B-EF7B4D?style=flat-square&logo=argo&logoColor=white" alt="ArgoCD"/>
  <img src="https://img.shields.io/badge/GPU%20workloads-ready-14B8A6?style=flat-square" alt="GPU"/>
  <img src="https://img.shields.io/badge/status-accepting%20clients-99F6E4?style=flat-square" alt="Status"/>
</p>

<br/>

> We give early AI startups the production-grade Kubernetes infrastructure they need —
> before they can justify hiring a full platform team.

<br/>

---

<img src="https://raw.githubusercontent.com/kubeply/.github/main/assets/banner-services.svg" alt="Services" width="100%"/>

We operate as a fractional platform engineering function for seed to Series A AI startups. Three engagement types, designed to match where you are.

<br/>

**`01` — AI Infra Audit**

A structured assessment of your current stack. We review your cloud setup, deployment patterns, observability gaps, secrets hygiene, and AI/GPU runtime configuration. You get a prioritised remediation report. This is how most client relationships start.

**`02` — Platform Foundation Setup**

We deploy a production-grade Kubernetes baseline from scratch — or clean up what you have. Terraform-provisioned cluster, ArgoCD GitOps, ingress, TLS, observability, secrets management, backups, RBAC, and any AI-specific modules your team needs. You own the infrastructure. We own the delivery.

**`03` — Platform Ops**

We maintain what we built. Upgrades, alert triage, module additions, incident response on the infra layer, cost optimisation, and ongoing infrastructure health reporting. Async-first, no on-call promises — but we're fast when it matters.

---

<img src="https://raw.githubusercontent.com/kubeply/.github/main/assets/banner-platform.svg" alt="Platform modules" width="100%"/>

Every client gets a baseline, then enables only the modules they need. Nothing unnecessary, nothing missing.

<br/>

**Core baseline** — every client

| Module | What it provides |
|--------|-----------------|
| `gitops/` | ArgoCD + Helm repo sources |
| `networking/ingress-nginx` | Ingress controller + TLS |
| `networking/cert-manager` | Let's Encrypt automation |
| `observability/kube-prometheus-stack` | Prometheus + Grafana + Alertmanager |
| `observability/loki` | Log aggregation |
| `security/external-secrets` | Secrets management — Vault, AWS SSM, GCP |
| `security/kyverno` | Policy engine + baseline rules |
| `storage/velero` | Cluster backup + restore |

**AI modules** — opt-in per client

| Module | What it provides |
|--------|-----------------|
| `ai/gpu/` | NVIDIA device plugin + time-slicing |
| `ai/vllm/` | LLM inference serving + autoscaling |
| `ai/qdrant/` | Vector DB + persistence + backups |
| `ai/postgres-operator/` | CloudNativePG + connection pooling |
| `ai/redis/` | Redis + Sentinel |
| `ai/argo-workflows/` | ML pipeline orchestration |

---

<img src="https://raw.githubusercontent.com/kubeply/.github/main/assets/banner-clients.svg" alt="Ideal clients" width="100%"/>

We work best with a specific type of company. If this sounds like you, we should talk.

<br/>

**Best fit**

- AI startup, seed to Series A
- 2–15 engineers, no dedicated platform or infra hire yet
- Running Docker Compose in production — or a single VM with a GPU attached
- Moving toward your first paying customers and need reliability
- Founder or CTO who has personally felt the infra pain

**Not a fit**

- Large enterprise with compliance-heavy requirements
- Company with an existing platform team
- Expecting 24/7 on-call coverage
- Pre-revenue, unfunded — no budget for infrastructure

---

<img src="https://raw.githubusercontent.com/kubeply/.github/main/assets/banner-process.svg" alt="How it works" width="100%"/>

<br/>

```
Step 1 — Audit
  We assess your current stack and deliver a prioritised report.
  This gets us aligned before any code is touched.

Step 2 — Setup
  We provision your cluster, deploy the platform baseline,
  and enable the AI modules you need. You get runbooks,
  architecture docs, and a handover session.

Step 3 — Operate
  We keep it running. Upgrades, monitoring,
  incident support on the infra layer, and regular reporting
  so you always know the state of your platform.

Step 4 — Handover (when you're ready)
  When you hire internally, we hand over cleanly.
  Well-documented, no lock-in, no drama.
```

---

## Repositories

Explore [`ai-infra-platform`](https://github.com/kubeply/ai-infra-platform), our open source reference platform for Terraform provisioning, ArgoCD GitOps, platform modules, and the AI stack we run in production.

---

## Architecture philosophy

Two layers. One clean handoff.

```
terraform/          → provisions cloud infrastructure
                      cluster, DNS, storage, secrets backend
                      outputs kubeconfig

clusters/ + platform/ → ArgoCD owns everything inside
                        opt-in modules per client
                        GitOps reconciliation loop
```

Terraform creates the box. GitOps fills it.
Every client cluster is isolated — separate repo, separate credentials, separate ArgoCD.
Shared implementation, isolated deployment.

---

## Stack

```
Cloud         Hetzner · GKE · EKS
Provisioning  Terraform
GitOps        ArgoCD
Ingress       ingress-nginx + cert-manager
Observability Prometheus + Grafana + Loki + Alertmanager
Secrets       External Secrets Operator
Backup        Velero
Policy        Kyverno
AI / GPU      vLLM · Qdrant · NVIDIA device plugin · Argo Workflows
Database      CloudNativePG · Redis
```

---

<br/>

<p align="center">
  <sub>
    Built by a team who runs this in production.<br/>
    Interested in working together? <a href="mailto:ops@kubeply.com">ops@kubeply.com</a>
  </sub>
</p>
