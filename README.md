# DASHBOARD-DEVELOPMENT
*COMPANY*: CODTECH IT SOLUTIONS
*NAME*: ONKAR DEVAKR
*INTERN ID*: CT12DF308
*DOMAIN*: DATA ANALYTICS
*DURATION*: 12 WEEKS
*MENTOR*: NEELA SANTOSH KUMAR

Here is a complete **Power BI Project Documentation** for your internship project titled **“Sales Performance Dashboard”**, based on the Superstore dataset. You can use this as part of your report or submission for the CODTECH internship.

---

## 1. 📌 Objective

The goal of this project was to develop a **dynamic and interactive dashboard** using Power BI to visualize sales, profit, orders, shipping, and customer behavior for a retail business. The dashboard is intended to provide **actionable insights** to help in decision-making regarding product performance, customer segments, regional sales, and shipping performance.

---

## 2. 📁 Dataset Overview

**File Used**: `Sample - Superstore.csv`
**Key Columns**:

* **Order Date, Ship Date** – Date of order and shipment
* **Sales, Profit, Discount** – Financial metrics
* **Product Name, Category, Sub-Category** – Product hierarchy
* **Customer Name, Segment** – Customer details
* **Region, State, City** – Geographic breakdown
* **Order ID** – Transaction-level identifier

---

## 3. 🛠️ Power BI Development Steps

### 3.1 Data Preparation (Power Query)

* Removed errors and ensured date formats were correct
* Cleaned null or missing values
* Created `minorderdate` and `maxshipdate` to define calendar range

### 3.2 Data Modeling

* Created a **Calendar Table** using DAX:

  ```DAX
  Calendar = CALENDAR(MIN(superstore[Order Date]), MAX(superstore[Ship Date]))
  ```
* Established relationships:

  * Active: `Calendar[Date]` ↔ `superstore[Order Date]`
  * Inactive: `Calendar[Date]` ↔ `superstore[Ship Date]`

### 3.3 DAX Measures

* **Revenue**:

  ```DAX
  Revenue = SUM(superstore[Sales])
  ```
* **Profit**:

  ```DAX
  Profit = SUM(superstore[Profit])
  ```
* **Orders**:

  ```DAX
  Total Orders = DISTINCTCOUNT(superstore[Order ID])
  ```
* **Revenue by Ship Date** (using inactive relationship):

  ```DAX
  Revenue by Ship Date = CALCULATE(SUM(superstore[Sales]), USERELATIONSHIP(Calendar[Date], superstore[Ship Date]))
  ```

---

## 4. 📊 Report Design

### Page 1: **Executive Summary**

* KPI Cards: Total Revenue, Total Profit, Total Orders, Total Customers
* Line Chart: Revenue over time (monthly)
* Map: Sales by State
* Bar Chart: Sales by Region

### Page 2: **Product Performance**

* Bar Chart: Sales by Category/Sub-Category
* Table: Top 10 Products by Revenue
* Tree Map: Profit contribution by product

### Page 3: **Customer Insights**

* Donut Chart: Sales by Customer Segment
* Table: Revenue per Customer
* Slicers: Region, Segment

### Page 4: **Shipping Analysis**

* KPI Card: Average Shipping Delay
* Line Chart: Order vs Ship Date trend
* Bar Chart: Avg Shipping Delay by Region

---

## 5. 📈 Insights & Findings

* **West Region** contributes highest revenue
* **Technology** category yields the highest profit margin
* Shipping delays are higher in the **South Region**
* Majority of customers belong to the **Consumer** segment
* Peak sales occur in **November and December**

---

## 6. ✅ Conclusion

The Power BI dashboard delivers key insights to stakeholders, allowing them to:

* Identify top-performing products and regions
* Track profitability over time
* Monitor customer segments
* Optimize logistics by analyzing shipping trends

---

## 7. 📎 Deliverables

* Power BI Report File: `codetech project 3.pbix`
* Project Documentation: `Sales_Dashboard_Documentation.docx`
* PDF Snapshot or PPT of Dashboard visuals (optional)

---

