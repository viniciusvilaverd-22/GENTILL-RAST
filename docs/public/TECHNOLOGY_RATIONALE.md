# Technology Rationale

This page explains the architectural role of the major technologies used by REST Gentill.

The objective is not to maximize the number of tools. Each technology exists because it owns a clear responsibility.

## FastAPI

**Role:** domain API and integration boundary.

Why it fits the case:

- typed request/response contracts;
- explicit routing;
- strong Python ecosystem for backend integration;
- straightforward OpenAPI support;
- suitable for a contract-driven Core.

## SQLAlchemy + Alembic

**Role:** persistence model and controlled schema evolution.

Why:

- domain model stays explicit;
- migrations are versioned;
- contract evolution can be tied to schema evolution;
- rollback and compatibility decisions remain visible.

## PostgreSQL

**Role:** primary relational persistence.

Why:

- strong transactional semantics;
- mature indexing and constraints;
- reliable operational tooling;
- compatible with geospatial extension through PostGIS.

## PostGIS

**Role:** geospatial context.

Why:

- location-aware queries belong close to persistent domain data;
- supports spatial validation and policy use cases;
- keeps geospatial capability inside the data platform rather than duplicating it in application code.

## Traccar

**Role:** specialized location authority.

Why:

- tracking is a specialized problem;
- GPS history, position ingestion and geofencing should not turn the Core into a tracking monolith;
- clean authority separation improves maintainability.

## React + TypeScript

**Role:** administrative product interface.

Why:

- complex operational states benefit from componentized UI;
- TypeScript reduces ambiguity in client contracts;
- ecosystem supports mapping and identity integrations.

## PWA

**Role:** mobile field interface for IT staff.

Why:

- fast deployment;
- installable mobile experience;
- appropriate for human field operations;
- intentionally separated from permanent endpoint telemetry.

## .NET Worker Service

**Role:** native Windows endpoint agent.

Why:

- integrates naturally with Windows Service lifecycle;
- appropriate access to Windows platform APIs;
- DPAPI support for machine-local secret protection;
- suitable for long-running managed endpoint processes.

## Kotlin + WorkManager

**Role:** native Android endpoint agent.

Why:

- Android background execution is platform-specific;
- WorkManager provides lifecycle-aware scheduled work;
- Kotlin integrates naturally with modern Android APIs;
- supports offline-first synchronization patterns.

## Android Keystore

**Role:** local secret protection on Android.

Why:

- agent credentials must not be plain configuration;
- platform-backed storage reduces secret exposure.

## OIDC + JWT + RBAC

**Role:** human identity and authorization.

Why:

- human administrators and machine agents require separate trust models;
- roles keep administrative permissions explicit;
- identity remains externalizable.

## Docker Compose

**Role:** reproducible control-plane composition.

Why:

- services remain isolated;
- dependencies and networks are explicit;
- environments are easier to reproduce and validate.

## Caddy

**Role:** edge and reverse proxy layer.

Why:

- TLS and external routing stay outside business logic;
- infrastructure concerns remain separated from the Core.

## Prometheus + Grafana

**Role:** observability.

Why:

- health and performance must be visible independently from business-domain data;
- operational diagnosis should not depend on manually inspecting application state.

## Principle

The stack follows one rule:

> **Choose a specialized authority for a specialized responsibility, then integrate through explicit contracts.**

That same principle appears across the rest of REST Gentill:

```text
REST Core ≠ Traccar
Human Identity ≠ Machine Identity
PWA ≠ Agent
Static Location ≠ Dynamic Position
Asset ≠ Device ≠ Agent Installation
```
