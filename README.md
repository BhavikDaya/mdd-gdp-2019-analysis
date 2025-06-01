# Global Patterns of Depression and Wealth: Analysing MDD Prevalence Against GDP

## Background

Major Depressive Disorder (MDD) is a critical public health concern globally. Understanding how economic prosperity relates to depression can inform policymakers, healthcare workers and researchers about potential areas for intervention and resource allocation. 

This analysis investigates links between national wealth - measured by Gross Domestic Product (GDP) per capita -  and MDD prevalence across countries in 2019. Data from the Institute for Health Metrics and Evaluation (IHME) and the World Bank will be utilised. The strength and statistical significance of the correlation will be calculated using the Pearson correlation coefficient. 

## Data Preparation

Data from three reputable organisations; namely, the [IHME](https://ourworldindata.org/grapher/depressive-disorders-prevalence-vs-gdp-per-capita) for MDD prevalence and [World Bank](https://data.worldbank.org/indicator/NY.GDP.PCAP.CD) for GDP per capita, was sourced through their publically-accessible websites. 

Two tabular CSV documents were obtained, with columns representing country names, year, GDP per capita and MDD prevalence. Quantitative data about GDP per capita is expressed in United States Dollars (USD) and MDD prevalence is expressed as cases per 100 000 per annum. 

The data is stored securely in a Github respository and are used under open licenses, perimtting analysis and redistribution with attribution. No personally identifiable information was used. 

The data sources are reputable and highly credible, being used in research settings. Whilst the data is not current and may contain reporting biases, the data generally meets ROCCC standards.

## Data Processing

The CSV files were imported into Google Sheets for cleaning, which included trimming white space, removing duplicated, omitted blank data, filtering by the year 2019, harmonising country names, ensuring correct data types and making column names lowercase. A histogram was created which showed no improbable outliers. The exported files were then imported into BigQuery and a Left Join was used to identify two countries that were not present in the World Bank data - Timor Leste and Vatican City. These two countries were then omitted from the analysis. The tables were then joined with an inner join based on country name and a single table with country name, MDD prevalence and GDP per capita for the year 2019 was exported into Posit Cloud for data analysis in R (as per the Google Data Analytics Certificate).

A data cleaning log has been uploaded to this repository. 

## Data Analysis

Having been imported into Posit Cloud for analysis, a scatterplot was chosen to best represent the relationship between GDP per capita and MDD prevalence per country. R libraries such as ggplot2 and dplyr were used to plot GDP per capita in USD (independent variable) on the x axis and MDD prevalence on the y axis as the dependent variable. An appropriately-labelled scatterplot was generated and a regression line was added, which showed a moderate negative correlation. A lower GDP per capita correlated with a higher MDD prevalence and a higher GDP per capita correlated with a lower MDD prevalence. As such, countries such as Malawi, the CAR, Chad and South Sudan had high prevalences of MDD whilst countries such as Japan, the USA, the Netherlands and Iceland had lower prevalences of MDD. 

Using cor.test() with the Pearson method, a correlation coefficient of -0.63 was found with a p value of 2.2 x 10<sup>-16</sup> with a 95% CI (-0.71 to -0.53). 

Notable outliers included South Korea, Ukraine, Brazil, Portugal, New Zealand and Saudi Arabia. 

<p align = "center">
  <img src = "scatterplot.png">
</p>

Additionally, the data was imported into Tableau and a dashboard was created to visualise and categorise countries based on their GDP per capita and MDD prevalences. 
[View it interactively here](https://public.tableau.com/app/profile/bhavik.daya/viz/GlobalPatternsofDepressionandWealthAnalyzingMDDPrevalenceAgainstGDP/Sheet1#1)
<p align = "center">
  <img src = "dashboard.png">
</p>

## Key Takeaways

This analysis explored the global relationship between GDP per capita and MDD prevalence in 2019. Whilst a statistically significant negative correlation of -0.63 was seen - suggesting that a higher GDP per capita is associated with a lower prevalence of MDD - the relationship is modest and is likely influenced my numerous confounding factors. 

Moreover, the correlation does not imply a causal relationship and the collected data may have been subject to underreporting and temporal misalignment. 

Numerous other factors such as access to mental health services, availability of such services, income inequality, education, unemployment, stigma, substance use, urbanisation, substance policies, housing and service delivery are likely important factors to explore. Additionally, this analysis does not track changes over time. 

## Recommendations

These findings could assist policymakers, healthcare workers and researchers in providing interventions in countries with high economic prosperity and high comorbid MDD prevalences. Conversely, relatively poor countries would benefit from improved healthcare access and awareness campaigns. 

## Steps for Stakeholders

### Healthcare workers
Focus on improving access to mental health services in underresourced areas. 

### Policymakers
Avoid relying solely on economic propsrity to determine resource allocation. 

### Researchers
Further investigate other factors that may improve reporting and explain the prevalences of MDD in each country.

## Future enhancement

- Track changes over time
- Explore other factors that may affect the MDD prevalence
- Include data about existing mental health care services and budget
