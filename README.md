# Platform Engineer · DevOps · SRE

**I build and operate Google Cloud infrastructure as code — and make high-blast-radius changes
boring.** The craft I care about is turning "this could cause an outage" into a routine,
reviewable, reversible operation: find the version of the change that can't break, prove it
can't with a `preview` or an empirical check, and encode the invariant so it can never silently
regress.

Everything here is **original, generic, and anonymized** — reference patterns and case studies
distilled from real production ownership, with no proprietary or customer data.

---

## What I do

| Area | In practice |
|---|---|
| **Infrastructure as Code** | Pulumi (Python), many small independent stacks, `StackReference` contracts, safe state surgery (`import`, `refresh`, `state delete`) |
| **Cloud security** | Least-privilege IAM, Workload Identity Federation (keyless CI), Binary Authorization, Shielded VMs, org policy, Cloud Armor WAF |
| **Reliability & DR** | Recreate-vs-restore disaster recovery, stateful snapshot recovery, deletion protection, multi-region uptime |
| **Observability** | Prometheus + Grafana + Alertmanager and GCP Cloud Monitoring; severity routing, on-call enrichment, SLO-style alerting |
| **Operational safety** | `preview`-gated deploys, adopting click-ops drift without outages, invariant-enforcing tests |
| **FinOps** | Cost reduction gated on empirical safety checks, not guesswork |

## Featured work

### 🏛️ [gcp-pulumi-reference-architecture](https://github.com/teamiumtree/gcp-pulumi-reference-architecture)
A multi-project GCP estate as many small, independent Pulumi stacks — dependency graph,
`StackReference` contracts, deploy ordering, **standing up a whole new environment (UAT) from
config with zero new code**, and a **recreate-vs-restore disaster-recovery** model.

### 🔐 [iac-security-patterns](https://github.com/teamiumtree/iac-security-patterns)
The patterns where a subtle IaC mistake becomes a security incident — each paired with the
failure mode it prevents and the test that stops it recurring:
- **Authoritative IAM** — one binding per role, enforced by an **AST regression test** that fails CI on a duplicate
- **Keyless CI (WIF/OIDC)** — no service-account keys; trust pinned to *immutable* repo claims
- **Adopting click-ops into IaC** — `import` + `protect` + `retain_on_delete`, minimal blast radius
- **Binary Authorization** — dry-run → enforce, with a risk-acceptance memo

### 📓 [platform-engineering-case-studies](https://github.com/teamiumtree/platform-engineering-case-studies)
Honest problem → constraints → approach → outcome write-ups: keyless-CI migration, race-free
IAM consolidation, click-ops adoption, zero-downtime Shielded-VM rollout, standing up a new UAT
environment, disaster recovery, and cost optimization with empirical safety gating.

### 📊 [prometheus-grafana-observability](https://github.com/teamiumtree/prometheus-grafana-observability)
A full observability & alerting stack — Prometheus (GCE service discovery) + Grafana (SSO,
dashboards-as-code) + Alertmanager, alongside GCP Cloud Monitoring — with severity-based routing
(page vs. chat), on-call enrichment, and a **two-tier public status page**.

## How I work

- **`preview` is the gate.** No change lands without a clean, understood plan — an unexpected
  *replace* is a stop-and-investigate signal, not a rubber-stamp.
- **Encode safety in the pipeline, not a runbook.** If a rule matters, a test enforces it; a
  comment that says "don't do this" will eventually be ignored.
- **Smallest blast radius that solves the problem.** Govern a resource without owning every
  field of it; touch only what the change requires.

## Toolbox

`Pulumi` · `Python` · `Google Cloud` · `GitHub Actions` · `Workload Identity Federation` ·
`Cloud Run` · `IAM` · `Binary Authorization` · `Cloud Armor` · `Ansible` · `Prometheus` ·
`Grafana` · `Alertmanager` · `PagerDuty` · `BigQuery` · `Bash`

---

<sub>All repositories contain original, generic, anonymized reference material — patterns and
case studies, never proprietary or customer data.</sub>
