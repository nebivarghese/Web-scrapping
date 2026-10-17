# Google-Maps-Business-Scraper

A Python-based data engineering project that collects business data from Google Maps using SerpApi, performs data cleaning and deduplication, caches API responses to reduce API costs, and exports validated gym leads to CSV and SQL Server.

## Project Objective

The goal of this project is to automate the collection of gym business information across Kochi, Kerala and create a clean lead dataset for business analysis, sales outreach, and reporting purposes.

## Topics 

- python
- web-scraping
- google-maps
- serpapi
- data-engineering
- pandas
- sql-server
- api-integration
- data-cleaning
- lead-generation

## Kochi Gym Data Collector

### Overview

This project collects gym business listings across Kochi, Kerala using Google Maps data through SerpApi.

The pipeline is designed to:
- Minimize API credit usage
-	Avoid duplicate businesses
-	Support resumable execution
-	Cache every API response
-	Export clean business leads
-	Load results into SQL Server

## Architecture

- Config
  
│

▼

- Area Grid Generator
  
│

▼

-SerpApi Requests
│
▼
Raw JSON Cache
│
▼
Data Extraction
│
▼
Data Cleaning
│
▼
Deduplication
│
▼
CSV Export
│
▼
SQL Server

## Features

### 1. Cost Optimization
Every API response is cached locally.
Benefits:
•	No duplicated API charges
•	Safe re-runs
•	Faster execution
Python
CACHE_DIR

### 2. Pagination Support
Collects multiple pages per search location.
Python
PAGES_PER_QUERY = 5

### 3. Retry Mechanism
Handles:
•	Rate limits
•	Temporary server failures
•	Network interruptions
Python
MAX_RETRIES = 4

### 4. Geographic Coverage
Searches multiple Kochi areas:
•	Ernakulam
•	Edappally
•	Kakkanad
•	Vyttila
•	Fort Kochi
•	Kalamassery
•	Angamaly
•	Aluva
•	Tripunithura
and more.
________________________________________
### 5. Deduplication Strategy
Businesses found through multiple searches are merged using:
Python
place_id
Fallback:
Python
data_id
Fallback:
Python
name + address
 
________________________________________
### 6. Data Cleaning
The pipeline normalizes:
Phone Numbers
Converts:

+91 9876543210
09876543210
91-9876543210
Into:

+919876543210
________________________________________
### Website URLs
Removes

UTM Parameters
Tracking Parameters
Example:

https://site.com?utm_source=google
↓
https://site.com
 
________________________________________
### 7. Lead Quality Scoring
Each business receives a score based on:
•	Phone availability
•	Website presence
•	Mobile number detection
Python
contact_score
 
________________________________________
### Technologies Used
**Technology**	**Purpose**
Python	Development
Pandas	Data Processing
Requests	API Consumption
SerpApi	Google Maps Search
SQLAlchemy	Database Layer
PyODBC	SQL Server Connectivity
SQL Server	Storage
TQDM	Progress Tracking


[Web_scraping](https://colab.research.google.com/notebooks/snippets/importing_libraries.ipynb)
