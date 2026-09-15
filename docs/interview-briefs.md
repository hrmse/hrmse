# Portfolio interview briefs

Use these as discussion starters, not as claims of production outcomes. Lead
with the engineering decision, explain its trade-off, then describe how you
would validate it in an authorised environment.

## AWS EKS platform blueprint

- Explain why a private EKS endpoint, controlled egress and KMS-backed secrets
  reduce platform exposure.
- Discuss the operational trade-off: private endpoints improve isolation but
  require deliberate CI runner and operator network access.
- Be ready to describe how Terraform plans, state access and Kubernetes
  admission boundaries should be separated.

## SLO control plane

- Explain that an SLO is a customer-oriented reliability target, not merely an
  infrastructure threshold.
- Discuss burn-rate alerting versus a single error-rate alert, including why
  multi-window alerts reduce noise.
- Describe the escalation path when an error budget is consumed: verify impact,
  pause unsafe delivery and align remediation with product owners.

## Delivery gatekeeper

- Explain digest-only deployment as a defence against mutable image tags.
- Discuss how OIDC short-lived identity, signatures, SBOMs and vulnerability
  policy complement one another; none is enough alone.
- Name the limitation: a gate is effective only if the deployment path cannot
  bypass it.

## PostgreSQL recovery drills

- Explain why a backup is not proof of recovery; restore integrity and RPO
  evidence must be exercised.
- Discuss recovery objectives as agreements that drive backup frequency,
  retention and testing—not as values to invent after an incident.
- Describe a safe drill: isolated target, no production overwrite, evidence
  capture and explicit cleanup.

## Ephemeral SSH access

- Explain the difference between a long-lived SSH key and a short-lived
  certificate bound to an identity and expiry.
- Discuss CA protection, revocation/expiry limits and how access logs become
  more useful during incident review.
- Note that break-glass access still needs a separate, audited procedure.

## Reliability command center

- Explain why the component creates evidence-based, approval-gated plans but
  never executes infrastructure changes.
- Discuss decision hashes, scoped/expiring approvals and independent
  least-privileged executors.
- Identify the boundary: automated triage can accelerate understanding, but a
  tool must not claim certainty or manufacture root cause evidence.
