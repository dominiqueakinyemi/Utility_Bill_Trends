# Utility Bill Trend Analysis

## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Trends and Predictions](#trends-and-predictions)
- [Results and Findings](#results-and-findings)
- [Recommendations](#recommendations)
- [Limitations](#limitations)

## Project Overview

I live in an apartment building that pools utility usage and charges each resident their share according to a rate based on occupancy. Previous bills have varied greatly, making it difficult to budget each month accurately. This project uses Excel to analyze data from historical bill statements, identify trends, and predict future bill costs. My aim is to make recommendations for myself and for members of my apartment community to budget for monthly bills properly and, if possible, reduce utility usage.

### Skills
- Data cleaning
- Statistical analysis
- Exploratory data analysis
- Data visualization
- Trend analysis
- Forecasting

### Tools
- Excel

## Data Sources

Data was obtained from billing statements from 9/25/2022 (apartment move-in) to 6/14/2024 (most recent statement period end). The data set contains the following information: statement date, bill period start date, bill period end date, number of billing days in the period, trash charges, sewer charges, water charges, and the rate used for calculations. I created a column to add the specific charges, calculating the total utility bill cost.

## Data Cleaning and Preparation

I performed the following tasks:
1. Entered raw data from billing statements
2. Coverted raw data range to a table
3. Standardized column data types and formatting
4. Removed the 9/25/22 statement period, as it was a significant outlier (shorter period length due to end-of-month move-in date)
5. Added a "Cost Per Day" calculated column
   - Formulated by dividing the total bill by billing days `=G2/B2`
   - I will use this to examine the variation between billing periods using a metric that factors in the number of days in each period.
6. Removed the following columns from the table: statement date, bill period end
   - I will use the “Bill Period Start” column rather than the “Statement Date.” The former represents the actual period, while the latter is unrelated to bill cost.
   - Each statement period lasts from the 14th of one month until the 14th of the next. All I need is the period start date.
7. Sorted data by bill period start date in ascending order (oldest dates to newest)

## Exploratory Data Analysis

In the initial phase of my analysis, I began by exploring the data's statistics. 

I asked and answered the following questions:

**What is the average monthly total bill cost? Are there any significant observations from viewing the data's statistics?**
- *Average bill is around $70.*
- All median values are lower than their corresponding averages, suggesting the data’s distribution is positively skewed.
- Used `=AVERAGE`, `=MEDIAN`, and =`RANGE` functions

**Are outliers present in the data? How is the data distributed?**
- As suggested by the statistics, the total bill's distribution is skewed right by two high values ($88.19 and 105.02). Since the outliers are true outliers and not errors, I will keep them in my data set and analysis.
- Used `=STDEV.S` and histograms

**Which months have the highest and lowest total bills?**
- December 2023 had the highest bill (one of the outliers, at $105.02). October 2022 had the lowest bill (first full month after move-in).
- Used `=MIN`, `=MAX`, and `=XLOOKUP` functions

![SummaryStatistics](https://github.com/user-attachments/assets/35452abc-61b1-40c1-b876-adfd17e30f98)

**How much does each type of utility contribute to the overall bill? How do they correlate with one another?**
- Water contributes almost half of the total bill. Sewer and Trash make up the remaining amount, usually equally split.
- Water and Sewer charges appear highly positively correlated with the total bill, while Trash charges show only a slight positive correlation.
- Used tables, pie charts, `=SUM` function, and scatter plots

![TotalBreakdown](https://github.com/user-attachments/assets/1b5b7e81-141d-4626-98f6-6630f15a12f5)
![TypeCorrelation](https://github.com/user-attachments/assets/c8944306-1f04-44a2-bf95-ac3a6dd15977)

**Which months have the lowest and highest costs per day?**
- The highest cost per day was December 2023 and the lowest cost per day was October 2022, the same months as the highest/lowest total bills.
- Used `=MIN` and `=MAX` functions, conditional formatting (color scales)

<img width="467" alt="RateCPD" src="https://github.com/user-attachments/assets/3f8d3d7b-cfb2-4ad2-bb7d-daeaf2fa2c4d">

**Is there a correlation between the rate and the total bill cost? Between the length of the period and the total bill cost?**
- Visually, the cost per day and total bill trends are similar. This suggests billing days are not a significant predictor of costs.
- When outliers for billing days (28 or 29 days for February) are filtered out, billing period length and bill cost have little correlation.
- Rate and bill total have a slightly positive correlation.
- Used line charts, scatter plots, filters

![DaysCorrelate](https://github.com/user-attachments/assets/5eed781a-5b43-4028-87fc-f7ee028ebc80)
![RateCorrelate](https://github.com/user-attachments/assets/a68fb2eb-b9ae-43a2-88e9-cff173eb42c2)

## Trends and Predictions

Next, I focused on understanding trends, determining potential factors affecting bill cost, and predicting future bills. 

I asked the following questions:

**What is the overall trend in total bill costs?**
- Total bill costs are **increasing!**
- Many year-to-year changes were extreme. October - January saw increases greater than 45%.
- Used line charts, trendlines, conditional formatting (color scales), and percent change calculations (pivot tables)

<img width="772" alt="Trends" src="https://github.com/user-attachments/assets/c64c9316-a9dd-4518-bd6a-abf5fc0ae5e9">

**Are there seasonal trends in the data?**
- There appear to be large increases at the start of each season, followed by decreases or little change.
- No season has consistently higher or lower usage, but there was a steady period of increases from August - December 2023. The highest bills all occurred from November 2023 - March 2024.
- Used line charts, trendlines, conditional formatting (color scales), and percent change calculations (pivot tables)

![SeasonalTrends](https://github.com/user-attachments/assets/fa625d8f-343c-4aae-ac53-48056d79d651)
![PerChangeChart](https://github.com/user-attachments/assets/9e3fd96e-9015-485f-b284-10659abd6ca9)

**Based on the historical data, what are the forecasted bill totals for the next year?**
- Overall increased total bill costs despite frequent ups and downs.
- Used moving averages, forecast trendlines, `=TREND` function

## Results and Findings

The following is a summary of my analysis findings:
1. Though utility bill totals fluctuate monthly, the overall trend is increasing.
2. In the coming year, total bill amounts will likely exceed the current average of $70. Expect bills ranging from $80-$100.
3. Water is the utility that contributes the most to usage. Increases in water usage correlate with increases in the overall bill more than the other utility types do.
4. Late fall and early winter months tend to have higher bills than spring and summer months. This is likely due to increased time spent at home and additional guests during the holiday months compared to travel and vacation peaks in the spring and summer.
   
## Recommendations

Based on this analysis, I recommend the following actions:

- Expect higher utility bills the first month of each season
- Expect substantial variability in costs on a month-to-month basis
- Develop a contingency budget
   - Save to accommodate unexpected spikes in costs.
- Conduct monthly data review and update
   - Adding each new month's data to the data set will provide more information for analysis and prediction. This can allow for more accurate forecasting in the future.
- Implement community conservation practices to reduce water usage during the Fall and Winter months including:
   - Sharing utility usage on bills in addition to charges to allow residents to better understand and control their usage and the community's.
   - Reminders before holidays about utility usage mindfulness
   - Urge residents to inspect appliances and plumbing, informing maintenance of leaks or inefficient operation.

## Limitations

The following considerations factored into this analysis:
- **Excluded statement period:** The initial statement period was removed from the dataset during cleaning as this shortened period (pro-rated after move-in) skewed the data analysis process.
- **Small sample size:** Data is only available for 20 statement periods, 19 of which were used in the analysis. While this amount of data is smaller than desired, it is comprehensive enough for analysis. I was still able to generate meaningful insights and predictions.
- **Access to bill cost and rate, not utility usage:** This analysis focuses solely on analyzing the utility charges billed each month, since statements do not give specific information on building usage. Charges may include taxes and other fees, as determined by utility management company and apartment complex management. This means it is not possible, with the information available, to distinguish if trends are due to rising costs or rising usage.
