# Chapter 01: Qubits and State Intuition

## Plain-English First
A qubit is like a flexible information unit. In this chapter you will see how one qubit can produce different outcomes and why repeated measurement matters.

## How to Use This Chapter
Read this chapter first, then open [Notebook 01](../notebooks/beginner/notebook-01-qubits-and-intuition.ipynb) to practice superposition and measurement with code.

## Quick Terms in this Chapter
| Term | Simple meaning |
|---|---|
| Qubit | Basic quantum information unit |
| Superposition | Combination of basis states before measurement |
| Measurement | Process that returns classical output |
| Shots | Number of repeated runs |

## What You Should Remember in 30 Seconds
1. Know the core terms before running experiments.
2. Use repeated runs and clear thresholds for decisions.
3. Report both quality and cost, not quality alone.


## 1-minute overview
A qubit is the basic unit of quantum information. Unlike a classical bit that is either 0 or 1, a qubit can be in a superposition of both states.

## Core concepts
1. Basis states: |0> and |1>
2. State vector form: alpha|0> + beta|1>
3. Probability rule: |alpha|^2 + |beta|^2 = 1
4. Measurement collapses superposition to one basis state

## Why this matters for evaluation
Evaluation starts with understanding expected probabilities. If a circuit should produce 50/50 outcomes but gives 80/20 repeatedly, your circuit quality is likely poor or noisy.

## Practical example
Goal: create a qubit in superposition and measure outcomes.

```python
from qiskit import QuantumCircuit
from qiskit_aer import AerSimulator

qc = QuantumCircuit(1, 1)
qc.h(0)             # put qubit in equal superposition
qc.measure(0, 0)

sim = AerSimulator()
job = sim.run(qc, shots=1024)
counts = job.result().get_counts()
print(counts)
```

Expected behavior: counts close to 50 percent 0 and 50 percent 1.

## Evaluation table

| Metric | Target | Example pass rule |
|---|---|---|
| p(0) and p(1) balance | Near 0.5 each | At 1024 shots, |p(0)-p(1)| <= 0.10 |
| Repeatability | Stable across repeats | Run 5 repeats, max deviation <= 0.08 |
| Cost discipline | Reasonable shot budget | Start at 512, then 1024 or 2048 if needed |

## Real-world example
In quantum random number generation workflows, balanced outcome behavior is a first sanity check before any downstream usage. If the observed distribution is strongly biased without explanation, the setup requires investigation.

## Expert checkpoint
1. Record 5 repeated runs at 1024 shots and report mean p(1).
2. Report the observed range and whether it passes your threshold.
3. Explain whether your pass decision is based on one run or repeated evidence.

## Checkpoint
1. Explain in your own words why repeated measurement is needed.
2. What happens if you remove the H gate?
3. Run with shots 128 and 4096, then compare stability.

## Common mistakes
1. Assuming one measurement run is enough.
2. Confusing amplitude with probability.
3. Ignoring shot count when interpreting results.
4. Making claims without documenting thresholds and repeat count.

## Next chapter
Gates and circuits: how we control qubit states deliberately.
