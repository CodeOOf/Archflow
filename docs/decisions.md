# Archflow Decision Log

## Table of contents

- [Purpose](#purpose)
- [Decisions](#decisions)
- [Review trigger](#review-trigger)
- [Continue reading](#continue-reading)

## Purpose

This document records the project’s current architectural decisions in a concise,
reviewable form. It is intentionally short and focused on stable decisions.

## Decisions

| ID | Decision | Rationale | Consequences | Status |
| --- | --- | --- | --- | --- |
| D-001 | YAML in Git is the source of truth | Keeps architecture diffable, reviewable, and reproducible | UI and generated outputs must remain derived | Accepted |
| D-002 | NetBox is the operational backend | Preserves NetBox as the DCIM/IPAM system of record | Archflow focuses on intent and synchronization | Accepted |
| D-003 | The platform is API-first | Keeps model access, validation, and generation independent of the UI | Services need stable contracts | Accepted |
| D-004 | The workbench is a projection over the model | Prevents the UI from becoming the source of truth | UI features must route through model services | Accepted |
| D-005 | Generated artifacts are derived outputs | Supports reproducibility and Git-native workflows | Generators must stay deterministic | Accepted |

## Review trigger

Review these decisions when a change affects:

- the model source of truth
- backend integration boundaries
- service contracts
- UI ownership of data or behavior
- generation or synchronization workflows

## Continue reading

- `docs/architecture.md`
- `docs/AGENTS.md`
- `README.md`