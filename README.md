# Win-Stay/Lose-Shift Heterogeneity in Rock-Paper-Scissors

Analysis of behavioral heterogeneity in the WXZ2014 Rock-Paper-Scissors dataset using
a GLM-HMM and a hierarchical Bayesian model.

## Authors
Meytav Shiller, Liam Yaakobi

## Repository Contents
- `analysis.ipynb` — full analysis notebook (data loading, preprocessing, all models, all figures)
- `paper.typ` — Typst source of the paper
- `references.bib` — bibliography
- `data/` — WXZ2014 dataset (raw + processed)

## Requirements
- Python 3.10+
- Google Colab (recommended) or local Jupyter environment

## Setup and Reproduction Instructions

1. Clone this repository:
   ```
   git clone https://github.com/<your-username>/<your-repo-name>.git
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
   - Run preliminary statistical tests (goodness-of-fit, chi-square independence, Cramér's V)
   - Fit the classical HMM and GLM-HMM variants (Transitions-Only, Emissions-Only, Full)
   - Select K via AIC/BIC comparison
   - Run the player-level bootstrap (B=35 iterations)
   - Fit the hierarchical Bayesian model (NUTS via numpyro)
   - Reproduce all figures used in the paper

## Notes
- Random seeds are fixed where applicable for reproducibility; exact figures may vary
  slightly across reruns due to MCMC sampling stochasticity.
- The full analysis (including Bayesian model fitting) takes approximately [X] minutes
  on Google Colab's standard CPU runtime.

## Data Source
Wang, Z., Xu, B., & Zhou, H.-J. (2014). Social cycling and conditional responses in the
rock-paper-scissors game. *Scientific Reports*, 4, 5830.
