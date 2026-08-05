# Appendix A: Benchmarking Standards

Use this appendix as the default evaluation policy for beginner and intermediate labs.

## 1. Core reporting template

| Field | Required value |
|---|---|
| Circuit name | Unique identifier |
| Circuit depth | Report integer depth |
| Qubit count | Report integer count |
| Shots | Report exact shot count |
| Backend | Simulator or hardware name |
| Expected distribution | Explicit probability targets |
| Observed distribution | Measured frequencies |
| Deviation metric | Absolute error per outcome and max error |
| Confidence estimate | 95 percent interval or repeated-run variance |
| Pass decision | Pass or investigate |

## 2. Suggested threshold table (beginner labs)

| Scenario | Suggested pass threshold |
|---|---|
| Deterministic output circuits (for example X then measure) | Expected outcome frequency >= 0.98 at 1024 shots |
| Balanced superposition circuits (for example H then measure) | Absolute difference between p(0) and p(1) <= 0.10 at 1024 shots |
| Bell-state correlation sanity check | p(00) + p(11) >= 0.90 on simulator at 1024 shots |
| Repeated-run stability check | Across 5 repeats, max deviation from expected <= 0.08 |

Note: These are starter thresholds for educational labs. Tighten or relax thresholds based on backend noise and chapter goals.

## 3. Statistical significance quick guide

| Method | When to use | Practical rule |
|---|---|---|
| Binomial confidence interval | Single-bit outcomes | Report 95 percent interval for key outcomes |
| Repeated-run variance | Same circuit, multiple runs | Run at least 5 repeats and report mean plus spread |
| Baseline comparison delta | Quantum vs classical result quality | Report absolute quality delta with same budget constraints |

## 4. Cost and runtime discipline

| Lever | Recommended default |
|---|---|
| Shot count in beginner labs | 512 to 2048 |
| Number of repeats | 3 to 5 |
| Hardware runs | Optional until comparison chapters |
| Claim policy | No speedup or quality claim without baseline and significance context |

## 5. Real-world benchmarking mindset
1. Always compare against a tuned classical baseline, not a weak baseline.
2. Keep methodology reproducible so other learners can verify your claim.
3. Treat one successful run as anecdote; treat repeated validated runs as evidence.
