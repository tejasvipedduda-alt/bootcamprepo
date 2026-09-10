# bootcamprepo
This repo contains three bootcamp projects 

# Project1 
Real-Time E-Commerce Analytics Engine (Retail Rocket)
An end-to-end near-real-time streaming and batch analytics pipeline built on Azure and Azure Databricks using the Medallion Architecture (Delta Lake) and Unity Catalog.

## Business Objectives Addressed
**Catalog Health & Pricing History:** Tracks changes in item pricing and availability over time using dimension snapshots.

**Real-Time Conversion Funnel Monitoring:** Computes live conversion metrics (views ➔ add-to-carts ➔ transactions) in stream processing rather than waiting for end-of-day batch reports.

**Cart Abandonment Detection:** Identifies active user sessions that executed an add-to-cart event without completing a transaction within a specified sliding time window.

**Trending Items:** Calculates rolling Top-N most viewed and most added-to-cart items over sliding windows (e.g., last 15-minute window).

**Revenue Attribution by Category:** Joins streaming transaction events with category dimensions to provide near-real-time revenue metrics broken down by category.

## Tech Stack & Tools
**Cloud & Platform:** Azure, Databricks Workspace

**Data Lakehouse:** Delta Lake (Bronze, Silver, Gold Layers)

**Governance & Security:** Unity Catalog (Storage Credentials, Access Connector, External Locations, Volumes)

**Streaming & Ingestion:** Azure Event Hubs, Spark Structured Streaming, PySpark

**Data Processing:** PySpark, Spark SQL, Structured Streaming (Watermarking, Checkpointing, Micro-batching)

**Serving & BI:** Databricks SQL Warehouse, Power BI

**CI/CD & Version Control:** Databricks Repos, GitHub

**Orchestration:** Databricks Workflow Jobs

## Architecture & Data Flow
[ Kaggle Events Data ] ➔ [ Producer Script ] ➔ [ Azure Event Hubs ] 
                                                      │
                                           (Spark Structured Streaming)
                                                      ▼
[ Kaggle Dimensions ]  ➔ [ ADLS Gen2 / Volumes ] ➔ [ Bronze Delta ] ➔ [ Silver Delta ] ➔ [ Gold Delta ] ➔ [ Databricks SQL ] ➔ [ Power BI ]

## Key Features
* Incremental data loading using Delta Lake merge operations.
* Optimized Spark performance through partition tuning and broadcast joins.
