# Hands-on labs

Start with one small reproducible lab per competence. Suggested sequence:

1. Hardware/workstation diagnosis and OS recovery — BC01
2. Support ticket, diagnosis, escalation and user handoff — BC01
3. Cisco Packet Tracer IPv4/VLAN/routing troubleshooting — BC02
4. Linux server deployment and incident recovery — BC02
5. Windows Server AD/DNS/GPO — BC02
6. KVM virtualization and virtual networking — BC02
7. Hybrid identity and access controls — BC02
8. Script testing and AI-assisted optimization — BC03
9. Backup/restore drill — BC03
10. Monitoring, patching and rollback — BC03

## Optional DevOps extension (planned)

These labs extend the TSSR roadmap; they do **not** replace the BC01–BC03 competency and professional-evidence requirements.

1. [Infrastructure Automation Lab: Terraform + cloud-init + Ansible + Zabbix on KVM/libvirt](https://github.com/oleyna80/it-infrastructure-skills/issues/1) — approved as the **next** hands-on project.
2. CI/CD foundations — GitHub Actions for normal project delivery; optional Jenkins lab using an isolated test deployment of DeFi Agents or AI Secretary.
3. Kubernetes fundamentals — deploy a minimal stateless application to K3s in the KVM lab; verify Pod, Service, Deployment, rollout and resource limits.
4. [GitOps Lab: GitHub Actions + GHCR + Kubernetes reconciliation](https://github.com/oleyna80/it-infrastructure-skills/issues/2) — **after** CI/CD and Kubernetes basics. Practice pull-based CD with Argo CD or Flux, drift detection, controlled sync, rollback and least-privilege access. [Video notes](https://docs.google.com/document/d/1cBD7f-zxsuIOIP9tRxfz7gauuez8WrwreI0IISKKCBI/edit) · [GitHub Actions notes](https://docs.google.com/document/d/1iuLccCeBFtaLSmn3BN6Dm3ozh14Z6ZwuiUJz_R60JtQ/edit)

Maintain existing production Docker Compose deployments unless a separate architectural decision justifies migration. No new paid infrastructure is needed for these local experiments.

Copy [LAB-TEMPLATE.md](LAB-TEMPLATE.md) for each exercise. Document failed tests as well as successes.
