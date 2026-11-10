# AI Semiconductor Supply Chain Analytics & Packaging Backlog Prediction

**Python | Tableau | Predictive Analytics | Regression Models | Supply Chain Risk | Semiconductor Manufacturing**

> **Project objective:** Identify semiconductor production bottlenecks, assess facility-level operational risk, predict advanced packaging backlogs, and help operations managers prioritize capacity interventions.

**Interactive Tableau dashboards:** [Descriptive supply chain performance & risk dashboard](https://public.tableau.com/views/AISemiconductorSupplyChain-OperationsOverview/Dashboard1-AISemiconductorSupplyChain-OperationsOverview?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link) · [Predictive packaging backlog dashboard](https://public.tableau.com/views/AISemiconductorPackagingBacklogPredictionOperationalPrioritization/Dashboard2-PredictiveBacklogAnalysis?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

*Note: This dashboard utilizes a simulated dataset to model high-end semiconductor packaging constraints, capacity metrics, and operational workflows for demonstration purposes.*

---

## Executive Summary

The AI semiconductor supply chain faces complex capacity constraints across wafer fabrication, advanced packaging, and high-bandwidth memory (HBM) integration. Even when wafer fabrication capacity is available, downstream packaging queues can delay the delivery of finished accelerators.

This project combines **descriptive and diagnostic supply chain analytics** with **predictive regression modeling** to evaluate manufacturing performance and anticipate advanced packaging congestion. Two Tableau dashboards translate the analysis into facility-level insights:

- **Dashboard 1 - Supply Chain Performance & Risk:** Examines wafer capacity, utilization, yield, packaging queues, supply chain vulnerability, and operational prioritization.
- **Dashboard 2 - Predictive Packaging Backlog & Capacity:** Presents model-predicted packaging backlog, highlights facilities with elevated forecasted delays, and supports capacity planning and prioritization.

The question we are answering is: **Where are the biggest production bottlenecks and supply chain risks, which facilities require attention today, and which may face packaging delays based on predicted backlog?**

## Project Background & Business Context

Semiconductor supply chains are interconnected. Wafer throughput, process nodes, accelerator demand, memory specifications, and advanced packaging capacity can each affect the pace at which AI chips reach customers.

Operations managers need answers to questions such as:

- Which facilities operate near their available wafer capacity?
- Where are advanced packaging queues longest?
- How do manufacturing characteristics relate to packaging backlog?
- Which facilities exhibit the greatest combined operational constraints and supply chain vulnerability?
- Can regression models estimate packaging backlog for facilities with different production characteristics?
- Where should managers focus investigation, capacity planning, or supplier coordination?

### Business Objectives

1. Monitor semiconductor manufacturing capacity, utilization, and yield.
2. Identify existing packaging bottlenecks and supply chain risk exposure.
3. Develop a facility-prioritization framework using operational indicators.
4. Train and evaluate regression models for **`packaging_backlog_weeks`**.
5. Visualize predicted delays and facility-level intervention priorities in Tableau.
6. Convert technical findings into actionable operational recommendations.

## Methodology

### Data Understanding and Preparation

### [Dashboard 1](https://public.tableau.com/views/AISemiconductorSupplyChain-OperationsOverview/Dashboard1-AISemiconductorSupplyChain-OperationsOverview?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link): Supply Chain Performance & Risk Analysis

**Business question:** *Where are current production bottlenecks and supply chain vulnerabilities, and which facilities should operations managers prioritize?*

The first dashboard examines:

- **Capacity utilization:** How heavily wafer manufacturing capacity is being used.
- **Production performance:** Wafer capacity and die yield across facilities.
- **Packaging congestion:** Observed backlog and queue patterns.
- **Supply chain vulnerability:** Facility-level exposure to broader disruption risks.
- **Priority classification:** Operational indicators combined to flag facilities requiring review.

**Operational value:** Helps managers understand **what is happening now** and identify the facilities where existing capacity constraints and risk indicators warrant attention.

### Predictive Modeling: Packaging Backlog

**Prediction target:** `packaging_backlog_weeks` (continuous, measured in weeks).

The predictive task estimates packaging queue duration using manufacturing and product characteristics, including wafer capacity, accelerator family, HBM specification, and process node.

**Regression approaches explored:**

| Model | Role |
|---|---|
| LightGBM Regression | Gradient-boosting decision trees for nonlinear relationships |
| CatBoost Regression | Gradient boosting suited to datasets with categorical features |
| Bayesian Ridge Regression | Linear benchmark for evaluating gains over a simpler model |

**Evaluation framework:**

- **MAE (Mean Absolute Error):** Average absolute prediction error, in weeks.
- **RMSE (Root Mean Squared Error):** Penalizes larger prediction errors, in weeks.
- **R² (Coefficient of Determination):** Measures the proportion of target variance explained on the evaluation data.

| Model | MAE (weeks) | RMSE (weeks) | R² |
|---|---:|---:|---:|
| LightGBM | 3.6084 | 4.7258 | 0.7999 |
| CatBoost | 3.5464 | 4.6459 | 0.8067 |
| Bayesian Ridge | 3.5338 | 4.6310 | 0.8079 |

### [Dashboard 2](https://public.tableau.com/views/AISemiconductorPackagingBacklogPredictionOperationalPrioritization/Dashboard2-PredictiveBacklogAnalysis?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link): Predictive Packaging Backlog & Capacity Analysis

**Business question:** *Which facilities are predicted to experience longer packaging delays, and where should managers intervene proactively?*

The second dashboard adds a forward-looking layer:

- Model-predicted packaging backlog in weeks.
- Comparison of forecasted delays across facilities and manufacturing segments.
- Identification of facilities with elevated predicted backlog.
- Operational attention indicators combining prediction outputs with capacity context.
- Interactive views to investigate facilities and relevant manufacturing characteristics.

**Note:** A facility with a **high predicted backlog** is forecast to face a longer packaging queue; a facility **requiring immediate attention** is identified by a broader prioritization rule. These groups may overlap, but they are not necessarily identical.

### End-to-End Analytical Workflow

```text
Semiconductor Supply Chain Data
             |
             v
     Python Data Preparation
             |
       +-----+------+
       |            |
       v            v
 Descriptive &   Regression Model
 Risk Analysis    Training/Evaluation
       |            |
       v            v
 Tableau          Predicted Backlog
 Dashboard 1      + Priority Outputs
                    |
                    v
                 Tableau
                 Dashboard 2
```

## Operational Recommendations

1. **Monitor packaging queues alongside wafer capacity.** Track both stages to avoid shifting bottlenecks downstream.
2. **Investigate facilities with consistently high observed backlog.** Review packaging allocation, scheduling, and dependencies before making capacity changes.
3. **Use model predictions as an early-warning indicator.** Compare forecasted queue lengths across facilities and review the highest-risk cases first.
4. **Apply consistent facility-prioritization criteria.** Document thresholds and scoring logic so operational teams can understand why a facility is flagged.
5. **Validate the model regularly.** Track out-of-sample error and check whether performance changes across process nodes, HBM specifications, and accelerator families.
6. **Separate operational scenarios from measured outcomes.** Quantify potential benefits only after testing interventions against appropriate operational assumptions.

## Tools & Technical Skills

| Area | Tools and methods |
|---|---|
| Programming | Python, Pandas, NumPy, Seaborn, Matplotlib, scikit-learn |
| Visualization | Tableau, KPI design |
| Predictive analytics | Regression modeling, gradient-boosted decision trees |
| Model evaluation | MAE, RMSE, R² |
| Supply chain analytics | Capacity utilization, bottleneck analysis, facility prioritization, vulnerability assessment |
