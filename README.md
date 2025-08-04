# ✈️ Travel Data Warehouse Project

A structured, cloud-based data warehouse pipeline that transforms messy travel-related CSV files into a clean, queryable format using AWS services and PostgreSQL/Redshift.

---

## ✨ Features

- Converts raw, denormalized CSV files into 3NF structure
- Loads cleaned data into Amazon Redshift and PostgreSQL
- Uses AWS Glue, S3, Redshift, and Athena for a modern warehouse workflow
- Visualized insights with Power BI dashboards
- Well-organized data schema following best normalization practices

---

## 🎯 Objective

To build a simple yet production-style data warehouse from travel-related raw data. The goal is to show how we can clean, normalize, store, and analyze data efficiently using cloud tools (AWS) and Python.

---

## 🏗️ Architecture Overview

![architecture](https://github.com/user-attachments/assets/ab1c2acf-4af4-4cd8-bd70-1da972a2a6f7)


1. **Raw CSV files** from a Kaggle dataset stored locally  
2. **Data cleaning and 3NF normalization** done using Python (Pandas)  
3. **Cleaned data stored** as CSV files in `data_3nf/` folder  
4. **Uploaded to S3** and **loaded into Redshift** using `COPY` commands  
5. **AWS Glue Crawlers** infer schema from S3 and make it queryable via Athena  
6. **Power BI** connects to Redshift/PostgreSQL for business dashboards

---

## 🛠️ Tech Stack

| Tool/Service    | Purpose                          |
|-----------------|----------------------------------|
| Python + Pandas | Cleaning & normalizing CSV data  |
| AWS S3          | Storage for raw and clean files  |
| AWS Glue        | Schema crawler and data catalog  |
| Amazon Redshift | Cloud data warehouse             |
| Amazon Athena   | SQL query engine over S3         |
| PostgreSQL      | Local data warehouse alternative |
| Power BI        | Dashboard for data visualization |

---

## 🧱 Database Schema (3NF)

Main entities after normalization:
- **User**
- **Company**
- **Gender**
- **Location**
- **Hotel**
- **Accommodation**
- **Travel**
- **FlightType**
- **Agency**

👉 See full schema in [`data schema travel data.txt`](./data%20schema%20travel%20data.txt)

---

## 📂 Project Structure

travel-data-warehouse/
│
- ├── data_raw/ # Original Kaggle CSVs
- ├── data_3nf/ # Cleaned, normalized 3NF CSVs
- ├── aws_redshift_15_06_2025 # Python ETL scripts 
- ├── aws_glue_script.txt # Glue + Redshift COPY commands
- ├── travel_dataset_dashboard.pbix # Power BI file
- ├── README.md


---

## 🔁 ETL Workflow

### 📥 Extract (Python)
- Load raw CSVs using `pandas`
- Identify issues (missing values, data types)

### 🔧 Transform (Pandas)
- Normalize into multiple related tables (3NF)
- Split columns into logical entities like `user`, `hotel`, `travel`, etc.

### 📤 Load
- Upload normalized CSVs to **S3**
- Use AWS **Glue** to infer schema and crawl
- Load into **Redshift** using `COPY` commands from Python
- Optionally, load into **PostgreSQL** for local querying

---

## 📊 Power BI Dashboard

- Flight type vs total revenue
- Hotel pricing trends
- User travel patterns
- Distance vs time vs price analysis
- Filterable visuals by location, date, gender

📁 File: `travel_dataset_dashboard.pbix`

---

## 🔐 IAM Permissions Used

- `AmazonS3FullAccess`
- `AWSGlueServiceRole`
- `AmazonAthenaFullAccess`
- `AmazonRedshiftFullAccess`

---

## 🧪 How to Run Locally

1. Clone the repo  
2. Place raw Kaggle CSVs in `/data_raw`  
3. Run the pandas scripts to clean and generate `/data_3nf`  
4. (Optional) Push to S3 using boto3  
5. Use `aws_glue_script.txt` to create tables and copy to Redshift  
6. Open Power BI and connect to Redshift/PostgreSQL

---

## 📌 Learnings / Highlights

- Implemented real-world normalization logic
- Built a warehouse-like architecture using AWS
- Learned to bridge between local and cloud data flows
- Visualized business-level insights in Power BI
- Managed IAM roles, S3 integration, Glue cataloging

---

## 📎 Related Files

- [`aws_glue_script.txt`](./aws%20glue%20script.txt): Redshift table creation + copy commands
- [`data schema travel data.txt`](./data%20schema%20travel%20data.txt): Full schema definition
- `travel_dataset_dashboard.pbix`: Final Power BI file

