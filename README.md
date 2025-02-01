# Analysis-of-Global-Wealth-Inequality-Azure-Data-Pipeline-Project


# Dataset Introduction - Two datasets have been used

- The first dataset has been downloaded from _ourworldindata.org_ (Source: World Bank Poverty and Inequality Platform (2024) – with major processing by Our World in Data). It contains the Gini coefficient for all the countries ranging from 1963-2023. But for this analysis, only the top 8 richest countries (except Japan) based on GDP (nominal, 2025) have been considered

- The second dataset - contains data on % wealth held by the top 10% of wealth holders by country. This has been visualized separately in Tableau because of the availability of impactful Map viz (Source - https://wid.world/data/)

# Data Engineering and Analysis perspective

- This project addresses a critical business use case by building a comprehensive data pipeline on Azure, by migrating on-premises SQL Server data using Azure Data Factory, storing semi-structured data in an Azure Data Lake container, transforming it with Databricks (PySpark), saving the processed data back to a transformed ADLS Gen2 container, and integrating it with Power BI for visualization.  

# Architecture & Tech Stack
- **Azure SQL Server** (Source Database)
- **Azure Storage Account (ADLS Gen2)** (Raw & Transformed Containers)
- **Azure Data Factory** (ETL & Migration)
- **Azure Key Vault** (Secure Credential Management)
- **Azure Databricks (PySpark)** (Data Transformation)
- **Power BI & Tableau** (Data Visualization)

---

# Project Workflow

## 1. Data Ingestion & Storage Setup
- Created a SQL Server database and uploaded the CSV dataset.
- Provisioned an Azure Storage Account with two containers:
  - **Raw Container**: For initial data storage.
  - **Transformed Container**: For processed data.

## 2. Data Migration using Azure Data Factory
- Created an Azure Data Factory (ADF) pipeline with a Copy Activity to migrate data from SQL Server to the Raw Container.
- Configured:
  - **Linked Service** to connect SQL Server as the data source.
  - **Self-Hosted Integration Runtime (SHIR)** for secure on-premises connectivity.
  - **Azure Key Vault** for secure credential management.
  - **Delimited Text Format** for CSV output in the Raw Container.

## 3. Data Transformation with Azure Databricks (PySpark)
- Launched Azure Databricks, created a single-node compute cluster, and developed a notebook for data processing.
- Mounted the ADLS Gen2 containers (Raw & Transformed) using the PySpark mount function.
- Performed data cleansing and transformation using PySpark:
  - Handled missing values.
  - Converted data types.
  - Standardized column names.
  - Derived new calculated fields.
- Saved the transformed dataset back into the Transformed Container in CSV format.

## 4. Data Visualization with Power BI & Tableau
- Connected Power BI to the Transformed Container via Azure Storage SQL Endpoint using the Access Key.
- Created line charts and insights to visualize trends in global wealth inequality.
- Additionally, loaded another dataset into Tableau for comparative analysis and alternative visualization.

---

# Additional Considerations & Enhancements
- ✅ **Data Governance & Security**: Used Azure Key Vault for secure credential management.
- ✅ **Scalability & Performance**: Optimized Databricks cluster configuration to enhance processing speed.
- ✅ **Logging & Monitoring**: Integrated Azure Monitor for tracking data pipeline execution.
- ✅ **CI/CD Pipeline (Future Scope)**: Automate deployment using Azure DevOps.

---

# Analysis and Final Thoughts - 

This project was primarily aimed at showcasing Data Engineering skills but the choice of dataset allows me to discuss some socio-economic issues or at the least help start a conversation. These are mostly from the 'Wealth Inequality Report 2022'. This is an excellent publication (with candid write-up) that should be run by every responsible citizen. Yes, it is 236 pages long but worth every minute of reading :)

- One of the common issues we face as a society is income/wealth inequality which is at levels seen back in the 1900s-1910s based on the Gini index of Global wealth inequality 1910 - 0.72, 2000 - 0.72, 2020 - 0.67 (World Inequality report, 2022). The economic power is increasingly being concentrated in the hands of very small minority of the super-rich. Wealth held by the Top 10% of wealth holders: Russia 74.1, US - 70.7%, France 67.8%,  India - 64%, UK - 57.1%. 

- Over the years the countries have become richer but the share of wealth held by the public is close to zero or negative in certain countries such as the UK and US. Meaning if "that country were to sell all its public assets to pay off its debt, then everything there is to own in that country (roads, schools, etc.) would end up in private hands. Citizens would then have to pay rent to the new private owners to use the privatized infrastructure (roads, schools, etc). 

- In terms of Carbon inequality the newest fad of super-rich Space travel, an 11-minute flight emits no less than 75 tonnes of carbon per passenger which is emitted by an average person in his/her entire lifetime. 

- It's easier for the rich to remain rich as they can incorporate themselves as corporations which helps them shift their income from personal income tax to corporate tax lowering tax liability.

- Lastly, there is a section in the report (starting on page 179) where an analysis of each country has been presented. On the page of India (page 197) it mentioned "Over the past three years, the quality of inequality data released by the government has seriously deteriorated, making it particularly  difficult to assess recent inequality changes". Wonder why and what kind of information is being held by the government. Is it because current policies or taxation systems are designed to favor certain sections or individuals while the heavy lifting of tax burden has been left to common public




