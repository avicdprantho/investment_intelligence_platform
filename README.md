# Investment Intelligence Platform

## Overview
An end-to-end data engineering platform that integrates UK company registry data 
and financial market data to build a unified company intelligence and risk 
analytics system for LSE-listed equities.

## Problem Statement
Company-related data is fragmented across multiple systems:
- **Legal registry data** — Companies House (officers, filings, company info)
- **Financial market data** — Yahoo Finance (prices, fundamentals, ratios)

This fragmentation makes it difficult to assess company health, risk, and 
performance in a unified way.

## Solution
This platform builds a unified data pipeline that:
- Ingests data from multiple external APIs
- Cleans and standardises datasets using a Medallion architecture
- Resolves entity mismatches across sources (ticker ↔ company number mapping)
- Generates analytical and risk-based insights at the gold layer

## Architecture
The system follows a **Medallion Architecture** on Databricks / Delta Lake:

### Layers
| Layer | Purpose |
|-------|---------|
| Bronze | Raw JSON data preserved as Delta tables, no transformation |
| Silver | Cleaned, typed, and structured data with SCD1 merges |
| Gold | Business intelligence, risk scoring and cross-company analytics |

## Data Sources
| Source | Data |
|--------|------|
| Companies House API | Company info, officers, filing history |
| Yahoo Finance API | Stock prices, balance sheet, income statement, cashflow, key stats |

## Companies Tracked
20 UK LSE-listed companies:

| Ticker | Company |
|--------|---------|
| TSCO.L | Tesco |
| LLOY.L | Lloyds Banking Group |
| AZN.L | AstraZeneca |
| NWG.L | NatWest Group |
| SHEL.L | Shell |
| SBRY.L | Sainsbury's |
| AV.L | Aviva |
| RR.L | Rolls-Royce |
| BT-A.L | BT Group |
| ABF.L | Associated British Foods |
| DGE.L | Diageo |
| GSK.L | GSK |
| HSBA.L | HSBC |
| IMB.L | Imperial Brands |
| LGEN.L | Legal & General |
| VOD.L | Vodafone |
| NG.L | National Grid |
| RKT.L | Reckitt |
| RIO.L | Rio Tinto |
| PRU.L | Prudential |

## Key Features
- Multi-source API ingestion with rate limiting
- Bronze layer: raw JSON preserved in Delta tables
- Silver layer: cleaned, typed, SCD1 merged tables
- Entity resolution: company number ↔ stock ticker mapping
- Financial time-series analysis (balance sheet, cashflow, income statement)
- Governance data: officer history and board composition
- Company risk scoring engine (gold layer — in progress)

## Tech Stack
- **Python** — ingestion and transformation logic
- **Databricks** — compute and orchestration
- **Delta Lake** — storage with ACID transactions
- **yfinance** — Yahoo Finance API wrapper
- **Companies House API** — UK company registry

## Project Structure
├── ingestion/
│   ├── yfinance_ingestion.py
│   └── companies_house_ingestion.py
├── bronze/
│   └── bronze_reader.py
├── silver/
│   ├── silver_balance_sheet.py
│   ├── silver_cashflow.py
│   ├── silver_income_statement.py
│   ├── silver_stats.py
│   └── silver_officers.py
└── gold/
└── (in progress)



## Future Improvements
- Gold layer: company risk scoring and cross-company benchmarking
- News sentiment ingestion — Yahoo Finance News integration for event detection
- Real-time streaming ingestion
- Machine learning-based risk prediction
- Interactive dashboards
- Expanded global company coverage
