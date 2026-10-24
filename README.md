# Predictive Analytics and Forecasting – Group Assignment

## Structure

```
notebooks/          Jupyter notebooks (exploration, modelling, forecasting)
src/                Reusable Python code (data loading, features, models)
data/raw/           Original, untouched data (not committed)
data/processed/     Cleaned / transformed data (not committed)
reports/figures/    Exported charts and figures for the report
```

## Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

## Working together

- Pull before you start: `git pull`
- Work on a branch per task: `git checkout -b my-task`
- Clear notebook outputs before committing large results, to keep diffs small.
- Don't commit large data files; share them separately and place them in `data/raw/`.
