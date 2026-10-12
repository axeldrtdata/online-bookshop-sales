# What really drives sales at an online bookshop?

Two years of sales and 680,000 purchases: revenue trends, catalogue tops and flops, customer concentration, and five statistical tests on what a customer profile really changes.

**Full case study:** [axeldrtdata.github.io/works/online-bookshop-sales](https://axeldrtdata.github.io/works/online-bookshop-sales/)

## Context

An online bookshop shared two years of sales data (March 2021 to February 2023) in three files: customers, products and transactions. Management wanted a picture of revenue, the catalogue and the customer base; the marketing team asked five precise questions about the link between customer profiles (gender, age) and buying behaviour.

## Key results

- **Revenue is stable and seasonal**: €5.57M in year 1, €5.58M in year 2, with dips in July and November 2021 and peaks in October 2021 and February 2022.
- **The catalogue is unbalanced**: the entry-level category makes up 70% of references but only 37% of revenue; 21.5% of references generate 80% of revenue.
- **The customer base is broad**: 52% of customers generate 80% of revenue (Gini index 0.40). Four B2B customers were analysed separately (7.35% of total revenue).
- **One strong correlation**: the younger the customer, the larger the average basket (Spearman ρ = −0.70). Age also separates the categories (median age 25 for premium, 43 for entry level, 57 for mid-range).

| Marketing question       | Test                     | Result     | Verdict                    |
| ------------------------ | ------------------------ | ---------- | -------------------------- |
| Gender × category        | Chi-squared              | p = 0.086  | No link                    |
| Age × total spend        | Spearman                 | ρ = −0.18  | No meaningful correlation  |
| Age × purchase frequency | Spearman                 | ρ = 0.21   | No meaningful correlation  |
| Age × average basket     | Spearman                 | ρ = −0.70  | Clear negative correlation |
| Age × category           | Kruskal-Wallis and ANOVA | p ≈ 0      | Strong link                |

All tests are run at customer level (one row per customer) to respect the independence of observations. Normality was rejected by Shapiro-Wilk, hence Spearman rather than Pearson.

## Repository structure

```
online-bookshop-sales/
├── notebooks/
│   └── bookshop-sales-analysis.ipynb   # cleaning, revenue, catalogue, customers, statistical tests
├── data/
│   ├── customers.csv
│   ├── products.csv
│   └── transactions.zip                # zipped CSV, read directly by pandas
├── requirements.txt
└── README.md
```

## How to run it

```bash
git clone https://github.com/axeldrtdata/online-bookshop-sales.git
cd online-bookshop-sales
pip install -r requirements.txt
```

Open the folder in VS Code (with the Python and Jupyter extensions) and run the notebook. The interactive Plotly charts appear when the notebook is run; GitHub's preview only shows the static charts.

## Limitations

- **Correlation is not causation**: age is linked to basket size, but the data does not explain why.
- **One category per customer**: for the category tests, each customer is summed up by the category they buy most, which hides customers who buy across several categories.
- **The ±0.25 threshold** used to call a correlation meaningful is a convention; other cut-offs would not change the one strong result.

## Stack

Python · pandas · NumPy · SciPy · statsmodels · Plotly · Seaborn · Matplotlib · VS Code

## Note

The notebook was first written in French during my OpenClassrooms Data Analyst training. Its text, comments and chart labels have since been translated into English and it has been re-run end to end; variable and column names were kept as in the original.

---

Axel Derobert · Data Analyst · [Portfolio](https://axeldrtdata.github.io) · [LinkedIn](https://www.linkedin.com/in/axel-derobert-5717463b1/)
