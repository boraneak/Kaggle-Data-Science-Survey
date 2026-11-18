# Copilot instructions

## Project overview

- This is a notebook-first exploratory data analysis of the shortened Kaggle 2021 Data Science Survey.
- The primary deliverable is `notebooks/kaggle_survey_analysis.ipynb`; `data/kaggle2021-short.csv` is the read-only source data.
- Keep claims descriptive: results show associations in the survey sample and do not establish causation.
- `src/main.py` is currently a placeholder and is not the analysis entry point.

## Environment and commands

- Use Python 3.14 and the checked-in `uv.lock`; run dependency and tool commands through `uv`.
- From the repository root, run `uv sync` after dependency or `pyproject.toml` changes.
- Run notebook work with the notebook directory as the working directory because `DATA_PATH = Path("../data/kaggle2021-short.csv")` is relative to that location.
- To launch Jupyter Lab from the repository root: `cd notebooks && uv run jupyter lab`.
- To validate the executed notebook: `cd notebooks && uv run jupyter nbconvert --to notebook --execute kaggle_survey_analysis.ipynb --inplace --ExecutePreprocessor.timeout=120`.

## Data and analysis conventions

- Read the source CSV with `pandas.read_csv` and retain the original `df` unchanged.
- Perform transformations on `clean = df.copy()` rather than mutating `df`.
- Preserve all 25,973 rows unless the user explicitly requests row removal.
- Keep the original six-column schema unless a change clearly requires derived columns.
- Preserve missing `most_used` responses as the visible category `"No answer"`; do not drop or silently encode them as a framework.
- Treat language-use columns as non-exclusive: count Python, R, and SQL independently and state that their shares do not sum to 100%.
- Flag compensation values at or above the 99th percentile with `high_compensation`; do not remove them silently.
- Use median compensation and Spearman rank correlation for compensation comparisons because compensation is skewed.
- Preserve uncertainty about compensation units and survey-processing assumptions; do not invent currency or causal interpretations.
- Add a limitation and an observation alongside any new chart or substantive finding.

## Notebook editing

- Reuse the existing pandas, NumPy, Matplotlib, and Seaborn imports and the seaborn `whitegrid` theme unless the task requires a new dependency.
- Keep code cells readable and deterministic: name intermediate data frames clearly and print or display the result needed to verify the analysis.
- Preserve section order and explanatory markdown: dataset, cleaning, visualizations, quantified relationships, and findings.
- Update README findings and limitations when a reproducible notebook change alters reported numbers or interpretation.
- Do not commit generated notebook execution output unless the task explicitly asks to refresh it; when refreshing, execute all cells and verify that relative paths work.
- Avoid adding extra dependencies when pandas, NumPy, or Matplotlib already provide the needed operation.

## Validation and change discipline

- For data, notebook, or analysis changes, execute the notebook with the nbconvert command above and inspect final counts, summary tables, and plots for correctness.
- Compare median, count, and correlation outputs after changes and update prose if numbers change.
- Make surgical edits; do not reformat unrelated notebook metadata or clear unrelated existing outputs.
- Do not modify `data/kaggle2021-short.csv` unless the user explicitly requests data preparation or correction.
