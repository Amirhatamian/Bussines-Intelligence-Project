# From Spreadsheets to Business Intelligence

Projects from my Business Intelligence course: taking raw Excel data, cleaning it, exploring it and turning it into tables, charts and forecasts that can be used for reporting.

## 1. Weekly order forecasting for a logistics company — `Arcese_Logistics2.ipynb`

**Problem:** forecast next week's number of orders on the busiest transport routes.

**What I did**
- Loaded the order history from Excel and summed orders per route per week.
- Picked the 5 routes with the highest average weekly orders (for example Romania → Belgium, Iberia → South Italy, Germany Ruhr → Belgium).
- Split each route's weekly series in time order: 60% train, 20% validation, 20% test.
- Fitted an ARIMA(1,1,0) model per route and measured the error on the test weeks (MAE and RMSE).
- Built a summary table with the forecast average weekly orders and the error for each route, and plotted actual vs forecast orders.

**Results**

| Route | Forecast avg. weekly orders | MAE (orders) |
|---|---|---|
| East North → Italy North-East/Centre | 488 | 153 |
| Romania → Belgium | 488 | 153 |
| Italy North-West → East Balkans | 496 | 163 |
| Iberia → Italy South | 436 | 138 |
| Germany Ruhr → Belgium | 423 | 156 |

The error is roughly a third of weekly volume, so a simple ARIMA gives a rough baseline only. Next steps would be adding seasonality (SARIMA) or calendar features.

## 2. Cleaning a messy spreadsheet — `Data preprocessing.ipynb`

A small Excel file of 50 student enrolment records (faculty, city of residence, academic year, ISEE income band, fees, discount) with typical spreadsheet problems.

- Found inconsistent capitalisation (`bologna`, `rome`, `CONTI`) and fixed city and surname columns.
- Found empty and partly empty rows and missing discount values; filled numeric gaps with the column mean.
- Filtered records by city (e.g. all students living in Turin) to check the data.

## 3. Exploring the data for reporting — `Data Modeling in BI.ipynb`

Charts on the same enrolment data, of the kind used in a BI dashboard:

- Students per faculty (Mathematics 10, Economics 9, Statistics 9, Engineering 8, Law 8, Computer Science 3, Humanities 3).
- Share of students by city of residence and by academic year.
- Distribution of fee discounts, and ISEE band by school location.
- Correlation heatmap of the numeric columns.

## Files

| File | Description |
|---|---|
| `Arcese_Logistics2.ipynb` | Weekly order forecasting with ARIMA |
| `Data preprocessing.ipynb` | Cleaning the enrolment spreadsheet |
| `Data Modeling in BI.ipynb` | Charts and summaries for reporting |

The Excel input files are not included in the repository.

## How to run

```bash
git clone https://github.com/Amirhatamian/Bussines-Intelligence-Project.git
cd Bussines-Intelligence-Project
pip install pandas numpy matplotlib seaborn statsmodels scikit-learn openpyxl jupyter
jupyter notebook
```

## Tools

Python, pandas, statsmodels (ARIMA), scikit-learn, Matplotlib, Seaborn, Excel
