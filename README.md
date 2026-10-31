# ProdAnal

[Русская версия](README.ru.md)

Team project (track A) for the course "Product Analytics", Bauman Moscow State Technical University, autumn 2026. Part 1 (PA-S1, "Getting started").

## Task

Part 1 fixes what we are building, on which data, and how it will be measured. The result is a single Jupyter notebook, `project.ipynb`, that runs from start to finish and is the basis for the next stages of the project.

We analyse Olist, a Brazilian e-commerce service, as a two-sided platform (buyers and sellers). The notebook contains:

1. Product: what we do, for whom, which problem it solves, value hypotheses, business model.
2. Data: sources, licenses, volume, period, limitations; quality checks (missing values, duplicates, outliers, test users, time boundaries); why the datasets fit.
3. Definitions: active user, conversion, retention, cohort, churn rule.
4. Metrics: North Star, two diagnostic metrics and one risk metric (metric pyramid).
5. Tracking: event table with trigger, parameters, metric, journey stage and dataset field.
6. First calculations: cohort retention, return within 30/60/90/180 days, LTV/CAC of sellers, DAU/WAU/MAU.
7. Ethics checklist.
8. Success criteria: target values of key metrics and how they are verified.
9. Repository.

## Repository structure

| Path | Content |
|---|---|
| `project.ipynb` | the notebook with all nine sections |
| `data/` | source CSV files of both datasets |
| `requirements.txt` | pinned versions of the libraries |
| `.gitignore` | excludes Python and Jupyter service files |
| `LICENSE.md` | full text of CC BY-NC-SA 4.0 |
| `README.md`, `README.ru.md` | this description in English and Russian |

## How to run

Python 3.10 or newer is recommended.

1. Clone the repository and go to its root:
   ```bash
   git clone https://github.com/iverid/ProdAnal.git
   cd ProdAnal
   ```
2. Create and activate a virtual environment:
   ```bash
   python -m venv .venv
   source .venv/bin/activate        # Windows: .venv\Scripts\activate
   ```
3. Install the dependencies with the pinned versions:
   ```bash
   pip install -r requirements.txt
   ```
4. Check that both dataset folders are present in `data/` (see the Data section).
5. Start Jupyter **from the repository root**, open `project.ipynb` and choose *Kernel → Restart & Run All*. The notebook reads data by the relative path `data/` and stops with a message if it is started from another folder. There are no absolute paths.

## Results

- New buyers are mostly one-time: 1.30% return within 90 days and 1.99% within 180 days (20 monthly cohorts, 93,094 new buyers). The share of buyers with at least two delivered orders is 3.0%, with purchases on two different dates 2.15%.
- Sellers: 43.2% of the 667 sellers with a full 90-day observation start selling within 90 days after the deal. With an assumed 15% commission, LTV90 per deal is 74 BRL; the maximum CAC at LTV/CAC = 3 is 25 BRL. Social-media leads convert worst (5.6% against 11.8–12.3% for search).
- MAU stays at 6–7 thousand buyers in 2018, 97–99% of them new; DAU/MAU is about 3%.
- Success criteria (section 8): +10% to the monthly number of successful deals (North Star), at least 1.8% repeat purchases within 90 days, at least 50% seller activation within 90 days, and cancelled orders not more than 0.5 percentage points above the base.

## Team and contributions

| # | Participant | Sections | Contribution |
|---|---|---|---|
| 1 | Кошелева А. И. | 3, 8, 9 | repository setup, definitions, success criteria |
| 2 | Пасхальная Д. А. | 2, 6 | data quality checks, licenses, why the datasets fit; cohort retention |
| 3 | Ушинский Д. В. | 4, 5 | metrics and tracking |
| 4 | Иванова Т. Ю. | 1, 7 | product description, ethics checklist, validation of participant 3 |
| 5 | Гайсин М. В. | 2, 6 | work with participant 2; LTV/CAC and additional metrics, validation of participant 2 |

## License and attribution

This project is licensed under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/).

It uses the following datasets, also licensed under CC BY-NC-SA 4.0:
- Brazilian E-Commerce Public Dataset by Olist, https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce (downloaded on 25th october, 2026, version 2)
- Marketing Funnel by Olist, https://www.kaggle.com/datasets/olistbr/marketing-funnel-olist/data (downloaded on 25th october, 2026, version 2)

Changes made: data cleaning, filtering of test users, merging of the two datasets by `seller_id`, and derived metric tables. File `olist_geolocation_dataset.csv` is dropped because it's not relevant for our purposes.

No endorsement by Olist is implied.
