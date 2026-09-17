⚠️ FOR DYNAMIC, 3D PLOTS AND BEST EXPERIENCE please view the notebook on nbviewer or Google Colab, as GitHub's built-in viewer cannot render heavy interactive JavaScript or 3D plots. ⚠️

[View full notebook on NBViewer](https://nbviewer.org/github/barofrx-svg/github_datascience_projects/blob/main/project_5_data_mining/data_mining.ipynb) or [View full notebook on Google Colab](https://colab.research.google.com/github/barofrx-svg/github_datascience_projects/blob/main/project_5_data_mining/data_mining.ipynb)

# Association Rule Learning & Market Basket Analysis (Apriori)

## 1. Overview
This project performs **Market Basket Analysis** on retail transaction logs to uncover hidden co-occurrence patterns and purchasing associations among items. Using **Association Rule Learning (ARL)** and the **Apriori algorithm**, the pipeline transforms raw invoice logs into actionable cross-selling insights, optimized product bundling strategies, and inventory recommendations.

---

## 2. Methodology & Pipeline

- **Data Hygiene & Cancellation Handling:** 
  - Parsed transaction timestamps, filtered out negative unit prices, and isolated transactions to the UK market.
  - Developed a robust cancellation-matching routine to pair positive purchases with corresponding return/negative quantity rows, purging non-profitable returned orders and cleaning null `CustomerID`/`Description` entries.
- **Basket Matrix Transformation:** 
  - Pivoted transaction records into a binary one-hot encoded invoice-by-item occurrence matrix ($\text{Invoices} \times \text{Items}$).
- **Apriori Algorithm & Rule Generation:** 
  - Executed the `apriori` algorithm (using `mlxtend`) with a defined minimum support threshold to extract frequent itemsets.
  - Generated association rules evaluated via key statistical metrics: **Support**, **Confidence**, and **Lift**.
- **Exploratory Visualizations:** 
  - Visualized rule distributions (Support vs. Confidence, colored and scaled by Lift) using Seaborn and interactive Plotly charts to isolate high-strength purchasing rules from background noise.

---

## 3. Results & Key Insights
- Successfully extracted hundreds of high-confidence item associations (e.g., matching themed home decor sets, kitchen accessories, and baking supplies).
- Highlighted the trade-off between **Lift** and **Support**: while high-lift rules identify niche, highly specialized product pairings (like specific herb markers or rare holiday items), high-support rules capture mainstream basket staples.
- Provided data-driven recommendations for retail product placement and cross-selling discounts.

---

## 4. Tech Stack
- **Language:** Python
- **Libraries:** `pandas`, `NumPy`, `mlxtend` (Apriori & Association Rules), `Plotly`, `Seaborn`, `Matplotlib`

---

## 5. How to Run
```bash
# Clone repository and navigate to project folder
cd project_5_data_mining

# Run the notebook
jupyter notebook data_mining.ipynb
