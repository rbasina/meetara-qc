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

## Visual Learning Map
```mermaid
flowchart LR
	A[Freeze circuit and protocol] --> B[Simulator repeats]
	A --> C[Hardware repeats]
	B --> D[Shared metrics]
	C --> D
	D --> E[Quality and resource delta]
	E --> F[Bounded comparison claim]
```

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

## Separate Three Different Questions
Simulator-versus-hardware studies often mix three questions that need different measurements:
1. **Does the circuit behave correctly?** Compare output quality against the expected distribution.
2. **Does the simulator predict device behavior?** Compare simulator and hardware distributions using the same metric.
3. **Is the hardware workflow practically useful?** Compare end-to-end quality, execution time, queue time, and cost against a classical baseline.

A low simulator-hardware delta does not establish a quantum speedup. Likewise, a long hardware queue does not mean the quantum circuit itself is slow. Keep compile time, queue time, execution time, and post-processing time as separate fields.

### Hardware context belongs in the record
For each hardware run, record backend name, calibration timestamp if available, qubit layout or transpilation settings, measurement mitigation status, and run time. Device calibration changes can explain differences between otherwise identical trials.

## Recommended experiment protocol
1. Freeze one circuit and one parameter set.
2. Define thresholds before execution.
3. Run simulator repeats first and record baseline spread.
4. Run hardware repeats with matching shots.
5. Compare deltas and decision consistency.
6. Record limitations and possible confounders.

If a noise-model simulator is used, state whether it is ideal, generic, or derived from a specific backend calibration. Do not compare an ideal simulator directly to hardware and call the difference “hardware error” without acknowledging the modeling gap.

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
