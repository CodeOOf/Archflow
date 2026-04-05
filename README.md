# Archflow

**Visual architecture. Real infrastructure.**

Archflow is a visual infrastructure architecture platform that lets you design 
systems graphically while keeping a Git-based YAML model as the source of truth.

It bridges the gap between diagrams and Infrastructure-as-Code by turning 
architecture into validated, structured models that can generate real automation 
and synchronize with infrastructure systems.

---

## 🚧 Status

Early development (v0.1.0)

Archflow is in its initial phase and APIs, schema, and workflows may change 
frequently.

---

## ✨ Vision

Design infrastructure once and project it across multiple perspectives:

* 🧠 Logical architecture (services, dependencies)
* 🌐 Network architecture (VLANs, ingress, routing)
* 🧱 Physical layout (racks, devices, placement)

Then:

* ✅ Validate constraints and architecture rules
* 🔁 Synchronize with infrastructure systems (e.g. NetBox)
* ⚙️ Generate automation (Ansible, Terraform)
* 📄 Produce documentation

---

## 🧩 Core Principles

* **YAML is the source of truth**
* **The UI is a projection, not the model**
* **Patterns over primitives**
* **Design once, reuse everywhere**
* **Git-native workflows**

---

## 🏗️ Planned Architecture

* Blazor-based visual workbench
* YAML-based design model
* Validation and policy engine
* Projection engine (multi-view)
* NetBox integration
* Automation generators

---

## 📦 Example (early concept)

```yaml
project: example

services:
  - id: proxy
    kind: proxy-cluster
    instances: 2

  - id: web
    kind: web-service
    depends_on:
      - proxy
```

---

## 🗺️ Roadmap

* [ ] YAML schema definition
* [ ] Basic Blazor UI (canvas + properties)
* [ ] Logical view rendering
* [ ] Validation engine
* [ ] Generator framework
* [ ] NetBox integration

---

## 📄 License

MIT License

---

## 🤝 Contributing

Contributions, ideas, and discussions are welcome.

---

## 🚀 Name

**Archflow** = Architecture + Flow

Design → Model → Validate → Generate → Deploy

---

## 🤖 AI-Assisted Development

This project uses AI-assisted tools with human oversight. All outputs are 
reviewed and validated, but users should verify behavior before production use.