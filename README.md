# Investment Intelligence Platform

## Overview

An enterprise-style investment intelligence platform built using PySpark, Databricks, Delta Lake, and Medallion Architecture principles.

The platform unifies UK company registry data and stock market financials into a centralized analytics model for investment screening, governance monitoring, and financial risk analysis.

It resolves cross-system entity mapping challenges and transforms nested API data into analytics-ready Delta tables for downstream BI and investment insights.

---

## Problem Statement

Company-related data is fragmented across multiple systems with incompatible identifiers, inconsistent schemas, and deeply nested structures.

* Companies House provides legal and governance data (company profiles, officers, filings)
* Yahoo Finance provides financial market data (balance sheets, income statements, cashflow, valuation metrics)

However:

* No shared identifier exists between systems
* Data is not analytics-ready (nested structs + JSON arrays)
* Cross-source analysis requires heavy manual processing

This leads to duplicated effort, inconsistent metrics, and no single source of truth.
This fragmentation prevents analysts from combining financial performance, market behaviour, and governance signals into a single investment view, limiting the ability to consistently assess company health and risk.


---

## Why This Project Matters

Business data is often scattered across disconnected systems.

This project demonstrates how modern data engineering solves that problem through:

* Multi-source API ingestion
* Medallion Architecture
* Entity resolution (ticker ↔ company number)
* Nested JSON transformation
* Analytics-ready data modelling

**Result:** A unified, queryable source of truth for investment and risk analysis.

---

## Solution

The platform implements an end-to-end data engineering pipeline:

* Ingests raw data from Companies House and Yahoo Finance into Bronze Delta tables (immutable JSON storage)
* Transforms and cleans data using Medallion Architecture (Bronze → Silver → Gold)
* Resolves entity mismatches via ticker ↔ company number mapping
* Converts nested structs and arrays into relational tables using PySpark
* Applies SCD Type 1 merges for consistent, idempotent datasets
* Generates Gold-layer insights for financial health, governance, and risk scoring

---

## Architecture

The system follows a Medallion Architecture on Databricks / Delta Lake.

See `architecture.md` for full system design.

* **Bronze Layer** → Raw API ingestion and immutable JSON storage
* **Silver Layer** → Cleaned, standardized, analytics-ready data
* **Gold Layer** → Investment insights, BI metrics, and risk scoring

---

## Data Sources

| Source              | Data                                                  |
| ------------------- | ----------------------------------------------------- |
| Companies House API | Company info, officers, filing history                |
| Yahoo Finance API   | Stock data, financial statements, cashflow, key stats |

---

## Companies Tracked

20 UK LSE-listed companies

---

## Key Features

* Multi-source API ingestion with rate limiting
* Bronze layer raw JSON storage in Delta tables
* Silver layer cleaned, typed, SCD Type 1 tables
* Entity resolution (company number ↔ ticker mapping)
* Financial time-series modelling
* Governance and officer history analysis
* Risk scoring engine (Gold layer)

---

## Tech Stack

* Python / PySpark — data ingestion and transformation
* Databricks — distributed processing and orchestration
* Delta Lake — ACID-compliant lakehouse storage
* Unity Catalog — data governance and cataloging
* yfinance API — financial data ingestion
* Companies House API — UK registry data

---

## Business Use Cases

* Investment screening across UK listed companies
* Financial risk and leverage analysis
* Governance and board monitoring
* Cross-company financial comparison
* Compliance and filing pattern analysis
* BI dashboards and reporting

---

## Outputs

* Unified investment intelligence dataset
* Silver Delta tables (analytics-ready)
* Ticker ↔ company mapping model
* Time-series financial datasets
* Governance and officer history tables
* Gold-layer risk scoring models (in progress)

---

## Future Improvements

* Gold layer: advanced company risk scoring
* News sentiment analysis (market event detection)
* Real-time streaming ingestion
* ML-based financial risk prediction
* Interactive dashboards
* Expansion to global equities
