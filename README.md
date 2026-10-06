<div align="center">

<img src="cozy_matcha_petals_only.gif" width="100%" alt="Bakery Production Optimization">

<br>

# 🥐 Bakery Production Optimization

### Integer Linear Programming · Excel Solver · What-If Analysis

**Optimizing daily production and resource allocation under limited operational capacity.**

![Excel Solver](https://img.shields.io/badge/Excel-Solver-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![Operations Research](https://img.shields.io/badge/Operations%20Research-ILP-2F4F4F?style=for-the-badge)
![Optimization](https://img.shields.io/badge/Optimization-Profit%20Maximization-B8860B?style=for-the-badge)

</div>

---

## Overview

This project presents an **Integer Linear Programming (ILP)** model for a bakery production-planning problem.

The objective is to determine the optimal daily production mix across four products while considering limited ingredient availability, labor capacity, production limits, and integer production requirements.

The model was implemented and solved using **Microsoft Excel Solver**, followed by resource-utilization analysis and What-If scenarios to translate the optimization results into practical managerial insights.

---

## At a Glance

| Metric | Optimal Result |
|---|---:|
| 💰 Maximum Daily Profit | **1,615 SAR** |
| 📦 Total Production | **28 batches** |
| Brownies | **4 batches** |
| Cheesecakes | **1 batch** |
| Cookies | **15 batches** |
| Pistachio Cups | **8 batches** |
| ⚠️ Primary Resource Bottleneck | **Labor** |

> **Core insight:** Labor capacity is fully utilized, while additional pistachio availability alone does not improve the optimal profit.

---

## Business Problem

The bakery produces four products:

- Brownies
- Cheesecakes
- Cookies
- Pistachio Cups

Each product generates a different profit and consumes different amounts of flour, chocolate, cream, pistachio, and labor.

The production-planning decision is therefore:

> **How many batches of each product should be produced per day to maximize profit without exceeding available resources and production limits?**

### Product Data

| Product | Profit (SAR) | Flour | Chocolate | Cream | Pistachio | Labor (min) |
|---|---:|---:|---:|---:|---:|---:|
| Brownies | 55 | 1.5 | 0.8 | 0.2 | 0.0 | 25 |
| Cheesecakes | 75 | 0.5 | 0.3 | 1.0 | 0.2 | 35 |
| Cookies | 40 | 1.2 | 0.4 | 0.1 | 0.0 | 15 |
| Pistachio Cups | 90 | 0.4 | 0.6 | 0.8 | 0.7 | 30 |

### Daily Resource Capacity

| Resource | Available Capacity |
|---|---:|
| Flour | 30 |
| Chocolate | 15 |
| Cream | 14 |
| Pistachio | 7 |
| Labor | 600 min |

The model also includes a maximum total production capacity of **35 batches** and product-specific production bounds.

---

## Mathematical Model

### Decision Variables

Let:

- `x₁` = number of Brownie batches
- `x₂` = number of Cheesecake batches
- `x₃` = number of Cookie batches
- `x₄` = number of Pistachio Cup batches

All decision variables are **non-negative integers**.

### Objective Function

The objective is to maximize daily profit:

```text
Max Z = 55x₁ + 75x₂ + 40x₃ + 90x₄
```

### Resource Constraints

**Flour**

```text
1.5x₁ + 0.5x₂ + 1.2x₃ + 0.4x₄ ≤ 30
```

**Chocolate**

```text
0.8x₁ + 0.3x₂ + 0.4x₃ + 0.6x₄ ≤ 15
```

**Cream**

```text
0.2x₁ + 1.0x₂ + 0.1x₃ + 0.8x₄ ≤ 14
```

**Pistachio**

```text
0.2x₂ + 0.7x₄ ≤ 7
```

**Labor**

```text
25x₁ + 35x₂ + 15x₃ + 30x₄ ≤ 600
```

### Production Constraints

```text
x₁ ≤ 12
x₂ ≤ 10
5 ≤ x₃ ≤ 15
x₄ ≤ 8

x₁ + x₂ + x₃ + x₄ ≤ 35
```

```text
x₁, x₂, x₃, x₄ ∈ Z≥0
```

---

## Excel Solver Implementation

The mathematical model was implemented in **Microsoft Excel**.

The spreadsheet uses:

- dedicated cells for the four decision variables;
- `SUMPRODUCT` formulas for total profit and resource consumption;
- explicit daily resource capacities;
- product-specific upper and lower production bounds;
- non-negativity requirements;
- integer restrictions on all production quantities.

Excel Solver was configured to **maximize total daily profit** while satisfying all model constraints.

📁 The Excel implementation is stored in:

```text
model/SweetCraft_Bakery_Optimization.xlsx
```

---

## Optimal Production Plan

Excel Solver produced the following optimal production mix:

| Product | Optimal Batches |
|---|---:|
| Brownies | **4** |
| Cheesecakes | **1** |
| Cookies | **15** |
| Pistachio Cups | **8** |
| **Total** | **28** |

### Maximum Daily Profit

```text
1,615 SAR / day
```

This solution satisfies the model's resource, production-capacity, and integrality constraints.

---

## Resource Utilization Analysis

The optimal solution does not consume every resource completely.

| Resource | Used | Available | Slack | Utilization |
|---|---:|---:|---:|---:|
| Flour | 27.7 | 30 | 2.3 | 92.3% |
| Chocolate | 14.3 | 15 | 0.7 | 95.3% |
| Cream | 9.7 | 14 | 4.3 | 69.3% |
| Pistachio | 5.8 | 7 | 1.2 | 82.9% |
| **Labor** | **600** | **600** | **0** | **100%** |

### Bottleneck Analysis

**Labor is the primary binding resource.**

The optimal production plan consumes all **600 available labor minutes**, leaving zero labor slack.

By contrast, the ingredient constraints retain unused capacity.

Two product-level constraints are also active:

- Cookies reach their maximum of **15 batches**.
- Pistachio Cups reach their maximum of **8 batches**.

This means increasing an ingredient does not automatically translate into higher profit—the complete constraint system must be considered.

---

## What-If Analysis

Two operational scenarios were evaluated to understand which capacity expansion would create greater value.

### Scenario 1 — Increase Pistachio Availability

Pistachio availability was increased from:

```text
7 → 10
```

The optimal solution remained:

```text
Brownies        = 4
Cheesecakes     = 1
Cookies         = 15
Pistachio Cups  = 8
```

Maximum profit remained:

```text
1,615 SAR
```

**Profit improvement: 0 SAR**

### Interpretation

Additional pistachio inventory alone provides no immediate economic benefit under the current model.

The original solution already contains unused pistachio capacity, while other constraints—particularly labor and product production limits—restrict further profitable expansion.

---

### Scenario 2 — Increase Labor Capacity

Daily labor capacity was increased from:

```text
600 → 720 minutes
```

The optimized production mix changed to:

| Product | Base Model | Labor Scenario |
|---|---:|---:|
| Brownies | 4 | **3** |
| Cheesecakes | 1 | **5** |
| Cookies | 15 | **15** |
| Pistachio Cups | 8 | **8** |

Maximum daily profit increased from:

```text
1,615 SAR → 1,860 SAR
```

### Impact

```text
Profit Increase = 245 SAR/day
Percentage Increase ≈ 15.2%
```

Labor usage under this scenario is:

```text
715 / 720 minutes
```

leaving only **5 minutes of unused labor capacity**.

---

## Scenario Comparison

| Scenario | Optimal Mix (B, C, Co, P) | Profit | Change |
|---|---|---:|---:|
| Base Model | (4, 1, 15, 8) | **1,615 SAR** | — |
| Pistachio: 7 → 10 | (4, 1, 15, 8) | **1,615 SAR** | **0 SAR** |
| Labor: 600 → 720 | (3, 5, 15, 8) | **1,860 SAR** | **+245 SAR** |

---

## Managerial Recommendation

The What-If analysis indicates that **expanding labor capacity has substantially greater value than purchasing additional pistachio inventory** under the current operating conditions.

An additional 120 minutes of daily labor capacity increases modeled daily profit by **245 SAR**, approximately **15.2%**, while increasing pistachio availability from 7 to 10 produces no improvement.

Therefore, if the cost of obtaining additional labor capacity is economically justified relative to the expected profit improvement, labor expansion should be prioritized.

Further capacity increases should still be re-optimized rather than assumed to provide the same benefit, because other resource constraints and product production bounds may become binding.

---

## Key Insights

- The optimal base production plan generates **1,615 SAR per day**.
- Only **28 of the allowed 35 batches** are produced; therefore, the total batch limit is not the primary restriction.
- Labor operates at **100% utilization** and is the main resource bottleneck.
- Flour and chocolate operate near capacity but retain positive slack.
- Cream and pistachio have greater unused capacity.
- Increasing pistachio availability alone creates **no additional profit**.
- Increasing labor capacity to 720 minutes raises modeled profit to **1,860 SAR**.
- The results demonstrate why capacity-expansion decisions should be based on the complete optimization model rather than on individual resource availability.

---

## Optimization Workflow

```text
Business Problem
       ↓
Decision Variables
       ↓
Objective Function
       ↓
Resource & Production Constraints
       ↓
Integer Linear Programming Model
       ↓
Excel Solver
       ↓
Optimal Production Mix
       ↓
Resource Utilization Analysis
       ↓
What-If Analysis
       ↓
Managerial Recommendation
```

---

## Tools & Concepts

### Tools

- Microsoft Excel
- Excel Solver

### Concepts Applied

- Operations Research
- Integer Linear Programming
- Mathematical Modeling
- Profit Maximization
- Resource Allocation
- Decision Variables
- Objective Functions
- Capacity Constraints
- Binding & Non-Binding Constraints
- Slack Analysis
- Bottleneck Analysis
- What-If Analysis
- Decision Support

---

## What I Practiced

This project strengthened my ability to translate an operational business problem into a structured mathematical model, implement that model in Excel Solver, validate an optimal integer solution, analyze resource utilization, evaluate alternative capacity scenarios, and convert quantitative results into practical managerial recommendations.

Rather than focusing only on the optimal objective value, the analysis examines **why the solution is optimal, which resources restrict performance, and which operational changes create measurable value**.

---

## Model Transparency

This repository documents an **Operations Research case study** developed for mathematical-modeling and optimization practice.

SweetCraft Bakery is used as the scenario context for the model and should not be interpreted as a real consulting client or commercial engagement.

### Solver Report Note

The original Solver-generated Answer Report contains a cell-reference discrepancy for the flour constraint: the report references `B13`, while the worksheet's calculated **Total Flour Used** value is stored in `C13`.

The base worksheet values are:

```text
Flour Used      = 27.7
Flour Available = 30
Slack           = 2.3
```

The Solver-generated report is preserved as originally produced rather than manually altered.

Because this is an **integer optimization model**, no LP-only sensitivity metrics such as shadow prices or reduced costs are claimed from the integer solution.

---

## Repository Structure

```text
-Bakery-Production-Optimization/
│
├── README.md
├── .gitignore
│
├── model/
│   └── SweetCraft_Bakery_Optimization.xlsx
│
├── docs/
│   └── model-notes.md
│
└── assets/
    └── README.md
```

---

<div align="center">

### From mathematical formulation to operational decision-making.

**Operations Research · Optimization · Business Analytics**

</div>
