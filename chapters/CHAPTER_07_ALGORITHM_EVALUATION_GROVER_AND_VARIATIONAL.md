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

## What the Algorithms Are Trying to Do
Grover's algorithm is an amplitude-amplification procedure. An oracle marks a target solution by changing its phase, then a diffusion step increases the target amplitude relative to the others. For a single marked item among $N$ candidates, the useful number of iterations is on the order of $\sqrt{N}$. Too few iterations leave the target weak; too many rotate probability away from it. Evaluation must therefore sweep iteration count rather than assume more iterations are always better.

Variational algorithms use a classical optimizer around a parameterized quantum circuit. The quantum part estimates an objective for parameters $\theta$; the classical part proposes the next $\theta$. An improving training curve is not enough: noisy objective estimates, shallow local minima, or a favorable initialization can create apparent progress that does not repeat.

### Fair algorithm comparison
Compare candidate configurations under a shared budget: same task instance, shots per objective estimate, maximum optimizer evaluations, stopping condition, and classical baseline effort. Otherwise, a better score might simply be the result of spending more evaluations.

## Grover-style evaluation workflow
1. Define marked target state and success probability metric.
2. Run multiple iteration settings.
3. Plot success probability vs iteration count.
4. Select operating point with best quality-per-cost.

For each point, report target probability, oracle calls, circuit depth, and confidence interval or repeat-run spread. This separates genuine amplification from a single favorable sample.

## Variational evaluation workflow
1. Define objective function and stopping criterion.
2. Run multiple random initializations.
3. Record best, mean, and variance of final objective.
4. Compare convergence quality against runtime and depth.

Also record whether the optimizer reached its stopping condition, exhausted its budget, or failed numerically. Failed and early-stopped runs belong in the summary because they describe reliability.

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
