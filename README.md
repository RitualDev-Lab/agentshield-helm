# AgentShield Production Kubernetes Helm Charts 🛡️

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/agentshield&style=for-the-badge)](https://artifacthub.io)
[![Air-Gapped Architecture](https://img.shields.io/badge/Architecture-100%25%20Air--Gapped%20VPC-00F59B?style=for-the-badge)](https://ritualdev.in/trust)
[![SOC 2 / DPDP Ready](https://img.shields.io/badge/Compliance-SOC%202%20Type%20II%20%2F%20DPDP-00D4FF?style=for-the-badge)](https://ritualdev.in/trust)

> Production-grade Kubernetes Helm charts, NetworkPolicies, and Docker Compose recipes for deploying AgentShield inside air-gapped enterprise Virtual Private Clouds (VPC).

---

## 🏛️ Architecture Overview

The AgentShield Helm Chart deploys an isolated, non-root DaemonSet/Deployment designed for zero-leak defense across autonomous agent execution pools:

- **Strict NetworkPolicy**: All outbound traffic to the public internet is blocked (`policyTypes: [Ingress, Egress]`). Only internal RFC 1918 VPC CIDRs are permitted.
- **Seccomp & Hardened PodSecurity**: Drops all Linux capabilities (`cap_drop: ALL`), read-only root filesystem, unprivileged user `10001`.
- **HMAC Audit Ledger**: Ingests and signs incident events locally with zero telemetry egress.

---

## 🚀 Quickstart with Helm

### 1. Add Repository

```bash
helm repo add ritualdev https://charts.ritualdev.in
helm repo update
```

### 2. Install to Kubernetes

```bash
helm install agentshield ./charts/agentshield \
  --namespace agentshield-system \
  --create-namespace \
  -f my-custom-values.yaml
```

---

## 🐳 Docker Compose (Air-Gapped Local Stack)

To run the complete isolated enterprise stack locally or on a private VM:

```bash
cd docker-compose
docker compose up -d
```

This provisions:
- `agentshield-runtime` (:3000)
- `dbshield-proxy` (:5433)
- `skillprism-cache` (:6379)
- `postgres-upstream` (:5432)
All bound to an `internal: true` Docker bridge network with no external internet gateway.

---

## 📄 License

MIT © [RitualDev Studio](https://ritualdev.in)

---

---

## 💖 Sponsor & Support

If you find this project valuable, consider supporting our open-source development:

[![Sponsor on Dodo Payments](https://img.shields.io/badge/Sponsor_via_Dodo-Payments-8b5cf6?style=for-the-badge&logo=shield&logoColor=white)](https://checkout.dodopayments.com/buy/pdt_0NpjONGugY5QkrFDUaPva)
[![Interactive Donation Portal](https://img.shields.io/badge/Donation_Portal-Cards%20%7C%20UPI%20%7C%20Apple%20Pay-ff5964?style=for-the-badge&logo=heart&logoColor=white)](https://ritualdev.in/donate)
[![GitHub Sponsors](https://img.shields.io/badge/GitHub_Sponsors-RitualDev--Lab-ea4aaa?style=for-the-badge&logo=githubsponsors&logoColor=white)](https://github.com/sponsors/RitualDev-Lab)

- [**⚡ 1-Click Dodo Payments Checkout**](https://checkout.dodopayments.com/buy/pdt_0NpjONGugY5QkrFDUaPva)
- [**🎁 Interactive Donation Portal**](https://ritualdev.in/donate)
- [**❤️ GitHub Sponsors**](https://github.com/sponsors/RitualDev-Lab)

---

## 🛡️ Community & Governance
- [Code of Conduct](CODE_OF_CONDUCT.md)
- [Contributing Guidelines](CONTRIBUTING.md)
- [Security Policy](SECURITY.md)
- [Accessibility Statement](ACCESSIBILITY.md)
- [License](LICENSE)
