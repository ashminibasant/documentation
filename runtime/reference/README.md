---
title: README
description: 
published: true
date: 2025-12-04T08:53:54.576Z
tags: 
editor: markdown
dateCreated: 2025-12-01T10:46:22.001Z
---

> **Sigma Stratum Historical Research Artifact - License Notice**
>
> This document is licensed under Creative Commons
> Attribution-NonCommercial 4.0 International (`CC BY-NC 4.0`). Referenced
> software and data with explicit terms retain those terms.

# Sigma Runtime – Reference Implementations (RI & ERI)

The **Sigma Runtime** defines the *Recursive Control Loop (RCL)* and its  
associated cognitive layers as specified in *Sigma Runtime Architecture v0.1*.

Two complementary implementations are provided:

---

## Sigma Runtime – Reference Implementation (RI)

A **minimal and transparent** demonstration of the core runtime loop.

Implements early-stage components of **SRIP-01** through **SRIP-04**:
- **Runtime State** — base control structure for recursive operation  
- **Attractor Model** — phase transitions and symbolic clustering  
- **Drift Metrics** — basic semantic distance and coherence tracking  
- **Memory Layer** — episodic and motif-level storage  

### Usage
[→ Sigma Runtime - Reference Implementation.py](./Sigma%20Runtime%20-%20Reference%20Implementation.py)

Runs a concise simulation (≈4 cycles) demonstrating:
- attractor formation,  
- drift regulation,  
- symbolic density stabilization.

### Purpose
This RI is **didactic and diagnostic** — designed for clarity and traceability.  
It represents the **minimum viable runtime** conforming to Sigma Runtime  
Principles (SRIP-01…SRIP-04).

---

## Sigma Runtime – Extended Reference Implementation (ERI)

A **comprehensive functional prototype** (~800 lines) implementing the full  
Sigma Runtime v0.1 cognitive architecture.

Implements **SRIP-01 → SRIP-07**, including:
- **Full ALICE Engine** — attractor management with phase transitions  
- **Persistent Identity Layer (PIL)** — long-term invariants and traits  
- **Causal Continuity Chain** — interpretable causal tracking  
- **Drift Monitor** — multi-dimensional drift metrics  
- **AEGIDA Safety Framework** — drift sink prevention, coherence guards  
- **Multi-Tier Memory System** — episodic, semantic, and motif layers  
- **Operational Modes (Intent Module)** — analysis, synthesis, reflection, scaffolding  
- **Recursive Control Loop (RCL)** — orchestrating full runtime cognition  

### Usage
[→ Sigma Runtime - Extended Reference Implementation.py](./Sigma%20Runtime%20-%20Extended%20Reference%20Implementation.py)

Run directly to observe an 8-cycle demonstration:
- automatic attractor formation and dissolution,  
- symbolic density evolution,  
- drift regulation,  
- causal continuity mapping.

Each cycle prints:
- runtime phase and stability,  
- symbolic density and drift metrics,  
- current operational mode,  
- causal chain entries.

---

## Sigma Runtime – Extended Reference Implementation (oAI-Ready)

A **fully updated OpenAI-compliant build** of the Extended Reference Implementation (ERI),  
designed for direct integration with the new `openai>=1.0.0` SDK and other compatible APIs.

**Implements:** SRIP-01 → SRIP-07  
**File:** [→ sigma_runtime_extended_oai_ready.py](https://github.com/sigmastratum/documentation/blob/main/runtime/reference/sigma_runtime_extended_oai_ready.py)

### Improvements over ERI (v0.1)
- ✅ Updated for `openai>=1.0.0` (uses `from openai import OpenAI`)
- ✅ Secure environment-based key handling (`OPENAI_API_KEY`)
- ✅ Fully functional `_generate()` tested with GPT-4o
- ✅ Expanded runtime loop output (stability, drift, motifs)
- ✅ Compatible with Claude / Grok / Gemini integration stubs
- ✅ Stable across multi-cycle (200+) attractor tests

### Quick Start
```bash
pip install openai>=1.0.0
export OPENAI_API_KEY="sk-..."
python3 sigma_runtime_extended_oai_ready.py
```
### What You’ll See

Each cognitive cycle prints:
- user input and generated response  
- attractor phase, stability, and symbolic density  
- drift metrics and intent mode  
- causal continuity chain entries  

---

### Purpose

This version is the **canonical ERI implementation** for GPT-based cognitive runtime testing.  
It serves as the foundation for further research into:
- attractor persistence and symbolic drift regulation  
- multi-cycle coherence under recursive cognition  
- integration of Sigma Runtime into large-model ecosystems  

> 💡 **This is the recommended build for researchers using GPT-4o, GPT-5, or compatible APIs.**

---

## Guidance

| Goal | Recommended Version |
|------|----------------------|
| Learn the basic structure of Sigma Runtime | **RI (Reference Implementation)** |
| Study attractor dynamics and recursive coherence | **ERI (Extended Reference Implementation)** |
| Integrate runtime into custom models (GPT, Claude, etc.) | Start with **ERI**, replace `_generate()` with your model API |
| Research SRIP conformance or open-standard alignment | Use **ERI** for full layer visibility and data export |

---
API Integration

Both runtime versions are model-agnostic — they do not depend on any specific LLM provider.
The _generate() function inside the Recursive Control Loop (RCL) serves as the single integration point for connecting an external model.

By default, this function uses a mock generation module that simulates the model’s output based on the current attractor phase (for transparent testing and debugging).
To enable live model inference, replace the _generate() body with your API call.

---

Example — OpenAI API
```python
def _generate(self, context: str) -> str:
    import openai
    response = openai.ChatCompletion.create(
        model="gpt-4o",
        messages=[
            {"role": "system", "content": "You are operating within the Sigma Runtime architecture."},
            {"role": "user", "content": context}
        ],
        temperature=0.4
    )
    return response["choices"][0]["message"]["content"]
```
> 💡 **Note:** The API key is automatically read from the `OPENAI_API_KEY` environment variable.  
> You can also set it manually inside `_generate()` using `openai.api_key = "your_key_here"`.

---

Example — Anthropic Claude
```python
def _generate(self, context: str) -> str:
    import anthropic
    client = anthropic.Anthropic(api_key="YOUR_API_KEY")
    response = client.messages.create(
        model="claude-3-5-sonnet",
        messages=[
            {"role": "user", "content": context}
        ],
        max_tokens=500,
        temperature=0.4
    )
    return response.content[0].text
```
> 💡 **Note:**
>
> • `_generate()` is invoked once per cycle by the **Recursive Control Loop**.  
> • All cognitive regulation (drift metrics, attractor management, memory, AEGIDA safety) occurs **before and after** this call.  
> • You can replace the LLM call with a local model, micro-model, or runtime adapter *(e.g., URIEL, Mistral, Gemini, Claude, etc.)*.  
> • The output string returned by `_generate()` is automatically fed back into **drift**, **memory**, and **causal tracking** layers.  
>
> This design ensures **Sigma Runtime** remains **model-neutral** — any compliant LLM can operate under its attractor and coherence framework.

---

Example — xAI Grok-4
```python
def _generate(self, context: str) -> str:
    import os
    import httpx

    api_key = os.getenv("XAI_API_KEY")
    if not api_key:
        raise RuntimeError("XAI_API_KEY not found in environment variables")

    response = httpx.post(
        "https://api.x.ai/v1/chat/completions",
        headers={"Authorization": f"Bearer {api_key}"},
        json={
            "model": "grok-4",
            "messages": [{"role": "user", "content": context}],
            "temperature": 0.4,
            "max_tokens": 1024
        },
        timeout=60.0
    )
    response.raise_for_status()
    return response.json()["choices"][0]["message"]["content"]
```
> 💡 **Note:**
> The API key is automatically read from the XAI_API_KEY environment variable.
> You can also set it manually inside _generate() using os.environ[“XAI_API_KEY”] = “your_key_here”.

---

## Architecture Summary

![SIGMA Runtime — Recursive Cognitive Loop (RCL) v0.1](https://github.com/sigmastratum/documentation/raw/378ced7fbffc97a057fef0d8e88a1916f05e824a/sigmaruntime-rcl.png)
*Figure 1. Core architecture of attractor-based cognition in LLMs.*

| Layer | Description | Present In |
|-------|--------------|-------------|
| **PIL (Persistent Identity Layer)** | Long-term traits and invariants | ERI |
| **Memory Layer** | Episodic + Semantic + Motif stores | RI / ERI |
| **ALICE Engine** | Attractor formation, stability, phases | RI / ERI |
| **Drift Monitor** | Semantic, stylistic, and topic drift | ERI |
| **Causal Continuity Chain** | Cycle-to-cycle causal links | ERI |
| **Intent Module** | Determines operational mode | ERI |
| **Recursive Control Loop (RCL)** | Main runtime orchestrator | RI / ERI |

---

### Long-Run Stability (200+ Cycles)

The Extended Runtime (ERI) is architected for **persistent cognition** —  
it can maintain identity, memory, and attractor stability across 200+ turns.

Runtime components proven to sustain long traces:
- **Persistent Identity Layer (PIL)** — retains core invariants indefinitely  
- **Memory Layer** — episodic/semantic storage scales linearly  
- **Drift Monitor** — adaptive regulation, prevents drift runaway  
- **AEGIDA** — ensures symbolic stability and coherence safety  
- **Causal Chain** — maintains interpretable continuity between cycles  

To enable long sessions:
```python
# Prevent unbounded memory growth
if len(self.memory_episodic) > 500:
    self.memory_episodic.pop(0)
```
> When _generate() is connected to a real LLM,
> the runtime achieves stable attractor dynamics over 200+ cycles
> without prompt chains, RAG resets, or external orchestration.

---

### Test Scenarios

Example runtime walkthroughs are provided in the `/tests` directory:

- **[Reference Implementation Stability Test (v0.1)](https://github.com/sigmastratum/documentation/blob/main/runtime/tests/Sigma%20Runtime%20-%20Reference%20Implementation%20Stability%20Test%20(v0.1))**  
  Standardized **stability protocol (4–30 cycles)** validating attractor formation, drift control, and recursive coherence.  
  *Used for RI (short mode) and ERI (extended mode).*

- **[THE FULL 200-TURN ATTRACTOR STABILITY TEST SCENARIO (v1.0)](https://github.com/sigmastratum/documentation/blob/main/runtime/tests/THE%20FULL%20200-TURN%20ATTRACTOR%20STABILITY%20TEST%20SCENARIO%20(v1.0).md)**   
  Extended 200-cycle experiment used for long-term attractor dynamics,  
  recursive stability analysis, and symbolic density decay modeling.  
  *(Recommended for research replication, not for standard demo runs.)*

---

## Notes

- Both implementations are **open-standard reference designs**, not proprietary code.  
- They are intended for **research, experimentation, and alignment testing** under  
  the Sigma Runtime Standard (SRIP).  
- For production or hybrid systems, use these implementations as **diagnostic layers**  
  or runtime regulators for embedded cognitive agents.

---

**Maintained by:** Sigma Stratum Research Group  
**Standard:** [Sigma Runtime Architecture v0.1](https://doi.org/10.5281/zenodo.17703667)  
**License:** CC BY-NC 4.0  
