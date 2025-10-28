# 🧠 Data Observability Framework (Spark + Airflow + Grafana)

A lightweight, end-to-end **data observability prototype** designed to monitor partition health, data quality, and performance metrics across Spark, Airflow, and Snowflake pipelines.

Built with a focus on **real-time visibility**, **cost optimization**, and **data reliability** — similar to enterprise-grade monitoring systems at Netflix or ThoughtWorks.

---

## 📂 Project Structure


---

## ⚙️ Key Components

| Component | Description |
|------------|-------------|
| **Airflow Metrics Collector** | Extracts DAG run stats and task durations from Airflow metadata DB |
| **Spark Partition Monitor** | Tracks small files, partition imbalance, shuffle inefficiencies |
| **Data Quality Collector** | Computes null %, duplicate %, and rule-based anomalies |
| **Prometheus Push Gateway** | Pushes job metrics for real-time tracking |
| **Grafana Dashboards** | Visualizes file counts, partition health, and data latency trends |

---

## 🧩 Example Metrics Pushed to Prometheus

| Metric | Description |
|---------|-------------|
| `spark_s3_avg_file_size_bytes` | Average file size in S3/Delta tables |
| `spark_s3_small_file_count` | Count of files < 50 MB |
| `airflow_task_duration_seconds` | Average task execution time per DAG |
| `dq_null_ratio` | Ratio of null values by column/table |
| `dq_duplicate_ratio` | Duplicate detection metric |
| `pipeline_cost_estimate_usd` | Cost proxy metric for Snowflake/Databricks workloads |

---

## 🧠 Example Use Case

1. A Spark job finishes writing data to S3.  
2. `spark_partition_monitor.py` collects S3 file metadata via Boto3.  
3. Metrics (avg file size, small file count) are pushed to Prometheus.  
4. Grafana displays live dashboards + alerts for threshold breaches.  

Example alert rule:

