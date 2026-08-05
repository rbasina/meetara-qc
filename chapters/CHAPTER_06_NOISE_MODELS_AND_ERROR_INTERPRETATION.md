# Chapter 06: Noise Models and Error Interpretation

## Plain-English First
Noise is unavoidable on real hardware. This chapter teaches how to measure degradation and decide whether a circuit is robust enough.

## How to Use This Chapter
Read this chapter first, then open [Notebook 06](../notebooks/intermediate/notebook-06-noise-models.ipynb) to compare ideal and noisy runs.

## Quick Terms in this Chapter
| Term | Simple meaning |
|---|---|
| Noise model | Approximation of hardware imperfections |
| Readout error | Measurement output corruption |
| Decoherence | State quality loss over time |
| Degradation | Quality drop from ideal to noisy runs |

## What You Should Remember in 30 Seconds
1. Know the core terms before running experiments.
2. Use repeated runs and clear thresholds for decisions.
3. Report both quality and cost, not quality alone.


## 1-minute overview
Noise models approximate hardware imperfections so you can test robustness before expensive hardware runs.

## Why this chapter matters
Quantum circuits that pass in ideal simulation may fail under realistic noise. Evaluation must quantify degradation.

The goal is not to remove all noise. The goal is to measure noise impact clearly and choose designs that remain useful under constraints.

## Noise concept table

| Noise factor | Practical impact | What to monitor |
|---|---|---|
| Readout error | Incorrect measurement bits | Outcome distribution drift |
| Gate error | Imperfect gate operations | Fidelity drop and leakage |
| Decoherence | State quality degrades over time | Deeper circuits degrade faster |

## Degradation metrics

| Metric | Definition | Interpretation |
|---|---|---|
| Quality drop percent | $(Q_{ideal} - Q_{noisy}) / Q_{ideal}$ | Relative robustness loss |
| Decision flip rate | Fraction of runs where pass changes to investigate | Operational stability risk |
| Leakage growth | Increase in unexpected outcomes | Error propagation indicator |

## Evaluation pattern
1. Run ideal simulation.
2. Run noisy simulation with same circuit and shots.
3. Compare key metrics (fidelity proxy, leakage, decision stability).

## Practical code pattern (noise comparison)

```python
def degradation_percent(ideal_score, noisy_score):
	if ideal_score == 0:
		return None
	return (ideal_score - noisy_score) / ideal_score
```

Use this with fixed circuit, fixed shots, and repeated runs.

## Practical lab
Notebook target: notebook-06-noise-models.ipynb

Minimum outputs:
1. Ideal vs noisy side-by-side table
2. Degradation percentage metric
3. Recommendation: acceptable, tune, or redesign

Recommended additions:
4. Repeat-run variance in noisy mode
5. Decision flip count
6. Resource impact note (depth vs degradation)

## Real-world example
Cloud hardware preparation workflows often use noise simulation to estimate whether a candidate circuit is worth executing on limited hardware budget.

This avoids spending hardware credits on fragile candidates that already fail stability checks in realistic simulation.

## Interpretation rubric

| Outcome | Typical action |
|---|---|
| Low degradation, stable decision | Candidate is ready for hardware comparison |
| Moderate degradation, unstable decision | Tune circuit depth or gate pattern |
| High degradation, repeated decision flips | Redesign before hardware run |

## Common mistakes
1. Changing shots between ideal and noisy runs.
2. Using one noisy run and calling it representative.
3. Ignoring circuit depth when diagnosing degradation.

## Checkpoint
1. Which metric best captures your circuit sensitivity to noise?
2. Why should shot count remain fixed when comparing ideal vs noisy runs?
3. What evidence is needed before escalating to hardware tests?

## Mini assignment
Take one circuit from Chapter 04 and create ideal vs noisy results across 5 repeats. Report degradation percent, leakage growth, and decision flip rate.
