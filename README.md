# Platform / DevOps / SRE Engineering

I design and operate **Google Cloud** infrastructure as code — the kind of work where a
subtle mistake is a security incident or an outage, so the craft is in making high-blast-radius
changes *boring*: find the version that can't break, prove it can't, and encode the invariant so
it can't silently regress.

The repositories here distill that practice into **generic, anonymized** reference material —
patterns and case studies, not any one organization's internals.

## Focus

- **Infrastructure as Code** — Pulumi (Python), multi-stack architectures, safe state operations
- **Cloud security** — least-privilege IAM, Workload Identity Federation, Binary Authorization, Shielded VMs, org policy
- **Operational safety** — `preview`-gated changes, adopting drift without outages, invariant-enforcing tests
- **CI/CD** — keyless GitHub Actions → GCP, changed-stack pipelines
- **FinOps** — cost optimization gated on empirical safety checks

## Repositories

### 🏛️ [gcp-pulumi-reference-architecture](https://github.com/teamiumtree/gcp-pulumi-reference-architecture)
A multi-project GCP estate as many small, independent Pulumi stacks — dependency graph,
`StackReference` contracts, deployment ordering, and the change-safety discipline that keeps a
growing estate manageable.

### 🔐 [iac-security-patterns](https://github.com/teamiumtree/iac-security-patterns)
The patterns where a subtle IaC mistake becomes a security problem — each with the failure mode
it prevents and, where it applies, the test that stops it recurring:
- **Authoritative IAM** — one binding per role, and an **AST regression test** that fails CI if a duplicate ever appears
- **Keyless CI (WIF/OIDC)** — no service-account keys; trust pinned to immutable repo claims
- **Adopting click-ops into IaC** — `import` + `protect` + `retain_on_delete`, minimal blast radius
- **Binary Authorization** — dry-run → enforce, with a risk-acceptance memo

### 📓 [platform-engineering-case-studies](https://github.com/teamiumtree/platform-engineering-case-studies)
Honest problem → constraints → approach → outcome write-ups: a keyless-CI migration, race-free
IAM consolidation, click-ops adoption, a zero-downtime Shielded-VM rollout, and cost optimization
with empirical safety gating.

### 📊 [prometheus-grafana-observability](https://github.com/teamiumtree/prometheus-grafana-observability)
A full observability & alerting stack: Prometheus (GCE service discovery) + Grafana (SSO,
dashboards-as-code) + Alertmanager, alongside GCP Cloud Monitoring — with severity-based routing
(page vs. chat), on-call enrichment, and a two-tier public status page.

## Toolbox

`Pulumi` · `Python` · `Google Cloud` · `GitHub Actions` · `Workload Identity Federation` ·
`Cloud Run` · `IAM` · `Binary Authorization` · `Cloud Armor` · `Ansible` · `Prometheus` · `Grafana` · `Alertmanager` · `PagerDuty`

---

<sub>All content is generic and anonymized — reference patterns, no proprietary or customer data.</sub>
