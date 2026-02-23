# California Water Quality Analysis 2023
 
 This project entails a comprehensive analysis of compliance of stream water at California monitor stations for the year 2023. It seeks to identify critical exceedances of EPA guidelines and limits on major inorganic toxins and contaminants, namely Arsenic, Copper, Fluoride, Lead, Mercury, Nitrates, Selenium, Uranium as well as water turbidity. These specific contaminants were chosen as they pose high level acute and chronic toxicity threats to individuals if consumed and should, therefore be closely monitored.

 This analysis culminates with a dashboard showing distribution of problem stations, areas of repeated limit exceedances and a breakdown of how often each contaminant shows level of exceedance out of the total number of tests drawn for the year.

![Dashboard Overview](./Images/California_Water_Quality_2023_Dashboard.png)

**NOTE** : This project only aims to analyze frequency of non conformance of stream water at stations to EPA contaminant limits and does not aim to analyze correlation between factors or identify potential causes for said non-conformances.

 ## Methodology
 This project follows a simple yet detailed roadmap from raw, sourced data to a simple to follow, interactive vizualization which can both easily display findings whilst also paving the way for further analyses.
 
 1. ### Sourcing Raw Data
    The raw data was sourced from the [Water Quality Portal](https://www.waterqualitydata.us/#countrycode=US&statecode=US%3A06&siteType=Stream&sampleMedia=Water&mimeType=csv&sorted=no&providers=NWIS&providers=STORET) set to extract data from the stations in California for the year 2023 on stream water. This yields two CSV files containining metadata about the individual stations as well as test data throughout the year from said stations.
    - [Raw Station Data](./Data/station.csv)
    - [Raw Water Data](./Data/resultphyschem.zip)

 2. ### Data Extraction
    The raw CSV files were uploaded to an SQL Database after which, columns from both tables were extracted and merged into one [singular table](./Data/v_water_quality_analysis), holding all the information needed for the analysis. This table was then merged with a [pre-made table showing the acceptable limit for contaminants by the EPA](./Data/health_standards.csv). This new table was then saved to be used as the "master file".
   
 3. ### Data Cleaning, Validation and Standardization
    The [master file](.Data/water_quality_master_file.csv) was then taken into Excel in order to do minor cleaning such as identifying and removing blank rows, as well as standardizing data values across contaminants to match with EPA limit values for analysis of exceedance. The latter was accomplished throught the use of nested IF statements to identify the multiplicative factor relative to mg/L (standard unit). 

  4. ### Data Analysis and Summarization
     Python Pandas was then used to summarize the data into pivot tables which were then further edited in order to calculate the exceedance rate of each station, as well as how severe the non-conformances were relative to the MCL (Maximum Contaminant Limit). The final [summary table](./Data/summary_data.csv) was exported to be used in Tableau for data vizualization.

  5. ### Data Visualization with Tableau
     The summmary table was used to create the dashboard shown above. [Click here](https://public.tableau.com/app/profile/liam.dujon/viz/WaterQualityDashboard_17712144790070/CaliforniaWaterQuality-HighRiskStations2023) to interact with it.



