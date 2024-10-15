# $\color{red}{\textsf{[DRAFT]}}$

# Scraping Certified BREEAM Assessments Data

## Executive Summary
Sustainability has become a paramount concern in contemporary architecture and construction, driving the adoption of various frameworks to evaluate and enhance the environmental performance of buildings. Among these, the Building Research Establishment Environmental Assessment Method (BREEAM) stands out as a leading international certification system, particularly influential in the UK and Europe. This study leverages advanced data science techniques to scrape, process, and analyze approximately 40,000 BREEAM-certified assessments from the GreenBookLive database. The objective is to uncover temporal and spatial trends, sectoral distributions, and regional concentrations of certified buildings. By doing so, the research provides actionable insights for architects, developers, and policymakers, supporting informed decision-making aligned with the UK’s ambitious net-zero targets. **FIGURE ONE IS SHOWING THAT --> REFERENCE FIGURE ALWAYS**

Key findings indicate a significant increase in high-level certifications ("Excellent" and "Outstanding") over the past five years, with London and the South East leading in certification counts. Emerging clusters in Scotland and the North West suggest regional shifts influenced by local government initiatives and urban regeneration efforts. The commercial and residential sectors dominate certifications, while the public sector, particularly infrastructure projects, shows notable growth in specific regions. These insights underscore the importance of targeted policies and incentives to promote sustainable practices in underrepresented areas, contributing to the broader goal of environmental sustainability in the built environment.

![BREEAM Outstanding Certified Assessments](links/Map_world.png)
*Figure 1: Global map showing BREEAM-certified project locations, colour-coded by use class (e.g., Residential, Commercial).*


## Methodology
The study employs a comprehensive methodology encompassing data extraction, cleaning, analysis, and visualization to achieve its objectives. The following sections outline the detailed processes involved:

### 1. Data Collection

#### Web-Scraping Process
The data extraction process involved sophisticated web scraping techniques with **Python** to retrieve BREEAM certification data from the GreenBookLive database. Given the website's dynamic nature, a combination of HTTP requests and browser automation via Selenium was employed to effectively interact with and extract data from dynamically loaded content.

#### Python Libraries:
    - `requests` for handling HTTP requests and fetching static content.
    - `lxml` for parsing HTML and extracting data fields.
    - `Selenium` with the Chrome WebDriver for automating browser interactions and handling JavaScript-rendered content.
    - `Pandas` for data cleaning, manipulation, and analysis.
    - `Folium` and `GeoPandas` for geospatial analysis and visualization.

#### Web Scraping Implementation:
Implementation Steps:

1. Selenium Configuration: Selenium WebDriver was configured with headless Chrome options to automate browser interactions without a graphical interface.
2. Page Navigation: Automated scripts navigated through multiple pages of the GreenBookLive database, handling pagination controls to ensure comprehensive data collection.
3. Data Extraction: Relevant data fields such as building name, location, certification date, certification level, and assessor information were identified and extracted from the HTML content using `lxml`.
4. Data Storage: The extracted data was initially stored in CSV files for intermediate storage and later imported into Pandas DataFrames for further processing.

### 2. Data Cleaning & Processing
Once the raw data was collected, extensive preprocessing was necessary to ensure accuracy and consistency, enabling reliable analysis.
#### Data Cleaning:
- **Duplicate Removal**: Redundant entries were eliminated using Pandas' drop_duplicates() function.
- **Standardizing Location Formats**: Inconsistent region names were standardized using mapping dictionaries (e.g., converting "N.W. England" to "North West England") to ensure uniformity across the dataset.
- **Date Format Standardization**: All certification dates were converted to a consistent YYYY-MM-DD format using Pandas' to_datetime() function, with erroneous entries coerced to NaT (Not a Time) and subsequently handled.
- **Handling Missing Data**:
    - **Imputation**: Missing geographical data were imputed based on known regional clusters of BREEAM-certified buildings. For categorical fields, mode substitution was applied where appropriate.
    - **Exclusion**: Records with critical missing fields, such as location or certification level, were excluded from specific analyses to maintain data integrity.
      
#### Categorization:
- **Building Type**: To facilitate sectoral analysis, buildings were classified into categories, including Residential, Commercial, Public Infrastructure, Industrial, and Others.
- **Region**: Data was grouped based on UK regions (e.g., London, Scotland, North West) to enable regional comparative studies.

### 3. Exploratory Data Analysis (EDA)

Exploratory Data Analysis was conducted to uncover patterns, trends, and insights within the BREEAM certifications dataset.

#### Temporal Trends:

- **Analysis:** Time-series analysis tracked annual changes in certification counts over the past five years.

- **Visualization:** Line charts illustrated the upward trend in certifications, particularly highlighting increases in higher certification levels during periods of significant regulatory changes.

![BREEAM Outstanding Certified Assessments](links/Office_Percentage.png)
*Figure 5: Pie chart depicting the number of office BREEAM certifications over each year from 2013 to 2022 colour-code by rating.*


#### Sectoral and Geographic Analysis:

- **Segmentation:** Data was segmented by building type and region to identify sector-specific and region-specific trends.

- **Visualization:** Bar charts and histograms were created using Matplotlib and Seaborn to represent the distribution of certifications across different sectors and regions. For instance, commercial buildings showed high certification rates in London, while residential certifications surged in the North West.

![BREEAM Outstanding Certified Assessments](links/Map_London.png)
*Figure 3: Detailed map of London showing BREEAM-certified project locations, color-coded by use class.*

#### Geospatial Visualization:

- **Tools Utilized:** Folium and GeoPandas were employed to create interactive maps displaying the density of BREEAM-certified buildings across the UK.

- **Findings:** High-density areas were identified in London and the South East, with emerging clusters in Scotland and the North West, particularly in regions experiencing urban renewal.

![BREEAM Outstanding Certified Assessments](links/Map_UK.png)
*Figure 2: Detailed map of Europe and the UK showing BREEAM-certified project locations, colour-coded by use class.*

### 4. Cluster Analysis with Machine Learning

To gain deeper insights into the relationships between building type, certification levels, and geographic distribution, unsupervised machine learning techniques were applied.

#### K-Means Clustering:
- **Objective:** Group buildings based on certification level, type, and location to identify distinct clusters within the dataset.

- **Feature Engineering:** Key features included certification rating, building type, geographic coordinates, and year of certification. These features were standardized to ensure uniformity across the dataset.

- **Cluster Determination:** The optimal number of clusters was identified using the Elbow Method and silhouette scores, ensuring meaningful and distinct groupings.

#### Evaluation of Clusters:

- **Insights:** Clusters revealed high-performing commercial buildings concentrated in central London and emerging residential clusters in northern regions such as Manchester and Liverpool. Public infrastructure projects, including schools and hospitals, were predominantly clustered in Scotland and Wales, reflecting regional government initiatives promoting sustainability.

### 5. Challenges and Solutions

The project encountered several challenges, each addressed with specific strategies to ensure the integrity and completeness of the data.

#### Dynamic Content Loading:

- **Challenge:** The reliance on JavaScript for content rendering complicated the scraping process.

- **Solution:** Utilized Selenium WebDriver to automate browser interactions, ensuring all dynamic content was fully loaded. Implemented explicit waits to handle varying load times effectively.

#### Data Quality Issues:

**Challenge:** Inconsistencies in location formatting and date records hindered data standardization.

**Solution:** Developed comprehensive mapping dictionaries for region standardization and employed Pandas' date parsing functions. Manual validation of a data subset ensured accuracy.

#### Rate Limiting and Scalability:

- **Challenge:** High-frequency HTTP requests risked triggering GreenBookLive's rate-limiting mechanisms, leading to potential IP blocking and incomplete data collection.

- **Solution:** Introduced request throttling using controlled delays between requests. Implemented robust error handling and retry mechanisms to manage intermittent failures, ensuring the scraping process could resume seamlessly.

#### Handling Large Datasets:

- **Challenge:** Managing a dataset of approximately 40,000 records required efficient data handling to prevent memory issues.

- **Solution:** Leveraged Pandas' optimized data structures and processed data in manageable chunks. Employed memory-efficient techniques such as data type optimization and selective column loading.

#### Ethical Considerations and Compliance:

- **Challenge:** Ensuring adherence to ethical standards and GreenBookLive's terms of service was crucial to avoid legal repercussions.

- **Solution:** Reviewed GreenBookLive's robots.txt and terms of service to ensure compliance. Limited scraping rates to minimize server load and avoided accessing non-public or sensitive information. Anonymized any potentially sensitive data to protect privacy.

### 6. Data Analysis and Insights

The cleaned and processed data underwent rigorous analysis to extract meaningful insights into BREEAM certifications.

#### Temporal Certification Trends:

**Observation:** The number of buildings receiving BREEAM certifications has steadily increased over the past five years, with a significant rise in higher-level certifications ("Excellent" and "Outstanding").

**Implication:** This trend aligns with increased regulatory pressures and heightened industry commitment to sustainability standards.

#### **Land Use and Sectoral Distribution**

- **Analysis:** The dataset was categorized by building type (residential, commercial, public infrastructure, industrial) to assess land use distribution trends.

- **Findings:** While commercial and residential buildings remain dominant, there is a noticeable increase in certifications within the public and industrial sectors.


![BREEAM Outstanding Certified Assessments](links/Land_Use_Percentage.png)
*Figure 4. xxx*



The chart highlights a diversification in land use among certified buildings, with significant growth in public infrastructure and industrial sectors. This shift indicates a broader adoption of sustainability practices across various types of developments, beyond the traditional commercial and residential domains.

#### Regional Disparities:

**Observation:** London and the South East maintain the highest number of certified buildings, while regions like Scotland and the North West are emerging as new sustainability hotspots.

**Implication:** Regional growth in certifications suggests effective local government initiatives and urban regeneration efforts promoting sustainable construction.

#### Sectoral Breakdown:

**Observation:** The commercial and residential sectors dominate BREEAM certifications. However, there is notable growth in the public sector, particularly in infrastructure projects within Scotland and Wales.

**Implication:** Increased public sector certifications indicate governmental support and incentives for sustainable development in key infrastructure areas.

![BREEAM Outstanding Certified Assessments](links/Office_Outstanding.png)
*Figure 6: Bar chart showing the number of "Outstanding" certifications in the Office sector.*

![BREEAM Outstanding Certified Assessments](links/Industrial_Outstanding.png)
*Figure 7: Bar chart showing the number of "Outstanding" certifications in the Industrial sector.* 

### 7. Ethical Considerations

The study adhered to ethical standards throughout the data collection and analysis processes. Web scraping was conducted in compliance with GreenBookLive's terms of service, ensuring minimal server load through controlled request rates. Only publicly available certification records were accessed, and any sensitive information was anonymized to protect privacy. These measures ensured that the research maintained integrity and respected data ownership rights.

### Conclusion

This study demonstrates the efficacy of data-driven approaches in understanding the dynamics of sustainable construction through the lens of BREEAM certifications. The significant growth in high-level certifications underscores the industry's commitment to environmental sustainability, while regional and sectoral analyses highlight areas of strength and opportunities for targeted policy interventions. As the UK progresses toward its net-zero goals, these insights provide valuable guidance for architects, developers, and policymakers in fostering sustainable building practices. Future research directions include expanding the analysis to other global sustainability frameworks, assessing the economic and human-centric impacts of certifications, and integrating Geographic Information Systems (GIS) for more nuanced spatial analyses.

