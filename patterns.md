---
layout: default
title: Patterns
---

# Patterns

Two related threads I keep coming back to when shipping event-driven domain services: getting the write and the publish to agree, and scaling Service Bus consumers without inventing duplicate work.

## Reliable messaging in a domain service

### Domain Service 2-phase Commit Problem

This diagram shows a naive domain-service request path: DTO deserialisation and validation (including an idempotency check), entity mapping, then a unit of work that persists the entity and publishes an event. The yellow grouping and warning are the point: when persistence and publish are separate steps without a shared transaction, the entity can land and the event can still fail to leave, which is the dual-write / 2-phase-commit problem in miniature.

<div class="pattern-card" style="--pattern-native-w: 1537.51">
<img src="{{ '/assets/images/patterns/patterns-domain-service-2pc.svg' | relative_url }}" alt="Domain Service 2-phase Commit Problem">
</div>

### Transactional Outbox Pattern

The transactional outbox splits that risk into a safe write path and an asynchronous relay. The domain service deserialises, validates, maps, and persists the entity together with an outbox row in one transaction, then returns 202. A separate outbox processing service polls the outbox table, publishes the event, and cleans up the outbox row, so the message only leaves after the business write is durable, without coordinating a distributed two-phase commit.

<div class="pattern-card" style="--pattern-native-w: 1982">
<img src="{{ '/assets/images/patterns/patterns-transactional-outbox.svg' | relative_url }}" alt="Transactional Outbox Pattern">
</div>

### Domain Service with Dead Letter Queue

This diagram shows how poison or invalid messages are parked instead of blocking the happy path. Failures in DTO deserialisation or validation are routed to a DLQ producer that publishes onto a dead-letter queue; a separate DLQ processing service consumes those messages and records them for inspection or remediation, so operators can diagnose bad payloads without losing them or endlessly retrying the main service.

<div class="pattern-card" style="--pattern-native-w: 1142">
<img src="{{ '/assets/images/patterns/patterns-domain-service-dlq.svg' | relative_url }}" alt="Domain Service with Dead Letter Queue">
</div>

## Scaling Azure Service Bus consumers

Once events leave the outbox onto Azure Service Bus, the next trap is fan-out under scale. A single `OrderCreated` event for Europe at amount 1500 can be filtered many ways; the diagrams below use that payload to show when replicas compete cleanly and when they accidentally duplicate work.

### Service Bus topic with duplicate consumers

A topic with filtered subscriptions is a natural fan-out, but a subscription that feeds three replicas of the same consumer delivers a copy to every replica. Subscription A (`OrderCreated`) is the cautionary case: scaling Consumer A horizontally multiplies processing. Subscriptions B and C show region and amount filters, including amount-based split across Consumer C replicas.

<div class="pattern-card" style="--pattern-native-w: 1162">
<img src="{{ '/assets/images/patterns/patterns-service-bus-duplicate-consumers.svg' | relative_url }}" alt="Service Bus topic with duplicate consumers">
</div>

### Service Bus sessions (solution 1)

Sessions keep the topic model but restore competing-consumer behaviour for a given key. With `SessionID` on the message and a session-enabled subscription, only one replica of Consumer A processes each session at a time. The same diagram still warns that Subscription B without sessions will duplicate again if you scale that consumer, and Subscription C continues to split on amount after the filter.

<div class="pattern-card" style="--pattern-native-w: 1277.51">
<img src="{{ '/assets/images/patterns/patterns-service-bus-sessions.svg' | relative_url }}" alt="Service Bus sessions for competing consumers">
</div>

### Service Bus queues for competing consumers (solution 2)

The other fix is to stop using a subscription where you need exactly-once competing consumers. Queue A carries `OrderCreated` so only one replica of Consumer A handles each message, while the Events topic still fans out region and amount filters to Consumers B and C. Same sample payload, clearer ownership for the scaled worker.

<div class="pattern-card" style="--pattern-native-w: 1122">
<img src="{{ '/assets/images/patterns/patterns-service-bus-competing-queues.svg' | relative_url }}" alt="Service Bus queues for competing consumers">
</div>
