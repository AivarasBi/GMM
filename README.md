# Regime-gated selective prediction

Code and data for the paper. The notebooks build the models, run the portfolio
backtest, and produce the tables and figures. Each one reads and writes the
`Data/` folder beside it.

Notebooks 7 and 8 print the tables; the figures are saved to
`Data/Article_figures/` (PNG and PDF).

## Notebooks

Run them in order. Notebooks 1–4 build the predictions and are slow (the LSTM wants
a GPU); 5–7 do the analysis and run in seconds.

1. **Train predictions** — trains the 45 models and saves their up-probabilities to `Data/Predictions_45/`.
2. **Validation predictions** — the same models on the 2021–2022 window → `Data/Predictions_45_val/`.
3. **Train_Crisis predictions** — train on 2000–2007, predict the 2008–2012 crash → `Data/Predictions_crisis/`.
4. **Validation_Crisis predictions** — the 2006–2007 selection window → `Data/Predictions_crisis_val/`.
5. **Backtest analysis** — the EqualWeight-Selected backtest against 1/N; writes the full grid to `Data/Backtest_results/`.
6. **Backtest analysis, crisis** — the same backtest on 2008–2012.
7. **Tables and figures** — the paper's tables and figures, straight from the two grids.

If you only want the tables and figures, run notebook 7; the grids it needs are
already in `Data/`.

## Data

- `features_1.parquet`, `features_2.parquet` — daily prices and eight technical features for the 40 stocks, 2000–2026 (split in two so every file stays under 25 MB; the notebooks read both).
- `Predictions_*/all_predictions*.parquet` — the saved up-probabilities and GMM regimes.
- `Backtest_results*/results_all.parquet` — end capital and drawdown for every configuration.
- `Article_figures/` — the five figures, as PNG and PDF.

## Running it

    python -m venv .venv
    source .venv/bin/activate
    pip install -r requirements.txt
    jupyter lab

## Citation

If you use this code or data, please cite:

```bibtex
@article{BielskisBelovas2026gmmlstm,
  title   = {Portfolio Construction with Regime-Gated Selective Prediction: A GMM--LSTM Approach},
  author  = {Bielskis, Aivaras and Belovas, Igoris},
  journal = {Expert Systems with Applications},
  year    = {2026}
}
```
