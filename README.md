Research Project: Philippine Agri-Farmgate and Retail Price Analysis

An automated data pipeline and analytical API designed to examine the relationship between farmgate prices and retail prices for key agricultural commodities in the Philippines (2021–2025).

📌 Project Overview
This project addresses the transparency gap in the Philippine agricultural supply chain. By integrating datasets from the Philippine Statistics Authority (PSA), the system provides real-time analysis of marketing margins and uses econometric tests to determine price transmission efficiency.

Key Objectives:
- Standardization: Transform disparate CSV/Excel datasets into a unified "Long Format" time-series.
- Margin Analysis: Calculate the "Marketing Margin" and "Farmer's Share" for 8 core commodities (Banana, Mango, Pineapple, Coconut, Cassava, Ube, Palay, and Corn).
- Predictive Analytics: Utilize Granger Causality to statistically verify if farmgate price fluctuations predict retail price changes.

🛠️ Technical Stack
Language: Python 3.10+
Framework: FastAPI (Backend API)
Data Science: Pandas, NumPy
Statistics: Statsmodels (Vector Autoregression & Granger Causality)
Documentation: Swagger UI / OpenAPI

📂 File Structure
Plaintext
├── FINAL Datasets- Farmgate & Retail Prices(Average, Margin)  # raw PSA datasets
├── standardize_data.py      # Script to clean and merge raw PSA datasets
├── main.py                  # FastAPI Backend containing analysis logic
├── Standardized_Farmgate_Retail_Final_Data.csv  # The processed, clean dataset
└── README.md                # Project documentation

🚀 Getting Started
1. Installation
Clone the repository and install the required dependencies:
Bash
pip install fastapi uvicorn pandas numpy statsmodels

2. Data Standardization
Before running the API, process the raw data:
Bash
python standardize_data.py

3. Running the API
Launch the FastAPI server:
Bash
python main.py

Once running, access the interactive documentation at: http://127.0.0.1:8000/docs

📊 API Endpoints & Analysis Features
1. Marketing Margin Analysis
Endpoint: /analysis/margin/{commodity}
Calculates the price spread and the percentage of the final price that actually returns to the farmer.
Formula: Margin = RetailPrice - FarmgatePrice
Formula: Farmer's Share = (FarmgatePrice / RetailPrice) x 100

2. Granger Causality Test
Endpoint: /analysis/causality/{commodity}
Determines if there is a lead-lag relationship between farmgate and retail prices.
Significance: A p-value < 0.05 suggests that farmgate prices are a significant predictor of retail trends, indicating a responsive supply chain.

3. Time-Series Trends
Endpoint: /analysis/trends
Aggregates data by year (YE) or month to visualize long-term inflation and seasonal price spikes.

📈 Economic Significance
This tool helps researchers and policymakers identify:
Market Inefficiency: High margins that suggest excessive middleman costs.
Price Rigidity: Commodities where retail prices remain high even when farmgate prices drop.
Food Security: Identifying volatility in staple crops like Palay and Corn.
