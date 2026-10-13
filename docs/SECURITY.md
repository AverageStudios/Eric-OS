# Security philosophy

Eric OS is designed around a simple rule: a model's ability to reason about an action must not give it authority to execute that action.

These are design principles and engineering goals. The implementation is private and still evolving. This document is not a security certification, a vulnerability report, or an operational guide.

## Least privilege

Give each specialist only the capabilities needed for its assignment. Treat account connection, agent activation, and permission to perform a sensitive action as separate decisions. Prefer bounded, read-only capabilities when they satisfy the task.

## Separate reasoning from privileged actions

Keep planning and content generation apart from privileged execution. Narrow gateways enforce the external-action boundary. Privileged components should be small and expose a limited purpose rather than a general execution surface.

## Explicit approval

Sensitive outbound actions require explicit human approval of the intended action. The user needs enough context to understand what will happen. Changed recipients, content, or attachments should trigger renewed review rather than silently extending prior approval.

The public repository does not describe approval credentials, verification formats, or gateway internals.

## Restricted runtime

A restricted background runtime should enforce capabilities independently of an agent's instructions. Runtime hardening and privilege separation are ongoing priorities. The aim is to reduce the authority available to reasoning and contain the effect of mistakes.

## Local-first sensitive data

Keep sensitive raw communication data local when possible. Share only the context needed for authorized processing, and avoid unnecessary retention or duplication. A local runtime still interacts with cloud services and model providers; local-first does not mean offline-only.

## Verified actions

An action presented for review should remain stable through execution. Verify that the action being executed matches the reviewed intent and that the agent package is still the expected version. Material changes should invalidate the previous decision. These are high-level integrity requirements, not a description of the private enforcement mechanism.

## Auditability

Record assignments, results, decisions, and meaningful state transitions so an operator can understand what happened and why work stopped. Logs should minimize sensitive content rather than become another copy of the source communications.

## Fail closed and recover deliberately

Missing authorization, unavailable verification, or ambiguous execution state should stop sensitive work. Uncertainty is a reason to request review. Do not automatically repeat an outbound action merely because a local job failed to report completion.

## Mac release direction

Signed and notarized Mac components, guided installation, and a clear background-service lifecycle are deployment goals. They are not claimed as completed release properties here.

## Public reporting

Keep public issues limited to the showcase documentation and fictional examples. Do not post credentials, business data, production logs, or private security findings. If a private concern arises, use an established private channel with the builder; this repository publishes no invented security contact.
