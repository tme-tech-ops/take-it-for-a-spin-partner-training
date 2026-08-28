# Take It For a Spin — Dell Automation Platform (DAP) Partner Training

Hands-on training materials for the "Take It For a Spin" Dell Automation Platform (DAP) session, built for **Partners**, **ISVs** (Independent Software Vendors), and **GSIs** (Global Systems Integrators).

## Why take this training

This half-day, hands-on session gets you out of slide decks and into the Dell Automation Platform interface. By the end, you will know how to navigate the DAP Portal, read Orchestrator health, browse infrastructure inventory, manage identity, find and deploy blueprints, and monitor deployments — all from the perspective of your role:

- **Link for DAP/DPC Deployment Competency:** [Dell Private Cloud with DAP Deployment Competency](https://www.delltechnologies.com/assetlink/doc/en-us/deployment-competency-guide-en-dl1m38p-original.pdf) — "Services Competencies are available across Dell Technologies product and service portfolios, enabling and authorizing you to deliver services to your end users"
- **ISVs** see how to package and publish their own software as a blueprint in the DAP Catalog.
- **GSIs** get a head start on Day-2 operations, RBAC, and automation at scale.

No prior DAP experience is required; the labs run in a simulated Demo Center environment with sample inventory and guided walkthroughs.

## Contents

| File | Description |
| --- | --- |
| [`Instructor/DAP_Hands-On_Training_Instructor_Guide.md`](./Instructor/DAP_Hands-On_Training_Instructor_Guide.md) | Instructor-only: agenda/timing, learning objectives, per-module talking points and audience-relevance notes, facilitation tips, pre-session setup checklist. Not for attendee distribution. |
| [`Student/DAP_Hands-On_Training_Student_Lab_Guide.md`](./Student/DAP_Hands-On_Training_Student_Lab_Guide.md) | Attendee-facing: Demo Center access steps and 6 step-by-step labs. |
| [`CHANGELOG.md`](./CHANGELOG.md) | Version history of the training materials. |

## Audience

This session is designed to serve three overlapping partner audiences in the same room:

| Segment | Primary motivation |
| --- | --- |
| **Partners** | Learn to demo, quote, and deploy DAP-based solutions for customers |
| **ISVs** | Package and publish their own software as a blueprint into the DAP Catalog |
| **GSI's** | Operate DAP at scale across many customer tenants — access control, automation, and Day-2 lifecycle |

## Master Agenda (High Level)

~4 hours (half-day), instructor-led, hands-on. Full timing and per-module detail live in the Instructor Guide.

| # | Module | Focus |
| --- | --- | --- |
| 0 | Welcome & Access | Environment access, objectives |
| 1 | Platform Overview | DAP Portal: Home, Assets, Catalog, Identity Management; onboarding prerequisites (PowerStore certificate/account, PowerEdge, entitlement tokens/certificates DDPC only) |
| 2 | Orchestrator Dashboard | Alerts, Events, Infrastructure & Deployments health, Rules & Tags |
| 3 | Orchestrator Administrator | System Settings, Entitlement, Security, Plugins, Support |
| 4 | Inventory & Infrastructure | Filter/browse Private Cloud, Edge, Storage, AI, External Connection, Free Pool; External Connection vCenter/Import to NativeEdge; PowerStore Manager link; Dell Private Cloud plugin showcase via vSphere; drill into a node |
| 5 | Blueprints Catalog | Offer vs Utility Blueprints; Deploy / Add / Upload |
| 6 | Deploy a Blueprint | End-to-end deploy wizard (Deployment Name → Configuration → Summary) |
| 7 | Monitor & Manage Deployments | Deployments list, status, revisions, Day-2 concepts preview |
| 8 | Wrap-up | Recap flow, audience-specific next steps, Q&A/feedback |

## Training Flow

```text
Portal (Home)
   │
   ▼
Orchestrator Dashboard  ──▶  Orchestrator Administrator  ──▶  Inventory: Infrastructure
   │                              (System Settings/Entitlement/   (External Connection/
   │                               Security/Plugins/Support)       PowerStore Manager/
   │                                                              Dell Private Cloud plugin/
   │                                                              drill into a node)
   ▼
Blueprints Catalog (Offer vs Utility)
   │
   ▼
Deploy Wizard  ──▶  Deployments List (monitor status, revisions)
   │
   ▼
Wrap-up: audience-specific next steps
   (Partner: demo/positioning | ISV: publish blueprints | GSI: Day-2/RBAC at scale)
```

## How to Use These Materials

1. Instructors: review the Instructor Guide in full before the session, and complete the **Pre-Session Setup Checklist** (last section).
2. Distribute only the Student Lab Guide to attendees.
3. Follow the **Tell → Show → Do** pattern per module: brief lecture, live instructor demo, then attendees complete the corresponding lab.

## Contributing / Updating

When you materially change the agenda, timing, or lab steps:

1. Update the relevant guide(s).
2. Bump the **Revisions** table at the top of the affected guide(s).
3. Add an entry to [`CHANGELOG.md`](./CHANGELOG.md).
