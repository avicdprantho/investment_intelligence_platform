#  Investment Intelligence Platform  
##Problem statement
Build an end-to-end investment intelligence platform that combines financial performance data (yfinance) and corporate governance data (Companies House) to help analysts identify, score, and monitor UK listed companies for investment suitability.

## Architecture
Ingestion → Ingest raw data and save from two API's ( yfinance & companies house)
Bronze → Convert  raw data to delta table and added two columns 1. timestamp and meta_data 
Silver → 
Gold → (Medallion Architecture)