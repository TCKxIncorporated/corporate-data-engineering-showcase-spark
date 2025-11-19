# **Corporate Data Engineering Showcase with Apache Spark**

An end-to-end **data engineering and analytics pipeline** built using **Apache Spark**.  
This project demonstrates real-world ETL workflows, multi-table joins, feature engineering, window functions, partitioned Parquet storage, performance tuning, and distributed analytics — all running inside a **cloud-based Google Colab environment**.

---

## **Project Overview**

This project processes a realistic corporate HR dataset consisting of multiple relational tables:

- `employees.csv`
- `departments.csv`
- `locations.csv`
- `salaries_annual.csv`
- `promotions.csv`
- `org_edges.csv`

Using Apache Spark, the project performs:

- Distributed ETL
- Data cleaning & type handling
- Multi-table joins
- Feature engineering
- Analytical queries
- Window function analysis
- Parquet partitioning & predicate pushdown
- Performance tuning (shuffle partitions, caching)

All code is fully contained in the Colab notebook.

---

## **Architecture**

```
            +--------------------------+
            |      Kaggle Dataset      |
            +------------+-------------+
                         |
                         ▼
             +----------------------+
             |  Spark DataFrames    |
             +---------+------------+
                       |
         +-------------+-----------------------------+
         |       Distributed ETL Pipeline            |
         |   - Multi-table joins                     |
         |   - Cleaning / Feature Engineering        |
         |   - Transformations                       |
         +-------------+-----------------------------+
                       |
                       ▼
            +------------------------------+
            |  Analytical Workloads        |
            |  - Salary insights           |
            |  - Country/Dept comparisons  |
            |  - Promotion effects         |
            |  - YOY salary growth         |
            +------------------------------+
                       |
                       ▼
        +---------------------------------------+
        | Advanced Spark Features               |
        |  - Window functions                   |
        |  - Parquet partitioning               |
        |  - Predicate pushdown                 |
        |  - Shuffle tuning / caching           |
        +---------------------------------------+
```

---

## **Key Features**

### End-to-End Spark Pipeline

Complete workflow from ingestion → transformation → analytics → optimization.

### Multi-table ETL

6 CSV files joined into a unified employee–year fact table.

### Feature Engineering

- Salary band
- Cost-adjusted salary (COLI normalized)
- Experience years
- Seniority flags
- Number of promotions
- Team size per manager

### Window Function Analytics

- Ranking top earners
- Ranking within countries
- Running average salary
- Year-over-year salary growth (lag)

### Performance Optimization

- Caching
- Changing shuffle partitions
- Measuring execution time
- Partitioned Parquet output

### Cloud Execution

100% executed in Google Colab.

---

## **Dataset Description**

The dataset simulates a corporate HR system, generated via the Faker library but structured like a real enterprise data warehouse.

| File                  | Description                               |
| --------------------- | ----------------------------------------- |
| `employees.csv`       | Employee demographics and job information |
| `departments.csv`     | Department names and categories           |
| `locations.csv`       | City, country, and cost-of-living index   |
| `salaries_annual.csv` | Salary history from 2014–2025             |
| `promotions.csv`      | Promotion events                          |
| `org_edges.csv`       | Manager → employee relationships          |

---

## **Installation & Running the Notebook**

### **1. Clone the Repository**

```bash
git clone https://github.com/yourusername/corporate-data-engineering-showcase-spark.git
cd corporate-data-engineering-showcase-spark
```

### **2. Open the Notebook in Google Colab**

Click the badge below to run it instantly:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](YOUR_COLAB_LINK_HERE)

### **3. Install Dependencies**

The notebook automatically runs:

```bash
pip install pyspark kagglehub pandas
```

### **4. Run SparkSession**

The notebook starts Spark automatically and loads all data.

---

## **Analytical Tasks Performed**

### Salary Insights

- Salary by department
- Salary by country
- Gender salary gap
- Senior vs non-senior differences
- Cost-of-living–adjusted salary

### Promotion Analysis

- Promotions vs salary growth
- Promotions vs seniority
- Promotion frequency distribution

### Time-Based Analytics

- Year-over-year salary change
- Salary progression per employee
- Running average salary per employee

---

## **Advanced Spark Features Demonstrated**

### 1. Window Functions

```python
rank().over(Window.partitionBy("year","department").orderBy(desc("salary")))
lag("salary").over(Window.partitionBy("employee_id").orderBy("year"))
```

### 2. Partitioned Parquet Output

Data partitioned by year:

```
emp_year_parquet/
    year=2020/
    year=2021/
    ...
```

### 3. Predicate Pushdown

Spark only reads relevant partitions:

```python
spark.read.parquet(path).filter("year = 2020")
```

### 4. Performance Tuning

- Caching
- Changing `spark.sql.shuffle.partitions`
- Measuring execution time

---

## **Results Summary**

- Significant salary variation across departments & countries
- Promotions strongly correlate with salary increases
- Year-over-year salary growth reveals employees with rapid increases
- Cost-of-living adjustment reverses certain salary rankings
- Partition pruning boosted performance for filtered queries
- Caching and shuffle tuning reduced groupBy execution time

---

## **Folder Structure**

```
project/
│
├── corporat data analysis showcase using spark.ipynb
├── README.md
│

│
├── slides/
│   └── Big Data Tool Apach Spark presentation.pptx
│
└── sample_data/
    ├── employees_sample.csv
    ├── departments_sample.csv
    └── ...
```

---

## **Author**

**Naif**  
Computer Science @ KFUPM  
Data Engineering • AI • Software Engineering
