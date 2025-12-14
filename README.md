# 🛡️ AegiOps: The Autonomous AI SRE

> **The AI Site Reliability Engineer that saves your sleep by fixing Kubernetes crashes before you even wake up.**

[![Kestra](https://img.shields.io/badge/Orchestrated%20with-Kestra-purple)](https://kestra.io)
[![AI](https://img.shields.io/badge/Powered%20by-Gemini%202.5-blue)](https://deepmind.google/technologies/gemini/)
[![Kubernetes](https://img.shields.io/badge/Target-Kubernetes-326ce5)](https://kubernetes.io/)

---

## 📖 About The Project

We've all been there: waking up at 3 AM just to restart a stuck pod or fix a typo in a YAML config. We built **AegiOps** to end that burnout. It’s an autonomous agent that lives inside your cluster and acts as your first line of defense.

Instead of just spamming you with Slack alerts when things break, AegiOps actually **fixes** them. It watches your infrastructure in real-time, uses Gemini AI to understand *why* an error is happening, and executes the right remediation strategy automatically via Kestra.

### ✨ Key Capabilities
* 🚑 **Self-Healing:** Detects crashes and performs safe restarts (Transient) or config patches (Drift).
* 🏗️ **Text-to-Infrastructure:** "Deploy Redis with 3 replicas" → Automatically generates and applies manifest.
* 💰 **FinOps:** Identifies "Zombie Namespaces" wasting resources.
* 🧠 **Deep Analysis:** Explains complex event logs in plain English.

---

## 🏗️ Architecture

AegiOps uses the **Observer-Orient-Decide-Act (OODA)** loop, orchestrated entirely by Kestra.

```mermaid
graph TD
    subgraph P1 ["Phase 1: Observation"]
        A[Kestra Trigger] --> B{Parallel Fetch}
        B --> C[Pods]
        B --> D[Events]
        B --> E[Deployments]
        B --> F[Namespaces]
    end

    subgraph P2 ["Phase 2: The Brain (Gemini)"]
        C & D & E & F --> G{AI Reasoning Core}
        G -->|Analyze Context| H[Determine Intent]
    end

    subgraph P3 ["Phase 3: Decision & Action"]
        H --> I{Intent Switch}
        I -->|REMEDIATE| J[Incident Response]
        J -->|Transient| K[Delete Pod]
        J -->|Config Error| L[Smart Patch Deployment]
        J -->|Fatal| M[Escalate to Human]
        I -->|DEPLOY| N[Apply AI-Generated YAML]
        I -->|COST| O[Analyze Namespace Waste]
        I -->|EXPLAIN| P[Troubleshoot Events]
    end

    subgraph P4 ["Phase 4: Notification"]
        K & L & M & N & O & P --> Q[Slack Alert]
    end

    %% Styling
    style G fill:#ff69b4,stroke:#333,stroke-width:2px,color:white
    style K fill:#b39ddb,stroke:#333,stroke-width:1px,color:black
    style L fill:#b39ddb,stroke:#333,stroke-width:1px,color:black
    style M fill:#b39ddb,stroke:#333,stroke-width:1px,color:black
    style N fill:#b39ddb,stroke:#333,stroke-width:1px,color:black
    style O fill:#b39ddb,stroke:#333,stroke-width:1px,color:black
    style P fill:#b39ddb,stroke:#333,stroke-width:1px,color:black
    style A fill:#e1d5e7,stroke:#9673a6,stroke-width:1px
    style B fill:#e1d5e7,stroke:#9673a6,stroke-width:1px
    style C fill:#e1d5e7,stroke:#9673a6,stroke-width:1px
    style D fill:#e1d5e7,stroke:#9673a6,stroke-width:1px
    style E fill:#e1d5e7,stroke:#9673a6,stroke-width:1px
    style F fill:#e1d5e7,stroke:#9673a6,stroke-width:1px
    style H fill:#e1d5e7,stroke:#9673a6,stroke-width:1px
    style I fill:#e1d5e7,stroke:#9673a6,stroke-width:1px
    style J fill:#e1d5e7,stroke:#9673a6,stroke-width:1px
    style Q fill:#b39ddb,stroke:#333,stroke-width:1px,color:black
```
