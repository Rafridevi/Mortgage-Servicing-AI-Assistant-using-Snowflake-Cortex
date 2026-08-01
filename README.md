# Mortgage Servicing AI Assistant using Snowflake Cortex

## Architecture Overview

This project demonstrates an end-to-end **Data Engineering + AI**
solution built on **Snowflake Cortex**. Mortgage datasets are ingested
into Snowflake, transformed through layered schemas, exposed through
analytics views, and queried using natural language via Cortex Agent.

------------------------------------------------------------------------

## Architecture

``` text
                 User
                   │
                   ▼
             Cortex Agent
                   │
      ┌────────────┴────────────┐
      │                         │
      ▼                         ▼
Cortex Analyst           Cortex Search
      │                         │
      ▼                         ▼
 Semantic View          Search Service
      │
      ▼
Analytics Views
      │
      ▼
CURATED Schema
      │
Streams + Tasks
      │
      ▼
RAW Schema
      │
      ▼
Internal Stage
      │
      ▼
Mortgage CSV Files
```

------------------------------------------------------------------------

## Project Layers

### 1. Internal Stage

-   Stores mortgage CSV files
-   Loaded using `COPY INTO`

### 2. RAW Schema

-   Landing zone
-   Stores source data without transformation

### 3. CURATED Schema

-   Cleansed and standardized data
-   Removes duplicates
-   Applies data quality checks

### 4. ANALYTICS Schema

Contains reporting views: - VW_MORTGAGE_ANALYTICS - VW_LOAN_PORTFOLIO -
VW_PAYMENT_SUMMARY - VW_DEFAULT_BORROWERS - VW_INVESTOR_SUMMARY -
VW_SERVICER_PERFORMANCE

### 5. Streams

-   Captures INSERT, UPDATE and DELETE changes
-   Supports incremental processing

### 6. Tasks

-   Automates scheduled refreshes
-   Executes transformation pipelines

### 7. Semantic View

Maps technical columns into business-friendly concepts for AI.

### 8. Cortex Analyst

Converts natural language into SQL.

Example: \> "Show all default borrowers."

### 9. Cortex Search

Searches mortgage policies, servicing guides and indexed documents.

### 10. Cortex Agent

Coordinates Cortex Analyst and Cortex Search to answer user questions.

------------------------------------------------------------------------

## Technology Stack

  Component             Technology
  --------------------- ---------------------------
  Cloud Data Platform   Snowflake
  Data Ingestion        Internal Stage, COPY INTO
  Data Transformation   SQL
  CDC                   Streams
  Scheduling            Tasks
  AI                    Snowflake Cortex
  NL-to-SQL             Cortex Analyst
  Semantic Layer        Semantic View
  Search                Cortex Search
  UI                    Streamlit (Optional)
  Version Control       GitHub

------------------------------------------------------------------------

## Repository Structure

``` text
Mortgage-Servicing-AI-Cortex/
├── 01_Database_Setup
├── 02_File_Formats_and_Stages
├── 03_Tables
├── 04_Data_Load
├── 05_Curated
├── 06_Analytics_Views
├── 07_Streams
├── 08_Tasks
├── 09_Cortex_Search
├── 10_Semantic_View
├── 11_Cortex_Agent
├── 12_Streamlit_UI
└── datasets
```





https://github.com/user-attachments/assets/d37f1d3b-9f7a-4f10-ac75-253271dac72f


