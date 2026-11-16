# Cluster Device Inventory & SSH Verification Spec

| Node Name | Role | IP Address / Mesh | Hardware / Platform | Active Models & Services |
| :--- | :--- | :--- | :--- | :--- |
| **Shuttle** | Primary Control Node & Agent Loop | Localhost (`127.0.0.1`) / Tailscale | Linux Workstation | Hermes Agent, `qwen2.5-fast-64k:0.5b`, `qwen2.5-coder:7b` |
| **Ocean** | Dedicated Scribe & State Log Node | `100.84.14.107` (Tailscale) | Motorola G7 Android (Termux / Linux) | Ollama API, `qwen2.5:1.5b` |
| **River** | Secondary Compute Node | `192.168.1.22` | Secondary Linux Server / Rig | Ollama API, `qwen2.5:1.5b`, `qwen:latest` |
| **Runner** | CI/CD & Task Execution Node | Tailscale Mesh | Dedicated Runner Instance | Execution Worker, Task Dispatch |

## Connectivity & Security
- **Mesh Network:** Secure Tailscale mesh interconnecting all nodes.
- **Authentication:** SSH key-verified access across all cluster hosts.
- **Lifecycle Hooks:** Hermes `post_llm_call` triggers `scribe-sync.sh` to push reasoning states directly to Ocean.
