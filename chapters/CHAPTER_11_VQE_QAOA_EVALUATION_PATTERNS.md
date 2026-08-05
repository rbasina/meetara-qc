# Chapter 11: VQE and QAOA Evaluation Patterns

## Plain-English First
Variational methods can look good by chance. This chapter teaches stable evaluation of VQE and QAOA using repeated runs and cost-aware scoring.

## How to Use This Chapter
Read this chapter first, then open [Notebook 11](../notebooks/advanced/notebook-11-vqe-qaoa-evaluation.ipynb) to evaluate the candidate runs.

## Quick Terms in this Chapter
| Term | Simple meaning |
|---|---|
| VQE | Variational method for energy-like objectives |
| QAOA | Variational method for combinatorial objectives |
| Seed sensitivity | Dependence on initialization |
| Robustness | Performance under noise and repeats |

## What You Should Remember in 30 Seconds
1. Know the core terms before running experiments.
2. Use repeated runs and clear thresholds for decisions.
3. Report both quality and cost, not quality alone.


## 1-minute overview
This chapter defines a professional evaluation framework for VQE and QAOA style hybrid algorithms.

## Why this chapter matters
Variational algorithms can appear to improve while actually overfitting noise or optimizer quirks.

This chapter teaches how to evaluate these algorithms with repeatable evidence rather than one-off best runs.

## Evaluation pattern table

| Evaluation axis | VQE focus | QAOA focus |
|---|---|---|
| Objective behavior | Energy convergence | Cost function improvement |
| Stability | Sensitivity to initialization | Sensitivity to depth and optimizer |
| Resource use | Iterations, depth, runtime | Layers, shots, runtime |
| Robustness | Performance under noise shifts | Decision consistency under repeats |

## Practical evaluation workflow
1. Choose one VQE-style or QAOA-style objective.
2. Run multiple initializations or parameter seeds.
3. Keep shot budget and runtime budget explicit.
4. Track best, mean, standard deviation, and failure cases.
5. Compare against at least one classical baseline.

## Scoring template

| Configuration | Best score | Mean score | Std dev | Runtime (s) | Quality per second | Decision |
|---|---:|---:|---:|---:|---:|---|
| config-a | ... | ... | ... | ... | ... | ... |
| config-b | ... | ... | ... | ... | ... | ... |

## Stability and robustness rules

| Signal | Interpretation | Typical action |
|---|---|---|
| High best, low mean | Unstable optimization | Increase repeats or adjust optimizer |
| Low variance, moderate score | Reliable candidate | Prefer for constrained deployments |
| Strong noise sensitivity | Fragile configuration | Reduce depth or redesign ansatz |

## Recommended reporting
1. Best score and average score across repeats.
2. Resource footprint per run.
3. Failure cases and sensitivity notes.
4. Baseline comparison against classical alternatives.

## Practical code pattern

```python
import pandas as pd

def summarize_runs(df, score_col="score", runtime_col="runtime_s"):
	out = {
		"best_score": df[score_col].max(),
		"mean_score": df[score_col].mean(),
		"std_score": df[score_col].std(),
		"mean_runtime": df[runtime_col].mean(),
	}
	out["quality_per_second"] = out["mean_score"] / out["mean_runtime"] if out["mean_runtime"] else None
	return out
```

## Real-world example
Hybrid optimization experiments in operations and scientific domains typically evaluate multiple optimizer settings and initialization seeds before selecting a deployable configuration.

Teams usually reject configurations that only succeed under narrow initialization conditions.

## Common mistakes
1. Publishing only the single best run.
2. Ignoring failed runs in averages.
3. Comparing configurations with different budget limits.

## Checkpoint
1. Which axis is most important for your target use case?
2. What sensitivity test should always be included?
3. How do you present robustness without hiding failure cases?

## Mini assignment
Run at least three parameter configurations with identical compute budget and produce a ranking using mean score, std deviation, and quality-per-second.
