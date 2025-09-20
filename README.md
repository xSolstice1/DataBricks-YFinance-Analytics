# Stock Data Analysis with Databricks

This repository contains a Databricks-based workflow to ingest, transform, and visualize stock market data using Yahoo Finance.

The project consists of three main components:

1. **Data Ingestion** (`01_data_ingestion`)
2. **Data Transformation for Analytics** (`02_transformation_for_analytics`)
3. **Analytical Dashboard** (`03_analytical_dashboard`)

---

## 📁 Project Structure
```plaintext
DataBricks-YFinance-Analytics/
├── 01_data_ingestion.ipynb # Ingests data from Yahoo Finance and stores as Delta
├── 02_transformation_for_analytics.ipynb # Transforms ingested data for analytical metrics
├── 03_analytical_dashboard.ipynb # Interactive dashboard for data visualization
├── README.md # This file
```

---

## 1️⃣ Data Ingestion (`01_data_ingestion`)

This notebook is responsible for fetching historical stock data from Yahoo Finance and saving it in a Delta table for further analysis.

### Features

- Fetches OHLCV data (Open, High, Low, Close, Volume) for selected tickers.
- Supports date range and interval selection (`1m`, `5m`, `15m`, `1d`, etc.).
- Converts raw data into Spark DataFrame and saves it as a Delta table.
- Automatically handles multiple tickers and column renaming for consistency.

### Dependencies

```bash
%pip install yfinance
```

## ⚡ Usage

1. Enter tickers, start date, end date, and interval using Databricks widgets.
2. Run the notebook to save data to your respective Delta path.
3. Verify the data using SQL or Spark queries.

---

## 2️⃣ Data Transformation (02_transformation_for_analytics)

This notebook prepares ingested data for analytical purposes.

### Features
- Computes daily returns, cumulative returns, daily volatility, and volume spikes.
- Calculates moving averages (MA15, MA30, MA60) and Bollinger Bands.
- Stores transformed metrics in a Delta view `workspace.default.stock_metrics` for downstream analysis.

### Sample SQL
```sql
SELECT * 
FROM workspace.default.stock_metrics
WHERE TICKER IN ('AAPL', 'MSFT')
ORDER BY DATETIME DESC;
```

### 3️⃣ Analytical Dashboard (03_analytical_dashboard)

Interactive visualization of stock metrics with widgets for user control.

#### Features
- Select multiple tickers and date ranges for plotting.
- Toggle moving averages (MA15, MA30, MA60) and Bollinger Bands.
- Interactive charts rendered using Matplotlib within Jupyter/Databricks notebooks.
- Automatic updates when selections change.

#### Dependencies
```bash
%pip install ipywidgets
%pip install nbformat>=4.2.0
```

## ⚡ Usage

1. Run the notebook in Databricks.

2. Use the widgets to select tickers, date ranges, and technical indicators.

3. Charts update dynamically to reflect the selected data.



