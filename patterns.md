---
layout: default
title: Patterns
---

# Patterns

These diagrams explain concepts. They are not implementations to follow, and the sample payloads and service names are teaching props, not a blueprint.

Two related threads I keep coming back to when shipping event-driven domain services: getting the write and the publish to agree, and scaling Service Bus consumers without inventing duplicate work. A third thread covers central orchestration, failure, and compensation as ideas, not as a preferred stack.

## Reliable messaging in a domain service

### Domain Service 2-phase Commit Problem

A naive domain-service request path: DTO deserialisation and validation (including an idempotency check), entity mapping, then a unit of work that persists the entity and publishes an event. The yellow grouping and warning highlight the concept: when persistence and publish are separate steps without a shared transaction, the entity can land and the event can still fail to leave. That is the dual-write / 2-phase-commit problem in miniature.

<div class="pattern-card" style="--pattern-native-w: 1537.51">
<img src="{{ '/assets/images/patterns/patterns-domain-service-2pc.svg' | relative_url }}" alt="Domain Service 2-phase Commit Problem">
</div>

### Transactional Outbox Pattern

The transactional outbox idea splits that risk into a safe write path and an asynchronous relay. The domain service deserialises, validates, maps, and persists the entity together with an outbox row in one transaction, then returns 202. A separate outbox processing path polls the outbox, publishes the event, and cleans up the row, so the message only leaves after the business write is durable, without a distributed two-phase commit.

<div class="pattern-card" style="--pattern-native-w: 1982">
<img src="{{ '/assets/images/patterns/patterns-transactional-outbox.svg' | relative_url }}" alt="Transactional Outbox Pattern">
</div>

### Domain Service with Dead Letter Queue

Poison or invalid messages can be parked instead of blocking the happy path. Failures in DTO deserialisation or validation route to a DLQ producer; a separate DLQ processing path consumes those messages and records them for inspection or remediation. The idea is diagnosis without endless retry on the main path.

<div class="pattern-card" style="--pattern-native-w: 1142">
<img src="{{ '/assets/images/patterns/patterns-domain-service-dlq.svg' | relative_url }}" alt="Domain Service with Dead Letter Queue">
</div>

## Scaling Azure Service Bus consumers

Once events leave onto Azure Service Bus, the next trap is fan-out under scale. A single sample `OrderCreated` event for Europe at amount 1500 can be filtered many ways; the diagrams below use that payload only to show when replicas compete cleanly and when they accidentally duplicate work.

### Service Bus topic with duplicate consumers

A topic with filtered subscriptions is a natural fan-out, but a subscription that feeds three replicas of the same consumer delivers a copy to every replica. Subscription A (`OrderCreated`) is the cautionary case: scaling Consumer A horizontally multiplies processing. Subscriptions B and C show region and amount filters, including an amount-based split across Consumer C replicas.

<div class="pattern-card" style="--pattern-native-w: 1162">
<img src="{{ '/assets/images/patterns/patterns-service-bus-duplicate-consumers.svg' | relative_url }}" alt="Service Bus topic with duplicate consumers">
</div>

### Service Bus sessions (solution 1)

Sessions keep the topic model but restore competing-consumer behaviour for a given key. With `SessionID` on the message and a session-enabled subscription, only one replica of Consumer A processes each session at a time. The same diagram still warns that Subscription B without sessions will duplicate again if you scale that consumer, and Subscription C continues to split on amount after the filter.

<div class="pattern-card" style="--pattern-native-w: 1277.51">
<img src="{{ '/assets/images/patterns/patterns-service-bus-sessions.svg' | relative_url }}" alt="Service Bus sessions for competing consumers">
</div>

### Service Bus queues for competing consumers (solution 2)

Another conceptual fix is to stop using a subscription where you need exactly-once competing consumers. Queue A carries `OrderCreated` so only one replica of Consumer A handles each message, while the Events topic still fans out region and amount filters to Consumers B and C. Same sample payload, clearer ownership for the scaled worker.

<div class="pattern-card" style="--pattern-native-w: 1122">
<img src="{{ '/assets/images/patterns/patterns-service-bus-competing-queues.svg' | relative_url }}" alt="Service Bus queues for competing consumers">
</div>

## Event-driven orchestration

A central orchestrator can drive a multi-service workflow over streams, materialising progress so you can see which step is still in flight. The three diagrams move from the happy path, to failure with rollback, to a separate compensation flow. Again: illustrative only.

### Simple event-driven orchestration

An orchestrator microservice receives an input stream event, then walks Steps 1 through 6: dispatch to Service A, wait for the response, then B, then C, and finally emit on an output stream while persisting state. The materialisation table shows completed versus in-flight input event IDs so the concept of durable orchestration state is visible.

<div class="pattern-card" style="--pattern-native-w: 1062">
<img src="{{ '/assets/images/patterns/patterns-event-driven-orchestration.svg' | relative_url }}" alt="Simple event-driven orchestration">
</div>

### Orchestration with failure and rollback

When Service C fails, the orchestrator can drive an ordered rollback: start and confirm rollback on Service B, then on Service A, and emit on the output stream. The materialisation row shows Services A and B as rolled back, Service C as error, and overall status Failure. The point is the idea of reversing prior work under a durable orchestrator, not a specific API design.

<div class="pattern-card" style="--pattern-native-w: 1042">
<img src="{{ '/assets/images/patterns/patterns-event-driven-orchestration-failure.svg' | relative_url }}" alt="Event-driven orchestration with failure and rollback">
</div>

### Orchestration with failure and compensation

A related idea is a compensation path rather than (or in addition to) direct rollback of earlier services. After Service C fails, a compensation orchestrator runs its own steps (here involving Service D), materialises compensation state alongside the primary orchestration row, and can mark the overall handling Completed even though the original step erred. Useful for talking through eventual consistency; not a recipe.

<div class="pattern-card" style="--pattern-native-w: 942">
<img src="{{ '/assets/images/patterns/patterns-event-driven-orchestration-compensation.svg' | relative_url }}" alt="Event-driven orchestration with failure and compensation">
</div>
