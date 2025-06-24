# 🧪 ETL Midterm Project – Data Warehousing & Mining

## 1. 📌 Project Overview

This ETL (Extract, Transform, Load) lab demonstrates the core data engineering process on simulated retail sales data. The project extracts raw and incremental datasets, applies meaningful cleaning and transformation steps, and loads the structured outputs into a queryable SQLite database — preparing the data for downstream analytics and decision-making.

---

## 2. 🔄 ETL Phases

### 🔹 `ETL_extract.ipynb`
- Loaded two datasets: `raw_data.csv` and `incremental_data.csv`
- Performed `.head()` and `.info()` inspections
- Noted missing values and duplicates
- Saved unmodified data into the `data/` folder

### 🔹 `ETL_transform.ipynb`
Applied a robust transformation pipeline:
- Dropped duplicate rows
- Imputed missing `customer_name` with `"Anonymous"`
- Standardized and cleaned `product` and `region` columns, fixing typos and invalid entries
- Validated `product` and `region` values against allowed categories
- Filled missing `quantity` using the most frequent quantity (mode) per `customer_name`
- Used smart imputation for `unit_price`:
  - If only one unique price exists for a region-product group, use it
  - Otherwise, fill with global product mode
- Converted `order_date` to datetime format and dropped invalid rows
- Enriched data with a new column: `total_price = quantity × unit_price`
- Categorized `unit_price` into `Budget`, `Mid-Range`, `Premium`, and `Luxury` using product-specific bins
- Reordered final columns for clarity
- Saved the transformed datasets to:
  - `transformed/transformed_full.csv`
  - `transformed/transformed_incremental.csv`

### 🔹 `ETL_load.ipynb`
- Loaded transformed datasets into SQLite databases:
  - `loaded/full_data.db`
  - `loaded/incremental_data.db`
- Verified loaded tables using SQL queries:
  ```sql
  SELECT * FROM orders LIMIT 5;
  ```

---

## 3. 🛠️ Tools Used

| Tool               | Purpose                          |
|--------------------|----------------------------------|
| Python             | Core programming language        |
| Pandas             | Data manipulation and I/O        |
| NumPy              | Numerical operations             |
| SQLite3            | Lightweight relational database  |
| Matplotlib & Seaborn | Data visualization |
| Jupyter Notebook   | Interactive scripting environment|

---

## 4. 🚀 How to Run the Project

### ✅ Requirements:
- Python 3.7+
- Jupyter Notebook or JupyterLab
- pandas, numpy, sqlite3, matplotlib, seaborn

### 📁 Folder Structure:
```plaintext
ETL_Midterm_Samuel_123/
├── data/
│   ├── raw_data.csv
│   └── incremental_data.csv
├── transformed/
│   ├── transformed_full.csv
│   └── transformed_incremental.csv
├── loaded/
│   ├── full_data.db
│   └── incremental_data.db
├── ETL_extract.ipynb
├── ETL_transform.ipynb
├── ETL_load.ipynb
├── README.md
└── .gitignore
```

### 🧪 Run Instructions:
1. Clone or download this repository
2. Open the project folder in Jupyter Notebook
3. Execute notebooks in this order:
   - `etl_extract.ipynb` → to load and inspect raw data
   - `etl_transform.ipynb` → to clean, enrich, and structure the data
   - `etl_load.ipynb` → to load the final datasets into SQLite
4. Explore SQLite databases using:
   - SQL queries within the notebook
   - Any external DB viewer (e.g., DB Browser for SQLite)

---

## 5. 🖼️ Screenshot

Below is a sample preview of the original dataset.

![image](https://github.com/user-attachments/assets/c509392f-456b-4cbe-a04c-6e2c7bff15fa)


Below is a sample preview of the transformed dataset with categorized pricing and calculated totals:

![image](https://github.com/user-attachments/assets/41adf3db-7fa5-4b5b-b72c-ad3cb3cb9ea5)

Below is one of the visualizations used for exploration of the data.

![image](https://github.com/user-attachments/assets/7bcc973a-c1fe-4c97-9be1-1536966ec333)

---
