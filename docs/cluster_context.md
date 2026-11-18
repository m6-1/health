# SICK0H Cluster: Hermes Operational Context & Architecture Map

## 1. Core Architecture & Routing Hub
- **Master Router & Control Node:** `Shuttle` (`Sick0h@Shuttle`, Shuttle DX30). 
- **Role:** Shuttle is the primary routing hub for the cluster. All cross-device terminal execution, script launching, and communications to mobile/tablet nodes (`Runner`, `Ocean`, `River`) route directly through Shuttle.
- **Client Interface:** Hermes runs locally on the main Windows PC (`Robert Doback`) and connects to Shuttle via SSH, bridging commands downstream.

## 2. Cluster Node Inventory & Connection Mappings

| Device Name | Hardware / OS | Role & Status | Connection / SSH Handle / Access Method |
| :--- | :--- | :--- | :--- |
| **Shuttle** | Linux (Shuttle DX30) | Master Router, AI Hub, Repository Core | `local` / `ssh shuttle` (`Sick0h@Shuttle`) |
| **Runner** | Dell Tablet | Mobile Node / Agent | Accessible via Shuttle SSH alias / Tailscale |
| **Ocean** | Motorola G7 (LineageOS + Termux) | Rooted ARM Node / Termux Daemon | Accessible via Tailscale / SSH |
| **River** | Motorola G7 (LineageOS + Termux) | Rooted ARM Node / Termux Daemon | Accessible via Tailscale / SSH |
| **Robert Doback** | Windows Main Rig | Primary Gaming & Heavy LLM Host | Standalone / Excluded from automated scraping |

## 3. Shuttle Directory Tree & Repository Index (`~/`)

### Core Repositories & Workspaces
- `~/rsmod/` — Primary Old School RuneScape private server codebase and package routing.
- `~/xerca/` (and `~/Xerca/`) — Local AI framework data, mounted 4TB external hard drive hosting local language models.
- `~/hermes-agent/` — Hermes agent source code and operational tooling.
- `~/shuttle-core/` & `~/shuttle-repo/` — Shuttle-specific system configurations and deployment scripts.
- `~/infra-catalog/` — Cluster infrastructure manifests and tracking configs.
- `~/WorkRoom/` — Active experimental workspace and scratch directory.

### Logs, Configs, & State Files
- `~/.hermes/` — Hermes persistent state, session logs, and cache.
- `~/hermes_workspace/` — Working data storage for active agent tasks.
- `~/cluster-health/` & `~/cluster-docs/` — System monitoring logs and topology documentation.
- `~/cluster-status.log` — Rolling node reachability log.

## 4. Execution Directives for Hermes
1. **Route via Shuttle:** Treat Shuttle as the primary jump host for executing tasks or scripts on `Runner`, `Ocean`, or `River`.
2. **Directory Awareness:** Check the Shuttle Directory Tree index above before locating or modifying repository files.
3. **Dynamic State Verification:** Reference the live node status block below for immediate reachability checks.

## 5. Live Node Status (Auto-Updated)
