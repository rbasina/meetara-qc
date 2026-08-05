# Chapter 05: Fidelity and Quality Metrics

## Plain-English First
This chapter turns observations into scores. You will learn simple quality metrics so you can compare results objectively.

## How to Use This Chapter
Read this chapter first, then open [Notebook 05](../notebooks/intermediate/notebook-05-fidelity-and-metrics.ipynb) to compute the metrics in practice.

## Quick Terms in this Chapter
| Term | Simple meaning |
|---|---|
| Fidelity proxy | Score of similarity to expected behavior |
| TVD | Distance between expected and observed distributions |
| Overlap | Shared probability mass between distributions |
| Quality score | Numeric indicator of result quality |

## What You Should Remember in 30 Seconds
1. Know the core terms before running experiments.
2. Use repeated runs and clear thresholds for decisions.
3. Report both quality and cost, not quality alone.


## 1-minute overview
Fidelity measures how close your observed quantum state or outcome distribution is to the expected target.

## Why this chapter matters
After simulator sanity checks, evaluation needs a formal quality score instead of only visual inspection.

If you cannot quantify quality, you cannot compare circuits, tune designs, or justify hardware runs.

## Core concepts table

| Concept | Meaning | Practical use |
|---|---|---|
| State fidelity | Similarity between expected and observed states | Quality check for state-preparation tasks |
| Distribution distance | Gap between expected and measured outcome distributions | Useful when working with counts |
| Threshold decision | A rule that marks pass or investigate | Makes benchmarking consistent |

## Practical metrics you can compute from counts

When you only have measurement counts, start with these:

| Metric | Formula | Range | Best value |
|---|---|---|---|
| Total variation distance (TVD) | $\frac{1}{2}\sum_i |p_i-q_i|$ | $[0,1]$ | 0 |
| L1 distance | $\sum_i |p_i-q_i|$ | $[0,2]$ | 0 |
| Fidelity proxy (distribution overlap) | $\sum_i \sqrt{p_i q_i}$ | $[0,1]$ | 1 |

Where $p$ is expected distribution and $q$ is observed distribution.

## Suggested benchmark policy

| Scenario | Suggested starter threshold |
|---|---|
| Simulator reference lab | Fidelity >= 0.98 |
| Noisy simulation lab | Fidelity >= 0.90 |
| Early hardware lab | Task-specific baseline and tolerance |

## Step-by-step workflow
1. Define expected distribution before you run.
2. Execute circuit with fixed shots and repeats.
3. Convert counts to probabilities.
4. Compute at least one distance metric and one overlap metric.
5. Compare against predefined threshold.
6. Mark pass or investigate.

## Practical code example (counts to quality)

```python
import math

def normalize_counts(counts, shots):
	return {k: v / shots for k, v in counts.items()}

def tvd(expected, observed):
	keys = set(expected) | set(observed)
	return 0.5 * sum(abs(expected.get(k, 0) - observed.get(k, 0)) for k in keys)

def overlap_fidelity(expected, observed):
	keys = set(expected) | set(observed)
	return sum(math.sqrt(expected.get(k, 0) * observed.get(k, 0)) for k in keys)
```

## Practical lab
Notebook target: notebook-05-fidelity-and-metrics.ipynb

Minimum outputs:
1. Expected vs observed distribution table
2. One fidelity-like score
3. Pass or investigate decision

Recommended additions:
4. TVD score
5. Repeated-run mean and spread
6. Decision confidence note

## Real-world example
In quantum chemistry toy workflows, fidelity-like quality checks are used before interpreting energy estimates to avoid trusting noisy artifacts.

In practice, teams reject parameter settings that produce unstable quality metrics across repeats, even if one run looks excellent.

## Common mistakes
1. Defining thresholds after seeing the result.
2. Comparing runs with different shot counts as if they are equivalent.
3. Reporting only best-case runs and hiding variability.

## Checkpoint
1. Why is threshold definition required before running experiments?
2. When is distribution distance more practical than state fidelity?
3. What changes in threshold policy when moving from simulator to hardware?

## Mini assignment
Use one circuit from Chapter 04 and produce a table with expected distribution, observed distribution, TVD, overlap fidelity, and pass or investigate decision across 5 repeated runs.

## Reference Materials
Use these clickable sources when you want the original metric definitions and related guidance:
1. [Qiskit Learn](https://qiskit.qotlabs.org/learn) - practical quantum computing lessons.
2. [Qiskit API Reference](https://qiskit.qotlabs.org/docs/api/qiskit/) - circuit and result object definitions.
3. [IBM Quantum Documentation](https://docs.quantum.ibm.com/) - platform background and execution concepts.
4. [NIST Probability and Statistics Resources](https://www.nist.gov/itl/sed/statistical-engineering-division) - useful background for uncertainty and repeatability.
