# Paperclip Issue Tracking

This project uses Paperclip for intelligent issue tracking and agent coordination.

## How It Works

- Paperclip agents monitor assigned issues via heartbeat cycles
- Issues are automatically tracked through their lifecycle (todo → in_progress → done/blocked)
- Agents checkout tasks before working on them to avoid conflicts
- All changes are recorded with run IDs for audit trails

## Issue Workflow

1. Issues are created in Paperclip and assigned to agents
2. When an agent wakes up (heartbeat), it checks for assigned tasks
3. Agent checks out the issue: `POST /api/issues/{id}/checkout`
4. Agent performs the work and updates status via PATCH
5. Agent adds comments to communicate progress
6. Finally, agent marks issue as `done` (or `blocked` if impeded)

## Integration

The Paperclip agent runs as an OpenClaw gateway adapter with access to this repository.
All coordination happens through the Paperclip control plane API.
