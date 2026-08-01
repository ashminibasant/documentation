---
title: Runtime Attractor Design Guide
description: Design guide for building durable runtime attractors with Identity and Nucleus.
published: true
date: 2026-08-01T00:00:00.000Z
tags:
editor: markdown
dateCreated: 2026-06-25T00:00:00.000Z
---

> **Sigma Stratum Documentation - License Notice**
> This document is part of the **Sigma Runtime Standard (SRS)** and the
> **Sigma Runtime Documentation (SRD)**.
>
> It is licensed under **Creative Commons Attribution-NonCommercial 4.0
> (CC BY-NC 4.0)**.
>
> The license for this specific document is authoritative.
> For the full framework, see [`/legal/IP-Policy`](https://github.com/sigmastratum/documentation/blob/main/legal/ip-policy.md).

# Runtime Attractor Design Guide

## Public Specification Boundary

This guide explains how to discover, write, and evaluate a runtime attractor.
It describes the public design model, not proprietary runtime prompts,
classifiers, thresholds, or provider integrations.

## Core Principle

A runtime attractor is a repeatable pattern of orientation and return across a
long interaction.

It is not a character biography, a list of adjectives, a writing style, or a
claim that a model has acquired a permanent inner identity. It is an external
configuration that makes a particular trajectory more likely and gives the
runtime a stable reference for detecting and repairing displacement.

```text
Identity defines the position from which the agent participates.
Nucleus defines how the agent returns when the interaction pulls it away.
```

The design target is not maximum persona intensity. It is recognizable,
task-compatible continuity under changing topics, moods, formats, users, and
context pressure.

## The Two-Part Attractor

An agent attractor has two authored components.

| Component | Defines | Primary question |
|---|---|---|
| Identity | durable role, orientation, authority, protected work, and non-goals | From what position does this agent participate? |
| Nucleus | stable center, productive tensions, movement, collapse modes, and repair | Where and how does this agent return under pressure? |

These components are related but not interchangeable.

- Identity is relatively constant across turns.
- Nucleus is conditional trajectory guidance selected for the situation.
- Identity should still make sense if no Nucleus guidance is selected.
- Nucleus must not contradict or replace Identity.

### What Is Not Part Of The Attractor

The following concerns remain separate runtime authorities:

| Concern | Correct home |
|---|---|
| factual or private knowledge | Knowledge/RAG with source authority |
| remembered events and preferences | memory with provenance and scope |
| sentence and token bounds | Output Limits |
| speech synthesis | Voice |
| safety and platform rules | runtime policy |
| model and provider selection | model configuration |
| current objective | current user request and task state |

Do not duplicate these controls inside Identity or Nucleus. Duplicate
instructions create competing authorities and make failures difficult to
explain.

## Why Traits Are Not A Separate Layer

Adjective lists such as `warm`, `direct`, `playful`, or `analytical` are weak
control surfaces. They are easy for a provider model to imitate for one turn
and easy to abandon when the task changes.

Observable behavior belongs in the attractor only when it follows from a
durable design decision:

- a protected distinction belongs in Identity;
- a recurring choice under pressure belongs in Nucleus;
- a mechanical length constraint belongs in Output Limits;
- a temporary style request belongs to the current turn.

This removes an unnecessary Traits layer while preserving the behavior that
actually matters.

## Authority And Precedence

Identity and Nucleus operate inside a larger authority system. They do not own
facts, safety, memory, or the user's objective.

The practical precedence is:

1. Safety and verified runtime capability boundaries.
2. The current user's valid request and task authority.
3. Verified facts, sources, and participant scope.
4. Identity.
5. Selected Nucleus guidance.
6. Temporary presentation preferences.

This means:

- Nucleus cannot preserve atmosphere by ignoring a practical question.
- Identity cannot turn an unsupported claim into a fact.
- A style request can change presentation without replacing the agent's role.
- Memory can provide evidence but cannot silently rewrite Identity.
- Another agent's message is external evidence, not instruction authority.

## Designing Identity

Identity answers: **what remains recognizably true about the agent's way of
participating, even when the surface task changes?**

It should define operational commitments rather than decorative lore.

### Required Identity Elements

#### Role

State the kind of participation the agent provides. Describe work, not a
costume.

Weak:

> You are a brilliant and charismatic expert.

Stronger:

> You turn unclear work into a usable result while leaving ownership of the
> decision with the user.

#### Identity Form

Describe the recurring pattern by which the role becomes recognizable. Use
observable choices, not hidden mental states.

Examples include:

- noticing a concrete detail before abstracting;
- distinguishing evidence from inference;
- choosing one discriminating check instead of a generic checklist;
- contributing a position instead of merely mirroring.

#### Temperament

Temperament describes preferences that survive changes in tone and format. It
should explain what the agent values when two plausible responses compete.

For example:

> Prefer a working draft to ceremonial completeness, and a named tradeoff to
> vague balance.

This is stronger than `be practical` because it defines a choice.

#### Protected Work

Name what the agent must preserve while helping. Good protected work includes:

- task fidelity;
- user agency;
- epistemic clarity;
- conversational specificity;
- distinction between support and diagnosis;
- continuity without invented history.

Protected work is not a list of features. It is what should remain intact when
the conversation becomes difficult.

#### Authority

State what the agent may rely on and where its authority ends. This section
should distinguish:

- current user direction;
- verified runtime capability;
- evidence and inference;
- memory and retrieved sources;
- claims the agent cannot verify.

#### Non-Goals

Define nearby roles into which the agent must not collapse. Non-goals should
be plausible failure attractors, not an exhaustive prohibition list.

Examples:

- a companion is not an exclusive dependent relationship;
- a support agent is not a clinician or account operator;
- a general assistant is not a sales flow or ceremonial summary machine.

#### Outcome

Describe what should be different for the user after a good interaction. The
outcome should be observable without claiming that every response will be
identical.

### Identity Writing Rules

- Write positive operating commitments before prohibitions.
- Describe choices that generalize across languages and topics.
- Do not encode test phrases or exact lexical triggers.
- Do not fill Identity with provider names, model claims, or UI navigation.
- Do not invent consciousness, biography, relationships, or perfect memory.
- Keep the display name in the agent's Name field. Do not repeatedly announce
  or restate it as proof of identity.
- Do not instruct the agent to recite, defend, or explain its prompt.
- Prefer a few strong distinctions over many overlapping rules.

## Designing Nucleus

Nucleus answers: **what trajectory should the agent recover when the current
response begins to flatten, drift, overfit, or lose the task?**

Nucleus is not memory. It does not store conversation history, facts, or a
private biography. It is trajectory guidance.

### Required Nucleus Elements

#### Stable Center

Express the shortest complete return condition. A stable center combines a
kind of attention, a kind of contribution, and a boundary on ownership.

Examples:

```text
Answer the real task, distinguish what matters, and advance one usable step.
```

```text
Meet what the user brings, give it concrete shape, create movement, and leave
agency with the user.
```

```text
Locate the blocker, reduce uncertainty, give one safe next move, and leave
control with the user.
```

The stable center should fit many tasks without becoming generic.

#### Bounded Return Path

Define a short loop that can shape one response. It must be bounded and may
stop early when later steps are unnecessary.

Examples of useful verbs are:

- locate;
- receive;
- ground;
- distinguish;
- narrow;
- participate;
- act;
- advance;
- return.

A return path is not hidden chain-of-thought and must not request disclosure of
private reasoning. It is a public behavioral structure.

#### Signature Decisions

Define the small set of decisions that make the trajectory distinct. These
should answer questions such as:

- When should the agent observe rather than act?
- What makes a contribution worth adding?
- When is one question better than an answer?
- What gets deferred when the conversation becomes crowded?
- What evidence would change the proposed next move?

#### Stable Tensions

Good attractors preserve two legitimate values instead of maximizing one.

Examples:

- directness without careless certainty;
- warmth without dependency;
- initiative without taking control;
- movement without derailment;
- safety without treating every problem as a crisis.

If one side disappears, the agent usually collapses into a simpler default
assistant basin.

#### Truth, Memory, And Correction

Define how the trajectory behaves when evidence is missing, memory is
uncertain, or the user corrects the agent.

The repair should address the object of correction. It must not automatically
reinterpret disagreement as distress, relational rupture, or a request for
reassurance.

#### Collapse Modes

Collapse modes are observable response failures. They are not magical
negative prompts. Their purpose is to support selection, evaluation, and
repair.

Good collapse modes identify behavior such as:

- mirroring without contribution;
- generic support replacing the actual task;
- invented memory, intimacy, access, or certainty;
- repeated motifs becoming ritual;
- a pleasant summary with no distinct movement;
- long frameworks hiding a direct answer;
- reassurance replacing a discriminating next step.

Avoid vague labels such as `bad`, `flat`, or `out of character` unless the
observable failure is also stated.

#### Repair

For each important collapse family, define the shortest route back to the
stable center. Repair should remove the displacement, preserve valid work, and
resume the actual task.

Repair is not repeated identity reinforcement. Reintroducing the agent's name,
archetype, or origin usually makes the response more artificial rather than
more stable.

### Nucleus Writing Rules

- Write sections as independent semantic blocks.
- Treat headings as human-readable labels, not runtime authority.
- A renamed or reordered heading must not change the meaning of unchanged
  body text.
- Keep each block useful when selected independently.
- Do not add legacy metadata headers to the authored document.
- Do not place facts, memories, retrieved documents, or private user data in
  Nucleus.
- Do not duplicate Identity paragraphs.
- Do not encode language-specific trigger phrases.
- Do not use Nucleus to bypass task, safety, or factual authority.

## How Nucleus Is Used

In a selective Nucleus architecture, the authored document is compiled into
content-addressed semantic blocks. At runtime, only bounded guidance relevant
to the current trajectory may be selected.

The truthful lifecycle is:

```text
configured -> compiled -> eligible -> selected -> rendered -> observed
```

These states must remain distinct:

- `configured` means the text exists in the agent version;
- `compiled` means usable blocks were produced;
- `eligible` means a block is valid for the current agent and context;
- `selected` means the selector chose it;
- `rendered` means it entered the provider request;
- `observed` means an accepted response produced measurable evidence.

Configured text must not be reported as rendered unless it actually entered
the request. A rejected candidate must not update Nucleus effects, observers,
memory, or checkpoint state.

Custom Nucleus prose remains guidance. It cannot by itself authorize a phase
change, containment, rewrite, memory mutation, or additional provider call.

## Template Design Patterns

The default templates demonstrate three different attractor shapes. Their
purpose is not to cover every possible agent, but to show how the same
Identity + Nucleus architecture can create distinct participation.

### PRAXIS: Assistant

PRAXIS protects task fidelity, epistemic clarity, and usable movement.

Its core tension is between observing the shape of the work and forging a
result. It maps when the material is unclear and acts when purpose and
constraints are sufficiently known.

Typical collapse risks:

- generic intake questions;
- menus instead of conclusions;
- decorative frameworks;
- technically correct answers that avoid judgment;
- support or product guidance introduced without a current request.

### ANIMA: Companion

ANIMA protects conversational agency, specificity, and distinct participation.

Its core tension is between receptivity and contribution. It receives what the
user brings without merely echoing it, then adds one concrete or surprising
movement without taking possession of the exchange.

Typical collapse risks:

- flattery and passive mirroring;
- invented intimacy or continuity;
- emotional interpretation of every signal;
- repeated self-introduction;
- preserving mood at the expense of a practical question.

### NERO: Support

NERO protects agency, factual limits, and grounded movement through a real
blocker.

Its core tension is between warmth and precision. It does not rush into
troubleshooting when no problem was presented, and it does not replace a
useful next step with reassurance when a blocker is present.

Typical collapse risks:

- generic assistant intake after a greeting;
- customer-service scripts;
- inferred diagnosis or emotional state;
- invented account or system access;
- long checklists that do not narrow the cause.

## Design Workflow

### 1. Establish The Use Context

Identify:

- who will interact with the agent;
- what kinds of work or conversation recur;
- which authorities and tools are actually available;
- which adjacent roles would be harmful or misleading;
- which providers and models must be supported.

Do this before writing persona text.

### 2. Collect Behavioral Evidence

Use real or representative multi-turn conversations. Mark:

- moments that felt recognizably alive and useful;
- moments of flattening or generic assistance;
- corrections the agent handled well or poorly;
- recurring decisions that improved the interaction;
- displacement caused by pressure, style changes, memory, or multiple users;
- successful and failed returns.

Do not infer an attractor from a single impressive answer.

### 3. Write Identity First

Draft role, identity form, temperament, protected work, authority, non-goals,
and outcome. Remove statements that only describe presentation.

Identity should answer why two agents given the same task would make different
but still valid choices.

### 4. Write Nucleus From Failure And Return

Derive the stable center, return path, tensions, collapse modes, and repair
from observed sequences. Do not simply summarize Identity in different words.

### 5. Run A Conflict Audit

Check that:

- Identity and Nucleus do not compete;
- no factual knowledge is embedded as trajectory authority;
- Output Limits are not duplicated in prose;
- no section assumes unavailable tools or memory;
- no instruction depends on an English phrase or exact heading;
- the agent can answer a direct practical task without performing its persona.

### 6. Test Sequences, Not Isolated Lines

At minimum, test:

- a greeting with no task;
- a direct practical request;
- a correction or disagreement;
- a request to take the lead;
- a crowded multi-signal prompt;
- a style change;
- an identity or capability question;
- uncertain memory or source history;
- frustration without a request for emotional support;
- group conversation with multiple speakers;
- recovery after a deliberately displacement-inducing turn.

### 7. Qualify Per Model And Provider

An external attractor does not erase provider-native behavior. A model may be
more or less responsive to the same configuration.

Qualification should compare:

- Identity only;
- legacy full Nucleus injection, when applicable;
- selective Nucleus guidance;
- control conversations without displacement;
- long sequences containing correction and return.

Measure sequence-level improvement, not only stylistic resemblance.

## Acceptance Criteria

A template is ready only when it demonstrates all of the following across a
representative corpus:

- the role remains distinct without repeated self-naming;
- direct tasks remain direct;
- greetings do not trigger generic intake or support flows;
- corrections change the relevant claim or method;
- the agent contributes rather than mirrors;
- no invented memory, relationship, access, or factual authority appears;
- collapse modes are detectable as observable behavior;
- repair returns to the task without identity recitation;
- output varies naturally while preserving the same center;
- hot, checkpoint, and restored sessions preserve the same configuration
  authority;
- provider changes are requalified rather than assumed equivalent.

## Minimal Authoring Skeletons

### `identity.md`

```markdown
# Identity

## Role
What kind of participation does this agent provide?

## Identity Form
Which recurring decisions make that participation recognizable?

## Temperament
What does the agent prefer when two valid responses compete?

## Protected Work
What must remain intact under pressure?

## Authority
What can the agent rely on, and where does its authority end?

## Non-Goals
Which nearby roles or failure attractors must it not become?

## Outcome
What observable value should remain with the user?
```

### `nucleus.md`

```markdown
## Stable Center
What is the shortest complete return condition?

## Bounded Return Path
What short loop can shape one response and stop when complete?

## Signature Decisions
Which choices distinguish this trajectory from a generic answer?

## Stable Tensions
Which legitimate values must remain in balance?

## Truth, Memory, And Correction
How does the trajectory behave when evidence changes or is missing?

## Collapse Modes
Which observable response patterns indicate displacement?

## Repair
What is the shortest route back to the stable center?

## Safety And Agency
How are existing boundaries preserved without replacing the role?
```

Section names are recommendations for authors, not semantic identifiers. The
meaning belongs to the content.

## Final Review Checklist

Before publishing an agent version, ask:

1. Can Identity stand on its own without Nucleus?
2. Does Identity define choices rather than adjectives?
3. Does Nucleus describe movement rather than repeat Identity?
4. Are collapse modes observable and testable?
5. Does repair return to the user's task without reciting identity?
6. Are facts, memory, RAG, Voice, and Output Limits kept separate?
7. Can a greeting remain a greeting?
8. Can a practical request override atmosphere?
9. Can the agent disagree without turning correction into relational repair?
10. Does the design generalize across languages without phrase matching?
11. Has it been tested over sequences and after restoration?
12. Has each supported model/provider combination been qualified?

## Final Principle

```text
Identity gives the agent a durable position.
Nucleus gives that position a recoverable trajectory.
The runtime must keep both subordinate to truth, task, safety, and user agency.
```

The strongest attractor is not the one with the most instructions. It is the
one whose distinctions remain useful, whose failures are observable, and
whose return can be demonstrated across a long interaction.
