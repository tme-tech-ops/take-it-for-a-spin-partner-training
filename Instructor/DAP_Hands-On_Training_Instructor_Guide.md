# Dell Automation Platform (DAP) — Hands-On Training

## Instructor Guide

### Abstract

This document is provided to assist instructors in delivering the "Dell Automation Platform (DAP) — Take It For a Spin" hands-on training session to **Partners, ISVs (Independent Software Vendors), and GSIs (Global Systems Integrators)**. It contains the session agenda, timing, learning objectives, facilitation notes/talking points, and environment setup checklist. It is a companion to the *DAP Hands-On Training — Student Lab Guide* and should not be distributed to attendees. While this is a simulator environment, it is built from a live functional environment to provide an authentic hands-on experience.

### Revisions

| Version | Date | Description |
| --- | --- | --- |
| 0.1 | 04-Aug-2026 | Initial draft, built from Dell Demo Center / DAP Orchestrator walkthrough content |
| 0.2 | 04-Aug-2026 | Retargeted for Partners, ISVs, and GSIs — added Audience Segments and per-module audience-relevance notes |
| 0.3 | 11-Aug-2026 | Added PowerStore storage onboarding, health check, and OS update guidance to Module 3 |
| 0.4 | 28-Aug-2026 | Swapped Module 3 (Inventory) and Module 4 (Identity Management) order |
| 0.5 | 28-Aug-2026 | Renamed Module 3 to "Orchestrator Administrator" with expanded tab coverage (System Settings, Entitlement, Security, Plugins, Support); added simulator note to abstract |
| 0.6 | 28-Aug-2026 | Added instructor pre-session note to pre-create demo room with 1510 HOL; added facilitation note to minimize lab guide to right side |
| 0.7 | 28-Aug-2026 | Added PowerStore onboarding certificate/user account, PowerEdge onboarding, and entitlement tokens/certificates (DDPC only) references to Module 1 |
| 0.8 | 28-Aug-2026 | Enhanced Module 4 with detailed walkthroughs for each Infrastructure filter chip; added External Connection vCenter/Import to NativeEdge, PowerStore Manager link, and Dell Private Cloud plugin showcase via vSphere with all tabs |
| 0.9 | 28-Aug-2026 | Changed specific vCenter connection name to generic vSphere connection reference in External Connection walkthrough |

### Disclaimer

This is a simulated/demo environment populated with placeholder data intended for training purposes only. Data within the environment does not bear any accuracy to actual pricing or configurations and should not be used as such. Creating, deleting, or updating data in this environment will not affect production systems.

---

## 1. Session Overview

| | |
| --- | --- |
| **Audience** | Partners, ISVs (Independent Software Vendors), and GSIs (Global Systems Integrators) new to Dell Automation Platform (DAP) |
| **Format** | Instructor-led, hands-on (lecture + guided lab per module) |
| **Duration** | ~4 hours (half-day), including breaks |
| **Prerequisites** | Web browser, Dell Demo Center / DAP Take it for a spin access credentials (issued by instructor), basic familiarity with infrastructure/IT ops concepts |
| **Environment** | Dell Demo Center-hosted DAP tenant (Orchestrator + Portal), pre-seeded with sample inventory (Private Cloud, Edge, Storage, Free Pool nodes) and sample blueprints |

### 1.1 Audience Segments

This session is designed to serve three overlapping but distinct partner audiences in the same room. Use these lenses when fielding questions and pacing modules:

| Segment | Primary motivation | Modules of highest interest |
| --- | --- | --- |
| **Partners** (resellers/field engineers) | Learn to demo, quote, and deploy DAP-based solutions for customers | Modules 1–4, 6–7 (portal tour, orchestrator administrator, inventory, deploy, monitor) |
| **ISVs** (Independent Software Vendors) | Understand how to package and publish their own software as a blueprint into the Catalog for customers to consume | Modules 5–6 (Blueprints Catalog, Deploy) — emphasize the Offer Blueprint model and Upload path |
| **GSIs** (Global Systems Integrators) | Operate DAP at scale across many customers/tenants — access control, automation, and Day-2 lifecycle matter most | Modules 3, 7 (Orchestrator Administrator, Deployments/Day-2 concepts) |

Call out audience relevance explicitly at the start of each module (see talking points below) so each group knows why a given screen matters to their role.

### 1.2 Learning Objectives

By the end of the session, attendees will be able to:

1. Navigate the DAP Portal (Home, Assets, Catalog, Identity Management) and the DAP Orchestrator.
2. Read the Orchestrator Dashboard (Alerts, Events, Infrastructure & Deployments health, Rules & Tags).
3. Browse and filter Inventory/Infrastructure across Private Cloud, Edge, Storage, AI, External Connection, and Free Pool asset types.
4. Drill into a physical node to review hardware health, firmware versions, and available updates.
5. Distinguish Offer Blueprints from Utility Blueprints in the Blueprints catalog.
6. Deploy a blueprint end-to-end using the Deploy wizard (Deployment Name → Configuration → Summary).
7. Monitor deployment status/history from the Deployments list and describe basic Day-2 concepts (reinstall, drift, update).

### 1.3 Facilitation Notes

- Keep a 1:6 instructor-to-attendee ratio if possible; use TAs to unblock login/access issues quickly — this is the most common time sink.
- Each module follows a **Tell → Show → Do** pattern: brief lecture, live instructor demo, then attendees repeat the steps themselves from the Student Lab Guide.
- Encourage attendees to explore filters/columns rather than only following steps verbatim — the portal is read-mostly and safe to click around in.
- Have a rollback/reset plan: know how to reset a given student environment/project if a deployment fails or gets stuck.
- Instruct attendees to minimize the lab guide to the right side of their screen for easy reference while working in the DAP interface.

---

## 2. Agenda & Timing

| Time | Duration | Module | Type |
| --- | --- | --- | --- |
| 0:00–0:15 | 15 min | Welcome, objectives, environment access | Lecture |
| 0:15–0:35 | 20 min | Module 1: Platform Overview (Home, Assets, Catalog, Identity Management cards) | Lecture + Demo |
| 0:35–1:00 | 25 min | Module 2: Orchestrator Dashboard | Demo + Lab |
| 1:00–1:35 | 35 min | Module 3: Orchestrator Administrator (System Settings, Entitlement, Security, Plugins, Support) | Demo + Lab |
| 1:35–1:45 | 10 min | Break | — |
| 1:45–2:15 | 30 min | Module 4: Inventory & Infrastructure deep dive | Demo + Lab |
| 2:15–2:30 | 15 min | Module 5: Blueprints Catalog | Demo |
| 2:30–3:15 | 45 min | Module 6: Deploy a Blueprint (guided lab) | Lab |
| 3:15–3:25 | 10 min | Break | — |
| 3:25–3:50 | 25 min | Module 7: Monitor & Manage Deployments | Demo + Lab |
| 3:50–4:00 | 10 min | Wrap-up, Q&A, feedback | Lecture |

---

## 3. Module Detail

### Module 1 — Platform Overview (20 min)

**Objective:** Orient attendees to the DAP Portal landing page and its three pillars.

**Audience relevance:** Baseline orientation for all three segments — Partners see the demo/sales surface, ISVs see where their blueprint will eventually surface (Catalog), GSIs see where multi-tenant administration happens (Identity Management).

**Talking points:**

- The Portal Home page is the entry point above the Orchestrator: **Assets** (onboard/monitor Dell hardware), **Catalog** (curated library of validated blueprints/plugins), **Identity Management** (users/access).
- **Manage Your Infrastructure → Orchestrator** is where day-to-day inventory, blueprint, and deployment work happens (opens in a new tab/window).
- Point out **Additional Services** (AIOps Integration, AI Solution Assistant) as "Coming Soon" — sets roadmap expectations without over-promising.
- **PowerStore onboarding prerequisites:** Mention that onboarding PowerStore arrays requires a dedicated local PowerStore account with the Storage Administrator role, and TLS trust with the PowerStore management certificate. The DAP OXY component must be able to reach the floating management IP and all cluster nodes.
- **PowerEdge onboarding:** Note that PowerEdge servers can be onboarded as individual assets or as part of clusters (Private Cloud, Free Pool). Onboarding typically involves network connectivity, credentials, and discovery mechanisms.
- **Entitlement tokens and certificates:** Explain that entitlement tokens and certificates are DDPC (Dell Demo Center) only features used for validating access and licensing in the demo environment. These are not used in production DAP deployments.

**Demo:** Log into the Portal, tour each card, click "Go to Orchestrator."

**Lab checkpoint:** Attendees log in and locate all three pillar cards plus the Orchestrator link.

---

### Module 2 — Orchestrator Dashboard (25 min)

**Objective:** Teach attendees to read platform health at a glance.

**Audience relevance:** Partners use this as their "is everything healthy before a customer demo" check. GSIs will use this daily/at scale across customer tenants — emphasize that Events and Alerts are the first triage screen when supporting many deployments.

**Talking points:**

- **Alerts (last 24 hours)**: Critical / Error / Warning / Information counts — first place to check platform health.
- **Events** table: chronological log of orchestrator activity (web-socket connections, executions, drift checks) — useful for troubleshooting.
- **Infrastructure and Deployments** rings: Infrastructure ring = count/state of onboarded assets (Processing, Online, Disconnected, Maintenance, Updating); Deployments ring = lifecycle status (Completed, In Progress, Cancelled, Failed).
- **Rules and Tags** tab: automation rules and resource tags applied across the environment.

**Demo:** Walk the dashboard top-to-bottom, click "View All" on Alerts/Events.

**Lab checkpoint:** Attendees identify current Online vs Disconnected asset counts and Completed vs Failed deployment counts.

---

### Module 3 — Orchestrator Administrator (35 min)

**Objective:** Understand the Orchestrator's administrative settings and configuration options.

**Audience relevance:** This is the **GSI headline module** — GSIs operating DAP across many customer environments need to understand system settings, entitlements, security configurations, and plugin management for proper platform administration. ISVs should pay attention to **Plugins** as this is where custom blueprint components and integrations are managed. Partners mainly need to understand the **Support** tab for troubleshooting and the **Entitlement** tab for license management during customer engagements.

**Talking points:**

- Reached via gear icon → **Settings**. Walk through each tab:

#### System Settings

- Platform-wide configuration options including time zone, date/time format, and regional settings
- System information such as version, build number, and platform details
- Notification settings and alert thresholds

#### Entitlement

- License management and subscription information
- Feature entitlements and capabilities enabled for the tenant
- Usage metrics and consumption tracking
- License expiration and renewal information

#### Security

- Authentication and authorization settings
- SSL/TLS certificate management
- Password policies and security configurations
- Audit logging and security event tracking

#### Plugins

- Available plugins for extending DAP functionality
- Plugin installation, configuration, and management
- Custom blueprint components and integration points
- Plugin versioning and update management

#### Support

- Platform health and diagnostic information
- Support ticket creation and management
- System logs and troubleshooting resources
- Contact information for Dell support

- Tie back to real-world scenarios per audience: a GSI managing 30 customer tenants needs to standardize system settings and security policies across tenants; an ISV uses Plugins to integrate their custom components; a Partner uses Support to resolve issues and Entitlement to validate customer licenses.

**Demo:** Open Settings, step through each tab (System Settings, Entitlement, Security, Plugins, Support) and explain the key options available in each.

**Lab checkpoint:** Attendees identify which settings tab they would use for common administrative tasks (e.g., where to check license status, where to manage plugins, where to configure security settings).

---

### Module 4 — Inventory & Infrastructure Deep Dive (30 min)

**Objective:** Navigate multi-asset-type inventory and drill into a physical node.

**Audience relevance:** Partners see the breadth of infrastructure they can position/sell against. ISVs should note that their software will ultimately run on top of these onboarded targets (Private Cloud, Edge, AI). GSIs should focus on how inventory scales and stays organized (tags, asset types) across many customer environments.

**Talking points:**

- Left nav under **Inventory**: Infrastructure, Virtual Machines, Deployments, Blueprints.
- Infrastructure filter chips: **All / Private Cloud / Edge / Storage / AI / External Connection / Free Pool** — step through each chip and explain the category:
  - **Private Cloud** = Nutanix/VMware/OpenShift clusters
  - **Edge** = edge computing assets
  - **Storage** = storage arrays including PowerStore
  - **AI** = AI infrastructure assets
  - **External Connection** = Kubernetes and vCenter connections at this time
  - **Free Pool** = unassigned/bare PowerEdge servers ready for provisioning
- Grid columns matter: Asset Type, Environment, Status, Provisioning State, Device Model, Version, Tags — these drive filtering/sorting at scale.
- Expandable rows show child hosts under a cluster (e.g., a Nutanix cluster expands into its member PowerEdge hosts with service tags).

#### External Connection walkthrough

- Select the **External Connection** chip to show Kubernetes and vCenter connections.
- Navigate to **Virtual Machines** and locate a vSphere connection.
- Click on a stopped VM, then click the **More** dropdown to show the **Import to NativeEdge** option. Explain this allows importing VMs to NativeEdge for edge computing scenarios.

#### Storage & PowerStore walkthrough

- Select the **Storage** chip to show storage assets.
- Click on a PowerStore row to open its summary.
- Click the **PowerStore Manager** link to launch the PowerStore management interface. This provides direct access to the native PowerStore console for advanced storage management.

#### Dell Private Cloud plugin showcase via vSphere

- Navigate to **Infrastructure → Private Cloud VMware vSphere**.
- Click **Launch Dell Private Cloud** in the top right to open the vSphere interface.
- Navigate to **Datacenter → Cluster** then click the **Configure** tab.
- Scroll to the **Dell Private Cloud** plugin and showcase all available tabs:
  - **System** — overall system health and status
  - **Physical View** — front/back chassis view with health information
  - **Settings** — configuration options
  - **Updates** — firmware and software updates (zero day patching allowed)
  - **Security** — security settings and policies
  - **Support** — support resources and diagnostics
- Emphasize that all Dell Private Cloud outcomes have the same set of tabs, allowing for administrative consistency across different outcomes.
- **Important:** When finished with the vSphere walkthrough, logout from vSphere to return to the Orchestrator simulator. Only show this vSphere perspective once during the module.

#### Node drilling walkthrough

- Drilling into a node opens its native management console view (Overview / Physical View / Updates / Security / Settings / Support) — show Physical View (front/back chassis view with health), and Updates tab (firmware/update advisor).

#### Storage & PowerStore lifecycle details

PowerStore arrays appear as **Storage** assets in DAP once onboarded. Use these points when attendees ask about PowerStore lifecycle management:

- **Prerequisites for onboarding:** PowerStore T or Q model running **PowerStoreOS 3.0 or later** (PowerStoreOS 4.0 or later is required for DAP-orchestrated software upgrades); a dedicated local PowerStore account with the **Storage Administrator** role; TLS trust with the PowerStore management certificate; the DAP OXY component able to reach the floating management IP and all cluster nodes.
- **Onboarding flow:** In the DAP Portal, go to **Home → Go to Assets → Add Assets → Storage**. Enter the floating management IP, the dedicated Storage Administrator credentials, and certificate information, then click **Onboard**.
- **In the Orchestrator:** Once onboarded, the PowerStore cluster is visible under **Inventory → Infrastructure**. Available actions include editing properties, testing the connection, running a **pre-upgrade health check**, and upgrading **PowerStoreOS** (PowerStoreOS 4.0 or later).
- **Health checks:**
  - **System Check** — built into PowerStoreOS; run before maintenance and periodically.
  - **Pre-Upgrade Health Check (PUHC)** — included with upgrade packages; run before any OS upgrade.
  - **Health Check thin packages** — off-release packages that add checks for newly discovered issues; upload and install separately.
- **OS updates through DAP:**
  1. Download the PowerStoreOS upgrade package from Dell Support.
  2. In the Orchestrator, select the PowerStore cluster and run a **pre-upgrade health check**.
  3. Review results and remediate any issues.
  4. Initiate **Upgrade** and apply the package.
  5. Monitor the job through **Events**, **Alerts**, and **Jobs**.
  6. Re-run health checks after the upgrade completes.
- **Planning note:** Nondisruptive upgrades (NDU) are supported, but plan them during maintenance windows or low activity because half of the system hardware resources may be unavailable during parts of the upgrade. Also verify that any installed Health Check, Language Pack, or Disk Firmware packages are compatible with the new PowerStoreOS release.

**Demo:** Step through each Infrastructure filter chip (All, Private Cloud, Edge, Storage, AI, External Connection, Free Pool). For External Connection, show the vCenter connection and Import to NativeEdge option. For Storage, show PowerStore Manager link. Launch Dell Private Cloud via vSphere and showcase all plugin tabs. Expand a cluster, open a member host, review Physical View and Updates.

**Lab checkpoint:** Attendees filter by each asset-type chip once, identify the External Connection options, locate PowerStore Manager link, and open one node's Physical View to identify health status and update information.

---

### Module 5 — Blueprints Catalog (15 min)

**Objective:** Understand blueprint sourcing before deploying one.

**Audience relevance:** This is the **ISV headline module**. The Catalog is the mechanism by which an ISV's packaged software/solution becomes discoverable and deployable by Partners and GSIs' customers. Be explicit that "Upload" is the ISV's path to publish their own blueprint, and that Offer Blueprint metadata (Tags, Revision, Deployments count) is what customers will use to evaluate and trust a published solution.

**Talking points:**

- Inventory → **Blueprints**, two tabs: **Offer Blueprints** (tailored to your specific product/configuration, e.g. `DPC_Nutanix_Cluster_Deployment`, `DPC_OpenShift_Cluster_Migration`) vs **Utility Blueprints** (support the infrastructure/services behind a deployment, not deployed directly).
- Grid shows Status (Uploaded), Revision, Type (Service), Deployments count, Created By, Tags — reinforces blueprint versioning and reuse. For ISVs, this is effectively their product's storefront listing.
- Three ways to get a blueprint into the catalog: **Deploy** (existing), **Add** (from catalog), **Upload** (your own package — the primary ISV workflow).
- Mention (don't deep-dive) that blueprint authoring/wrapping is covered in a separate, follow-on session for ISVs who want to publish their own software.

**Demo:** Open Offer Blueprints tab, sort by Deployments to show which blueprints are most used.

---

### Module 6 — Deploy a Blueprint (45 min, core lab)

**Objective:** Attendees perform a full deployment using the wizard.

**Audience relevance:** Common ground for all three segments — this is the "moment of truth" experience a Partner will demo to customers, an ISV should validate for their own published blueprint, and a GSI will repeat at scale (often via automation/API rather than the wizard UI — mention this parallel without demoing it).

**Talking points:**

- Select a blueprint (e.g., `DPC_Nutanix_Cluster_Deployment`) → **Deploy**.
- Wizard steps: **Deployment Name** → **Configuration** (Deployment Inputs — optionally load from a file, then fill required fields like File Server Root Path, cluster host table with service_tag/hypervisor_ip/controller_vm_ip) → **Summary** (review before submit).
- Point out required-field markers (`*`) and inline info tooltips (`ⓘ`) — a recurring UX pattern across all DAP forms.
- Reference the embedded **simulated walkthrough video** pattern DAP surfaces for complex targets (e.g., "Nutanix Cluster Deployment walkthrough") — these substitute for a live target hardware demo in a training environment.

**Demo:** Run the full wizard live once, narrating each field.

**Lab checkpoint:** Each attendee deploys the assigned sample blueprint end-to-end and confirms it appears in the Deployments list with status "Deployed" (or watches progress if async).

**Common issues to pre-empt:**

- Required cluster-host rows must be added via the **Add** button before **Update**/Next is enabled.
- If using the platform file server for images, the checkbox must be ticked before the path field is usable.

---

### Module 7 — Monitor & Manage Deployments (25 min)

**Objective:** Close the loop — verify and track what was deployed.

**Audience relevance:** Second GSI headline module — Day-2 lifecycle (update, drift, reinstall) is exactly the operational burden GSIs are hired to manage across large customer estates. ISVs should note the Revision column: this is how customers will track which version of their published blueprint is running where. Partners use this to confirm/report deployment success back to the customer.

**Talking points:**

- Inventory → **Deployments**: Name, Target, Created, Status (Deployed / Uninstalled / Failed Install), Blueprint Name, Revision, Type, Deployments (sub-deployment count), Tags.
- Point out revision badges (e.g., "1.3.0" with an icon) indicating blueprint version used at deploy time — segues into Day-2 concepts.
- Briefly preview Day-2 lifecycle actions available from a deployment: **Update**, **Run workflow**, drift check status, reinstall — full depth is out of scope for this session but should be named as a GSI-relevant follow-on topic.

**Demo:** Open the Deployments list, locate the attendee's own deployment, open it to show its detail/execution history.

**Lab checkpoint:** Attendees locate their deployment and report its current status to the instructor.

---

### Module 8 — Wrap-up (10 min)

- Recap the flow: **Portal → Orchestrator → Inventory (Infrastructure) → Blueprints → Deploy → Deployments (monitor)**.
- Preview next-level topics, tailored by audience:
  - **Partners:** deeper product-specific deploy scenarios, quoting/positioning guidance.
  - **ISVs:** blueprint authoring/wrapping (Blueprint Assist), publishing to the Catalog, versioning strategy.
  - **GSIs:** Day-2 update/drift/reinstall workflows, RBAC/multi-tenant standardization, Rules & Tags automation, API/CLI-driven deployment at scale.
- Collect feedback (use the in-app Feedback tab shown throughout the portal as a talking point).

---

## 4. Pre-Session Setup Checklist (Instructor)

- [ ] A couple days before the class start, pre-create the demo room and have the 1510 HOL loaded.
- [ ] Confirm Demo Center / DAP Take it for a spin room URL and per-student jumphost/login list.
- [ ] Verify sample inventory is online (Private Cloud, Edge, Storage, Free Pool nodes all "Online"/"Connected").
- [ ] Verify at least one deployable Offer Blueprint per attendee/project namespace.
- [ ] Pre-stage any required input files (e.g., service tags, IPs) attendees will need to paste into the Configuration step.
- [ ] Test the full deploy wizard once end-to-end in the training tenant before class.
- [ ] Have a reset/rollback procedure ready in case a deployment needs to be deleted and redeployed mid-class.
