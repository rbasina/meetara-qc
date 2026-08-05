# Chapter 07: Algorithm Evaluation - Grover and Variational Forms

## Plain-English First
Now we evaluate full algorithms, not only circuits. You will compare quality, stability, and cost across different algorithm settings.

## How to Use This Chapter
Read this chapter first, then open [Notebook 07](../notebooks/intermediate/notebook-07-algorithm-evaluation.ipynb) to rank candidate configurations.

## Quick Terms in this Chapter
| Term | Simple meaning |
|---|---|
| Objective | Metric the algorithm tries to optimize |
| Convergence | How scores improve across iterations |
| Stability | Consistency across repeats or seeds |
| Quality per cost | Performance normalized by resource use |

## What You Should Remember in 30 Seconds
1. Know the core terms before running experiments.
2. Use repeated runs and clear thresholds for decisions.
3. Report both quality and cost, not quality alone.


## 1-minute overview
This chapter moves from gate-level tests to algorithm-level evaluation using Grover-style and simple variational workflows.

## Why this chapter matters
Circuit correctness is necessary but not sufficient. You now evaluate whether an algorithm achieves its intended task efficiently.

Algorithm evaluation connects output quality, robustness, and resource cost in one report.

## Evaluation dimensions

| Dimension | Grover-style focus | Variational focus |
|---|---|---|
| Task success | Target-state amplification | Objective convergence quality |
| Resource cost | Circuit depth and iteration count | Iteration count and circuit depth |
| Stability | Repeatability across runs | Sensitivity to initialization |

## Grover-style evaluation workflow
1. Define marked target state and success probability metric.
2. Run multiple iteration settings.
3. Plot success probability vs iteration count.
4. Select operating point with best quality-per-cost.

## Variational evaluation workflow
1. Define objective function and stopping criterion.
2. Run multiple random initializations.
3. Record best, mean, and variance of final objective.
4. Compare convergence quality against runtime and depth.

## Practical scoring table

| Metric | Description | Why it matters |
|---|---|---|
| Best quality | Best achieved objective | Upper bound potential |
| Mean quality | Average across repeats | Typical performance |
| Quality variance | Spread across repeats | Stability and reliability |
| Cost per quality | Runtime or depth per quality gain | Practical deployability |

## Practical lab scope
1. Define a task objective.
2. Run baseline algorithm configuration.
3. Report quality, cost, and stability.

Recommended additions:
4. Add two alternative parameter settings.
5. Compare quality-per-cost across settings.
6. Flag unstable settings.

## Real-world example
Optimization pilot workflows often compare variational configurations by convergence quality per unit runtime rather than raw iteration counts alone.

In many cases, the most stable configuration wins over the best single-run score.

## Common mistakes
1. Reporting only final best score.
2. Ignoring initialization sensitivity in variational methods.
3. Comparing configurations with unequal compute budgets.

## Checkpoint
1. What is your algorithm success metric?
2. How do you normalize quality against circuit cost?
3. What failure mode appears first when noise is introduced?

## Mini assignment
Evaluate one Grover-style and one simple variational setup under equal shot and runtime budgets. Submit a comparison table with best, mean, variance, and cost-per-quality.
