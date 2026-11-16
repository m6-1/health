# Distributed Scribe & File Understanding Architecture

## Core Topology
- **Controller / Primary Node (`Shuttle`):** Runs the primary control loop using `gpt-oss:20b`. It performs deep file understanding (e.g., parsing `/mnt/xerca_brain`, reconstruction blueprints, and system layouts).
- **Scribe / Logger Node (`Ocean` / Motorola G7):** Hosted at `100.84.14.107:11434` via Tailscale mesh. Runs Ollama (`qwen2.5:1.5b`) to process, summarize, and archive reasoning/telemetry states offloaded from Shuttle.
- **Sync Mechanism:** Hermes `post_llm_call` lifecycle hooks trigger `~/bin/scribe-sync.sh`, which uses robust `jq` payloads to dispatch reasoning text to Ocean, appending results locally to `~/.scribe_history.log`.
- **Persistence & Telemetry (`Health` Repo):** Automatically backed up and synced to the GitHub `health` repository via `~/bin/push-health.sh`.
