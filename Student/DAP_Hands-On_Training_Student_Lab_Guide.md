# Dell Automation Platform (DAP) — "Take It For a Spin" Hands-On Training

## Student Lab Guide

### Abstract

This document is provided to assist Partners, ISVs (Independent Software Vendors), and GSIs (Global Systems Integrators) with completing the appropriate labs to apply the concepts and knowledge learnt throughout the Dell Automation Platform (DAP) hands-on training session. It is not intended to be used or distributed in isolation and may not contain all required information.

### Revisions

| Version | Date | Description |
| --- | --- | --- |
| 0.1 | 04-Aug-2026 | Initial draft |
| 0.2 | 04-Aug-2026 | Retargeted for Partners, ISVs, and GSIs — updated abstract and "What's next" section |

### Disclaimer

The information in this publication is provided "as is." Dell Inc. makes no representations or warranties of any kind with respect to the information in this publication, and specifically disclaims implied warranties of merchantability or fitness for a particular purpose.

This is a simulated environment populated with placeholder data intended for demonstration purposes only. Data within this environment does not bear any accuracy to actual pricing or configurations and should not be used as such. Creating, deleting, or updating data in this environment will not have an effect on the initial items displayed before the change.

© 2026 Dell Inc. or its subsidiaries. All Rights Reserved. Dell, EMC, Dell Technologies and other trademarks are trademarks of Dell Inc. or its subsidiaries. Other trademarks may be trademarks of their respective owners.

---

## Dell Demo Center Access

1. Open a web browser and access the following URL: `https://democenter.dell.com/`
2. Click the **Customer Sign In** link.
3. Sign in with an existing account or create a new account.
4. The URL to the Demo Center Test Drive room for **Dell Automation Platform** will be provided by your instructor.
5. You will see a list of Jumphosts. Select and launch the Jumphost that corresponds to your assigned student number.
6. Log in to the Windows virtual machine with the username and password provided prior to class. Expand the blue panel on the right of the jumphost window and use the **Paste Text** function to copy/paste your username and password.
7. Launch Chrome. If prompted to configure a default search engine on first login, complete it (or skip if not prompted).
8. Enter the URL of the DAP Portal provided by your instructor into the browser address bar.

---

## Lab 1: Exploring the DAP Portal and Orchestrator Dashboard

**Goal:** Get oriented in the DAP Portal, understand the three portal pillars, and learn to read the Orchestrator health dashboard.

1. Open a browser and navigate to the DAP Portal URL provided by your instructor.
2. Accept the self-signed certificate if prompted.
3. Sign in with the credentials provided.
4. On the **Home** tab, review the three cards under "Explore Dell Automation Platform":
   - **Assets** — onboard and monitor Dell hardware from a centralized location.
   - **Catalog** — access a curated library of validated blueprints and plugins.
   - **Identity Management** — manage users and access for the portal and orchestrator.
5. Under "Manage Your Infrastructure," click **Go to Orchestrator** (opens in a new tab).
6. On the Orchestrator **Dashboard**, review:
   - **Alerts (last 24 hours)** — Critical / Error / Warning / Information counters.
   - **Events** — the running log of orchestrator activity.
   - **Infrastructure and Deployments** rings — note the current counts (e.g., Online vs Disconnected assets; Completed vs Failed deployments).
   - **Rules and Tags** — automation rules and resource tags (may be empty in this environment).
7. Click **View All** next to Events to see the full event log, then navigate back to the Dashboard.

*Checkpoint: You should be able to state how many assets are Online and how many deployments are Completed/Failed in the current environment.*

---

## Lab 2: Browsing Infrastructure Inventory

**Goal:** Filter and inspect onboarded infrastructure across asset types, and drill into a physical node.

1. In the left navigation, expand **Inventory** and select **Infrastructure**.
2. Note the filter chips across the top: **All**, **Private Cloud**, **Edge**, **Storage**, **AI**, **External Connection**, **Free Pool**. Click through each to see how the grid filters.
3. Select the **Private Cloud** chip. You should see clusters such as a VMware, Red Hat OpenShift, and/or Nutanix private cloud.
4. Click the expand arrow (`>`) next to a cluster row (e.g., `ntnx-dpcvm...`) to reveal its member hosts (service tags, device models).
5. Click on one member host's service tag link (e.g., an `8SP5L84`-style link) to open its native management console view.
6. In the node console, review the **Overview** tab (power status, health, firmware versions) and the **Physical View** tab (front/back chassis view).
7. Click the **Updates** tab to see currently installed versions and whether updates are available.
8. Close the node console and return to the Infrastructure grid. Select the **Free Pool** chip to see servers that are online and ready for provisioning but not yet assigned to a cluster.

*Checkpoint: You should be able to name at least 3 of the 6 infrastructure categories and describe what a Free Pool asset is.*

---

## Lab 3: Reviewing Identity Management

**Goal:** Understand how access is controlled in DAP.

1. From the Orchestrator, click the gear icon (**Settings**) in the top-right, then select **Identity Management**.
2. Select the **Roles** tab. Review the predefined roles and note the **Role Type** column (Portal vs Orchestrator):
   - Portal Viewer / Portal Administrator / Portal Operational Manager
   - Orchestrator Viewer / Orchestrator Administrator / Orchestrator Application Admin / Orchestrator Operational Manager
3. Select the **Users** tab and click **Manage Users** to see how users are associated with roles.
4. Select the **Clients** tab to see service-account/API client entries.
5. Select the **Web Sessions** tab to see currently active sessions.

*Checkpoint: Identify which role your training account has been assigned.*

---

## Lab 4: Browsing the Blueprints Catalog

**Goal:** Understand the difference between Offer Blueprints and Utility Blueprints before deploying one.

1. In the left navigation under **Inventory**, select **Blueprints**.
2. On the **Offer Blueprints** tab, review the grid: Name, Status, Revision, Type, Revision Date, Deployments, Created By, Tags.
3. Sort by the **Deployments** column (click the column header) to see which blueprints have been used most often.
4. Click the **Utility Blueprints** tab and note that these support infrastructure/services behind a deployment rather than being deployed directly.
5. Return to the **Offer Blueprints** tab — you will deploy one of these in Lab 5.

---

## Lab 5: Deploying a Blueprint

**Goal:** Deploy a sample blueprint end-to-end using the Deploy wizard.

1. On the **Offer Blueprints** tab, select the blueprint assigned by your instructor (e.g., `DPC_Nutanix_Cluster_Deployment`).
2. Click **Deploy**.
3. **Step 1 — Deployment Name:** Enter a unique deployment name (e.g., `<your-student-number>-cluster-deploy`) and click **Next**.
4. **Step 2 — Configuration:**
   - Optionally click **Browse** to load Deployment Inputs from a file.
   - Fill in the required fields marked with `*` (hover the `ⓘ` icon next to any field for a description). For a Nutanix cluster deployment example, this includes:
     - **File Server Root Path**
     - Whether to use the Dell Automation Platform file server for AHV/AOS images
     - **Cluster Hosts** table entries: `service_tag`, `hypervisor_ip`, `controller_vm_ip` (click **Add** after entering each row)
   - If your blueprint links to a simulated walkthrough video (e.g., "Nutanix Cluster Deployment walkthrough"), watch it to see what the real target-side configuration (network interfaces, cluster settings) would look like.
   - Click **Next**.
5. **Step 3 — Summary:** Review all entered values. If everything looks correct, click **Deploy** (or **Finish**, depending on the wizard's final label).
6. Wait for the deployment to be created, then navigate to **Inventory → Deployments** to confirm your deployment appears in the list with the name you chose.

*Checkpoint: Your deployment should be visible in the Deployments list. Status may show as "Deployed," or "In Progress" depending on the target and simulation.*

---

## Lab 6: Monitoring Deployments

**Goal:** Track and interpret the status of your deployment.

1. Go to **Inventory → Deployments**.
2. Locate your deployment by the name you assigned in Lab 5.
3. Review the columns: Target, Created, **Status** (Deployed / Uninstalled / Failed Install), Blueprint Name, **Revision**, Type, Deployments (sub-deployment count), Last Updated, Tags.
4. Click on your deployment's name to open its detail view and review its execution history.
5. If your deployment shows **Failed Install**, click into it to review the execution log and identify which step failed (this is for observation only — do not attempt to fix production issues during class; ask your instructor).

*Checkpoint: You can describe your deployment's current status and which blueprint/revision it was deployed from.*

---

## Summary

Congratulations — you have completed the Dell Automation Platform (DAP) hands-on training session. You have practiced the full end-to-end workflow: **Portal → Orchestrator Dashboard → Infrastructure Inventory → Identity Management → Blueprints Catalog → Deploy → Monitor Deployments**

### What's next?

- **If you're a Partner:** deeper, product-specific deployment scenarios and customer demo/positioning guidance.
- **If you're an ISV:** authoring and publishing your own blueprints (Blueprint Assist), and versioning your Catalog listing.
- **If you're a GSI:** Day-2 operations (updates, drift detection, reinstall workflows), RBAC/multi-tenant standardization, and automation via Rules and Tags.
