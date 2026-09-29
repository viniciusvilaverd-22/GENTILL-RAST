# REST Gentill — Public Roadmap

This roadmap describes product direction at a public portfolio level. It intentionally omits implementation details, private infrastructure and internal delivery dates.

## Current foundation

The current architecture is centered on:

- asset and endpoint identity;
- custody and authorization;
- Windows and Android endpoint agents;
- dynamic location through a dedicated telemetry authority;
- administrative dashboard;
- IT field PWA;
- physical environments and indoor mapping support;
- OIDC/RBAC;
- auditability;
- backup, restore and rollback discipline;
- observability.

## Near-term direction

### Production hardening

Focus areas:

- stronger deployment controls;
- signing and distribution discipline for agents;
- environment isolation;
- improved operational runbooks;
- continued secret-management hardening.

### Identity and access

Evolution areas:

- production identity provider integration;
- finer-grained authorization policies;
- clearer machine-credential lifecycle visibility.

### Endpoint operations

Evolution areas:

- richer fleet health signals;
- safer update orchestration;
- clearer enrollment and credential rotation workflows.

### Indoor context

Evolution areas:

- validation of indoor mapping workflows;
- stronger relationship between physical environments and operational presence;
- measured use of Wi-Fi/BLE evidence where appropriate.

## Medium-term direction

### Multi-site operations

The architecture should support multiple physical locations while preserving:

- explicit asset ownership;
- environment hierarchy;
- telemetry separation;
- consistent authorization.

### Operational analytics

Potential portfolio direction:

- fleet health trends;
- asset movement insights;
- policy exceptions;
- custody and utilization views.

### Policy automation

The policy engine can evolve from passive validation toward controlled operational automation while retaining auditability and human oversight.

## Long-term principle

The roadmap must preserve the architectural separation that defines REST Gentill:

```text
Asset ≠ Device ≠ Agent Installation ≠ Last Position
Human Identity ≠ Machine Identity
Static Location ≠ Dynamic Position
PWA ≠ Agent
REST Core ≠ Traccar
```

New features should strengthen those boundaries, not blur them.

## Portfolio note

REST Gentill is under active development.

The public repository documents architecture, decisions and product direction. Source code and private operational material remain outside the public portfolio.
