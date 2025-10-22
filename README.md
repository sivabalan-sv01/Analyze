# Auto-generated README (Round 1)

**Project brief:** You are given two attachments: execute.py and data.xlsx.

- Commit execute.py after fixing the non-trivial error in it.
- Ensure it runs on Python 3.11+ with Pandas 2.3.
- Convert data.xlsx to data.csv and commit it.
- Add a GitHub Actions push workflow at .github/workflows/ci.yml that:
  - Runs ruff and shows its results in the CI log
  - Runs: python execute.py > result.json
  - Publishes result.json via GitHub Pages
- Do not commit result.json; it must be generated in CI.

**Attachments:**
- execute.py (text/x-python): preview: import json\n\nimport pandas as pd\n\n\ndef main():\n    # Read the data\n    df = pd.read_excel("data.xlsx")\n\n    # Compute revenue\n    df["revenue"] = df["units"] * df["price"]\n\n    # row_count\n    row_count = len(df)\n\n    # regions: count of distinct regions\n    regions_count = df["region"].nunique()\n\n    # top_n_products_by_revenue (n=3)"""  """\n    n = 3\n    top_products = (\n        df.groupby("product")["revenue"]\n        .sum()  # Intentional bug: wrong column name\n        .sort_values(ascending=False)\n        .head(n)\n        .reset_index()\n    )\n    top_products_list = [\n        {"product": row["product"], "revenue": float(row["revenue"])}\n        for _, row in top_products.iterrows()\n    ]\n\n    # rolling_7d_revenue_by_region: for each region, last value of 7-day moving average of daily revenue\n    df["date"] = pd.to_datetime(df["date"])  # ensure datetime\n    daily_rev = (\n        df.groupby(["region", "date"])["revenew"]  # daily revenue per regio\n- data.xlsx (application/vnd.openxmlformats-officedocument.spreadsheetml.sheet): 20348 bytes

**Checks to meet:**
execute.py, data.csv, and .github/workflows/ci.yml exist\nresult.json is NOT committed\nexecute.py does not contain the typo "revenew"\ndata.csv content equals data.xlsx (attachment)\nCI YAML has steps for ruff, executing execute.py, and Pages deploy\nGitHub Actions ran for this commit and logs show ruff + execute.py\nresult.json is published on GitHub Pages

## Setup
1. Open `index.html` in a browser.
2. No build steps required.

## Notes
This README was generated as a fallback (OpenAI did not return an explicit README).
