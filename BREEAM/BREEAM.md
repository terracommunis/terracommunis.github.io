# $\color{red}{\textsf{[DRAFT]}}$

# Scraping Certified BREEAM Assessments Data

## Introduction
Sustainability in design and construction has become a critical focus in contemporary building practices, with various frameworks developed to assess environmental performance. One such framework, the Building Research Establishment Environmental Assessment Method (BREEAM), provides an internationally recognized certification system for evaluating the sustainability of buildings based on factors such as energy efficiency, water usage, and pollution reduction. In this study, we employ data science techniques to scrape, process, and analyze data from the publicly available BREEAM-certified assessments. The goal is to uncover trends and patterns across various regions, building types, and certification levels.

## Project Objective
The primary objective of this study is to systematically extract and analyze data on BREEAM-certified buildings from the GreenBookLive database. The analysis focuses on:
- Tracking temporal changes in the number of certified buildings.
- Examining sectoral and typological distributions of buildings with BREEAM certifications.
- Identifying regional trends and geographic concentrations of certified buildings.
- Providing data-driven insights for architects, developers, and policymakers to support informed decision-making in sustainable construction.

## Relevance of the Study
As sustainability metrics become a standard part of architectural practice, it is essential to analyze the proliferation of BREEAM certifications to better understand the progress of green building initiatives. This research provides a quantitative approach to track certification trends over time, visualize regional discrepancies, and assess the sectors most aligned with sustainable practices. By utilizing advanced data analysis techniques, this study contributes valuable insights to the field of sustainable development.

## Methodology

### Web-Scraping Process
The data extraction process involved web scraping techniques to retrieve BREEAM certification data from the GreenBookLive database. Given the dynamic nature of the site, a combination of HTTP requests and browser automation via `Selenium` was employed to interact with and retrieve data from dynamically loaded content.

- **Technologies Used**: The web scraping pipeline was implemented using Python’s `requests` library for static data extraction, and `Selenium` for simulating browser interactions to handle dynamic web elements.
- **Data Fields**: Key data fields extracted included building name, location (city, region), certification date, assessor information, and certification level (e.g., “Excellent”, “Very Good”).
- **Challenges in Scraping**: The dynamic content loading mechanisms required extensive use of HTML parsing and interaction simulation. Additionally, throttling mechanisms were implemented to balance the frequency of requests to avoid overburdening the web server.

### Data Cleaning & Processing
Once extracted, the raw data required significant preprocessing before analysis:
- **Data Cleaning**: Using `Pandas`, data was cleaned by removing duplicates, standardizing location formats, and resolving inconsistencies in date formats. Missing or incomplete data entries were handled through imputation or exclusion based on predefined thresholds.
- **Categorization**: The dataset was categorized by building type (residential, commercial, public infrastructure) and region to facilitate both temporal and spatial comparative analysis.

### Exploratory Data Analysis (EDA)
Exploratory Data Analysis was performed to uncover patterns and trends in the BREEAM certifications dataset:
- **Temporal Trends**: Time-series analysis was conducted to track changes in certification counts over the years, providing insights into industry adoption rates.
- **Sectoral and Geographic Analysis**: Data was segmented by building type and region to identify concentrations of certified buildings. Visualizations, including bar charts and histograms, were generated using `Matplotlib` and `Seaborn` to illustrate these distributions.
- **Geospatial Visualization**: Geospatial analysis was performed using `Folium` and `GeoPandas` to visualize certification densities across regions of the UK, identifying geographic hotspots and growth areas for sustainable building certifications.

### Cluster Analysis with Machine Learning
To provide a more nuanced understanding of the relationships between building type, certification levels, and geographic distribution, unsupervised learning techniques were employed:
- **K-Means Clustering**: A K-means clustering algorithm was applied to group buildings based on their certification level, type, and location. This method allowed for the identification of latent patterns within the dataset, revealing clusters of high-performing buildings in specific regions or sectors.
- **Feature Engineering**: Features such as certification rating, building type, geographic coordinates, and year of certification were selected as input variables for clustering. These features were standardized prior to model fitting to ensure uniformity across the dataset.
- **Evaluation of Clusters**: The optimal number of clusters was determined using the Elbow Method and silhouette scores to maximize within-cluster homogeneity and between-cluster separation. Cluster centroids were analyzed to draw conclusions about the distribution of certifications across regions and sectors.

## Challenges Encountered
Several challenges were faced during the project:
- **Dynamic Content Loading**: The web page’s dynamic elements necessitated the use of browser automation (`Selenium`), complicating the scraping process. Careful inspection of JavaScript-rendered content and DOM elements was required.
- **Data Quality Issues**: The dataset exhibited inconsistencies, particularly in location formatting and date records, requiring robust cleaning procedures to standardize entries.
- **Rate Limiting and Scalability**: To avoid potential IP blocks or overloading the server, request throttling and error handling mechanisms were implemented, which affected the overall efficiency of the scraping process.

## Key Insights

- **Temporal Certification Trends**: Analysis indicates a marked increase in the number of buildings receiving BREEAM certifications over the past five years. Moreover, there is a growing trend toward higher certification levels (e.g., “Excellent” and “Outstanding”).
- **Regional Disparities**: Geospatial analysis revealed that London and the South East dominate in the number of certified buildings, though there is notable growth in regions such as Scotland and the North West.
- **Sectoral Breakdown**: Commercial and residential buildings comprise the majority of certifications. However, there has been a significant increase in public sector certifications, particularly for infrastructure such as schools and healthcare facilities.

## Conclusions
This study underscores the importance of data-driven approaches in understanding the evolving landscape of sustainable construction. The growth in BREEAM certifications, particularly at higher levels, suggests an increasing industry commitment to sustainability. Regional disparities in certification uptake highlight the need for targeted policies and incentives to promote green building practices in underrepresented areas. Future research could explore the impact of regulatory changes on certification rates and expand the analysis to other global sustainability frameworks.

## Technical Details for Scraping
- **Libraries Used**:
    - `requests` for HTTP requests and data extraction.
    - `BeautifulSoup` for HTML parsing and data field extraction.
    - `Selenium` for simulating user interaction and handling dynamic content.
    - `Pandas` for data cleaning, manipulation, and analysis.
- **Scraping Workflow**:
    - The process involved fetching raw HTML using `requests` and rendering dynamic content via `Selenium`.
    - HTML tags corresponding to relevant data fields were identified, and extracted data was stored in a structured format.
    - Error handling and request throttling were incorporated to ensure reliable and ethical scraping.
  
## Further Directions
This research serves as a foundational exploration of BREEAM certifications, opening avenues for future work. Potential directions include:
- Extending the analysis to other sustainability certification frameworks, such as LEED or WELL, to enable comparative studies.
- Conducting longitudinal studies to assess the correlation between policy changes and certification rates.
- Utilizing more advanced machine learning techniques, such as hierarchical clustering or neural networks, to gain deeper insights into certification patterns.


