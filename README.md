# Kaggle Data Science Survey Analysis

An exploratory data analysis of a shortened 2021 Kaggle Data Science Survey dataset. The project examines coding experience, Python/R/SQL usage, machine-learning framework preference, and reported compensation.

## Project Goals

This notebook answers:

- How much coding experience do survey respondents report?
- How widely are Python, R, and SQL used?
- Which machine-learning framework is the most commonly named?
- How does reported compensation vary across experience groups?
- How sensitive are compensation comparisons to extreme values?

## Key Findings

- **25,973 respondents** are represented in the dataset.
- **42.83%** of respondents report 0–2 years of coding experience.
- **21,860** respondents use Python, **5,335** use R, and **10,757** use SQL.
- **Scikit-learn** is the most commonly named machine-learning framework, with **7,934** respondents.
- Median compensation is **54,010**; mean compensation is **53,252.82**.
- Excluding the top 1% of compensation values changes the median to **53,765**.
- The rank correlation between coding experience and compensation is **0.1455**.

These results describe associations in this survey sample; they do not establish causation.

## Dataset

The analysis uses [`data/kaggle2021-short.csv`](/workspaces/Kaggle-Data-Science-Survey/data/kaggle2021-short.csv), with six fields:

- `experience_coding`
- `python_user`
- `r_user`
- `sql_user`
- `most_used`
- `compensation`

The original Kaggle survey source and the transformation used to produce this shortened dataset should be documented before publication.

## Analysis

The complete analysis is in [`notebooks/kaggle_survey_analysis.ipynb`](/workspaces/Kaggle-Data-Science-Survey/notebooks/kaggle_survey_analysis.ipynb).

The notebook includes:

- Dataset loading and data-quality checks
- Missing-value and duplicate analysis
- Numeric range validation
- Experience grouping
- Language and framework summaries
- Compensation distributions
- Median compensation comparisons
- Top-1% sensitivity analysis
- Rank correlation

Missing framework responses are preserved as `No answer` instead of being dropped or assigned to a framework. High compensation values are flagged and tested, but not silently removed.

## Tools

- Python
- pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter
- uv

## Setup

From the repository root:

```bash
uv sync
```

## Run the Notebook

```bash
cd notebooks
uv run jupyter lab
```

Open `kaggle_survey_analysis.ipynb` and run all cells.

To execute it from the command line:

```bash
cd notebooks
uv run jupyter nbconvert --to notebook --execute kaggle_survey_analysis.ipynb --inplace --ExecutePreprocessor.timeout=120
```

## Limitations

- Compensation is self-reported.
- Currency units and compensation-processing assumptions are not fully documented in the shortened dataset.
- The survey sample may not represent the complete data-professional population.
- Missing framework values may reflect non-response or question behavior.
- The dataset does not include country, role, industry, organization size, or remote-work status.
- Coding-experience and compensation comparisons cannot establish causal effects.

## Future Work

With the complete survey and additional variables, the next project phases could include:

- Cross-tabulations by country and role
- Inflation-adjusted compensation analysis
- Regression with role, country, experience, and education controls
- Confidence intervals and uncertainty estimates
- A dashboard for interactive exploration