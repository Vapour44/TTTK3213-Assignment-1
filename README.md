# Assignment 1 — Data Profiling (EDA) Report

This project profiles the real UCI Online Retail transaction workbook, documents data-quality decisions, and creates a purpose-specific completed-sales view in a Jupyter notebook. It focuses on missingness, outliers, other quality problems, privacy, country coverage, and fitness for cautious descriptive sales analysis. It does not perform predictive modeling.

## Team

| Name | Matric number |
|---|---|
| ZHANG KAIYI | A207404 |
| YANG LIZIXUAN | A207402 |
| YUAN YIWEI | A207421 |
| ZHOU XIUSHI | A207418 |

## Dataset and credit

- **Name:** Online Retail (UCI Machine Learning Repository, dataset 352)
- **Official page:** https://archive.ics.uci.edu/dataset/352/online+retail
- **Official ZIP used by the notebook:** https://archive.ics.uci.edu/static/public/352/online%2Bretail.zip
- **File:** `data/Online Retail.xlsx`, the original Excel workbook extracted from UCI's ZIP
- **Citation:** Chen, D. (2015). *Online Retail* [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5BW33
- **License:** CC BY 4.0, as stated on the UCI dataset page.

The workbook contains 541,909 transaction lines and eight original fields: `InvoiceNo`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`, `UnitPrice`, `CustomerID`, and `Country`. The notebook calculates all quality findings from the workbook rather than using invented records or fixed issue counts.

## Files

```text
Assignment-1-Data-Profiling/
├── Assignment1_Data_Profiling.ipynb  # Full report and runnable code
├── README.md                          # Project and run instructions
├── requirements.txt                   # Python dependencies
└── data/
    └── Online Retail.xlsx             # Original UCI workbook
```

## Setup and run

Use Python 3.10 or newer. From this project directory:

```bash
python -m venv .venv
```

Activate the environment with `.\.venv\Scripts\Activate.ps1` on Windows PowerShell (or `source .venv/bin/activate` on macOS/Linux), then:

```bash
python -m pip install -r requirements.txt
python -m notebook
```

Open `Assignment1_Data_Profiling.ipynb` and select **Run All**. Run it from the project directory so `data/` resolves correctly. The notebook reads the included original workbook and keeps it untouched in `raw_df`. Cleaning and exclusion flags are stored in a separate `audit_df`; `sales_df` is the completed-sales view.

If the workbook is not present after cloning, the first code cell downloads the official UCI ZIP and extracts `Online Retail.xlsx` to `data/`. If downloading fails, the cell raises an explicit error. To download manually, open the official page above, click **Download**, extract `Online Retail.xlsx`, put it inside `data/`, and rerun the notebook. No simulated dataset is used.

## Assignment coverage

The notebook includes a 2–3 sentence scenario; source URL, download method and field meanings; raw shape, sample, types, summary, missingness (including the disguised `Unspecified` country placeholder) and duplicates; reasoned missing-value handling; IQR outlier detection followed by inspection of the most extreme rows and classification of outliers (same-day cancellation reversals, non-product/accounting stock codes, and genuine wholesale extremes kept uncapped); data-type fixes, stock-code case normalization, canonical product descriptions, country-label standardization and invalid-value rules; four labeled diagnostic figures (raw outlier boxplots, missing values, country coverage, and post-handling distributions); CustomerID privacy and country-level bias discussion; a calculated issue summary, exclusion breakdown and before/after comparison; and an explicit fitness-for-purpose conclusion.
