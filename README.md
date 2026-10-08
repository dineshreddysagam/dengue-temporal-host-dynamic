# Dengue temporal host–virus dynamics — research code

Code-only reviewer package prepared from three submitted Jupyter notebooks. Original analysis logic has been retained; saved outputs have been removed and two machine-specific Windows paths replaced by relative paths. **Not yet end-to-end validated:** the source dataset was not supplied with the notebooks.

## Notebooks in execution order

1. `notebooks/01_Data_Audit.ipynb` — dataset checks, missingness, observation coverage.
2. `notebooks/02_Cohort_Definition.ipynb` — DOI-4 event timing and cohort definition; exports `outputs/audit/DOI4_Patient_Level_Cohort_Definition.csv`.
3. `notebooks/03_PreLandmark_Modeling.ipynb` — DOI 3→4 dynamics, post-landmark outcome checks, predictive models and calibration/bootstraps.

## Reproduction

1. Obtain the original **Longitudinal viremia and platelet 22May2024.csv** from its authoritative dataset host, observing its license and citation instructions. This archive does **not** redistribute the dataset.
2. Put that exact filename at `data/Longitudinal viremia and platelet 22May2024.csv`.
3. Open a terminal in the repository root and execute:

   ```bash
   python -m venv .venv
   # On Windows: .venv\Scripts\activate
   # On macOS/Linux: source .venv/bin/activate
   pip install -r requirements.txt
   jupyter lab
   ```
4. In Jupyter, enter `notebooks/` and **Run All** for each notebook in the listed order. Run the cohort notebook before the modeling notebook because it creates the cohort CSV.
5. Verify generated summary tables and figures against the published manuscript. Package versions are not frozen; create a tested environment lock file after validation.

## Important limitations

- Source CSV and generated audit/cohort files are absent; the analysis could not be executed here. **Do not claim full reproducibility until an independent run succeeds.**
- Manuscript-wide completeness has not been established from these three files alone. Check that *every* reported result and figure is covered, and add any omitted analysis notebooks.
- `Patient_ID` is constructed from source study and participant codes. Do not publicly commit derived row-level patient data without confirming the original data sharing terms.
- Keep confidential work, credentials, proprietary project code, and local patient data outside this public repository.
- This public repository allows anonymous read access. For Cell Press, confirm the repository URL opens in an incognito window and that all supporting code is present before submission.

## Software

See `requirements.txt`. Python/scientific package versions should be pinned after running the analysis in a clean environment.
