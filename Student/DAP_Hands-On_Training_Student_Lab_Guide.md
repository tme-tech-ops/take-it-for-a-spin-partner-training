# Dell Automation Platform (DAP) "Take It For a Spin" Hands-On Training

## Student Lab Guide

### About This Guide

This guide accompanies the instructor-led DAP hands-on session for Partners, ISVs (Independent Software Vendors), and GSIs (Global Systems Integrators). Each lab follows the same pattern: your instructor explains the topic, demonstrates it, and then you complete the steps yourself.

Use this guide alongside the instructor's walkthrough. It does not cover everything discussed in class and is not intended for use on its own.

The labs run in a simulator built from a live DAP environment, so the screens and workflows match the real product.

### Revisions

| Version | Date | Description |
| --- | --- | --- |
| 0.1 | 04-Aug-2026 | Initial draft |
| 0.2 | 04-Aug-2026 | Retargeted for Partners, ISVs, and GSIs; updated abstract and "What's next" section |
| 0.3 | 11-Aug-2026 | Added PowerStore health check and OS update steps to Lab 2 |
| 0.4 | 28-Aug-2026 | Swapped Lab 2 (Infrastructure Inventory) and Lab 3 (Identity Management) order |
| 0.5 | 28-Aug-2026 | Renamed Lab 2 to "Orchestrator Administrator" with expanded tab coverage; added simulator note to abstract |
| 0.6 | 28-Aug-2026 | Added student prerequisites with link to Partner-Access-Demo-Center.pdf; added lab guide placement note |
| 0.7 | 28-Aug-2026 | Added PowerStore and PowerEdge onboarding prerequisites to Lab 1 |
| 0.8 | 28-Aug-2026 | Added External Connection, PowerStore Manager link, and Dell Private Cloud plugin demonstration to Lab 3 |
| 0.9 | 28-Aug-2026 | Replaced specific vCenter connection name with a generic vSphere reference |
| 1.0 | 08-Oct-2026 | Updated for accuracy against the latest releases |
| 1.1 | 09-Oct-2026 | Restructured labs into parts; added lab overview, key terms, note-taking tables, and checkpoint questions; tightened wording |

### Disclaimer

The information in this publication is provided "as is." Dell Inc. makes no representations or warranties of any kind with respect to the information in this publication, and specifically disclaims implied warranties of merchantability or fitness for a particular purpose.

This is a simulated environment populated with placeholder data for demonstration purposes only. The data does not reflect actual pricing or configurations and should not be used as such. Changes you make in the simulator (creating, updating, or deleting items) do not alter the baseline data.

© 2026 Dell Inc. or its subsidiaries. All Rights Reserved. Dell, EMC, Dell Technologies and other trademarks are trademarks of Dell Inc. or its subsidiaries. Other trademarks may be trademarks of their respective owners.

---

## Before the Session

- Read [Partner-Access-Demo-Center.pdf](../docs/Partner-Access-Demo-Center.pdf) for instructions on accessing and navigating Dell Demo Center.
- Make sure you have a Dell Demo Center account. If not, create one at `https://democenter.dell.com/` before the session.

---

## Accessing the Lab

1. Go to `https://democenter.dell.com/` and click **Customer Sign In**.
2. Sign in with your Demo Center account.
3. Open the DAP "Take It For a Spin" room using the URL your instructor provides.
4. From the list of Hands-On Labs, launch the lab your instructor specifies.

Your instructor will orient you within the lab environment.

---

## Lab Overview

| Lab | Topic | Hands-on time |
| --- | --- | --- |
| 1 | DAP Portal and Orchestrator Dashboard | 
| 2 | Orchestrator Administration |
| 3 | Infrastructure Inventory | 
| 4 | Blueprints Catalog | 
| 5 | Deploying a Blueprint |
| 6 | Monitoring Deployments |

### Key Terms

| Term | Meaning |
| --- | --- |
| **Portal** | The DAP entry point for Assets, Catalog, and Identity Management |
| **Orchestrator** | Where inventory, blueprints, and deployments are managed day to day |
| **Blueprint** | A deployable automation package that defines infrastructure or software and how to install it |
| **Offer Blueprint** | A blueprint for a specific product or configuration that you deploy directly |
| **Utility Blueprint** | A blueprint that supports the infrastructure or services behind a deployment; not deployed directly |
| **Deployment** | An instance of a blueprint, created when you deploy it |
| **Free Pool** | Servers that are online and ready for provisioning but not yet assigned to a cluster |
| **External Connection** | A connection to an existing external platform, such as Kubernetes or vCenter |

---

## Lab 1: DAP Portal and Orchestrator Dashboard

**Goal:** Find your way around the DAP Portal and read platform health from the Orchestrator Dashboard.

### Part A: The Portal

1. Open the DAP Portal URL provided by your instructor.
2. On the **Home** tab, locate the three cards under **Explore Dell Automation Platform**:

   | Card | Purpose |
   | --- | --- |
   | **Assets** | Onboard and view Dell Storage, Network, and Compute devices from one asset register |
   | **Catalog** | Browse a library of validated and non-validated blueprints and tools |
   | **Identity Management** | Manage users and access for the Portal and Orchestrator |

3. Follow along as your instructor walks through the Catalog, Identity Management, and Asset onboarding.

**Onboarding prerequisites to note:**

- **PowerStore:** A dedicated local PowerStore account with the Storage Administrator role, and TLS trust with the PowerStore management certificate.
- **PowerEdge:** Servers are onboarded as individual assets. The Orchestrator or an Orchestrator Proxy needs network connectivity to each server's iDRAC. The exception is FIDO Device Onboarding (FDO), which your instructor will cover.

### Part B: The Orchestrator Dashboard

4. Under **Manage Your Infrastructure**, click **Orchestrator**.
5. Review each area of the Dashboard:
   - **Alerts (last 24 hours):** Counts by severity (Critical, Error, Warning, Information).
   - **Events:** A running log of Orchestrator activity.
   - **Infrastructure and Deployments:** Rings showing asset states (such as Online and Disconnected) and deployment states (such as Completed and Failed).
   - **Rules and Tags:** Automation rules and resource tags. Rules may be empty in the lab environment.
6. Click **View All** next to **Events** to open the full log, then return to the Dashboard.

**Checkpoint**

- How many assets are Online?
- How many deployments are Completed?

---

## Lab 2: Orchestrator Administration

**Goal:** Learn where the Orchestrator's key administrative settings live.

1. In the Orchestrator, click the gear icon (**Settings**) at the top right.
2. Your instructor will step through each menu. Use the table below to note what the key menus are for:

   | Menu | What it is used for |
   | --- | --- |
   | **Entitlement** | |
   | **Plugins** | |
   | **Support** | |
   | **Proxy Servers** | |

3. Open the remaining menus and identify the purpose of each.

**Checkpoint:** Which menu would you use to:

- Check license status?
- Install or update a plugin?
- Configure security settings?
- Gather information for a support case?

---

## Lab 3: Infrastructure Inventory

**Goal:** Filter onboarded infrastructure by type, drill into a host, and review a PowerStore storage cluster.

### Part A: Filter the Inventory

1. In the left navigation, expand **Inventory** and select **Infrastructure**.
2. Click each filter chip and watch how the grid changes: **All**, **Private Cloud**, **Edge**, **Storage**, **AI**, **External Connection**, **Free Pool**.
3. Select **External Connection** and note the Kubernetes and vCenter connections.
4. Select **Free Pool**. These servers are online and ready for provisioning but not yet assigned to a cluster.

### Part B: Drill Into a Host

5. Select **Private Cloud**. Clusters may include VMware vSphere, Red Hat OpenShift, and Nutanix.
6. Click the expand arrow (`>`) next to a cluster (for example, `demo-ntx01`) to show its member hosts, including service tags and device models.
7. Click a host's hostname link to open its native management console view.
8. Close the console and return to the **Infrastructure** grid.

### Part C: Review PowerStore Storage

9. Select **Storage** and click the PowerStore cluster name (for example, `demo-powerstore01`) to open its summary.
10. Note the cluster status and the installed PowerStoreOS version.
11. Click **Run Health Check** and note the available checks: **Pre-Upgrade Health Check (PUHC)** and any installed **Health Check packages**.
12. Click **Update** and note the installed PowerStoreOS version and whether an upgrade package is available.
13. Locate the **PowerStore Manager** link. It opens the native PowerStore management interface.

**Instructor demonstration:** Your instructor will show the Dell Private Cloud plugin in vSphere, covering the **System**, **Physical View**, **Settings**, **Updates** (including zero-day patching), **Security**, and **Support** tabs. Dell Private Cloud outcomes provide the same value propositions, so the outcome is consistent across platforms.

**Checkpoint**

- Name at least three of the six infrastructure categories.
- What is a Free Pool asset?
- What types of External Connection are listed?
- Where is the PowerStore Manager link?
- Where do you find PowerStore health status and OS update information?

---

## Lab 4: Blueprints Catalog

**Goal:** Tell Offer Blueprints and Utility Blueprints apart before deploying one.

1. In the left navigation under **Inventory**, select **Blueprints**.
2. On the **Offer Blueprints** tab, review the grid columns: Name, Status, Revision, Type, Revision Date, Deployments, Created By, Tags.
3. Click the **Deployments** column header to sort by usage.
4. Open the **Utility Blueprints** tab. These support the infrastructure and services behind a deployment and are not deployed directly.
5. Return to the **Offer Blueprints** tab. You will deploy one of these in Lab 5.

**Checkpoint**

- What is the difference between an Offer Blueprint and a Utility Blueprint?
- Which Offer Blueprint has the most deployments?

---

## Lab 5: Deploying a Blueprint

**Goal:** Deploy a blueprint end to end using the Deploy wizard, and watch it run.

1. On the **Offer Blueprints** tab, select the blueprint your instructor assigns (for example, `DPC_VSphere_Cluster_Deployment`) and click **Deploy**.
2. **Deployment Name:** A name is filled in automatically. Change it if you like, and make a note of it for Lab 6. Click **Next**.
3. **Configuration:** Deployment inputs are pre-loaded from a file. Required fields are marked with `*`. Hover over the `ⓘ` icon next to a field for its description. Leave the pre-loaded values unless your instructor tells you otherwise, then click **Next**.
4. Review the summary and click **Deploy**.
5. Open the new deployment and select **Logs**. Follow the execution graph and log output until the deployment finishes.

**Checkpoint:** Your deployment appears in the Deployments list. Its status shows **Deployed** or **In Progress**, depending on the target and the simulation.

---

## Lab 6: Monitoring Deployments

**Goal:** Read deployment status and trace a failed deployment to the step that caused it.

1. Go to **Inventory > Deployments**.
2. Find your deployment by name.
3. Review the columns: Target, Created, Status, Blueprint Name, Revision, Type, Deployments (number of sub-deployments), Last Updated, Tags.
   - **Status** shows Deployed, Uninstalled, or Failed Install.
   - **Revision** shows which blueprint version the deployment used.
4. Click your deployment's name to open its Logs and review its execution graph.

**Checkpoint**

- What is your deployment's current status?
- Which blueprint and revision was it deployed from?

---

## Summary

You have completed the DAP hands-on session and worked through the core workflow:

**Portal > Orchestrator Dashboard > Orchestrator Administration > Infrastructure Inventory > Blueprints Catalog > Deploy > Monitor Deployments**

### What's Next?

- **Partners:** Product-specific deployment scenarios, plus customer demo and positioning guidance.
- **ISVs:** Authoring and publishing your own blueprints with Blueprint Assist, and versioning your Catalog listing.
- **GSIs:** Day-2 operations (updates, drift detection, reinstall), RBAC and multi-tenant standardization, and automation with Rules and Tags.
