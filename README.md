
# 🌱 S&P 500 ESG Risk Analysis Dashboard – Power BI

_An interactive Power BI dashboard that compares ESG (Environmental, Social, Governance) risk across 503 S&P 500 companies by sector, industry, controversy level and company size._

---

## 📌 Table of Contents
- <a href="#overview">Overview</a>
- <a href="#business-problem">Business Problem</a>
- <a href="#dataset">Dataset</a>
- <a href="#tools--technologies">Tools & Technologies</a>
- <a href="#project-structure">Project Structure</a>
- <a href="#data-cleaning--preparation">Data Cleaning & Preparation</a>
- <a href="#exploratory-data-analysis-eda">Exploratory Data Analysis (EDA)</a>
- <a href="#research-questions--key-findings">Research Questions & Key Findings</a>
- <a href="#dashboard">Dashboard</a>
- <a href="#how-to-run-this-project">How to Run This Project</a>
- <a href="#final-recommendations">Final Recommendations</a>
- <a href="#author--contact">Author & Contact</a>

---
<h2><a class="anchor" id="overview"></a>Overview</h2>

An end-to-end data analytics project built on the S&P 500 ESG Risk Ratings dataset, covering **503 companies across 11 sectors and 116 industries**.
The data was loaded and transformed in **Power Query**, enriched with **DAX calculated columns** (risk category and employee-size bins), and visualized in a single-page **Power BI** dashboard.
The dashboard shows how ESG risk is spread across the index, which sectors and industries carry the most risk, and how risk relates to controversy level and company size.

---
<h2><a class="anchor" id="business-problem"></a>Business Problem</h2>

ESG risk scores are published per company, which makes it hard to see the bigger picture across a whole index. Investors, analysts and risk teams need to know where risk is concentrated before they can act on it.
This project addresses the following questions:

- **Risk Distribution:** How are companies spread across Negligible, Low, Medium, High and Severe risk?
- **Sector & Industry Comparison:** Which sectors and industries carry the highest average ESG risk?
- **Risk Pillars:** How do Environmental, Social and Governance scores compare?
- **Controversy Analysis:** Do companies with higher controversy levels also score worse on ESG risk?
- **Company Size:** Does a larger workforce mean higher ESG risk?

---
<h2><a class="anchor" id="dataset"></a>Dataset</h2>

- Source: [S&P 500 ESG Risk Ratings](https://www.kaggle.com/) dataset on Kaggle (CSV)
- 503 companies, 15 raw columns
- Key fields:
  - **Sector / Industry:** Business area of the company, from broad to specific.
  - **Full Time Employees:** Headcount, used as a proxy for company size.
  - **Total ESG Risk Score:** Overall ESG risk rating; higher means higher risk.
  - **Environment / Social / Governance Risk Score:** Risk score for each pillar.
  - **Controversy Level / Score:** How significant the company's controversies are.
  - **ESG Risk Percentile:** Rank of the company against its peers.
  - **ESG Risk Level:** Qualitative label for the risk score.
- 73 companies (14.5%) have no ESG risk score in the source file
- Dataset description reference: [Colorstech](https://colorstech.net/data-analytics/sp-500-esg-risk-ratings-dataset-description-and-data-analysis-report-ideas/)

---
<h2><a class="anchor" id="tools--technologies"></a>Tools & Technologies</h2>

- **Power BI Desktop:** Dashboard development, slicers and interactive visuals.
- **Power Query (M):** Data import, type conversion, index column and sorting.
- **DAX:** Calculated columns for ESG risk category and employee-count bins.
- **Git & GitHub:** Version control, project documentation, and repository management.

---
<h2><a class="anchor" id="project-structure"></a>Project Structure</h2>

```
esg-risk-analysis-powerbi/
│
├── README.md
│
├── ESG_Risk_Analysis.pbix
│
└── images/
    └── dashboard.png
```

---
<h2><a class="anchor" id="data-cleaning--preparation"></a>Data Cleaning & Preparation</h2>

Prepared in Power Query and DAX:

- Loaded the CSV and promoted the first row to headers.
- Set data types: text for names and categories, whole number for employees, decimal for scores.
- Added an `Index` column (1 to 503) as a unique row key for counting.
- Sorted rows by ESG Risk Level.
- Created **ESG Risk Category** with DAX, using the total score: ≤10 Negligible, ≤20 Low, ≤30 Medium, ≤40 High, >40 Severe.
- Created **Full Time Employees (bins)** with DAX, splitting the employee range into 50 equal-width bins.

---
<h2><a class="anchor" id="exploratory-data-analysis-eda"></a>Exploratory Data Analysis (EDA)</h2>

- **Overall Scores**: Among the 430 scored companies, the average total ESG risk score is 21.5 (range 7.1 to 41.7).
- **Risk Pillars**: Average Social risk (9.1) is the largest pillar, followed by Governance (6.7) and Environment (5.7).
- **Sector Analysis**: Energy has the highest average risk (32.3); Real Estate has the lowest (13.1).
- **Industry Analysis**: Oil & Gas Integrated (39.1), Oil & Gas E&P (36.1) and Aerospace & Defense (35.0) lead among industries; some industries have only one or two scored companies.
- **Controversy Analysis**: Average risk rises with controversy level, from 16.2 (None) to 36.8 (Severe).
- **Company Size**: Most companies have fewer than about 42,000 employees, and average risk shows no clear trend by workforce size.

---
<h2><a class="anchor" id="research-questions--key-findings"></a>Research Questions & Key Findings</h2>

1. **How Is Risk Distributed?**: Of 430 scored companies, 188 are Low risk, 183 Medium, 50 High, 6 Negligible and 3 Severe. Only 3 companies cross 40: Occidental Petroleum (41.7), Exxon Mobil (41.6) and General Electric (40.5).
2. **Which Sectors Carry the Most Risk?**: Energy (32.3), Basic Materials (26.7), Utilities (26.7) and Consumer Defensive (25.4) are highest. Real Estate (13.1) and Technology (16.9) are lowest.
3. **Which Pillar Drives Risk?**: Social (9.1) > Governance (6.7) > Environment (5.7) on average, but Environment has the widest spread (0 to 25).
4. **Does Controversy Track Risk?**: Yes. Average risk goes 16.2 (None), 18.9 (Low), 22.0 (Moderate), 24.2 (Significant), 30.1 (High), 36.8 (Severe). Almost half of scored companies (46%) sit at Moderate controversy.
5. **Does Company Size Matter?**: Not clearly. Risk is similar for small and mid-size workforces, and the largest bins contain only one or two companies each.

---
<h2><a class="anchor" id="dashboard"></a>Dashboard</h2>

🔍 **Key Features:**

- ✅ **KPI Cards** – Quick view of Total ESG Risk, Environment Risk, Social Risk and Governance Risk scores.
- ✅ **ESG Risk Level Distribution** – Donut chart grouping companies into Negligible, Low, Medium, High and Severe ESG risk.
- ✅ **Controversy Analysis** – Pie chart showing average ESG risk score for each controversy level.
- ✅ **Sector-Wise ESG Risk** – Treemap showing average ESG risk by sector.
- ✅ **Industry-Wise ESG Score** – Column chart comparing ESG risk scores across industries.
- ✅ **Employee Count Impact** – Line and column combo chart showing company count and ESG risk by full-time employee bins.
- ✅ **Interactive Filters** – Slicers for Sector and Industry to update every visual.

**Caveats:**
  - 73 companies have no ESG score. In the DAX category column, a blank score falls into the "Negligible" bucket, so the donut shows 79 Negligible companies instead of 6. Fix by adding a blank check at the top of the `SWITCH`.
  - The KPI cards and the industry column chart use **Sum** of scores, not **Average**, so values scale with the number of companies. Switch to Average for fair comparison.
  - Many industries contain very few companies, so industry averages can be unstable.

<img width="1317" height="727" alt="ESG_Dashboard_image" src="https://github.com/user-attachments/assets/2bac0995-1395-4d4c-84f3-854490e204c0" />

---
<h2><a class="anchor" id="how-to-run-this-project"></a>How to Run This Project</h2>

1. Clone the repository:
```bash
git clone https://github.com/Sruthi-M-Suresh/esg-risk-analysis-powerbi.git
```
2. Download the **S&P 500 ESG Risk Ratings** CSV from Kaggle and save it as `SP 500 ESG Risk Ratings.csv`
3. Open `ESG_Risk_Analysis.pbix` in Power BI Desktop
4. In **Transform data → Source**, change the file path to where you saved the CSV (it currently points to a local Downloads folder), then click **Refresh**

---
<h2><a class="anchor" id="final-recommendations"></a>Final Recommendations</h2>

- Treat Energy, Basic Materials and Utilities as the main areas of ESG risk exposure in the index.
- Monitor companies with High or Severe controversy levels, since they also tend to have the highest risk scores.
- Handle the 73 unscored companies separately instead of grouping them into a risk category.
- Use average scores rather than totals when comparing sectors and industries.
- Add company counts next to industry averages so small-sample industries are not over-read.
- Extend the analysis with market cap or returns to test whether ESG risk relates to financial performance.

---
<h2><a class="anchor" id="author--contact"></a>Author & Contact</h2>

**Sruthi Suresh**  
SQL | Power BI | Tableau | DuckDB </br>
📧 Email: thesruthisuresh@gmail.com  
🔗 [LinkedIn](https://www.linkedin.com/in/sruthi-suresh-724b231ba/)
🔗 [GitHub](https://github.com/Sruthi-M-Suresh)
