# Roadmap

Status reflects inspected source and design direction as of October 13, 2026. “Current” means an implementation exists in the private project; it does not imply that every integration is enabled or production-ready. Items are priorities, not release dates or commitments.

## Current foundations

- Web dashboard for workspace access, agent activity, workflow visibility, and human approval review.
- CEO/planner coordination and bounded Email, Files, and Research specialists.
- Gmail integration paths and protected outbound-action handling, subject to setup and approval.
- Read-only Dropbox discovery and supported-content reading.
- Approved-source research and shared business knowledge with provenance and conflict handling.
- Durable assignments, results, and waiting decisions.
- Runtime agent enable/pause controls.
- Mac desktop companion for sign-in, health, and integration visibility, with some simulated or partial behavior.

## In progress

- **Restricted runtime hardening:** strengthen least privilege and separation between reasoning and privileged execution.
- **Agent enable/disable experience:** make activation state and its effect on work clearer in the dashboard.
- **Native Messages integration:** develop local messaging support with deliberate commissioning and user consent.
- **Protected outbound messaging:** carry the approval philosophy into messaging before general availability.
- **Workflow recovery:** improve interruption handling and safe continuation without blind replay of outbound actions.
- **Business knowledge ingestion:** improve how supported business context and source evidence are curated and used.
- **Background-runtime lifecycle:** improve supervised operation and health visibility independently of the desktop window.

## Planned

- **Guided near-zero-touch Mac installer:** reduce setup steps, explain consent, and make readiness clear.
- **Signed/notarized distribution:** prepare a trustworthy Mac release and update experience.
- **CRM integration:** add bounded relationship and business-record workflows.
- **Calendar integration:** add scheduling workflows with appropriate review for changes.
- **Broader knowledge ingestion:** support more sources and document types without losing provenance.
- **Reusable deployment framework:** adapt the foundations for other small businesses without embedding one business's private context.

## What readiness should mean

A capability should graduate from development when its complete workflow is understood: setup, authorization, ordinary operation, a human decision where needed, and recovery from an interruption. A dashboard card or a source file alone is not evidence that a feature is ready.

This repository makes no claims about customers, revenue, funding, benchmarks, adoption, or uptime. It is a public view of an early-stage private project.
