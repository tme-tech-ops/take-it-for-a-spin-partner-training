# Changelog

All notable changes to the "Take It For a Spin" DAP partner training materials are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [Unreleased]

### Added (Unreleased)

- Added instructor pre-session note to pre-create demo room with 1510 HOL a couple days before class.
- Added facilitation note to minimize lab guide to right side of screen in Instructor Guide.
- Added student prerequisite activities section in Student Lab Guide with link to Partner-Access-Demo-Center.pdf.
- Added on-premises login option instruction in Student Lab Guide.
- Added lab guide minimization note in Student Lab Guide.
- Added simulator note to abstract in both Instructor Guide and Student Lab Guide, clarifying that the environment is built from a live functional environment.
- Added PowerStore onboarding certificate/user account, PowerEdge onboarding, and entitlement tokens/certificates (DDPC only) references to Module 1 in Instructor Guide.
- Added PowerStore onboarding certificate/user account, PowerEdge onboarding, and entitlement tokens/certificates (DDPC only) references to Lab 1 in Student Lab Guide.
- Updated README.md master agenda to include onboarding prerequisites in Module 1 description.
- Enhanced Module 4 in Instructor Guide with detailed walkthroughs for each Infrastructure filter chip (All, Private Cloud, Edge, Storage, AI, External Connection, Free Pool).
- Added External Connection walkthrough in Module 4 showing vCenter connection and Import to NativeEdge option for stopped VMs.
- Added Storage & PowerStore walkthrough in Module 4 showing PowerStore Manager link to launch native management interface.
- Added Dell Private Cloud plugin showcase via vSphere in Module 4 with all tabs (System, Physical View, Settings, Updates, Security, Support) and administrative consistency note.
- Enhanced Lab 3 in Student Lab Guide with External Connection vCenter/Import to NativeEdge steps and PowerStore Manager link reference.
- Added Dell Private Cloud plugin demonstration note to Lab 3 in Student Lab Guide.
- Updated README.md master agenda and training flow diagram to reflect Module 4 enhancements (External Connection, PowerStore Manager, Dell Private Cloud plugin).

### Changed (Unreleased)

- Changed specific vCenter connection name to generic vSphere connection reference in External Connection walkthrough in both Instructor Guide and Student Lab Guide.
- Renamed Module 3 in Instructor Guide from "Identity Management" to "Orchestrator Administrator" with expanded coverage of System Settings, Entitlement, Security, Plugins, and Support tabs.
- Renamed Lab 2 in Student Lab Guide from "Reviewing Identity Management" to "Orchestrator Administrator" with expanded coverage of System Settings, Entitlement, Security, Plugins, and Support tabs.
- Updated audience segment references in the Instructor Guide to reflect the new module name (Partners: orchestrator administrator, GSIs: Orchestrator Administrator).
- Updated the master agenda and training flow diagram in README.md to reflect the new module name and tab coverage.
- Swapped Module 3 (Inventory & Infrastructure) and Module 4 (Identity Management) order in the Instructor Guide — Identity Management now comes before Infrastructure.
- Swapped Lab 2 (Infrastructure Inventory) and Lab 3 (Identity Management) order in the Student Lab Guide — Identity Management now comes before Infrastructure.
- Updated audience segment references in the Instructor Guide to reflect the new module order (Partners: Modules 1–4, GSIs: Module 3).
- Updated the master agenda and training flow diagram in README.md to reflect the new module order.
- Replaced the Partner bullet in `README.md` with a link to the Dell Private Cloud with DAP Deployment Competency guide.
- Reorganized repo: guides moved into dedicated `Instructor/` and `Student/` folders; removed `example-content/` reference material after incorporation into the guides.
- Updated README file paths to match new folder structure.
- Simplified the wrap-up agenda item by removing the Day-2 preview reference in the Instructor Guide.

## [0.2.0] - 2026-08-04

### Added (0.2.0)

- README with master high-level agenda, training flow diagram, and contribution notes.
- CHANGELOG (this file).

### Changed (0.2.0)

- Retargeted both guides to explicitly serve **Partners, ISVs, and GSIs**:
  - Instructor Guide: added an "Audience Segments" table and per-module "Audience relevance" callouts; framed Module 4 (Identity Management) as the GSI headline module and Module 5 (Blueprints Catalog) as the ISV headline module; audience-specific wrap-up next steps.
  - Student Lab Guide: updated abstract and closing "What's next" section with per-audience follow-on paths.

## [0.1.0] - 2026-08-04

### Added (0.1.0)

- Initial Instructor Guide: session overview, learning objectives, agenda/timing (8 modules, ~4 hours), per-module talking points/demo/lab-checkpoint notes, pre-session setup checklist.
- Initial Student Lab Guide: Demo Center access steps and 6 hands-on labs (Portal/Dashboard tour, Infrastructure inventory, Identity Management, Blueprints Catalog, Deploy a Blueprint, Monitor Deployments).
