# landscape
Example Tech Landscape
| Area | Capability | Pillar | Tool(s) in use | Owner | Hosting | Status (TIME) | Gap / Notes |
|---|---|---|---|---|---|---|---|
| Build & Deliver | Source control | Documented | Azure DevOps Repos | SWE Director | SaaS | Invest | Repo creation limited to one team; code also in SharePoint and on laptops |
| Build & Deliver | CI/CD | Secured | Azure DevOps Pipelines | SWE Director | SaaS | Invest | Recently adopted; no standard templates |
| Build & Deliver | Artifact storage | Documented | TBD | TBD | TBD | TBD | |
| Build & Deliver | Code quality & security scanning | Secured | None | — | — | — | Gap: no linting, testing, SAST or DAST |
| Build & Deliver | Infrastructure as code | Recoverable | None | — | — | — | Gap: no Terraform; Azure is built by hand |
| Secure | Identity & privileged access | Secured | TBD | TBD | TBD | TBD | Production access model undefined |
| Secure | Secrets management | Secured | TBD | TBD | TBD | TBD | |
| Secure | Vulnerability management | Secured | Rapid7 | Security | TBD | TBD | |
| Operate | Monitoring & observability | Monitored | SolarWinds | TBD | On-prem | Eliminate | Replacement under evaluation |
| Operate | Logging & SIEM | Monitored | TBD | TBD | TBD | TBD | |
| Operate | ITSM / ticketing | Documented | TBD | TBD | TBD | TBD | |
| Operate | Backup & DR | Recoverable | TBD | TBD | TBD | TBD | |
| Operate | Service mapping / CMDB | Documented | TBD | TBD | TBD | TBD | Long-term CMDB effort |
| Platform | Compute / virtualization | — | TBD | Infrastructure | On-prem | TBD | Limited control and visibility |
| Platform | Cloud | — | Azure | TBD | Azure | Invest | Small footprint; manual, ungoverned |
| Platform | Containers & orchestration | — | None | — | — | — | Not planned for this phase |
| Platform | Scheduling & workflow orchestration | Recoverable | Windows Task Scheduler | Various | On-prem | Migrate | Evaluating Temporal vs Airflow |
| Platform | RPA & low-code | — | Power Automate, Foxtrot, Blue Prism | TBD | TBD | TBD | Consolidation candidate |
| Platform | Endpoint & configuration management | Secured | TBD | TBD | TBD | TBD | |
| Collaboration | Documentation & knowledge | Documented | SharePoint | TBD | SaaS | Tolerate | Shouldn't hold code |
