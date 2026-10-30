# ServiceOps — Deep Product & Market Research

**Owner / Content Creator:** Sandeep Barupal  
**Copyright:** © 2026 Sandeep Barupal. All rights reserved, except third-party resources under their own terms.  
**Research status:** Deep-research baseline v1.0 — desk research, pending service-management workflow validation.

## 1. Product thesis
ServiceOps should connect service desk, assets/configuration, change/release, incidents, problem management and operational reliability without forcing teams to maintain disconnected records. Its core differentiator should be a traceable service-to-asset-to-incident relationship and safe cross-team workflows.

## 2. Category boundaries
ITSM focuses on service delivery workflows; IT operations management covers monitoring, automation and infrastructure operations; IT asset management tracks lifecycle and ownership; ITOM/observability supplies signals and topology. Combining these areas is valuable only when data ownership and integration boundaries are clear. ServiceNow documentation describes ITSM around incidents, requests, problems and changes; Atlassian's ITSM guide explains service-management practices; OpenTelemetry supplies a standard telemetry foundation. Sources: [ServiceNow ITSM](https://www.servicenow.com/docs/r/it-service-management/r_ITServiceManagement.html), [Atlassian ITSM](https://www.atlassian.com/itsm), [OpenTelemetry](https://opentelemetry.io/docs/).

## 3. Competitor comparison
| Reference category | Examples | Focus to study |
|---|---|---|
| Enterprise ITSM suite | ServiceNow | Broad workflows, CMDB, governance and automation |
| Agile/dev-centric service management | Jira Service Management | Incident/change coordination and developer workflow |
| Cloud service desk | Freshservice | Setup speed, portal, knowledge, agent experience |
| Observability/incident tooling | Grafana, Datadog, PagerDuty | Signal-to-incident handoff, on-call and operational context |
| Asset management | ITAM platforms | Lifecycle, reconciliation, contract and ownership |

Do not assume all-in-one architecture is best; research whether target teams prefer modular adoption.

## 4. Feature specification
### P0
- Unified service catalog and ownership registry.
- Incidents, service requests, problems and change requests with linked records.
- Asset inventory and service/asset relationship graph.
- SLA/OLA calendars, approvals, knowledge articles and audit log.
- Integrations for email, webhook, identity, monitoring and issue tracking.
- Unified search and role-aware dashboards.
### P1
- Change risk assessment, maintenance windows, release calendar and rollback evidence.
- Event-to-incident correlation and runbook association.
- CMDB reconciliation rules, duplicate/conflict queues and relationship history.
- Automation with approval gates, retries and run history.
### P2
- Service health scorecards, dependency impact, AI-assisted triage and cross-system workflow orchestration.

## 5. Page map
Operations Home; Service Catalog; Services; Service Map; Incidents; Requests; Problems; Changes; Releases; Assets/CMDB; SLA/OLA; Knowledge; Automation; Integrations; Reports; Audit; Admin.

## 6. Data and architecture
Core entities: tenant, service, team, user, asset, configuration item, relationship, incident, request, problem, change, release, SLA policy, approval, automation run and audit event. Keep each record's source and last-sync timestamp. Use integration adapters and event bus; define a canonical state model but preserve external IDs and source states. Avoid silent overwrites during sync.

## 7. Governance and security
Role- and record-level permissions; separation of duties for high-risk changes; approval and rollback requirements; immutable audit events; secret management; scoped integration tokens; privacy-aware incident logs; tenant isolation and retention policies. AI-generated recommendations should show the evidence and require human approval for operational changes.

## 8. Metrics and acceptance criteria
- A service has a named owner and support path.
- Incident can be traced to affected service, assets, changes and response timeline.
- CMDB conflicts are surfaced and reconciled.
- Change approvals record approver, risk, evidence and rollback plan.
- Metrics: MTTR, change failure rate, SLA attainment, repeat incidents, stale-CMDB rate, automation success and handoff count.

## 9. Risks and validation
Risks: over-broad scope, poor CMDB data, complex customization, integration loops and unsafe automation. Validate the top 3 workflows with IT teams before building a broad suite. Run an incident/change tabletop and compare the number of manual handoffs to current practice.

## 10. References
- [ServiceNow ITSM documentation](https://www.servicenow.com/docs/r/it-service-management/r_ITServiceManagement.html)
- [Atlassian ITSM guide](https://www.atlassian.com/itsm)
- [Freshservice pricing/features](https://www.freshworks.com/freshservice/pricing/)
- [OpenTelemetry docs](https://opentelemetry.io/docs/)
- [Google SRE Book](https://sre.google/sre-book/table-of-contents/)

## 11. Next work
Define initial product boundary (ITSM-first versus operations-first), create a canonical data dictionary, research current plan limits, and validate cross-module user journeys before committing to all-in-one scope.