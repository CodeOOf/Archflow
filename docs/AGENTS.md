# Archflow – AI Context

This document provides context for AI-assisted development of Archflow.
It describes the purpose, direction, and constraints of the project.

---

## What Archflow is

Archflow is a platform for designing infrastructure visually while keeping a YAML-based model in Git as the source of truth for architecture intent.

The purpose of Archflow is to connect:

- visual architecture and infrastructure design
- Architecture-as-Code and Documentation-as-Code
- operational backend systems such as NetBox
- generated implementation artifacts such as Ansible inventory and Terraform-oriented outputs

Archflow is intended to help architects and operators move from diagramming and planning into real, versioned infrastructure implementation.

---

## Why this project exists

Existing tools tend to solve only one part of the problem:

- visual tools are easy to sketch in, but weak as structured sources of truth
- inventory/DCIM tools are powerful, but often too heavy or not intuitive for fast architectural design
- automation tools can deploy infrastructure, but do not provide a good architecture design workflow

Archflow exists to bridge these gaps.

The chosen path is:

- use a visual workbench for design and exploration
- keep the architecture model in YAML stored in Git
- project that model into multiple views
- validate it with rules and constraints
- synchronize concrete inventory/state with NetBox
- generate automation-oriented outputs for Ansible and Terraform
- allow architecture changes to flow toward implementation repositories and deployment workflows

This is the Architecture-as-Code approach for the project.

---

## Core idea

Design infrastructure once -> represent it as structured YAML -> project it into multiple views -> validate it -> synchronize it with backend systems -> generate implementation artifacts.

The same model should support:

- logical architecture
- network architecture
- physical/rack architecture
- operational inventory/state integration
- implementation-facing generated outputs

---

## Role of NetBox

NetBox is not just an optional integration.

NetBox is intended to function as a core backend service for Archflow.

Archflow should use NetBox as the operational system for things such as:

- inventory representation
- DCIM/IPAM data
- racks, devices, interfaces, VLANs, prefixes, addresses
- concrete infrastructure state that should exist outside the drawing tool

Archflow should not try to replace NetBox as a full DCIM/IPAM system.
Instead, Archflow should sit above it as the architecture and modeling layer.

In this model:

- Archflow defines architecture intent
- NetBox stores and exposes concrete operational infrastructure data
- Archflow synchronizes selected model data into NetBox through APIs

This is why API-driven integration is important.

---

## Role of APIs

API-first design is important for the project.

Archflow should expose and consume APIs so that:

- the workbench can operate against a backend service
- model transformations and validation can happen in services
- NetBox can be used as a connected backend system
- generated outputs can be consumed by other tooling
- design changes can affect implementation repositories and automation workflows

The platform should be designed so that its capabilities are not locked into the UI.

---

## Role of Git and YAML

Git and YAML are central to the chosen approach.

YAML is the architecture source model.
Git is the versioned collaboration and review layer.

This means:

- design intent should be representable in YAML
- design changes should be reviewable in Git
- generated outputs should be reproducible
- architecture should be diffable, auditable, and automatable

The UI should help edit and understand the model, but should not become the source of truth.

---

## Role of generated outputs

Archflow should generate implementation-oriented artifacts from the architecture model.

Important examples:

- Ansible inventory
- Terraform-oriented inputs, variables, or module scaffolding
- documentation
- later possibly repository content or machine-consumable manifests

These outputs are how the architecture model begins to affect real implementation.

The long-term goal is that architecture changes can drive updates in Git-managed implementation workflows, without losing reviewability and control.

---

## Architecture-as-Code mental model

Archflow should be treated as an Architecture-as-Code platform.

A useful mental model is:

- YAML = architecture source code
- parser/domain model = structured architecture representation
- projections = derived views of the same architecture
- validation = architecture policy and constraints
- NetBox sync = operational backend synchronization
- generators = implementation artifact production
- Git repos = collaboration and execution boundary
- UI = visual editor and navigator for the architecture model

Archflow is not just for drawing.
It is intended to connect architecture intent to operational and automation reality.

---

## What we are building

Archflow consists of several core parts:

### 1. YAML Model
A structured YAML schema describing architecture intent:
- services
- clusters
- networks
- dependencies
- physical concepts
- metadata

### 2. Domain Model
An internal representation derived from YAML:
- used by UI, validation, projection, sync, and generators

### 3. Projection Engine
Transforms the domain model into:
- logical views
- network views
- physical views

### 4. Workbench UI
A visual editor:
- built with Blazor
- supports design and exploration
- edits the YAML-backed model

### 5. Validation Engine
Applies rules such as:
- dependency requirements
- architecture constraints
- placement constraints
- network and routing rules

### 6. Generator Layer
Produces outputs such as:
- Ansible inventory
- Terraform-oriented output
- Markdown documentation

### 7. NetBox Integration Layer
Synchronizes architecture intent into operational inventory structures:
- devices
- racks
- VLANs
- interfaces
- IP-related objects
- other mapped entities where appropriate

### 8. Service/API Layer
Provides application-facing functionality:
- model loading/saving
- validation
- projection
- synchronization
- generation

---

## Immediate project focus

The immediate goal is to reach a useful v1 foundation before June.

The most important capabilities are:

1. Core model foundation
2. Projection engine
3. Workbench MVP
4. Validation engine
5. Generators MVP
6. NetBox integration
7. v1 readiness

This means NetBox integration and generated outputs are part of the intended core direction, not side topics.

---

## Constraints

- Do not treat the UI as the source of truth
- Do not tightly couple model semantics to drawing primitives
- Do not try to replace NetBox entirely
- Prefer API-first and modular design
- Prefer Git-friendly structures
- Avoid overengineering early, but keep the architecture extensible

---

## AI usage guidelines

AI is used as a development assistant, not as an authority.

When generating code or suggestions:

- align with the YAML-first and Git-first model
- preserve the role of NetBox as backend service
- preserve the goal of generated Ansible/Terraform outputs
- avoid introducing architecture that traps functionality in the UI
- prefer modular service boundaries
- keep future synchronization and generator workflows in mind

---

## Summary

Archflow is a platform for Architecture-as-Code.

It exists to let users design infrastructure visually, store architecture intent as YAML in Git, validate and project that model, synchronize operational data with NetBox, and generate outputs that influence real implementation workflows such as Ansible and Terraform.

It is not just a diagram tool and not just an inventory tool.
It is the layer that connects architecture design, backend infrastructure data, and implementation automation.