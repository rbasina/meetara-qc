# Chapter 10: Reproducible Benchmark Methodology

## Plain-English First
Reproducibility turns experiments into evidence. This chapter gives you a repeatable method so others can validate your benchmark claims.

## How to Use This Chapter
Read this chapter first, then open [Notebook 10](../notebooks/advanced/notebook-10-reproducible-benchmarks.ipynb) to build the reproducibility bundle.

## Quick Terms in this Chapter
| Term | Simple meaning |
|---|---|
| Reproducibility | Ability to recreate same result |
| Protocol | Predefined run and scoring procedure |
| Artifact | Saved file proving experiment details |
| Drift | Unexpected change across reruns |

## What You Should Remember in 30 Seconds
1. Know the core terms before running experiments.
2. Use repeated runs and clear thresholds for decisions.
3. Report both quality and cost, not quality alone.


## 1-minute overview
Reproducibility turns benchmark results from anecdote into evidence.

## Why this chapter matters
Without reproducibility, performance claims cannot be trusted or compared.

Reproducibility is the difference between a demo and evidence.

## Reproducibility checklist

| Item | Requirement |
|---|---|
| Environment | Pin package versions |
| Inputs | Save circuit definitions and parameters |
| Randomness | Set and report seeds when supported |
| Protocol | Document shot counts, repeats, and thresholds |
| Output | Store raw counts and summary tables |

## Minimum artifact package

| Artifact | Example file |
|---|---|
| Run configuration | `artifacts/run_config.json` |
| Raw counts | `artifacts/raw_counts.csv` |
| Summary table | `artifacts/summary_metrics.csv` |
| Notebook or script | `notebooks/...` or `scripts/...` |
| Environment snapshot | `requirements.txt` and Python version note |

## Protocol-first rule
Define this before execution:
1. Success metric and threshold.
2. Shot count and number of repeats.
3. Candidate configurations to test.
4. Decision rule for pass or investigate.

Changing these after looking at outcomes introduces bias.

## Reproducible Does Not Always Mean Identical
For stochastic algorithms and quantum hardware, a correct rerun may not reproduce every count exactly. The reproducible object is the protocol: the same environment, inputs, configuration, analysis, and decision rule should produce results within a declared tolerance.

Define the tolerance before rerunning. For example, a simulator benchmark may require an identical decision plus a TVD change no larger than $0.02$, while a hardware study may permit a wider range due to calibration drift. A failed reproduction is evidence, not an inconvenience: determine whether the cause is an environment change, protocol drift, sampling variation, or device change.

### Provenance checklist
Save these fields with every benchmark run:
1. Git commit or source version identifier.
2. Python, package, and backend versions.
3. Circuit source, transpilation settings, and random seeds where supported.
4. Start time, backend or simulator configuration, shots, and repeat index.
5. Raw outputs before aggregation.

## Practical workflow
1. Define benchmark protocol before execution.
2. Run repeated trials with fixed settings.
3. Save artifacts and summary report.
4. Re-run on fresh environment for verification.

For hardware work, a fresh environment alone is insufficient. Repeat at a different time and compare against recorded backend calibration information.

## Reproducibility validation checklist

| Check | Pass condition |
|---|---|
| Environment reproduction | Fresh setup runs successfully |
| Data consistency | Raw counts align with summary metrics |
| Protocol consistency | Threshold and repeat policy unchanged |
| Decision reproducibility | Same protocol yields same decision class |

## Real-world example
Research and industry benchmark teams commonly require run sheets and artifact logs before accepting performance claims for internal review.

In practice, teams often reject strong claims that cannot be rerun in a clean environment within a defined tolerance.

## Common mistakes
1. Saving only charts and not raw data.
2. Omitting shot counts or random seed details.
3. Mixing results from changed protocols in one summary.

## Checkpoint
1. Which artifact is most likely to be missing in beginner reports?
2. What minimum information allows another learner to replicate your result?
3. How would you detect accidental environment drift?

## Mini assignment
Create a reproducibility bundle for one Chapter 08 comparison experiment, then validate it in a clean environment and record any drift.
