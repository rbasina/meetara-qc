# Real-World Examples Playbook

Use this playbook to ground chapter concepts in practical, decision-focused examples.

## How to use this file
1. Pick one example per chapter as a discussion anchor.
2. Map the example to one metric, one threshold, and one pass or investigate rule.
3. Reuse the same example in the chapter notebook so concept and practice stay aligned.

## Example 1: Route Optimization Under Constraints

| Item | Details |
|---|---|
| Domain | Logistics and delivery planning |
| Core problem | Large constrained route combinations become expensive to search |
| Quantum role | Hybrid candidate generation using variational or sampling-style subroutines |
| Baseline | Classical heuristic solver with fixed runtime budget |
| Key metrics | Objective score, runtime, decision consistency across repeats |
| Practical takeaway | Choose the configuration with best quality-per-cost, not best one-off score |

Chapter fit:
1. Chapter 07 algorithm evaluation
2. Chapter 09 resource metrics
3. Chapter 12 capstone reporting

## Example 2: Portfolio Rebalancing with Risk Constraints

| Item | Details |
|---|---|
| Domain | Finance decision support |
| Core problem | Constraint-heavy optimization with competing objectives |
| Quantum role | QAOA-style candidate scoring with classical refinement |
| Baseline | Classical mixed-integer optimization under equal budget |
| Key metrics | Feasible solution rate, risk-adjusted score, runtime |
| Practical takeaway | Report feasibility stability, not only best objective value |

Chapter fit:
1. Chapter 08 simulator vs hardware comparison
2. Chapter 11 VQE and QAOA evaluation patterns

## Example 3: Molecular Feature Estimation for Drug Discovery

| Item | Details |
|---|---|
| Domain | Scientific AI and molecular modeling |
| Core problem | Expensive high-fidelity simulation for molecular properties |
| Quantum role | VQE-like routines to estimate selected properties |
| Baseline | Classical approximation workflow |
| Key metrics | Property estimation error, runtime, reproducibility across runs |
| Practical takeaway | Reject unstable high-score runs that fail reproducibility checks |

Chapter fit:
1. Chapter 05 fidelity and quality metrics
2. Chapter 10 reproducible benchmark methods

## Example 4: Quantum Kernel Classification (Small-Scale)

| Item | Details |
|---|---|
| Domain | Machine learning experimentation |
| Core problem | Complex nonlinear separability on selected datasets |
| Quantum role | Quantum feature map with classical classifier |
| Baseline | Tuned classical kernel model |
| Key metrics | Validation score, variance across seeds, training and inference time |
| Practical takeaway | Compare mean and spread, not only top run |

Chapter fit:
1. Chapter 06 noise and error interpretation
2. Chapter 07 algorithm evaluation

## Example 5: Hardware Queue Budget Decision

| Item | Details |
|---|---|
| Domain | Practical cloud hardware usage |
| Core problem | Limited hardware credits and queue windows |
| Quantum role | Filter candidate circuits by simulator-first robustness before hardware |
| Baseline | Random hardware trial strategy |
| Key metrics | Hardware pass rate, cost per successful run, cycle time |
| Practical takeaway | Simulator pre-filtering improves cost efficiency and reliability |

Chapter fit:
1. Chapter 04 first benchmark discipline
2. Chapter 08 simulator vs hardware comparison

## Example 6: Academic Lab Benchmark Reproducibility Audit

| Item | Details |
|---|---|
| Domain | Research quality control |
| Core problem | Results cannot be trusted without rerun stability |
| Quantum role | Structured run protocol and artifact logging |
| Baseline | Informal notebook-only reporting |
| Key metrics | Re-run drift, decision consistency, artifact completeness |
| Practical takeaway | Publish evidence bundle with raw data and run configuration |

Chapter fit:
1. Chapter 10 reproducibility methods
2. Chapter 12 capstone quality standard

## Notebook integration template

Use this checklist in any notebook:
1. Scenario statement in one paragraph.
2. Baseline definition under same budget.
3. Metrics table with thresholds.
4. Repeated-run summary.
5. Final pass or investigate decision.
6. Limitations note.

## Recommended first three examples for beginners
1. Hardware Queue Budget Decision
2. Route Optimization Under Constraints
3. Academic Lab Benchmark Reproducibility Audit
