# Model Notes

This document records the verified model inputs, optimal solution, resource utilization, and What-If results used in the Bakery Production Optimization case study.

## Base Model Capacities

| Resource | Capacity |
|---|---:|
| Flour | 30 |
| Chocolate | 15 |
| Cream | 14 |
| Pistachio | 7 |
| Labor | 600 minutes |
| Maximum Total Production | 35 batches |

## Optimal Solution

| Product | Optimal Batches |
|---|---:|
| Brownies | 4 |
| Cheesecakes | 1 |
| Cookies | 15 |
| Pistachio Cups | 8 |
| **Total Production** | **28** |

**Maximum Daily Profit: 1,615 SAR**

## Resource Utilization

| Resource | Used | Available | Slack | Utilization |
|---|---:|---:|---:|---:|
| Flour | 27.7 | 30 | 2.3 | 92.3% |
| Chocolate | 14.3 | 15 | 0.7 | 95.3% |
| Cream | 9.7 | 14 | 4.3 | 69.3% |
| Pistachio | 5.8 | 7 | 1.2 | 82.9% |
| Labor | 600 | 600 | 0 | 100% |

Labor is the primary binding resource in the base solution.

Cookies also reach their upper production bound of 15 batches, while Pistachio Cups reach their upper bound of 8 batches.

## What-If Scenario 1 — Pistachio Capacity

Pistachio availability was increased from 7 to 10.

The optimal solution remained:

- Brownies: 4
- Cheesecakes: 1
- Cookies: 15
- Pistachio Cups: 8

**Maximum Daily Profit: 1,615 SAR**

**Profit Improvement: 0 SAR**

Increasing pistachio capacity alone therefore does not improve the objective value under the current constraint structure.

## What-If Scenario 2 — Labor Capacity

Labor capacity was increased from 600 to 720 minutes.

The new optimal production mix was:

- Brownies: 3
- Cheesecakes: 5
- Cookies: 15
- Pistachio Cups: 8

**Maximum Daily Profit: 1,860 SAR**

**Profit Improvement: 245 SAR/day (~15.2%)**

Labor utilization in this scenario is:

**715 / 720 minutes**

leaving 5 minutes of unused labor capacity.

## Solver Report Transparency Note

The original Excel Solver-generated Answer Report contains a cell-reference discrepancy for the flour constraint.

The report references `B13`, while the worksheet's calculated **Total Flour Used** value is located in `C13`.

The verified base worksheet values are:

- Flour Used: 27.7
- Flour Available: 30
- Flour Slack: 2.3

The original Solver-generated report should be preserved without manual alteration.

Because the model uses integer decision variables, LP-only sensitivity measures such as **shadow prices** and **reduced costs** are not claimed from the integer solution.

## Reproducibility

All values documented here are derived from the Excel optimization model and the verified What-If scenarios used in this repository.

No additional optimization results or sensitivity metrics have been fabricated or inferred beyond the solved model outputs.
