# AWS Core Services Hands-on Project (ITCS 6190 / 8190 - Cloud Computing for Data Analysis)

## 📘 Overview
This practical lab focuses on utilizing **AWS core services** — **Amazon S3**, **AWS Glue**, **Amazon CloudWatch**, and **Amazon Athena** — to perform analytical tasks on an e-commerce dataset.  
The aim is to build a seamless data workflow that moves data from ingestion to analysis within AWS, producing insights efficiently through SQL-based queries.

---

## 🧩 AWS Services Utilized
- **Amazon S3** – Serves as the storage layer for both raw input and processed data outputs.
- **AWS Glue** – Automatically crawls and structures data into a queryable format.
- **Amazon CloudWatch** – Captures logs and tracks Glue crawler executions.
- **Amazon Athena** – Provides a serverless SQL querying interface for data in S3.

---

## 🗂️ Dataset
**Source:** [Unlock Profits with E-Commerce Sales Data (Kaggle)](https://www.kaggle.com/datasets/thedevastator/unlock-profits-with-e-commerce-sales-data)

This dataset contains detailed records of transactions across multiple product categories and states, making it suitable for examining sales performance, profitability, and growth trends.

---

## ⚙️ Implementation Workflow

### 1. **Amazon S3 Setup**
- Create two buckets:
  - `raw-data-bucket` → stores the uploaded raw CSV file.
  - `processed-data-bucket` → stores query results and refined datasets.
- Upload the CSV file into the raw-data-bucket.

### 2. **IAM Role Configuration**
- Create an **IAM Role** with permissions for:
  - `AmazonS3FullAccess`
  - `AWSGlueServiceRole`
- Assign this role to your Glue crawler to allow S3 and Glue access.

### 3. **Glue Crawler Setup**
- Configure a Glue Crawler with the following:
  - **Data source:** `raw-data-bucket`
  - **Target:** Glue Data Catalog
  - **IAM Role:** the one created in Step 2
- Run the crawler to infer the schema automatically and register the table in the Data Catalog.

### 4. **Monitoring with CloudWatch**
- Open **Amazon CloudWatch** to:
  - Review crawler job logs.
  - Detect potential errors or execution warnings.

### 5. **Querying with Athena**
- Navigate to **Amazon Athena**.
- Select the database created by the Glue Crawler.
- Execute SQL queries to generate sales, discount, and profitability insights.

---

### 📷 Screenshots
<img width="975" height="537" alt="image" src="https://github.com/user-attachments/assets/cbc068d2-54e0-4b96-afe3-7842d5110f5a" />
<img width="975" height="583" alt="image" src="https://github.com/user-attachments/assets/d5676ee3-0488-46a6-a506-e3bff8e04c70" />
<img width="975" height="580" alt="image" src="https://github.com/user-attachments/assets/0ddd41a6-4766-4cb6-aed7-a61a1b893d7d" />
<img width="975" height="581" alt="image" src="https://github.com/user-attachments/assets/78732e98-4245-4849-8e6e-4e1eaa25ae80" />
<img width="975" height="584" alt="image" src="https://github.com/user-attachments/assets/cc7a6bbc-22e6-42e2-80c3-a442b519e835" />


---

## 🧮 SQL Queries Executed in Athena

Each query includes a `LIMIT 10` condition to limit preview rows.

1. **Cumulative Sales by Date (Specific Year)**  
   Calculates cumulative daily sales totals for a chosen year.

2. **Geographical Analysis of Unprofitable Regions**  
   Identifies states with the most negative profitability trends.

3. **Discount vs Profitability Analysis by Sub-Category**  
   Studies how discount variations influence the profit ratio per sub-category.

4. **Top 3 Profitable Products by Category**  
   Uses a ranking function to list the top three profitable products per category.

5. **Monthly Sales and Profit Growth Trends**  
   Evaluates month-to-month changes in total sales and estimated profit.

---

## 📂 Repository Layout

```
AWS-HANDSON-CORE-SERVICES/
├── Output CSV Files/               # Athena query results
│   ├── query1_cumulative_sales.csv
│   ├── query2_unprofitable_states.csv
│   ├── query3_discount_profitability.csv
│   ├── query4_top3_products.csv
│   └── query5_monthly_growth.csv
├── Screenshots.zip                 # Screenshots of AWS services
├── AWS HandsOn Report.pdf          # Project documentation
└── README.md                       # Main report (this file)
```

---

## 📊 Output Summary
All query results were saved as **CSV files** inside the `Output CSV Files` folder. Each file corresponds to one of the analytical SQL queries executed through Amazon Athena.

---

## 📸 Screenshot Collection
Screenshots provided in `Screenshots.zip` illustrate each AWS step:
- **S3 Buckets:** raw and processed storage layers.
- **IAM Role Configuration:** access permissions for Glue crawler.
- **AWS Glue Crawler:** automatic schema creation.
- **CloudWatch Logs:** monitoring crawler activities.
- **Athena Query Execution:** executing SQL statements and viewing output.

---

## 🧠 Key Takeaways
- Learned to integrate multiple AWS services into one analytical pipeline.
- Gained experience in data ingestion, cataloging, and querying using serverless tools.
- Improved ability to monitor and debug with CloudWatch.
- Strengthened understanding of scalable, cost-efficient cloud data workflows.

---

## 📤 Deliverables
This submission includes:
- ✅ CSV outputs from Athena (`Output CSV Files/`)
- ✅ Screenshots archive (`Screenshots.zip`)
- ✅ Project report (`AWS HandsOn Report.pdf`)
- ✅ This README summary

---

## 🧑‍🏫 Course Details
**Course:** ITCS 6190 / 8190 – Cloud Computing for Data Analysis  
**Instructor:** Marco Vieira  
**Semester:** Fall 2025

---

## 🎯 Conclusion
This project demonstrates how AWS services can be connected to form an **end-to-end data analytics pipeline**. By combining S3, Glue, CloudWatch, and Athena, we established a scalable and serverless solution capable of efficiently handling and analyzing large datasets.
