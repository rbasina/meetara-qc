# Chapter 02: Gates and Circuits

## Plain-English First
A circuit is a sequence of steps. Gates are individual steps that change qubit states. This chapter shows how simple gate sequences create predictable outcomes.

## How to Use This Chapter
Read this chapter first, then open [Notebook 02](../notebooks/beginner/notebook-02-gates-and-circuits.ipynb) to run the gate and circuit exercises.

## Quick Terms in this Chapter
| Term | Simple meaning |
|---|---|
| Gate | Operation that changes a qubit state |
| Circuit | Ordered set of gates plus measurement |
| Entanglement | Correlation that links qubits |
| Depth | Number of sequential operation layers |

## What You Should Remember in 30 Seconds
1. Know the core terms before running experiments.
2. Use repeated runs and clear thresholds for decisions.
3. Report both quality and cost, not quality alone.


## 1-minute overview
Quantum gates transform qubit states. A quantum circuit is an ordered set of gates plus measurement.

## Core gates in this chapter
1. X gate: flips |0> to |1>
2. H gate: creates superposition
3. Z gate: phase flip (important in interference patterns)
4. CX gate: two-qubit entangling gate

## Why this matters for evaluation
Evaluation often checks whether a known gate sequence produces expected output distributions. Gate-level mistakes are a major source of benchmark failure.

## Practical example A: deterministic flip
```python
from qiskit import QuantumCircuit
from qiskit_aer import AerSimulator

qc = QuantumCircuit(1, 1)
qc.x(0)
qc.measure(0, 0)

sim = AerSimulator()
counts = sim.run(qc, shots=512).result().get_counts()
print(counts)
```
Expected result: mostly or entirely 1.

## Practical example B: Bell state circuit
```python
from qiskit import QuantumCircuit
from qiskit_aer import AerSimulator

qc = QuantumCircuit(2, 2)
qc.h(0)
qc.cx(0, 1)
qc.measure([0, 1], [0, 1])

sim = AerSimulator()
counts = sim.run(qc, shots=1024).result().get_counts()
print(counts)
```
Expected behavior: dominant outcomes are 00 and 11.

## Evaluation table

| Circuit | Expected behavior | Suggested beginner threshold |
|---|---|---|
| X flip | Almost all results are 1 | p(1) >= 0.98 at 512 to 1024 shots |
| Bell state | 00 and 11 dominate | p(00) + p(11) >= 0.90 on simulator |
| Bell state leakage | 01 and 10 remain low | p(01) + p(10) <= 0.10 on simulator |

## Depth and cost note
When two circuits solve the same toy task, prefer the lower-depth variant for better noise resilience in later hardware experiments.

## Real-world example
Entanglement sanity checks are used in quantum communication and hardware calibration workflows where verifying correlated outcomes is a baseline quality signal.

## Expert checkpoint
1. Report circuit depth for Example A and B.
2. Repeat the Bell circuit 5 times and report p(00)+p(11) mean and min.
3. If leakage exceeds threshold, list two possible root causes.

## Checkpoint
1. Why does CX need a control and target qubit?
2. What output would you expect if H is removed from qubit 0 in the Bell circuit?
3. Modify the circuit and test your hypothesis.

## Next chapter
Measurement and probabilities: how to read circuit outcomes rigorously.
