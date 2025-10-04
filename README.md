Aime Muganga - 232

## 🧾 **Adidas Sales OLAP Assignment**

This project demonstrates the design and implementation of a **mini OLAP system** using **SQLite + Pandas** based on Adidas sales data from Kaggle.
It showcases **ROLAP, MOLAP, and HOLAP** architectures and performs the core **OLAP operations: Slice, Dice, Roll-Up, and Drill-Down**.

---

### 📂 **Repository Structure**

```
DSA2040A_OLAP_Assignment/
│
├── olap_assignment.ipynb      # Main Jupyter Notebook with OLAP code
├── olap_demo.db               # SQLite database file (fact & dimension tables)
├── app.py                     # Optional Streamlit dashboard (interactive OLAP)
└── README.md                  # Project documentation
```

---

### 🏗️ **Data Warehouse Design**

The data warehouse follows a **Star Schema**, with one fact table and four dimension tables:

**Fact Table:** `fact_sales_table`

| Column      | Description                       |
| ----------- | --------------------------------- |
| sale_id     | Unique sale record ID             |
| date_id     | Foreign key → `dim_date`          |
| product_id  | Foreign key → `dim_product`       |
| city_id     | Foreign key → `dim_city`          |
| retailer_id | Foreign key → `dim_retailer`      |
| Total_Sales | Total sales amount (fact/measure) |

**Dimension Tables**

* `dim_date(date_id, date, year, quarter, month)`
* `dim_product(product_id, product)`
* `dim_city(city_id, city)`
* `dim_retailer(retailer_id, retailer)`

---

### ⚙️ **OLAP Implementations**

#### 🧮 **ROLAP (Relational OLAP)**

ROLAP queries were executed directly in **SQLite** to perform aggregate operations such as:

* Average revenue by product category
* Total sales by year
* Best-selling product in each region

These SQL queries demonstrate OLAP aggregation using the relational database.

---

#### 📊 **MOLAP (Multidimensional OLAP)**

Pandas **pivot tables** were used to create multidimensional data cubes in memory.
Example cube:

> Total Sales by Product × Year

This approach allows fast computation and slicing of data using DataFrame operations.

---

#### 🔄 **HOLAP (Hybrid OLAP)**

HOLAP combines both techniques:

* **SQL queries (ROLAP)** are used to fetch detailed data from SQLite.
* **Pandas (MOLAP)** is then used for in-memory aggregation and visualization.

This hybrid approach provides both flexibility and speed.

---

### 🧠 **OLAP Operations**

#### 🟦 **Slice**

Filters data along a single dimension (e.g., Sales in *2024 only*).
This helps focus on a specific subset of data, like performance in one year.

#### 🟩 **Dice**

Applies multiple filters across dimensions (e.g., Sales in *Q1 2024* for *Foot Locker* in *New York*).
This gives a multi-dimensional view of performance.

#### 🟨 **Roll-Up**

Aggregates data to a higher level of hierarchy (e.g., from *Product → Category → Year*).
Useful for summarizing data at a broader level.

#### 🟥 **Drill-Down**

Moves from summary data to finer details (e.g., *Year → Quarter → Month*).
Enables deeper analysis to identify trends or anomalies.

---

### 📈 **Visualization**

The analysis includes visual charts to better interpret results:

1. **Line Chart:** Visualizes total sales over the years.

   > Helps track Adidas sales trends across time.
2. **Bar Chart:** Compares total sales by city.

   > Shows which cities drive the highest or lowest revenue.

---


### 📊 **Dataset**

**Source:** [Adidas Sales Dataset — Kaggle](https://www.kaggle.com/)
Contains retail sales data across cities, products, and retailers including metrics like price, units sold, and total sales.

---

### 🧩 **Tools Used**

* **Python** (Pandas, SQLite3, Matplotlib, Seaborn)
* **SQLite** (for ROLAP queries and data storage)
* **Pandas** (for MOLAP & HOLAP operations)
* **Streamlit & Plotly** (for optional dashboard visualization)

---

### 🏁 **Outcome**

This mini OLAP project successfully demonstrates:

* Understanding of **ROLAP, MOLAP, HOLAP**
* Implementation of **OLAP operations (Slice, Dice, Roll-Up, Drill-Down)**
* Integration of **analytical visualization and data aggregation** techniques

