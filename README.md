# 🔋 Battery on Wheels - Global EV Analysis Dashboard (2010 - 2024)

## 📌 Overview
The dashboard analyzes global EV adoption across regions, categories, powertrain types, transport modes, and time periods. It provides insights into EV growth, market trends, and global transition toward clean transportation.

## 🌍 Data Source
Dataset: Global EV Data 2010 - 2024 (IEA)
Format: CSV
Download: Global EV Dataset (IEA)

## 📂 Data Description
Fields Included:
- region – Geographic area or country
- category – Vehicle type (car, bus, 2-wheeler, truck)
- parameter – Metric recorded (stock, sales, energy use, etc.)
- mode – Transport mode (road, rail, freight, passenger)
- powertrain – BEV, PHEV, FCEV, etc.
- year – Year of records (2010-2024)
- unit – Measurement unit
- value – Numerical metric value
  
## 🎯 Project Goals
- Analyze EV adoption patterns globally
- Study category-wise and region-wise market performance
- Understand growth trends in BEV, PHEV, and other powertrains
- Explore EV parameters such as stock, sales, and energy use
- Compare EV evolution across years, regions, and modes

## 🛠️ Tools Used
- Power BI Desktop
- Power Query
- DAX
- CSV dataset (IEA Global EV Data)
- Data modeling & relationship design

## 🧮 Data Modelling
The dashboard follows a star schema:
- Fact Table: EV dataset
- Dimensions: Year, Region, Category, Powertrain
Transformations performed:
- Cleaned units and numeric fields
- Standardized category and region names
- Derived fields (YoY growth, CAGR, category share)
- Removed duplicates and missing fields

## 🧠 Key DAX Measures
### Measure Tools
1. EV Growth %
```sh
EV Growth % = 
VAR StartYear = CALCULATE(MIN('IEA Global EV Data 2024'[year]))
VAR EndYear = CALCULATE(MAX('IEA Global EV Data 2024'[year]))
VAR StartValue = CALCULATE(SUM('IEA Global EV Data 2024'[value]), 'IEA Global EV Data 2024'[year] = StartYear)
VAR EndValue = CALCULATE(SUM('IEA Global EV Data 2024'[value]), 'IEA Global EV Data 2024'[year] = EndYear)
RETURN DIVIDE(EndValue - StartValue, StartValue) * 100
```
### Column Tools
1. Mode-Powertrain
```Sh
Mode-Powertrain = 
'IEA Global EV Data 2024'[mode] & " - " & 'IEA Global EV Data 2024'[powertrain]
```
2. Region Group
```sh
Region Group = 
SWITCH(
    TRUE(),
    'IEA Global EV Data 2024'[region] IN {"World", "China", "Europe", "USA","Rest of the world"}, "Developed",
    "Developing"
)
```
3. Total EVs Developed
```sh
Total EVs Developed = 
CALCULATE(SUM('IEA Global EV Data 2024'[value]), 'IEA Global EV Data 2024'[Region Group] = "Developed")
```
4. Transport Type
```sh
Transport Type = 
SWITCH(
    TRUE(), 'IEA Global EV Data 2024'[mode] IN {"Cars", "Buses", "2-wheelers"}, "Passenger",'IEA Global EV Data 2024'[mode] IN {"Trucks", "Vans", "LCV","HCV"}, "Freight","Other")
```

## 🖥️ Dashboard Visuals
Includes diverse Power BI visuals:
- Cards
- Bar charts
- Column charts
- Area charts
- Line charts
- Scatter plots
- Matrix tables
- Pie and donut charts
- Boxplots
- Funnels
- Waterfall charts
- Slicers for interactive filtering

## 📊 Analysis Sections
### Regional and Category Trends
- Total EV values by region over the years
- Top regions leading EV adoption
- Category comparison across regions
- Regional dominance by vehicle category
- Developed vs developing region comparison

### Powertrain and Mode Insights
- Distribution of BEV, PHEV, FCEV across the world
- Fastest-growing powertrain type
- Powertrain usage by transport mode
- Region-wise mode-powertrain dominance
- Powertrain trend comparison (2020–2024)
- Five-year trend for each powertrain

### Parameter & Unit Analysis
- Most recorded EV parameters
- Region contribution by parameter
- EV energy consumption trend by region
- Unit-wise distribution (vehicle count, TWh, etc.)
- Stock vs registrations year-over-year
- Regions with highest EV sales

### Time Series & Comparative Analysis
- Year-wise trend of global EV stock
- Growth comparison for top 3 regions
- Cumulative EV values across years
- BEV vs PHEV trend comparison
- Peak EV sales/stock year by region
- Category with highest year-over-year spike

## 💡 Key Insights
- Asia and Europe show the strongest EV expansion
- BEVs dominate globally with rapid year-on-year growth
- PHEVs show moderate growth in certain regions
- EV stock has consistently grown in all major regions
- Sales trends highlight accelerating global adoption
- Categories like 2-wheelers and cars show fastest expansion
- Energy use values indicate rising electricity demand from EVs

## 🌐 Region Grouping (Used in Dashboard)
Developed Regions:
- Europe, North America, Japan, Korea, Australia
Developing Regions:
- India, China, Africa, Latin America, Southeast Asia

## ⚙️ Future Enhancements
Great to include for your GitHub reviewers:
- Add forecasting using Power BI’s analytics pane
- Add cluster analysis for similar regions
- Use ArcGIS maps for deeper geographic insights
- Add dark/light theme variations
- Integrate with external APIs for live EV data

## 🔍 Testing and Validation
- Checked for duplicate records
- Verified numeric fields and units
- Ensured no year gaps in time-series
- Validated totals using cross-filtering
- Performed DAX performance checks

## 🏆 Key Achievements of the Dashboard
- Covers full EV lifecycle metrics
- Supports multi-mode evaluation
- Offers deep powertrain analytics
- Uses 20+ visuals for rich analysis
- Offers interactive filtering for all views

## 🚀 How to Run
1. Download the .pbix file
2. Open it in Power BI Desktop
3. Use slicers to filter region, year, category, powertrain, and mode
4. Explore visuals to analyze global EV market trends
5. Export insights or visuals as needed

## 🤝 Contributing
- Fork the repository
- Create a branch
- Commit changes
- Open a pull request

---
Battery on Wheels(EV) 🚗🔌⚡️
