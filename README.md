# Win-Stay/Lose-Shift Heterogeneity in Rock-Paper-Scissors

Analysis of behavioral heterogeneity in the WXZ2014 Rock-Paper-Scissors dataset using a GLM-HMM and a hierarchical Bayesian model. We ask whether players exhibit the classic Win-Stay/Lose-Shift heuristic, and how this tendency is distributed across the population, using three convergent approaches: player-level statistical tests, an unsupervised GLM-HMM, and a hierarchical Bayesian model.

## Authors
Meytav Shiller, Liam Yaakobi

## Repository Contents
- `analysis.ipynb` — full analysis notebook (data loading, preprocessing, all models, all figures)
- `paper.typ` — Typst source of the paper
- `references.bib` — bibliography
- `data/` — WXZ2014 dataset

## Requirements
- Python 3.10+
- Google Colab (recommended) or local Jupyter environment

## Setup and Reproduction Instructions

1. Clone this repository:
   ```
   git clone https://github.com/meytav123456/rps-analysis.git
   ```

2. Open `analysis.ipynb` in Google Colab or Jupyter.

3. Install dependencies (first cell of the notebook):
   ```
   pip install pyreadr
   pip install git+https://github.com/lindermanlab/ssm.git
   pip install pymc numpyro arviz
   ```

4. Run all cells in order, top to bottom. The notebook will:
   - Load and preprocess the WXZ2014 dataset (`data/WXZ2014.rda`)
   - Run preliminary statistical tests (goodness-of-fit vs. Nash equilibrium, chi-square test of independence, Cramér's V — both pooled and per-player)
   - Fit the classical HMM and three GLM-HMM variants (Transitions-Only, Emissions-Only, Full), and compare via AIC/BIC
   - Select the number of hidden states K via AIC/BIC comparison across K=1..4
   - Run the player-level bootstrap (B=35 iterations) to obtain confidence intervals on emission parameters, with Bonferroni correction for multiple comparisons
   - Fit the hierarchical Bayesian model with player-specific random slopes (NUTS via numpyro)
   - Compare both models via held-out predictive log-likelihood and a permutation test for convergent validity
   - Reproduce all figures used in the paper

## Notes
- Random seeds are fixed where applicable for reproducibility; exact figures may vary slightly across reruns due to MCMC sampling stochasticity.
- The full analysis (including Bayesian model fitting) takes approximately 30–40 minutes on Google Colab's standard CPU runtime.

## Data Source
Wang, Z., Xu, B., & Zhou, H.-J. (2014). Social cycling and conditional responses in the rock-paper-scissors game. *Scientific Reports*, 4, 5830. https://doi.org/10.1038/srep05830
