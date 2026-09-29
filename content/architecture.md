# ThreeTwinArchitectureNext — Architecture Overview

## 1. Architecture Principle

ThreeTwinArchitectureNext separates **persistent educational memory** from **active reasoning and action**.

The Three Twins retain governed educational knowledge and state over time. Active reasoning components interpret learner interaction, make pedagogical decisions, realize educational actions, assess responses, and propose state transitions. Persistence changes only through explicit governed boundaries.

The enduring division is:

- **Knowledge Twin** — learner-independent domain knowledge and mathematical truth.
- **Learner Twin** — persistent estimated state of an individual learner.
- **Teaching Twin** — reusable pedagogical, observation, evidence, and policy semantics.
- **Reasoning and action layer** — learner-specific decision-making, interpretation, assessment, realization, and state-transition logic operating over the Twins.

A generated answer, diagnosis, assessment result, recommendation, or state proposal does not become persistent truth merely because a model or algorithm produced it. Semantic authority, admission, and persistence remain explicit.

---

## 2. The Three Twins

### Knowledge Twin

The Knowledge Twin owns learner-independent domain semantics and mathematical truth.

Let \(K\) denote governed Knowledge. Knowledge may include primitive elements and explicitly admitted composed elements. Relations between Knowledge elements do not automatically create new composed coordinates, and graph structure does not imply propagation of learner state.

The Knowledge Twin also owns the semantic vocabulary of **Responsibilities** \(R\): stable, learner-independent, problem-independent observable performances over Knowledge, such as executing a procedure or applying knowledge in context. \(R\) is separately governed; it is not computed mechanically from \(K\).

### Learner Twin

The Learner Twin stores the accepted estimate of an individual learner.

The canonical learner-state address is an admitted exact Knowledge–Responsibility pair. Persistent state therefore distinguishes different observable performances over the same Knowledge.

A Knowledge-only summary may be derived for presentation under an explicit aggregation policy, but it is not the canonical learner state and is not a Pedagogical Decision input.

### Teaching Twin

The Teaching Twin stores reusable pedagogical semantics and policy.

Let \(P\) denote reusable Teaching policy. Teaching semantics include assessment policy, evidence policy, ambiguity and error-tolerance policy, intervention intent, observation semantics, and other governed instructional policy.

Learner-specific selection is not persistent Teaching memory. It occurs in the active control layer.

---

## 3. Semantic Spaces

The architecture uses two principal semantic structures.

### 3.1 Knowledge–Responsibility domain

The ambient product is

\[
K\times R.
\]

The canonical semantic domain is the **admitted subset**

\[
Z_{KR}\subseteq K\times R.
\]

Membership in \(Z_{KR}\) means that the exact \((K,R)\) pair is governed and admitted as an observable semantic coordinate. Bounded registries and exact pair records in the implementation materialize or prove membership in \(Z_{KR}\); they do not define a second canonical mathematical object.

Two important fields live over this domain:

\[
E_t: Z_{KR}\rightarrow \mathcal E,
\]

\[
X_t: Z_{KR}\rightarrow \mathcal X.
\]

Here \(E_t\) is learner evidence and \(X_t\) is persistent learner state.

### 3.2 Teaching semantic space

Let \(Z_T\) denote the conceptual Teaching-side semantic space containing reusable observation/evidence semantics and reusable Teaching policy \(P\).

\(P\) is an explicit constituent of \(Z_T\), but the architecture does not freeze one universal ontology such as Observation × Policy. Different educational modalities may materialize different governed structures within this conceptual space.

The assessment observation \(D_t\) lives on this Teaching side: it is a governed observation object or field **over** conceptual \(Z_T\). It need not be a total function on \(Z_T\). This contrasts directly with learner evidence \(E_t\), which is a field over admitted \(Z_{KR}\):

- \(D_t\) records **what the educational interaction observed** under governed Teaching semantics;
- \(E_t\) records **what that observation implies as learner evidence** at exact admitted Knowledge–Responsibility coordinates.

The two semantic structures therefore remain distinct and are connected only through governed bindings such as \(B_J\) in an admitted assessment template.

```mermaid
flowchart LR
    K["Knowledge K"]
    R["Responsibility R"]
    A["Ambient K × R"]
    ZKR["Admitted domain Z_KR"]
    P["Teaching policy P"]
    ZT["Conceptual Teaching semantics Z_T"]
    D["Observation D_t over Z_T"]
    E["Evidence field E_t over Z_KR"]

    K -->|"product coordinate"| A
    R -->|"product coordinate"| A
    A -->|"governed admission"| ZKR
    P -->|"constituent"| ZT
    ZT -->|"governed observation semantics"| D
    ZKR -->|"evidence address domain"| E
```

All boxes in the diagrams denote objects or states. Maps and transitions appear on arrows.

---

## 4. Reusable Assessment Architecture

Assessment is one Educational Action modality with a formal measurement path.

### 4.1 Reusable admitted assessment template

A reusable admitted assessment resource is

\[
J=(M,A),
\]

where:

- \(M\) is the Knowledge-side mathematical family and its governed demand over \(Z_{KR}\),
- \(A\) is the fixed assessment facet carrying Teaching-side measurement semantics, policy, provenance, and governed bindings.

The canonical authoring map \(G\) constructs a reusable template candidate from explicit admitted Knowledge–Responsibility targets and governed authoring context:

\[
(KR^*,P,H)\xrightarrow{G}J_{candidate}=(M,A)_{candidate}.
\]

Here \(H\) denotes learner-independent governed authoring context, including mathematical/problem content, criterion semantics, identifiers, and provenance. Construction of the bounded `AssessmentSpecification` representation of the \(A\)-side is an internal implementation substrate of \(G\), not a separate canonical architecture map.

The resulting \(J_{candidate}\) becomes authoritative only through

\[
J_{candidate}\xrightarrow{Adm_J}J.
\]

Template admission validates authority and version integrity, realization parameter domains, family invariants, exact admitted \(Z_{KR}\) claims, assessment capability consistency, provenance, and the requirement that concrete realization still pass \(Adm_M\).

### 4.2 Fixed cross-space binding

Each admitted assessment template fixes a governed relation

\[
B_J\subseteq Z_T\times Z_{KR}.
\]

\(B_J\) links Teaching-side observation semantics to exact Knowledge–Responsibility coordinates. It is fixed before the learner response and remains invariant across realizations of the same admitted template.

In the current bounded implementation, criterion-addressed diagnostic bindings are the concrete authority that resolves \(B_J\).

### 4.3 Concrete learner-facing item

An admitted template contains a mathematical family \(M\) and exposes governed realization parameters \(\rho\). At the mathematical level the realization map is

\[
(M,\rho)\xrightarrow{Inst_M}\widetilde M_{candidate}.
\]

Operationally, this occurs under the authority of the admitted \(J=(M,A)\): `Inst_M` may instantiate \(M\), but it may not change the fixed \(A\), \(B_J\), semantic target, intent, or modality carried by the admitted template.

The candidate then passes the separate post-instantiation admission boundary

\[
\widetilde M_{candidate}\xrightarrow{Adm_M\;\text{under admitted }J}\widetilde M.
\]

Only after successful \(Adm_M\) is the learner-facing item materialized:

\[
(\widetilde M,A)\xrightarrow{materialize}\widetilde J.
\]

The materialization step is representational; it introduces no second semantic admission decision.

```mermaid
flowchart LR
    JC["J_candidate"]
    J["Admitted J = (M,A)"]
    M["Mathematical family M"]
    RHO["Allowed ρ"]
    MC["M~ candidate"]
    MT["Admitted M~"]
    JT["Learner-facing J~ = (M~,A)"]

    JC -->|"Adm_J"| J
    J -->|"mathematical facet"| M
    M -->|"Inst_M with ρ"| MC
    RHO -.->|"parameter"| MC
    MC -->|"Adm_M under J"| MT
    MT -->|"materialize with fixed A and B_J"| JT
    J -.->|"fixed A and B_J"| JT
```

---

## 5. Learner-Specific Control

The generic adaptive control path is best read as objects connected by maps:

\[
X_t\xrightarrow{PD}Q_t\xrightarrow{EA}EducationalActionItem_t.
\]

### 5.1 Pedagogical Decision

Pedagogical Decision \(PD\) is the sole learner-specific selector. It reads governed learner state and policy context and maps the current learner state to the educational requirement that should be acted on next.

Its semantic output is the transient object

\[
Q_t=(M_t^*,A_t^*).
\]

- \(M_t^*\) is the Knowledge–Responsibility-side requirement over \(Z_{KR}\).
- \(A_t^*\) is the Teaching-side requirement over \(Z_T\), including pedagogical intent, modality, and realization constraints.
- cross-part constraints and decision provenance may relate the two sides.

The bounded runtime represents this structure as an explicit `EducationalActionRequirement` containing an exact target, pedagogical intent, admissible modality set, hard constraints, decision provenance, and optional realization guidance.

### 5.2 Educational Action realization

Educational Action \(EA\) maps \(Q_t\) plus learner-independent resource authority to a learner-facing Educational Action Item. It does not re-read learner state to select a different target.

Its conceptual stages are:

1. hard eligibility,
2. governed soft fit among eligible resources,
3. permitted realization,
4. modality-specific admission.

If hard requirements cannot be satisfied, realization fails closed rather than silently weakening \(Q_t\).

The generic EA architecture is intentionally broader than the currently validated runtime. The fixed-template assessment branch is validated; generalized non-assessment realization remains a target architecture.

```mermaid
flowchart LR
    X["Persistent learner state X_t"]
    Q["Requirement Q_t"]
    I["EducationalActionItem_t"]

    X -->|"PD"| Q
    Q -->|"EA"| I
```

---

## 6. Assessment as an Educational Action

For the assessment modality, \(EA_{assessment}\) first maps the transient requirement to a selected admitted reusable assessment resource. Realization then proceeds through the mathematical-family and admission boundaries:

\[
Q_t
\xrightarrow{EA_{assessment}}
J=(M,A)
\xrightarrow{Inst_M(\,M,\rho\,)}
\widetilde M_{candidate}
\xrightarrow{Adm_M}
\widetilde M
\xrightarrow{materialize\;with\;fixed\;A}
\widetilde J_t.
\]

The notation above abbreviates the fact that `Inst_M` acts on \(M\) and \(\rho\) under admitted-\(J\) authority. EA performs assessment-resource eligibility and fit over admitted learner-independent \(J\) resources and binds permitted \(\rho\); it does not absorb the authority of \(Adm_J\), \(Inst_M\), or \(Adm_M\).

```mermaid
flowchart LR
    Q["Q_t"]
    J["Admitted J = (M,A)"]
    M["M"]
    MC["M~ candidate"]
    MT["Admitted M~"]
    JT["J~_t"]

    Q -->|"EA assessment: eligibility + selection"| J
    J -->|"mathematical facet"| M
    M -->|"Inst_M with bound ρ"| MC
    MC -->|"Adm_M under J"| MT
    MT -->|"materialize with fixed A"| JT
```

`Adm_J` occurs before this runtime path: only admitted reusable \(J\) resources are eligible for EA matching.

---

## 7. Response, Observation, and Evidence

A learner-facing admitted assessment item \(\widetilde J_t\) enters the measurement path.

The learner produces a raw response

\[
A_{raw,t}.
\]

Semantic Interpretation maps the learner-facing item and raw response to a governed semantic answer:

\[
(\widetilde J_t,A_{raw,t})\xrightarrow{S}A_{sem,t}.
\]

Assessment then maps the semantic answer, under the fixed assessment semantics of \(\widetilde J_t\), to the Teaching-side observation:

\[
(A_{sem,t},\widetilde J_t)\xrightarrow{\delta}D_t.
\]

\(D_t\) is the governed Teaching-side observation object or field over conceptual \(Z_T\). Evidence projection uses the fixed binding \(B_J\) to map that observation directly to learner evidence:

\[
D_t\xrightarrow{T_{B_J}}E_t,
\]

where

\[
E_t:Z_{KR}\rightarrow\mathcal E.
\]

Thus \(B_J\) is part of the definition of the map \(T_{B_J}\); there is no need to introduce an additional `Obs(Z_T)` object in the execution notation. Because \(B_J\) is fixed before the learner answers, evidence projection preserves predetermined semantic coordinates rather than reconstructing them after assessment.

```mermaid
flowchart LR
    JT["Admitted J~_t"]
    AR["Raw answer A_raw,t"]
    AS["Semantic answer A_sem,t"]
    D["Teaching observation D_t"]
    E["Evidence field E_t over Z_KR"]

    AR -->|"S under J~_t"| AS
    JT -.->|"fixed interpretation context"| AS
    AS -->|"δ under fixed assessment semantics"| D
    JT -.->|"fixed A"| D
    D -->|"T_B_J using fixed B_J"| E
```

This keeps three semantic layers explicit:

- \(D_t\): governed assessment observation over Teaching semantics;
- \(E_t\): learner evidence field over admitted \(Z_{KR}\);
- \(X_t\): persistent learner-state field over admitted \(Z_{KR}\).

---

## 8. Learner-State Update

Evidence does not become persistent state directly. Objects are linked by explicit transition maps:

\[
E_t
\xrightarrow{U_{local}}
\widehat X_t
\xrightarrow{Admission}
Z_t
\xrightarrow{U_{long}(X_t,\cdot)}
X_{t+1}.
\]

- \(\widehat X_t\) is a session-local state proposal;
- \(Z_t\) is an admitted update;
- \(X_{t+1}\) is persistent longitudinal state.

The exact \(Z_{KR}\) coordinate is preserved through this pipeline. Evidence for one Responsibility does not automatically alter another Responsibility, and Knowledge graph structure does not imply automatic state propagation.

```mermaid
flowchart LR
    E["Evidence E_t"]
    XH["Local proposal X_hat_t"]
    Z["Admitted update Z_t"]
    XN["Persistent state X_t+1"]

    E -->|"U_local"| XH
    XH -->|"Admission"| Z
    Z -->|"U_long with prior X_t"| XN
```

---

## 9. Closed Adaptive Assessment Loop

The validated bounded assessment cycle is a sequence of semantic objects connected by maps and governed transitions:

\[
X_t
\xrightarrow{PD}
Q_t
\xrightarrow{EA_{assessment}}
J
\xrightarrow{Inst_M\;on\;(M,\rho)}
\widetilde M_{candidate}
\xrightarrow{Adm_M}
\widetilde M
\xrightarrow{materialize\;with\;A}
\widetilde J_t
\xrightarrow{learner\;interaction}
A_{raw,t}
\xrightarrow{S}
A_{sem,t}
\xrightarrow{\delta}
D_t
\xrightarrow{T_{B_J}}
E_t
\xrightarrow{U_{local}}
\widehat X_t
\xrightarrow{Admission}
Z_t
\xrightarrow{U_{long}}
X_{t+1}.
\]

`Adm_J` is the admission map that creates the reusable \(J\) before it becomes eligible for this runtime cycle.

```mermaid
flowchart LR
    X["X_t"]
    Q["Q_t"]
    J["Admitted J = (M,A)"]
    MC["M~ candidate"]
    MT["Admitted M~"]
    JT["J~_t"]
    AR["A_raw,t"]
    AS["A_sem,t"]
    D["D_t"]
    E["E_t"]
    XH["X_hat_t"]
    Z["Z_t"]
    X2["X_t+1"]

    X -->|"PD"| Q
    Q -->|"EA assessment"| J
    J -->|"Inst_M on M with ρ"| MC
    MC -->|"Adm_M"| MT
    MT -->|"materialize with fixed A"| JT
    JT -->|"learner interaction"| AR
    AR -->|"S"| AS
    AS -->|"δ"| D
    D -->|"T_B_J"| E
    E -->|"U_local"| XH
    XH -->|"Admission"| Z
    Z -->|"U_long with prior X_t"| X2
```

The architecture closes the learner experience without collapsing semantic responsibilities: state, requirement, reusable resource, realized item, response, observation, evidence, and persistent state are objects; decision, realization, interpretation, assessment, projection, admission, and state update are maps between them.

---

## 10. Architecture → Implementation Mapping

The architecture is defined by authority, not by class names. The table below shows where the current bounded implementation materializes each principal object. A conceptual object may have multiple representations or no single runtime class.

### 10.1 Principal objects

| Object | Architectural meaning | Current implementation / representation | Current maturity |
|---|---|---|---|
| \(K\) | Learner-independent Knowledge and mathematical domain semantics | `domain/knowledge/`, `services/knowledge_access/` | `validated_reusable_bounded` |
| \(R\) | Stable learner-independent, problem-independent observable Responsibility semantics | `authority/knowledge/bounded_responsibilities_v1.yaml`, `domain/teaching/model.py` | `validated_reusable_bounded` |
| \(Z_{KR}\) | Admitted subset of ambient \(K\times R\) | `authority/knowledge/bounded_responsibility_observation_v1.yaml`; exact admitted-pair records in runtime | `validated_reusable_bounded` |
| \(P\) | Reusable Teaching policy | `authority/teaching/bounded_pedagogical_decision_policy_v1.yaml` | `implemented_bounded` |
| \(Z_T\) | Conceptual Teaching observation/evidence/policy semantic space | No single runtime class; materialized through governed Teaching and assessment semantics, notably `domain/teaching/model.py` and assessment structures | conceptual architecture |
| \(J=(M,A)\) | Admitted reusable assessment template/family | `domain/assessment_item/template.py` (`AssessmentItemTemplate`) | `validated_reusable_bounded` |
| \(M\) | Knowledge-side mathematical family of an admitted assessment template | `domain/assessment_item/template.py`, `domain/assessment_item/generic_template.py` | `validated_reusable_bounded` |
| \(A\) | Fixed assessment facet and measurement semantics | Bounded \(G\) materializes the A-side primarily as `AssessmentSpecification` and Teaching structures through `domain/assessment_item/construction.py` and `domain/teaching/model.py`; admitted template structures bind the resulting assessment semantics | `validated_reusable_bounded` for the bounded substrate |
| \(B_J\) | Fixed admitted relation from Teaching observations to exact \(Z_{KR}\) coordinates | `domain/assessment_item/template.py` (`DiagnosticBinding`) | `validated_reusable_bounded` |
| \(\widetilde M\) | Admitted realized mathematical instance | `domain/assessment_item/realization.py` | `validated_reusable_bounded` |
| \(\widetilde J=(\widetilde M,A)\) | Learner-facing admitted assessment item | `domain/assessment_item/realization.py` materialization into `domain/assessment_item/model.py` representation | `validated_reusable_bounded` |
| \(Q_t\) | Transient Educational Action Requirement \((M_t^*,A_t^*)\) | `domain/educational_action/model.py` (`EducationalActionRequirement`) | bounded assessment branch validated; generic EA target-only |
| \(A_{raw,t}\) | Raw learner response | `application/learning_workflow/assessment_turn.py` boundary | bounded composition |
| \(A_{sem,t}\) | Governed semantic interpretation of the response | `domain/semantic_interpretation/`, `services/semantic_interpretation/` | `validated_reusable_bounded` |
| \(D_t\) | Governed Teaching-side assessment observation object/field over \(Z_T\) | `services/assessment/verification_projection.py`, assessment-policy and verification services | `validated_reusable_bounded` |
| \(E_t\) | Learner-evidence field over \(Z_{KR}\) | `services/evidence_projection/answer_assessment_adapter.py`, `services/evidence_projection/knowledge_element_mapping.py` | `validated_reusable_bounded` |
| \(X_t\) | Persistent learner-state field over \(Z_{KR}\) | `domain/learner/`, `domain/learner_state/`, `services/learner_state/` | `validated_reusable_bounded` for bounded exact-pair path |

### 10.2 Principal maps and transitions

| Map / transition | Architectural role | Current implementation | Current maturity |
|---|---|---|---|
| \(G\) | Author reusable \(J_{candidate}=(M,A)_{candidate}\) from explicit admitted \(K\)-\(R\) targets plus governed Teaching/authoring context, without learner-specific target reselection | `domain/assessment_item/authoring.py`; internally uses `domain/assessment_item/construction.py` and `domain/teaching/model.py` to construct the bounded A/`AssessmentSpecification` substrate | `validated_reusable_bounded` for the selected explicit-target authoring substrate |
| \(Adm_J\) | Admit reusable assessment template \(J\) | `domain/assessment_item/template.py::admit_assessment_template` | `validated_reusable_bounded` |
| \(Inst_M\) | Map mathematical family \(M\) and admitted family-local \(\rho\) to \(\widetilde M_{candidate}\), under admitted-\(J\) authority | `domain/assessment_item/realization.py`, `domain/assessment_item/generic_template.py` | `validated_reusable_bounded` |
| \(Adm_M\) | Post-instantiation admission of \(\widetilde M\) under admitted-\(J\) context | `domain/assessment_item/realization.py` | `validated_reusable_bounded` |
| \(PD\) | Sole learner-specific map from governed learner state/context to the next educational requirement \(Q_t\) | `domain/pedagogical_decision/model.py`, `services/pedagogical_decision/service.py` | `validated_reusable_bounded` for bounded exact-pair selection |
| \(EA\) | Map \(Q_t\) to a governed EducationalActionItem without learner-specific target reselection | `domain/educational_action/`, `services/educational_action/` | generic: `target_only`; assessment fixed-template branch: `validated_reusable_bounded` |
| \(S\) | Interpret raw learner work into governed semantic answer | `domain/semantic_interpretation/`, `services/semantic_interpretation/` | `validated_reusable_bounded` |
| \(\delta\) | Assess semantic answer under admitted assessment semantics and produce \(D_t\) | `services/mathematical_verification/`, `services/assessment_policy/`, `services/assessment/verification_projection.py` | `validated_reusable_bounded` |
| \(T_{B_J}\) | Map \(D_t\) directly to \(E_t\), with fixed \(B_J\) defining the Teaching-to-\(Z_{KR}\) coordinate projection | `services/evidence_projection/answer_assessment_adapter.py`, `services/evidence_projection/knowledge_element_mapping.py` | `validated_reusable_bounded` |
| \(U_{local}\) | Convert evidence into session-local state proposal | `services/learner_state/inference.py`, `domain/learner_state/proposal.py` | `validated_reusable_bounded` |
| `Admission` | Admit proposed learner-state update | `services/learner_state/admission.py`, `domain/learner/state_admission.py` | `validated_reusable_bounded` |
| \(U_{long}\) | Combine admitted update with prior persistent state | `services/learner_state/probabilistic_update.py`, `domain/learner/probabilistic_state.py` | `validated_reusable_bounded` |

The current bounded implementation of \(G\) should be read as a concrete authoring substrate for the canonical responsibility \(G:(KR^*,P,H)\rightarrow J_{candidate}\). It validates explicit admitted targets, builds target bindings, and constructs the A-side `AssessmentSpecification` candidate. It does **not** yet constitute a fully generalized authoring implementation that directly produces the final `AssessmentItemTemplateCandidate` representation for every assessment family.

### 10.3 End-to-end composition

The current bounded executable proof of the architecture is the adaptive assessment cycle implemented through `application/learning_workflow/assessment_turn.py`, with supporting domain and service modules listed above.

That bounded proof establishes the separation of responsibilities and the exact semantic flow. It does not claim production-scale registries, curriculum-wide coverage, arbitrary-family realization, calibrated production ranking, generalized non-assessment action realization, or complete Educational Action history persistence.

---

## 11. Authority and Documentation Boundary

This document is explanatory. The current architecture authority remains in `thatao72/three-twin-architecture-next`, primarily:

- `authority/architecture/three_twin.md`
- `authority/product_architecture/execution_dependency_model.yaml`
- `authority/product_architecture/assessment_semantics.yaml`
- `product/current.yaml`

This version is synchronized to architecture repository main commit `1f673497dfd93a9aa1f7519f5dd1f3055a371222`.

When implementation details and conceptual architecture differ in level of abstraction, the architectural responsibility and authority files govern the interpretation; implementation paths in the tables are traceability references, not definitions of the conceptual model.