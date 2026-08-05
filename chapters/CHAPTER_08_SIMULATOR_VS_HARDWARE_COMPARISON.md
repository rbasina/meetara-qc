# Chapter 08: Simulator vs Hardware Comparison Design

## Plain-English First
This chapter teaches fair simulator vs hardware comparison. You will learn how to avoid misleading conclusions using controlled protocols.

## How to Use This Chapter
Read this chapter first, then open [Notebook 08](../notebooks/intermediate/notebook-08-simulator-vs-hardware.ipynb) to compare simulator and hardware-style outputs.

## Quick Terms in this Chapter
| Term | Simple meaning |
|---|---|
| Baseline | Reference result for comparison |
| Delta | Difference between simulator and hardware metrics |
| Control variable | Setting kept identical for fairness |
| Decision consistency | How often pass/fail decision is stable |

## What You Should Remember in 30 Seconds
1. Know the core terms before running experiments.
2. Use repeated runs and clear thresholds for decisions.
3. Report both quality and cost, not quality alone.


## 1-minute overview
This chapter teaches fair comparison between simulator and hardware executions using controlled protocols.

## Why this chapter matters
Without controlled design, simulator-vs-hardware conclusions can be misleading.

The purpose is to identify practical utility under real constraints, not to chase a single impressive run.

## Fair comparison checklist

| Control variable | Requirement |
|---|---|
| Circuit definition | Keep identical |
| Shot count | Keep identical |
| Report format | Keep identical |
| Decision thresholds | Predefine before runs |
| Repeats | Use same repeat policy |

## Recommended experiment protocol
1. Freeze one circuit and one parameter set.
2. Define thresholds before execution.
3. Run simulator repeats first and record baseline spread.
4. Run hardware repeats with matching shots.
5. Compare deltas and decision consistency.
6. Record limitations and possible confounders.

## Comparison report table

| Metric | Simulator result | Hardware result | Delta | Interpretation |
|---|---|---|---|---|
| Core quality score | ... | ... | ... | ... |
| Leakage or error proxy | ... | ... | ... | ... |
| Runtime | ... | ... | ... | ... |
| Decision consistency | ... | ... | ... | ... |

## Delta interpretation guide

| Pattern observed | Likely explanation | Suggested action |
|---|---|---|
| Small quality delta, stable decisions | Hardware behaves close to model | Candidate is strong for next-stage tests |
| Moderate delta, occasional decision flips | Noise or calibration sensitivity | Tune depth and rerun controlled repeats |
| Large delta, frequent flips | Simulator assumptions not matching hardware | Revisit noise model and redesign circuit |

## Real-world example
Teams running limited cloud hardware allocations often pre-filter circuits on simulator benchmarks and only run top candidates on hardware to control cost.

This process reduces wasted credits and improves the reliability of final benchmark conclusions.

## Common mistakes
1. Comparing different shot counts across simulator and hardware.
2. Using a single hardware run as final proof.
3. Ignoring queue time and calibration context in runtime interpretation.

## Checkpoint
1. Which results are expected to diverge the most and why?
2. How do you avoid over-claiming speedup from one hardware run?
3. What minimum reproducibility evidence should accompany your comparison?

## Mini assignment
Create one simulator-vs-hardware report for a two-qubit benchmark circuit using matched shots and 3 to 5 repeats. Include delta analysis and final recommendation.
