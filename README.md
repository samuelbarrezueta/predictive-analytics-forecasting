# Predictive Analytics and Forecasting – Group Assignment

## Structure

```
docs/                   Assignment brief and material from the teacher
contributions/          Each person's drafts and handovers (folder per person, e.g. person1_joao_problem_framing/)
notebooks/              Task2_Data_Understanding_Preparation.ipynb (Olena, Samuel), Task3_Predictive_Modelling.ipynb (Joao, Nuno, Pedro)
src/                    Reusable Python code (data loading, features, models)
data/raw/               Original, untouched data, e.g. highway_accidents.csv (not committed)
data/processed/         Cleaned / transformed data (not committed)
reports/figures/        Exported charts and figures for the report
reports/presentation/   Final presentation (.pptx) where we paste our results
```

## Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

## Running the notebooks

1. Get `highway_accidents.csv` from Samuel (not in git) and put it in `data/raw/`.
2. Run `notebooks/Task2_Data_Understanding_Preparation.ipynb` first: it saves the prepared data to `data/processed/`.
3. Then run `notebooks/Task3_Predictive_Modelling.ipynb`, which loads that prepared data.

In Colab, each notebook asks you to upload the files it needs instead.

## Working together

- Pull before you start: `git pull`
- Work on a branch per task: `git checkout -b my-task`
- Clear notebook outputs before committing large results, to keep diffs small.
- Don't commit large data files; share them separately and place them in `data/raw/`.
