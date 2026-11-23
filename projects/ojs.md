---
layout: single
title: "KMANweb & Open Journal Systems (OJS)"
permalink: /projects/ojs/
excerpt: "My work on OJS plugins, developer tooling, infrastructure, and AI-assisted software engineering at KMAN Publication."
classes: wide
---

## Overview

**KMAN Publication · 2024–present**

I develop and maintain **KMANweb**, the software and infrastructure supporting academic-journal hosting and editorial workflows built around [Open Journal Systems (OJS)](https://pkp.sfu.ca/software/ojs/).

OJS itself is a substantial **open-source publishing platform**, not a project I created. My work involves understanding its existing PHP codebase and building integrations, plugins, and operational tools around it. Many requirements have meant tracing OJS internals—editorial decisions, payment flows, hooks, templates, and database behavior—before deciding how to implement a change safely.

## My role and scope

I have handled the **development and project management of this work independently**: gathering requirements, designing solutions, coordinating tasks, testing changes, maintaining deployments, and deciding what ships. I use AI coding agents extensively, but remain responsible for architecture, review, integration, and operational decisions.

The [**OJS-Inator GitHub organization**](https://github.com/ojs-inator) contains **90+ repositories** across plugins, tooling, infrastructure, and maintenance. Many plugins originated **before AI coding assistants**; later work has included revisiting, refactoring, and upgrading them with agent assistance.

## Selected engineering work

- **Editorial workflow and payments:** [Review Fee Gate](https://github.com/ojs-inator/review-fee-gate-plugin) adds a pre-review payment step after editorial screening, integrates with OJS's native payments, and keeps publication charges separate. It includes permission checks and duplicate-payment protections. *The repository documents staging tests; external payment-gateway acceptance is not yet complete.*
- **Submission validation:** [Submission File Validator](https://github.com/ojs-inator/submission-file-validator-plugin) compares manuscript contents with submission metadata, handles identified and anonymous manuscripts, and integrates with KMANweb's text-extraction services for PDF, DOCX, and HTML.
- **Journal operations:** [OJS Toolkit](https://github.com/ojs-inator/ojs-toolkit) provides a host-side command-line interface for deployments, plugins, diagnostics, configuration, upgrades, and routine journal administration.
- **Migration and backups:** [OJS Move Tool](https://github.com/ojs-inator/ojs-move-tool) packages journal files and databases for migration and restoration, with archive integrity checks and recovery-oriented workflows.
- **Reusable infrastructure:** [KMANweb Service Kit](https://github.com/ojs-inator/kmanweb-service-kit) provides small Bash primitives for transactional filesystem changes, rollback, and recovery after interrupted installations.

These are examples from a broader set of plugins and internal platform work, rather than a complete list of deliverables.

## Infrastructure and DevOps

I work across **Dockerized OJS instances, Linux servers, Apache, PHP services, databases, shell automation, and CI pipelines**. The operational side includes deployment and upgrades, troubleshooting across application and infrastructure layers, backups, and changes that need to work across multiple journals without breaking existing workflows.

## How I work with AI coding agents

Rather than treating an agent's output as finished code, I organize the work into reviewable changes:

1. Define the task and its constraints, often using GitHub issues and repository-specific instructions such as `AGENTS.md`.
2. Split work into focused agent tasks or isolated branches/workspaces when useful.
3. Inspect changes against the actual OJS interfaces and cross-repository contracts.
4. Run appropriate regression tests and CI checks, review pull requests, and validate operational changes before integration.

I also maintain the instructions and workflows used by these agents. This has been particularly useful for upgrading older plugins while preserving behavior and managing changes across several related repositories.

## Technical challenges

- **Extending a large unfamiliar codebase:** finding the right OJS extension points instead of modifying core behavior unnecessarily.
- **Preserving correctness across workflows:** authorization, payment state, duplicate requests, and compatibility between plugins.
- **Keeping deployments recoverable:** careful migrations, reproducible administration commands, tests, and rollback paths.
- **Managing breadth as one developer:** prioritizing diverse projects and reviewing AI-assisted changes instead of letting parallel work fragment the system.

## Technology

**PHP · JavaScript · Python · Bash · SQL · Docker · Linux · Apache · GitHub Actions · Git**

---

[Browse the OJS-Inator repositories](https://github.com/ojs-inator) · [General portfolio](/portfolio/) · [JetBrains-focused portfolio](/portfolio/jetbrains/) · [All projects](/projects/)
