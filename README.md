# CAI4_AIS5_G1_Transport_Analysis

## Project Overview

This project focuses on analyzing public transportation datasets using Azure cloud technologies. The system was designed to ingest, process, transform, analyze, and visualize transport trip data in order to generate operational and business insights.

The project follows a modern cloud analytics architecture using:

* Azure Data Lake Storage Gen2 (ADLS)
* Azure Synapse Analytics
* Apache Spark
* Serverless SQL
* Power BI

The final solution supports batch ingestion, automated data pipelines, parquet-based analytics, SQL querying, and dashboard visualization.

---

# Project Architecture

Raw CSV Transport Data
→ Azure Data Lake Storage Gen2 (Raw Layer)
→ Synapse Pipelines (Batch Ingestion & Validation)
→ Apache Spark Notebooks (CSV → Parquet Transformation)
→ Curated Parquet Layer
→ Serverless SQL Analytics Views
→ Power BI Dashboards

---

# Technologies Used

* Azure Synapse Analytics
* Azure Data Lake Storage Gen2
* Apache Spark (PySpark)
* Synapse Pipelines
* Serverless SQL Pool
* Power BI
* GitHub

---

# Dataset Description

The project uses transportation datasets containing:

* Trip information
* Route information
* Station information

Main columns include:

* trip_id
* route_id
* vehicle_id
* pickup_station
* dropoff_station
* pickup_zone
* dropoff_zone
* trip_distance_km
* fare_egp
* payment_method
* passenger_count
* trip_datetime
* day_of_week
* hour_of_day

---

# Medallion Architecture

## Raw Layer

Stores original uploaded CSV files.

Folders:

* raw/trips/
* raw/routes/
* raw/stations/

---

## Curated Layer

Stores cleaned and transformed datasets.

Transformations performed:

* duplicate removal
* schema validation
* CSV to Parquet conversion

Folders:

* curated/trips/
* curated/routes/
* curated/stations/

---

## Curated Parquet Layer

Optimized parquet datasets for analytics and querying.

Folders:

* curated_parquet/trips/
* curated_parquet/routes/
* curated_parquet/stations/

---

# Pipeline Workflow

A Synapse pipeline was created to automate batch ingestion.

Pipeline Features:

* file ingestion
* metadata validation
* file size validation
* error handling
* scheduled trigger execution
* automated copying into curated layer

Trigger:

* Daily scheduled trigger for automated ingestion.

---

# Apache Spark Processing

PySpark notebooks were used to:

* read CSV files from ADLS
* clean and validate data
* remove duplicates
* transform data
* write parquet outputs

Example transformation:

* deriving analytical fields such as hour_of_day and day_of_week

---

# SQL Analytics

Serverless SQL was used to query parquet datasets directly.

Analytical queries include:

* Peak rush hours
* Busiest routes
* Busiest pickup stations
* Busiest dropoff stations
* Revenue analysis
* Passenger volume analysis
* Weekday vs weekend demand analysis
* Zone-based congestion analysis

Views were created to support Power BI integration.

Example Views:

* vw_peak_hours
* vw_busiest_routes
* vw_weekday_weekend
* vw_revenue_analysis

---

# Automation & Monitoring

The project includes automation using:

* Synapse pipeline triggers
* Scheduled refresh workflows
* Automated parquet refresh process

This ensures that analytics dashboards reflect the latest available transportation data.

---


# Repository Structure

The repository is connected directly to Azure Synapse Git integration and contains Synapse workspace artifacts.

```text
CAI4_AIS5_G1_Transport_Analysis/
│
├── credential/              # Synapse credentials and workspace identity metadata
├── dataset/                 # Integration datasets for raw and curated transport files
├── integrationRuntime/      # Synapse integration runtime configuration
├── linkedService/           # Linked services for ADLS and Synapse connections
├── notebook/                # Apache Spark notebooks for CSV → Parquet processing
├── pipeline/                # Synapse ingestion and transformation pipelines
├── sqlscript/               # SQL analytics scripts and views
├── trigger/                 # Scheduled pipeline triggers
├── publish_config.json      # Synapse publish configuration
└── README.md
```


# Conclusion

This project demonstrates the implementation of a scalable cloud-based transportation analytics platform using Azure technologies. The solution integrates data engineering, big data processing, SQL analytics, automation, and business intelligence visualization into a complete end-to-end analytics workflow.
