# Chapter 04: Simulator Basics and First Benchmark

## Plain-English First
You will build a simple benchmark process. The goal is to compare expected vs observed behavior with clear pass or investigate rules.

## How to Use This Chapter
Read this chapter first, then open [Notebook 04](../notebooks/beginner/notebook-04-simulator-first-benchmark.ipynb) to build the first simulator benchmark report.

## Quick Terms in this Chapter
| Term | Simple meaning |
|---|---|
| Expected distribution | Target probabilities before running |
| Observed counts | Measured outcomes after running |
| Threshold | Rule for pass or investigate |
| Decision | Evaluation outcome based on metrics |

## What You Should Remember in 30 Seconds
1. Know the core terms before running experiments.
2. Use repeated runs and clear thresholds for decisions.
3. Report both quality and cost, not quality alone.


## 1-minute overview
A simulator gives a controlled environment for baseline evaluation before moving to hardware.

## Benchmark goal
Evaluate whether three simple circuits behave as expected:
1. Identity circuit
2. X-gate flip circuit
3. H-gate superposition circuit

## What a Simulator Can and Cannot Prove
An ideal simulator applies the circuit model exactly. It is the right place to test circuit construction, expected distributions, bit ordering, and scoring logic. It does not demonstrate that the same circuit will perform equally well on hardware, because real devices add gate error, readout error, limited connectivity, and time-dependent calibration effects.

Use an ideal simulator as a reference baseline. Then introduce a documented noise model in Chapter 06 before interpreting a simulator result as a hardware prediction.

### A benchmark is a precommitted decision rule
A benchmark is more than running code and looking at a chart. Before execution, define the expected distribution, metric, threshold, shots, repeats, and action for pass or investigate. This avoids choosing a threshold only after seeing a favorable result.

## Evaluation template
For each circuit, record:
1. Expected distribution
2. Observed counts
3. Deviation notes
4. Pass or investigate

## Benchmark threshold table

| Circuit | Suggested expected behavior | Suggested pass threshold |
|---|---|---|
| identity | Mostly 0 | p(0) >= 0.98 at 1024 shots |
| x_flip | Mostly 1 | p(1) >= 0.98 at 1024 shots |
| h_superposition | Near-balanced | $\lvert p(0)-p(1)\rvert \leq 0.10$ at 1024 shots |

Use these as starter thresholds for simulator-first labs.

## Practical benchmark script
```python
from qiskit import QuantumCircuit
from qiskit_aer import AerSimulator

sim = AerSimulator()
shots = 1024

circuits = {
    "identity": QuantumCircuit(1,1),
    "x_flip": QuantumCircuit(1,1),
    "h_superposition": QuantumCircuit(1,1)
}

circuits["identity"].measure(0,0)
circuits["x_flip"].x(0)
circuits["x_flip"].measure(0,0)
circuits["h_superposition"].h(0)
circuits["h_superposition"].measure(0,0)

for name, qc in circuits.items():
    counts = sim.run(qc, shots=shots).result().get_counts()
    print(name, counts)
```

## Reporting format (required)
For each circuit report this table:

| Circuit | Depth | Shots | Expected | Observed | Max deviation | Pass decision |
|---|---:|---:|---|---|---:|---|
| identity | ... | ... | ... | ... | ... | ... |
| x_flip | ... | ... | ... | ... | ... | ... |
| h_superposition | ... | ... | ... | ... | ... | ... |

## Real-world example
This mirrors early-stage benchmark practice in cloud quantum projects, where teams standardize expected distributions, pass thresholds, and report templates before running larger algorithm studies.

## Checkpoint
1. Which circuit is deterministic and why?
2. Which circuit should be approximately balanced?
3. What threshold would you use to flag unusual results?

## Expert checkpoint
1. Run each circuit 5 times and report mean plus worst-case deviation.
2. Identify which benchmark result is most sensitive to shot count.
3. State one change that improves rigor without increasing cost too much.

## Next step
Move to Chapter 05 for fidelity and error metrics.
