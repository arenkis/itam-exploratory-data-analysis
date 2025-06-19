# US Funeral-Services Sector: Open-Data Analysis (2013 – 2022)

This repository contains the Jupyter Notebook used for an exploratory data analysis (EDA) of the funeral-services industry in the United States.  Using **open data from [Data USA](https://datausa.io/)**, the notebook scrapes, cleans and visualises key indicators—number of establishments (NAICS 8122), employed workforce and average wage—by state and year.

---

## Folder structure

```

funeral-services-eda/
│
├─ eda_funerarias.ipynb          # full, step-by-step analysis (Spanish commentary)
├─ funerarias_estados_unidos.csv # dataset completo 2013-2022
├─ funerarias_2013_2016.csv      # establecimientos (2013-2016)
├─ funerarias_2014_2016.csv      # establecimientos + empleo + wage (2014-2016)
├─ funerarias_2017_2022.csv      # empleo + wage (2017-2022)
└─ README.md                     # you are here

```

---

## Reproducibility

```bash
# 1. create environment and install deps
python -m venv venv
source venv/bin/activate   # or .\venv\Scripts\activate on Windows
pip install -r requirements.txt
# requirements: requests beautifulsoup4 pandas numpy matplotlib seaborn

# 2. start notebook
jupyter notebook notebook.ipynb
```

The notebook is self-contained: it downloads raw JSON from the Data USA API, so no additional credentials are required.

---

## Analysis workflow

1. **Web scraping**
   *Built-in requests + BeautifulSoup* calls the Data USA API three times to fetch:

   * **Total Number of Establishments**
   * **Total Population** (workforce)
   * **Average Wage**

2. **Data wrangling**

   * Conversion of types, removal of `#null` states, handling of missing years.
   * Creation of three analysis windows:

     * 2013-2016 – establishments only
     * 2014-2016 – establishments + workforce + wage
     * 2017-2022 – workforce + wage

3. **Descriptive statistics**
   `pandas.DataFrame.describe()` for each window, plus narrative insights.

4. **Visualisation** (Seaborn/Matplotlib)

   * **Employees per establishment** (bar-chart top-10 states)
   * **Average-wage evolution** 2017-2022 (line chart)
   * **Average establishments per state** 2013-2016 (trend line)
   * **Correlation heat-map** for the 2014-2016 window
   * **Box-plot** of wage by workforce terciles

5. **Insights**
   Conclusions, strategic recommendations for a funeral-services start-up, and study limitations are documented in Spanish inside the notebook.

---

## Key findings (TL;DR)

* Moderate positive correlation (ρ≈0.54) between workforce size and number of establishments.
* Wage growth outpaces employment growth; Louisiana shows the fastest wage acceleration 2017-2022.
* States with **small funeral workforces can host high-paying outliers**, hinting at niche / premium service opportunities.
* Data coverage is uneven: establishments stop at 2016, while wage & workforce continue to 2022.

---

## License

Data scraped from Data USA is available under **GNU AGPL v3**.
All notebook code in this repo is released under the **MIT License** (see `LICENSE`).