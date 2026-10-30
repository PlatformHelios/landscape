# landscape
Example Tech Landscape
| Tool | Area | Capability | Pillar | Owner | Used by / Scope | Hosting | Status (TIME) | Gap / Notes |
|---|---|---|---|---|---|---|---|---|
| Azure DevOps Repos | Build & Deliver | Source control | Documented, Secured, Recoverable | SWE Director | SWE team (~95%) | SaaS | Invest | Repo creation limited to one team; other code in SharePoint and on laptops |
| Azure DevOps Pipelines | Build & Deliver | CI/CD | Secured, Documented | SWE Director | SWE team | SaaS | Invest | Recently adopted; no standard templates |
| TBD | Build & Deliver | Artifact storage | Recoverable, Secured | TBD | TBD | TBD | TBD | |
| None | Build & Deliver | Code quality & security scanning | Secured | — | — | — | — | Gap: no linting, testing, SAST or DAST |
| None | Build & Deliver | Infrastructure as code | Recoverable, Secured, Documented | — | — | — | — | Gap: no Terraform; Azure is built by hand |
| TBD | Secure | Identity & privileged access | Secured | TBD | Enterprise-wide | TBD | TBD | Production access model undefined |
| TBD | Secure | Secrets management | Secured | TBD | TBD | TBD | TBD | |
| Rapid7 | Secure | Vulnerability management | Secured, Monitored | Security | Enterprise-wide | TBD | TBD | |
| SolarWinds | Operate | Monitoring & observability | Monitored | TBD | TBD | On-prem | Eliminate | Replacement under evaluation |
| TBD | Operate | Logging & SIEM | Monitored, Secured | TBD | TBD | TBD | TBD | |
| TBD | Operate | ITSM / ticketing | Documented | TBD | Enterprise-wide | TBD | TBD | |
| TBD | Operate | Backup & DR | Recoverable | TBD | TBD | TBD | TBD | |
| TBD | Operate | Service mapping / CMDB | Documented, Monitored | TBD | TBD | TBD | TBD | Long-term CMDB effort |
| TBD | Platform | Compute / virtualization | Foundation | Infrastructure | Enterprise-wide | On-prem | TBD | Limited control and visibility |
| Azure | Platform | Cloud | Foundation | TBD | Limited teams | Azure | Invest | Small footprint; manual, ungoverned |
| None | Platform | Containers & orchestration | Foundation | — | — | — | — | Not planned for this phase |
| Windows Task Scheduler | Platform | Scheduling & workflow orchestration | Monitored, Recoverable | Various | .NET integration teams, others | On-prem | Migrate | Evaluating Temporal vs Airflow |
| Power Automate | Platform | RPA & low-code | Foundation | TBD | Business-side teams | SaaS | TBD | Overlaps with Foxtrot and Blue Prism |
| Foxtrot | Platform | RPA & low-code | Foundation | TBD | TBD | TBD | TBD | Overlaps with Power Automate and Blue Prism |
| Blue Prism | Platform | RPA & low-code | Foundation | TBD | SWE RPA team | TBD | TBD | Overlaps with Power Automate and Foxtrot |
| TBD | Secure | Endpoint & configuration management | Secured, Recoverable | TBD | TBD | TBD | TBD | |
| SharePoint | Collaboration | Documentation & knowledge | Documented | TBD | Enterprise-wide | SaaS | Tolerate | Shouldn't hold code |


# Technology Landscape — Current-State Breakdown

*Draft, based on the initial inventory. Items marked TBD still need confirmation from their owners.*

## At a glance

| Metric | Count |
|---|---|
| Capabilities assessed | 19 |
| Known tools | 10 |
| Capabilities with **no tool** (gaps) | 3 |
| Capabilities still **TBD** | 9 |
| Capabilities with **overlapping tools** | 1 (RPA & low-code: 3 tools) |
| Known tools with **no confirmed owner** | 6 of 10 |

---

## 1. Coverage by pillar

Capabilities can support more than one pillar, so each capability is counted under every pillar it supports.

| Pillar | Capabilities | In place | Gap / at risk | TBD | Read |
|---|---|---|---|---|---|
| **Secured** | 10 | Azure DevOps Repos, Azure DevOps Pipelines, Rapid7 | Code quality & security scanning (none); Infrastructure as code (none) | Artifact storage, Identity & privileged access, Secrets, Endpoint & config mgmt, Logging & SIEM | Broadest pillar; access and secrets are unconfirmed |
| **Monitored** | 5 | Rapid7 | SolarWinds (eliminate); Windows Task Scheduler (migrate) | Logging & SIEM, Service mapping / CMDB | No go-forward monitoring tool in place |
| **Documented** | 6 | Azure DevOps Repos, Azure DevOps Pipelines, SharePoint | Infrastructure as code (none) | ITSM, Service mapping / CMDB | Source control exists but most teams can't use it |
| **Recoverable** | 6 | Azure DevOps Repos | Infrastructure as code (none); Windows Task Scheduler (migrate) | Artifact storage, Endpoint & config mgmt, Backup & DR | Least mature; environments can't be rebuilt from code |
| *Foundation* | 4 | Azure, Power Automate, Foxtrot, Blue Prism | Containers (none, deferred) | Compute / virtualization | Azure is manual and ungoverned |

**Takeaway:** *Monitored* and *Recoverable* have no healthy go-forward tooling today. Infrastructure as code is a gap in three pillars at once, which makes it the highest-leverage single investment.

---

## 2. Gaps (no tool in place)

| Capability | Pillar | Risk | Direction |
|---|---|---|---|
| Code quality & security scanning | Secured | Defects and vulnerabilities reach production undetected; no audit evidence of code review controls | Linting, tests, secret/dependency scanning and SAST built into pipeline templates |
| Infrastructure as code | Recoverable, Secured, Documented | Environments can't be reproduced or audited; changes are untracked | Terraform for Azure, starting with a governed landing zone |
| Containers & orchestration | — | Low near-term risk | Deferred until foundations are in place |

---

## 3. Overlaps (consolidation candidates)

| Capability | Tools | Observation |
|---|---|---|
| RPA & low-code | Power Automate, Foxtrot, Blue Prism | Three platforms for one capability, split across SWE and business teams. Candidate for a single standard through the Automation CoE |
| Monitoring & observability | SolarWinds → *replacement under evaluation* | Avoid a period of running two tools in parallel without a cutover plan |

---

## 4. Disposition (TIME)

| Status | Tools | Meaning |
|---|---|---|
| **Invest** | Azure DevOps Repos, Azure DevOps Pipelines, Azure | Expand and standardize |
| **Tolerate** | SharePoint | Keep for documents; remove code from it |
| **Migrate** | Windows Task Scheduler | Move jobs to the enterprise orchestrator (Temporal vs Airflow under evaluation) |
| **Eliminate** | SolarWinds | Retire once replacement is live |
| **Not yet rated** | Rapid7, Power Automate, Foxtrot, Blue Prism | Need owner input |

---

## 5. Ownership and access

| Finding | Detail |
|---|---|
| Tools without a confirmed owner | SolarWinds, Azure, Power Automate, Foxtrot, Blue Prism, SharePoint |
| Shared, unowned operation | Windows Task Scheduler jobs owned by "various" teams |
| Concentrated access | Repo creation limited to one team; ~95% of source control use is the SWE team |

Clear ownership is a prerequisite for every other improvement, and an expected control in a regulated environment.

---

## 6. Key findings

1. **No automated quality or security checks on code.** Nothing between a developer's machine and production checks for defects, vulnerabilities or leaked credentials.
2. **Infrastructure can't be rebuilt from code.** Azure and on-prem environments are configured by hand, which limits recovery and auditability.
3. **Observability is in transition with no destination yet.** SolarWinds is being retired and the replacement isn't selected.
4. **Code lives outside source control.** Most teams store and run code from SharePoint or local machines.
5. **Ownership is unclear for most tools.** This needs resolving before standards can be enforced.
6. **Automation tooling is fragmented.** Three RPA platforms plus Windows scheduled jobs, with no common orchestrator.

---

## 7. Next steps to complete the inventory

- Confirm the 9 TBD capabilities with Security, Infrastructure, Identity and Service Desk leads
- Assign an owner for every known tool
- Rate the unrated tools (Rapid7 and the RPA platforms) on TIME
- Review findings with tool owners before presenting more widely
