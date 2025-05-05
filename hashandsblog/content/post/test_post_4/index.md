+++
title = "Making Meaningful Models - 2"
date = "2025-05-05"
author = "Hashan Fernando"
description = "Exploring spatial TDA + Bayesian models"
categories = ["Research"]
tags = ["TDA", "Bayesian"]
toc = true  # Table of contents (requires config below)
image = 'card-img.jpg'

+++

## Motivation

In epidemiological modeling, we often rely on spatial covariates like poverty or unemployment. But even with rich data, **unmeasured spatial factors** continue to influence disease risk. Traditional models like the **Besag-York-Mollié (BYM)** framework attempt to capture these unknowns with structured random effects, but they don’t always tell us *why* certain patterns emerge.

This post explores how **Topological Data Analysis (TDA)** can help us understand latent spatial structures and augment Bayesian disease models with geometric insight.

---

## Methods

We used **simulated overdose mortality data** across Tennessee counties and constructed **adjacency-based simplicial complexes** to represent shared social and geographic features. Using TDA, we extracted summaries like:

- **Persistence diagrams** of 1D loops (cycles of connectivity),
- **Connected component counts**,
- **Homology group statistics** based on socioeconomic variables.

These topological summaries were then included as covariates in a **Bayesian Poisson regression** model using the BYM2 specification:

```python
y_i ~ Poisson(μ_i)
log(μ_i) = α + β1 * x1_i + β2 * H1_i + u_i + v_i
```

Where:
- `H1_i` is a topological feature summary,
- `u_i` is the spatially structured effect,
- `v_i` is unstructured.

---

## Results

Adding topological summaries improved model fit (measured by WAIC and posterior predictive checks). Specifically:

- Areas with high **1D Betti numbers** (indicating loop-like structures) showed **strong correlation** with high overdose risk.
- These patterns were **not captured** by traditional covariates like income or unemployment alone.
- Visualizations of topological spaces helped identify *regions of latent connectivity* — e.g., clusters of isolated rural counties with shared risk.

---

## Conclusion

This work suggests that **topological summaries provide interpretable, complementary insights** into spatial risk beyond what structured priors or raw covariates offer. By integrating TDA into Bayesian frameworks, we move closer to understanding the hidden geometry of health disparities.

Next steps include applying this method to real overdose data and extending it to spatiotemporal modeling.

---

*Want to dive deeper? Feel free to reach out or check out the code on GitHub.*
