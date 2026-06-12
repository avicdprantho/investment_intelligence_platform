# Investment Intelligence Platform

## Overview
An enterprise-style investment intelligence platform built using PySpark,
Databricks, Delta Lake, and Medallion Architecture principles.

The platform unifies UK company registry data and stock market financials
into a centralized analytics model that supports investment screening,
governance monitoring, and financial risk analysis.

The solution resolves cross-system entity mapping challenges and transforms
nested API data into analytics-ready Delta tables for downstream BI and
investment insights.


## Problem Statement

Company-related data is fragmented across multiple systems with incompatible
identifiers, inconsistent schemas, and deeply nested structures.

* **Companies House** provides legal and governance data such as company
  profiles, officer appointments, and filing history.
* **Yahoo Finance** provides financial market data including balance sheets,
  income statements, cash flow, and market valuation metrics.

However, neither source exposes a shared identifier, making cross-source
analysis difficult. In addition, the raw API responses are not analytics-ready:
financial statements are delivered as nested timestamp-based structs, while
governance records arrive as large embedded JSON arrays.

As a result, analysts cannot efficiently evaluate company performance,
financial stability, and governance risk within a single unified model.
Teams must repeatedly perform manual data preparation, leading to duplicated
effort, inconsistent metrics, and no centralized source of truth.

## Why This Project Matters

Business data is often spread across disconnected systems with incompatible
identifiers and inconsistent structures.

This project demonstrates how data engineering solves that challenge through:

* Multi-source API ingestion
* Medallion Architecture
* Entity resolution (ticker ↔ company number)
* Nested JSON transformation
* Analytics-ready data modelling

The result is a unified and queryable source of truth for investment and
risk analysis.


## Solution

The platform implements an end-to-end data engineering pipeline that unifies
financial, market, and governance datasets into a centralized analytics model.

Ingests raw data from Companies House and Yahoo Finance APIs into Bronze
Delta tables while preserving immutable JSON records
Cleans, standardises, and transforms nested API responses using a
Medallion Architecture (Bronze → Silver → Gold)
Resolves cross-system entity mismatches through centralized ticker ↔
company number mapping logic
Converts deeply nested structs and arrays into analytics-ready relational
tables using PySpark transformations
Applies SCD Type 1 merge logic to maintain consistent and idempotent
datasets
Generates Gold-layer investment insights including financial health,
governance stability, and risk-oriented company analysis

## Architecture

The system follows a **Medallion Architecture** on Databricks / Delta Lake:

See architecture.md for the complete system design, data flow, and table structure.

* **Bronze Layer** → Raw API ingestion and immutable JSON storage
* **Silver Layer** → Cleaned, standardized, and analytics-ready data
* **Gold Layer** → Investment insights, business intelligence, and risk scoring



## Data Sources

| Source | Data |
|--------|------|
| Companies House API | Company info, officers, filing history |
| Yahoo Finance API | Stock prices, balance sheet, income statement, cashflow, key stats |

## Companies Tracked
20 UK LSE-listed companies:

## Key Features

- Multi-source API ingestion with rate limiting
- Bronze layer: raw JSON preserved in Delta tables
- Silver layer: cleaned, typed, SCD1 merged tables
- Entity resolution: company number ↔ stock ticker mapping
- Financial time-series analysis (balance sheet, cashflow, income statement)
- Governance data: officer history and board composition
- Company risk scoring engine (gold layer )

## Tech Stack

* **Python / PySpark** — data ingestion and transformation pipelines
* **Databricks** — distributed data processing and orchestration
* **Delta Lake** — ACID-compliant lakehouse storage
* **Unity Catalog** — centralized data governance and cataloging
* **yfinance API** — stock market and financial data ingestion
* **Companies House API** — UK company registry and governance data

## Business Use Cases

* Investment screening across UK listed companies
* Financial risk and leverage analysis
* Governance monitoring using officer activity and board changes
* Cross-company financial comparison
* Compliance and filing pattern analysis
* Centralized analytics for BI dashboards and reporting

## Outputs

* Unified investment intelligence dataset
* Analytics-ready Silver Delta tables
* Ticker ↔ company number mapping model
* Time-series financial statements by fiscal year
* Queryable governance and officer history records
* Gold-layer investment and risk scoring models *(in progress)*



## Future Improvements
- Gold layer: company risk scoring and cross-company benchmarking
- News sentiment ingestion — Yahoo Finance News integration for event detection
- Real-time streaming ingestion
- Machine learning-based risk prediction
- Interactive dashboards
- Expanded global company coverage
