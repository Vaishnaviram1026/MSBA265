# MSBA 265 — Module 1

## French Motor Claims: Data Quality Audit, EDA & Production Pipeline

**Name:** Vaishnavi
**MS Business Analytics**
**MSBA 265 — Module 1**

## Project Overview

This project analyzes the French Motor Third-Party Liability Claims Frequency (freMTPL2freq) dataset. The workflow covers raw data quality auditing, business data dictionary creation, exploratory data analysis, correlation analysis, distribution audits, and Tukey IQR-based outlier filtering.

The project is structured as a reproducible workflow so that another user can clone the repository, create a Python virtual environment, install the required dependencies, obtain the dataset, execute the analysis notebook, and run the production cleaning script.

## Project Structure

```
module1/
│
├── data/
│   ├── download_data.py
│   ├── raw_business_data.csv
│   └── cleaned_business_data.csv
│
├── notebooks/
│   └── 01_eda_and_data_dictionary.ipynb
│
├── reports/
│   ├── data_dictionary.csv
│── figures/
│       ├── feature_distributions.png
│       ├── correlation_heatmap.png
│       └── outlier_filtering_comparison.png
│
├── src/
│   └── clean_outliers.py
│
├── Module1_Homework_report.pdf
├── README.md
├── requirements.txt
└── .gitignore
```

## 1. Prerequisites

The following software is required:

- Python 3.10 or later
- Git
- Visual Studio Code
- VS Code Jupyter extension or Jupyter Notebook

## 2. Clone the Repository

Open a terminal and navigate to the location where you want to store the project.

```bash
git clone https://github.com/Vaishnaviram1026/MSBA265
```

Navigate into the project:

```bash
cd MSBA265/module1
```

## 3. Create and Activate the Virtual Environment

Creating a virtual environment keeps the project dependencies isolated from other Python projects.

**Windows PowerShell**

```powershell
python -m venv venv
```

Activate the environment:

```powershell
.\venv\Scripts\Activate
```

If PowerShell prevents activation, run the following command in the current PowerShell session:

```powershell
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process
```

Then activate the virtual environment:

```powershell
.\venv\Scripts\activate
```

## 4. Install Project Dependencies

Install the required packages using the provided `requirements.txt` file:

```bash
pip install -r requirements.txt
```

The main packages support:

- **Pandas** — data loading, cleaning, analysis, and CSV export
- **NumPy** — numerical operations
- **Matplotlib** — data visualization
- **Seaborn** — statistical visualizations and heatmaps
- **SciPy** — statistical analysis
- **Jupyter/IPykernel** — notebook execution
- **Requests** — web/data access support

Using `requirements.txt` allows another user to recreate the required Python environment.

## 5. Obtain the Raw Dataset

The raw dataset can be downloaded programmatically using:

```
data/download_data.py
```

From the `module1` directory, run:

```bash
python data/download_data.py
```

The script retrieves the French Motor Claims Frequency dataset from OpenML using the configured data URL and saves it as:

```
data/raw_business_data.csv
```

The script also reports the number of rows and columns downloaded.

If `raw_business_data.csv` is already present in the repository, the included file can be used directly.

## 6. Run the EDA Notebook

Open the project in VS Code:

```bash
code .
```

Open: `notebooks/01_eda_and_data_dictionary.ipynb`

Select the Python interpreter from the project venv. Run the notebook cells sequentially.

The notebook performs the following analyses:

1. Raw dataset inspection using `df.info()` and `df.describe().T`
2. Boundary audits for DrivAge, Exposure, and BonusMalus
3. Business data dictionary creation
4. Pearson correlation analysis
5. Correlation heatmap visualization
6. ClaimNb skewness assessment
7. Distribution audits
8. Box plots and KDE histograms
9. Outlier and multicollinearity assessment

## 7. Data Dictionary

The notebook generates the business data dictionary and exports it to:

```
reports/data_dictionary.csv
```

This artifact provides a structured reference for the dataset variables and their characteristics.

## 8. Visualization Outputs

The notebook generates the required visualization artifacts under:

```
reports/figures/
```

Expected files include:

- `feature_distributions.png`
- `correlation_heatmap.png`
- `outlier_filtering_comparison.png`

These figures support the distribution, correlation, and outlier analyses presented in the final report.

## 9. Run the Production Outlier Pipeline

The production cleaning script is located at:

```
src/clean_outliers.py
```

From the `module1` directory, run:

```bash
python src/clean_outliers.py
```

The script applies Tukey's 1.5 × IQR rule to identify and filter observations outside the calculated bounds.

The resulting cleaned dataset is saved as:

```
data/cleaned_business_data.csv
```

The script reports the number of observations before and after filtering and the number of records removed.

## 11. Final Deliverables

The project contains the following major deliverables:

| File | Purpose |
|---|---|
| `data/download_data.py` | Programmatically downloads the raw dataset |
| `data/raw_business_data.csv` | Raw French Motor Claims dataset |
| `data/cleaned_business_data.csv` | Dataset after Tukey IQR filtering |
| `notebooks/01_eda_and_data_dictionary.ipynb` | EDA, audits, visualizations, and analysis |
| `src/clean_outliers.py` | Production outlier-filtering script |
| `reports/data_dictionary.csv` | Business data dictionary |
| `reports/figures/` | Required visualization outputs |
| `Module1_Homework_report.pdf` | Final written homework report |