---
layout: default
title: Patterns
---

# Patterns

## Domain Service 2-phase Commit Problem

This diagram shows a naive domain-service request path: DTO deserialisation and validation (including an idempotency check), entity mapping, then a unit of work that persists the entity and publishes an event. The yellow grouping and warning are the point — when persistence and publish are separate steps without a shared transaction, the entity can land and the event can still fail to leave, which is the dual-write / 2-phase-commit problem in miniature.

<div class="pattern-card" style="--pattern-native-w: 1537.51">
<img src="{{ '/assets/images/patterns/patterns-domain-service-2pc.svg' | relative_url }}" alt="Domain Service 2-phase Commit Problem">
</div>

## Transactional Outbox Pattern

The transactional outbox splits that risk into a safe write path and an asynchronous relay. The domain service deserialises, validates, maps, and persists the entity together with an outbox row in one transaction, then returns 202. A separate outbox processing service polls the outbox table, publishes the event, and cleans up the outbox row — so the message only leaves after the business write is durable, without coordinating a distributed two-phase commit.

<div class="pattern-card" style="--pattern-native-w: 1982">
<img src="{{ '/assets/images/patterns/patterns-transactional-outbox.svg' | relative_url }}" alt="Transactional Outbox Pattern">
</div>

## Domain Service with Dead Letter Queue

This diagram shows how poison or invalid messages are parked instead of blocking the happy path. Failures in DTO deserialisation or validation are routed to a DLQ producer that publishes onto a dead-letter queue; a separate DLQ processing service consumes those messages and records them for inspection or remediation, so operators can diagnose bad payloads without losing them or endlessly retrying the main service.

<div class="pattern-card" style="--pattern-native-w: 1142">
<img src="{{ '/assets/images/patterns/patterns-domain-service-dlq.svg' | relative_url }}" alt="Domain Service with Dead Letter Queue">
</div>
