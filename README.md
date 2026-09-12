# Shashi Prakash Dubey

**Platform Engineer · DevOps · SRE** — Google Cloud, Pulumi (Python), and the discipline that
makes high-blast-radius infrastructure changes boring.

![Google Cloud](https://img.shields.io/badge/Google%20Cloud-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![Pulumi](https://img.shields.io/badge/Pulumi-8A3391?style=flat-square&logo=pulumi&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Terraform-free](https://img.shields.io/badge/IaC-Pulumi%2C%20not%20Terraform-555?style=flat-square)

I own a multi-project GCP estate end to end — infrastructure as code, keyless CI, observability,
on-call, and the security posture around all of it.

Everything below is **original, generic and anonymized**: reference architectures, patterns and
case studies distilled from real production ownership, with no proprietary or customer data.

---

## Start here

Three entry points, depending on what you came to find out:

| If you want to see… | Read this | Time |
|---|---|---|
| **How I think about failure** — the IaC mistakes that become security incidents, each paired with the test that stops it recurring | [iac-security-patterns](https://github.com/shashiprakashdubey/iac-security-patterns) | ~2 min |
| **How I structure a platform** — a multi-project GCP estate as many small, independent Pulumi stacks | [gcp-pulumi-reference-architecture](https://github.com/shashiprakashdubey/gcp-pulumi-reference-architecture) | ~3 min |
| **How it actually went** — problem → constraints → approach → how I knew it worked | [platform-engineering-case-studies](https://github.com/shashiprakashdubey/platform-engineering-case-studies) | ~2 min |

## All repositories

| Repo | What it is | The idea worth stealing |
|---|---|---|
| 🏛️ **[gcp-pulumi-reference-architecture](https://github.com/shashiprakashdubey/gcp-pulumi-reference-architecture)** | A multi-project GCP estate as many small, independent Pulumi stacks | Stacks talk *only* through `StackReference` outputs, so deploy order falls out of the dependency graph |
| 🔐 **[iac-security-patterns](https://github.com/shashiprakashdubey/iac-security-patterns)** | The four IaC patterns where a subtle mistake is a security incident, not a broken build | An **AST regression test** that fails CI if a second authoritative IAM binding for a role ever appears |
| 📦 **[dependabot-at-scale](https://github.com/shashiprakashdubey/dependabot-at-scale)** | Dependency automation once it stops being a checkbox | `ignore` + `update-types` never constrains **security** updates — so every semver hold is advisory until CI enforces it |
| 📓 **[platform-engineering-case-studies](https://github.com/shashiprakashdubey/platform-engineering-case-studies)** | Seven honest write-ups of migrations I led | Finding the version of a change that *can't* cause an outage, then proving it |
| 📊 **[prometheus-grafana-observability](https://github.com/shashiprakashdubey/prometheus-grafana-observability)** | Prometheus + Grafana + Alertmanager alongside GCP Cloud Monitoring | Severity decides the channel: what pages a human at 3am vs. what just posts to chat |
| 🔎 **[elasticsearch-on-gcp-pulumi](https://github.com/shashiprakashdubey/elasticsearch-on-gcp-pulumi)** | Elasticsearch + Kibana on GCP, two ways: one hardened cluster, or a per-tenant fleet | Managing a *stateful* VM with Pulumi without ever letting it be **replaced** |

## What I work on

| Area | In practice |
|---|---|
| **Infrastructure as Code** | Pulumi (Python), many small stacks, `StackReference` contracts, safe state surgery (`import`, `refresh`, `state delete`) |
| **Cloud security** | Least-privilege IAM, Workload Identity Federation (keyless CI), Binary Authorization, Shielded VMs, org policy, Cloud Armor |
| **Reliability & DR** | Recreate-vs-restore recovery, stateful snapshot recovery, deletion protection, multi-region uptime |
| **Observability** | Prometheus, Grafana, Alertmanager, Cloud Monitoring; severity routing, on-call enrichment |
| **Supply chain** | Dependabot across several ecosystems and dozens of manifest directories, with CI guards that enforce what the config alone can't |
| **FinOps** | Cost reduction gated on empirical safety checks, not guesswork |

## How I work

- **`preview` is the gate.** No change lands without a clean, understood plan — an unexpected
  *replace* is a stop-and-investigate signal, not a rubber-stamp.
- **Encode safety in the pipeline, not a runbook.** If a rule matters, a test enforces it; a
  comment saying "don't do this" will eventually be ignored.
- **Smallest blast radius that solves the problem.** Govern a resource without owning every
  field of it; touch only what the change requires.

## Toolbox

`Pulumi` · `Python` · `Google Cloud` · `GitHub Actions` · `Workload Identity Federation` ·
`Cloud Run` · `IAM` · `Binary Authorization` · `Cloud Armor` · `Ansible` · `Prometheus` ·
`Grafana` · `Alertmanager` · `PagerDuty` · `Elasticsearch` · `Kibana` · `BigQuery` ·
`Dependabot` · `Bash`

---

<sub>All repositories contain original, generic, anonymized reference material — patterns and
case studies, never proprietary or customer data.</sub>
