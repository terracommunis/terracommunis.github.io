# $\color{red}{\textsf{[DRAFT]}}$

# Scraping Certified BREEAM Assessments Data

## Executive Summary
Sustainability has become a paramount concern in contemporary architecture and construction, driving the adoption of various frameworks to evaluate and enhance the environmental performance of buildings. Among these, the Building Research Establishment Environmental Assessment Method (BREEAM) stands out as a leading international certification system, particularly influential in the UK and Europe. This study leverages advanced data science techniques to scrape, process, and analyze approximately 40,000 BREEAM-certified assessments from the GreenBookLive database. The objective is to uncover temporal and spatial trends, sectoral distributions, and regional concentrations of certified buildings. By doing so, the research provides actionable insights for architects, developers, and policymakers, supporting informed decision-making aligned with the UK’s ambitious net-zero targets.

Key findings indicate a significant increase in high-level certifications ("Excellent" and "Outstanding") over the past five years, with London and the South East leading in certification counts. Emerging clusters in Scotland and the North West suggest regional shifts influenced by local government initiatives and urban regeneration efforts. The commercial and residential sectors dominate certifications, while the public sector, particularly infrastructure projects, shows notable growth in specific regions. These insights underscore the importance of targeted policies and incentives to promote sustainable practices in underrepresented areas, contributing to the broader goal of environmental sustainability in the built environment.

[BREEAM Outstanding Certified Assessments](links/Map_world.png)
Figure 1: Distribution of BREEAM Outstanding Certified Buildings by Region (2023)  

[BREEAM Outstanding Certified Assessments](links/Map_UK.png)
Figure 2. xxx 

[BREEAM Outstanding Certified Assessments](links/Map_London.png)
Figure 3. xxx 

[BREEAM Outstanding Certified Assessments](links/Land_Use_Percentage.png)
Figure 4. xxx  

[BREEAM Outstanding Certified Assessments](links/Office_Percentage.png)
Figure 5. xxx 

[BREEAM Outstanding Certified Assessments](links/Office_Outstanding.png)
Figure 6. xxx 

[BREEAM Outstanding Certified Assessments](links/Industrial_Outstanding.png)
Figure 7. xxx 

## Methodology
The study employs a comprehensive methodology encompassing data extraction, cleaning, analysis, and visualization to achieve its objectives. The following sections outline the detailed processes involved:

### 1. Data Collection

#### Web-Scraping Process
The data extraction process involved sophisticated web scraping techniques with **Python** to retrieve BREEAM certification data from the GreenBookLive database. Given the website's dynamic nature, a combination of HTTP requests and browser automation via Selenium was employed to effectively interact with and extract data from dynamically loaded content.

### Python Libraries:
    - `requests` for handling HTTP requests and fetching static content.
    - `lxml` for parsing HTML and extracting data fields.
    - `Selenium` with the Chrome WebDriver for automating browser interactions and handling JavaScript-rendered content.
    - `Pandas` for data cleaning, manipulation, and analysis.
    - `Folium` and `GeoPandas` for geospatial analysis and visualization.

### Web Scraping Implementation:
Implementation Steps:

1. Selenium Configuration: Selenium WebDriver was configured with headless Chrome options to automate browser interactions without a graphical interface.
2. Page Navigation: Automated scripts navigated through multiple pages of the GreenBookLive database, handling pagination controls to ensure comprehensive data collection.
3. Data Extraction: Relevant data fields such as building name, location, certification date, certification level, and assessor information were identified and extracted from the HTML content using `lxml`.
4. Data Storage: The extracted data was initially stored in CSV files for intermediate storage and later imported into Pandas DataFrames for further processing.

### 2. Data Collection
Once the raw data was collected, extensive preprocessing was necessary to ensure accuracy and consistency, enabling reliable analysis.
Data Cleaning:
- **Duplicate Removal**: Redundant entries were eliminated using Pandas' drop_duplicates() function.
- **Standardizing Location Formats**: Inconsistent region names were standardized using mapping dictionaries (e.g., converting "N.W. England" to "North West England") to ensure uniformity across the dataset.
- **Date Format Standardization**: All certification dates were converted to a consistent YYYY-MM-DD format using Pandas' to_datetime() function, with erroneous entries coerced to NaT (Not a Time) and subsequently handled.
- **Handling Missing Data**:
    - **Imputation**: Missing geographical data were imputed based on known regional clusters of BREEAM-certified buildings. For categorical fields, mode substitution was applied where appropriate.
    - **Exclusion**: Records with critical missing fields, such as location or certification level, were excluded from specific analyses to maintain data integrity.
