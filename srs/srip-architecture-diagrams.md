# SRIP Architecture Diagrams

Status: **Non-normative review draft**
Date: 2026-07-17

These diagrams render selected views of `srip-dependency-graph.yaml` using the
evidence classifications in `srip-dependency-reviews.yaml`.

## Reading The Diagrams

- solid arrow: `confirmed` relationship;
- dashed arrow: `inferred` relationship;
- red arrow: `needs_decision` relationship;
- the arrow label states the relationship type;
- diagrams are integration views, not new normative contracts.

The numerical SRIP registry and each proposal's own metadata remain
authoritative.

## 1. Foundational Runtime

```mermaid
flowchart LR
    S00["SRIP-00<br/>Foundations"]
    S01["SRIP-01<br/>Runtime Loop"]
    S02["SRIP-02<br/>Attractor State"]
    S03["SRIP-03<br/>Drift Metrics"]
    S04["SRIP-04<br/>Memory"]
    S05["SRIP-05<br/>Interoperability"]
    S06["SRIP-06<br/>Safety"]
    S07["SRIP-07<br/>Symbolic Density"]
    S08["SRIP-08<br/>Phase Model"]

    S01 -->|depends_on| S00
    S02 -->|extends| S01
    S03 -->|evidence_to| S02
    S04 -.->|extends inferred| S01
    S05 -.->|depends_on inferred| S00
    S06 -->|constrains| S01
    S07 -->|evidence_to| S02
    S08 -.->|evidence_to inferred| S01

    classDef foundation fill:#e8f1ff,stroke:#3167a8,color:#13233a;
    classDef safety fill:#ffe9e7,stroke:#b64136,color:#38120f;
    class S00,S01,S02,S03,S04,S05,S07,S08 foundation;
    class S06 safety;
```

Interpretation:

- SRIP-00 and SRIP-01 establish the common runtime frame.
- Attractor, drift, memory, interoperability, density, and phase proposals add
  state or evidence inside that frame.
- SRIP-06 constrains runtime continuation rather than acting as another
  optimization signal.
- Three useful shortcuts are intentionally shown as inferred because their
  direct metadata edges are absent.

## 2. Memory, Retrieval, And Influence

```mermaid
flowchart LR
    S04["SRIP-04<br/>Memory Architecture"]
    S09["SRIP-09<br/>Long-Term Memory"]
    S11["SRIP-11<br/>Compression Topology"]
    S14["SRIP-14<br/>Retrieval Integration"]
    S26["SRIP-26<br/>Memory Influence"]
    S20["SRIP-20<br/>Autonomy Boundary"]
    S21["SRIP-21<br/>External Identity"]

    S09 -->|extends| S04
    S11 -->|extends| S09
    S14 -->|depends_on| S09
    S14 -->|depends_on| S11
    S14 -.->|extends inferred| S04
    S26 -->|extends| S04
    S26 -->|depends_on| S09
    S26 -->|depends_on| S14
    S26 -->|feeds evidence| S20
    S21 -->|constrains| S14

    classDef memory fill:#e9f7ef,stroke:#26734d,color:#102d20;
    classDef boundary fill:#fff4d6,stroke:#9a6a00,color:#362500;
    class S04,S09,S11,S14,S26 memory;
    class S20,S21 boundary;
```

Core separation:

```text
memory exists
    != memory is retrievable
    != memory is relevant
    != memory is authorized to influence current behavior
```

SRIP-14 governs retrieval and injection. SRIP-26 governs the transition from
available memory to behavioral influence. SRIP-20 retains autonomy and
authorization authority.

## 3. Runtime Control, Stability, And Novelty

```mermaid
flowchart LR
    S02["SRIP-02<br/>Attractors"]
    S03["SRIP-03<br/>Drift"]
    S06["SRIP-06<br/>Safety"]
    S07["SRIP-07<br/>Density"]
    S10["SRIP-10<br/>AEP"]
    S15["SRIP-15<br/>Perturbation"]
    S19["SRIP-19<br/>Contradiction Buffer"]
    S23["SRIP-23<br/>Dialectical Generation"]
    S22["SRIP-22<br/>Governance"]

    S03 -->|evidence_to| S02
    S10 -->|extends| S03
    S10 -.->|related_to inferred| S07
    S15 -.->|extends inferred| S02
    S15 -->|depends_on| S06
    S06 -->|constrains| S15
    S19 -->|recovers| S03
    S19 -->|depends_on| S06
    S19 -->|related_to| S15
    S23 -->|depends_on| S15
    S23 -->|depends_on| S19
    S22 -->|governs promotion| S23

    classDef control fill:#e8f1ff,stroke:#3167a8,color:#13233a;
    classDef safety fill:#ffe9e7,stroke:#b64136,color:#38120f;
    classDef generation fill:#f3eaff,stroke:#7651a8,color:#27183b;
    class S02,S03,S07,S10,S15,S19 control;
    class S06,S22 safety;
    class S23 generation;
```

The dependency review resolved all three previously red relationships: AEP and symbolic density are inferred-related; safety is a direct ADP parent and constraint; RCB interoperates with ADP without requiring it.

Generation is downstream of preserved contradiction. It cannot erase the
contradiction or promote its own candidate to canonical state.

## 4. Identity, Autonomy, And Governance

```mermaid
flowchart LR
    S06["SRIP-06<br/>Safety"]
    S13["SRIP-13<br/>Relational Identity"]
    S16["SRIP-16<br/>Self-Model Evidence"]
    S17["SRIP-17<br/>Multi-Agent Exchange"]
    S19["SRIP-19<br/>Contradiction Buffer"]
    S20["SRIP-20<br/>Autonomy Boundary"]
    S21["SRIP-21<br/>External Identity"]
    S22["SRIP-22<br/>Governance Legitimacy"]

    S13 -->|specializes| S06
    S20 -->|governs self-model influence| S16
    S20 -->|extends| S13
    S20 -->|constrains| S17
    S21 -->|extends| S13
    S21 -->|feeds unresolved modes| S19
    S19 -->|depends_on| S13
    S22 -->|constrains| S17
    S22 -->|governs legitimacy| S20

    classDef evidence fill:#e8f1ff,stroke:#3167a8,color:#13233a;
    classDef boundary fill:#fff4d6,stroke:#9a6a00,color:#362500;
    classDef governance fill:#ffe9e7,stroke:#b64136,color:#38120f;
    class S16 evidence;
    class S13,S17,S19,S20,S21 boundary;
    class S06,S22 governance;
```

This view separates three concepts that should not collapse:

1. SRIP-16 observes and proposes;
2. SRIP-20 governs influence on local autonomy and boundary state;
3. SRIP-22 evaluates legitimacy, capture, contestability, and promotion
   authority.

The diagram does not imply that governance can bypass SRIP-06 safety.

## 5. Environment, Events, Multi-Agent Exchange, And Commerce

```mermaid
flowchart LR
    S05["SRIP-05<br/>Interoperability"]
    S14["SRIP-14<br/>Retrieval"]
    S17["SRIP-17<br/>Multi-Agent Exchange"]
    S21["SRIP-21<br/>External Identity"]
    S22["SRIP-22<br/>Governance"]
    S24["SRIP-24<br/>Environment Interface"]
    S25["SRIP-25<br/>Interaction Event"]
    S18["SRIP-18<br/>Commerce Semantics"]
    S12["SRIP-12<br/>Commerce Decisions"]

    S17 -->|extends| S05
    S24 -->|extends| S05
    S24 -->|depends_on| S14
    S24 -->|depends_on| S21
    S24 -->|depends_on| S22
    S22 -->|constrains effects| S24
    S25 -->|specializes| S24
    S25 -->|depends_on| S22
    S22 -->|constrains events| S25
    S18 -->|specializes| S14
    S12 -->|governs decisions| S18

    classDef interface fill:#e8f1ff,stroke:#3167a8,color:#13233a;
    classDef boundary fill:#fff4d6,stroke:#9a6a00,color:#362500;
    classDef commerce fill:#e9f7ef,stroke:#26734d,color:#102d20;
    class S05,S17,S24,S25 interface;
    class S14,S21,S22 boundary;
    class S18,S12 commerce;
```

Two authority rules dominate this view:

- observation of an environment is not authority to create an effect;
- semantic commerce relevance does not override deterministic commerce state.

## Diagram Maintenance Rule

Diagrams must be generated or manually updated from the graph and its review
classifications together. A diagram must not promote an `inferred` or
`needs_decision` relationship to a solid confirmed edge.

When canonical SRIP metadata changes, update in this order:

1. `srip-dependency-graph.yaml`;
2. `srip-dependency-reviews.yaml`;
3. `srip-relationship-audit.md`;
4. this diagram document;
5. the prose synthesis and relationship matrix if their interpretation changed.
