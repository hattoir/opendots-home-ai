# Autonomous Engineering Loop Architecture
## Milestone 24-28 Specification

### 1. Purpose & Scope
This document specifies the operational invariants and security architecture of the
Autonomous Engineering Orchestrator within OpenDots Home AI / AI Lab.

### 2. Verified Safety Invariants
1. **Mutation Gate Mandatory**: Every external HTTP mutation (POST, PUT, PATCH, DELETE) against GitHub, Todoist, and Google Drive must execute under a cryptographically verified, single-use Human Approval context.
2. **Permission Probe Ban**: Mutation-endpoint probes are strictly prohibited. Zero network mutation requests are sent during permission verification.
3. **Pre-Merge Validation**: PR merges are restricted to squash merges, require WORK_RESULT_VERIFIED status from the ResultVerifier, matching head SHA, and clean CI runs.
4. **Isolated Worktrees**: Autonomous edits, builds, and tests occur strictly within isolated scratch worktrees without host secret leakage.
5. **Durable Audit Trail**: Every engineering activity reconstructs the complete audit graph from task ingestion to knowledge capture.

- Timestamp: 2026-10-13T23:49:00+09:00
- Repository: hattoir/opendots-home-ai
- Orchestrator Version: v1.0
