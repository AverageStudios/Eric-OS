# Architecture

Eric OS separates coordination, reasoning, local execution, and external actions. This document presents responsibilities and boundaries; it does not describe the private protocols or deployment layout.

## Components and responsibilities

| Component | Responsibility |
| --- | --- |
| Web dashboard | Workspace access, activity, workflow visibility, and human review |
| Mac desktop companion | Local health and integration visibility, with a guided setup direction |
| Durable control plane | Assignments, results, workflow state, agent activation, and recorded decisions |
| CEO/planner | Interpret the goal, choose bounded assignments, evaluate results, and ask for human judgment |
| Specialist agents | Complete focused tasks within their permitted capabilities and return a result |
| Local runtime | Execute enabled assignments and report progress within enforced limits |
| Protected gateways | Mediate external access and enforce action requirements outside model reasoning |
| Business knowledge | Supply shared context and source-backed facts, including uncertainty and conflicts |

The private web implementation uses Next.js, TypeScript, and a hosted database/authentication control plane. The Mac companion uses Tauri, React, TypeScript, and Rust. The local runtime is Node-based, with model-assisted planning and email reasoning. Some specialists use deterministic code rather than a model call. These are stack descriptions, not instructions for reconstructing the private implementation.

## Planner and specialists

The planner owns the workflow's next decision. A specialist receives a limited assignment, performs its permitted work, and returns a result. It does not inherit unrestricted authority over other agents or the business.

Email, Files, and Research have implementations in the inspected core source. Messages is under development. CRM and Calendar are future specialists. Agent controls separate an installed capability from a capability enabled for execution.

Results need to represent missing information as well as success. A file search can be ambiguous; research can return conflicting or unavailable evidence. The planner should clarify, try another permitted source, or ask a person rather than turn uncertainty into a claim.

## Workflow continuity

Durable state lets a workflow wait for a specialist or an approval and later continue with the recorded context. A workflow's continuity is distinct from replaying an individual job after interruption.

If execution ends with an uncertain external effect, automatic replay can duplicate an action. Recovery needs to identify what is known, what remains uncertain, and which decision requires an operator. General resumability and recovery are still being developed; this showcase does not claim exactly-once behavior across external providers.

## Local sensitive-data boundary

Local execution is intended to keep sensitive raw communications and related processing on the Mac when possible. A hosted control plane still coordinates the work, and authorized providers may receive the bounded context needed for a task.

Local-first is a data-minimization choice, not a promise that every byte remains on-device. Approval to connect an integration does not imply unrestricted access to every account resource.

## Reasoning and action boundary

Model output is a proposal. A separate execution boundary checks whether an action is permitted and, where required, approved. Narrow gateways mediate external access; the public showcase deliberately omits their implementation.

Sensitive outbound changes need review of the intended action. A materially changed action should be reviewed again. The desktop companion provides local visibility; approval review belongs in the web experience.

## Deployment direction

The target is a restricted background runtime with narrow privileged components, a guided Mac installer, and signed/notarized releases. Background operation should be independent of whether the desktop window is open.

The inspected source contains desktop and runtime foundations, alongside simulated and partial modes. Restricted execution, automatic startup, installation, and recovery remain active engineering work. This diagram and these notes describe the direction without certifying a deployed configuration.

For the simplified Mermaid diagram, see the [README](../README.md#architecture-overview). The [security document](SECURITY.md) describes the principles behind these boundaries.
