# $\color{red}{\textsf{[DRAFT]}}$

# Scraping Certified BREEAM Assessments Data

## Introduction
Sustainable design and construction are becoming increasingly central to how we build for the future. One key metric for assessing sustainability in buildings is the BREEAM certification, which rates structures based on energy efficiency, water use, pollution reduction, and other factors. In this project, I set out to scrape and analyze data on certified BREEAM assessments to track trends and gain insights into the distribution of these certifications across building types and regions.

## Project Objective
The primary goal of this project is to extract data on BREEAM-certified buildings from the publicly available GreenBookLive database. By analyzing this dataset, I aim to:
- Track changes in the number of certified buildings.
- Examine the types and sectors of buildings receiving BREEAM ratings.
- Identify trends in sustainable building certifications across regions.
- Provide insights for architects, developers, and policymakers focused on sustainable construction.

## Why This Matters
Sustainability is not just a buzzword—it’s a measurable factor in modern building design. The growth in BREEAM-certified buildings reflects an industry-wide shift toward greener construction practices. By analyzing the certifications, we can gain a clearer understanding of where progress is being made and identify areas for improvement. This project serves as a data-driven exploration into sustainable development trends.

## Methodology

### Web-Scraping Process
Using Python libraries such as `requests`, `BeautifulSoup`, and `Selenium`, the process of scraping Certified BREEAM data involved handling dynamic web elements and simulating user interactions to access fully rendered data. This required:
- Inspecting the HTML structure of the certification search page to locate key data fields such as building name, location, certification date, assessor, and rating (e.g., “Excellent” or “Good”).
- Addressing dynamic content loading by leveraging `Selenium` to mimic user interactions and retrieve the fully populated data.

To avoid overwhelming the server, the scraper was throttled by introducing delays between requests. Error handling was also implemented to manage unexpected changes in the page structure.

### Data Cleaning & Processing
Once the data was extracted, it underwent thorough cleaning using `Pandas`:
- Duplicates were removed.
- Missing or incomplete entries were handled.
- Location data was standardized, and certification dates were formatted consistently.

The cleaned data was categorized by building type and region to facilitate comparative analysis.

### Data Visualization
Data visualization played a crucial role in exploring patterns in BREEAM certifications:
- **Exploratory Data Analysis (EDA)**: Initial EDA using scatterplots and heatmaps highlighted significant regional variations and sectoral dominance in certifications.
- **Geospatial Mapping**: Using geospatial analysis, we visualized certification hotspots, revealing that London and the South East lead in sustainable building practices. Tools such as `Folium` were used to map the distribution of certifications across the UK.

These visualizations helped uncover trends and insights that laid the foundation for deeper analysis with machine learning techniques.

### Cluster Analysis with Machine Learning
To uncover deeper insights into certification patterns, I performed cluster analysis using K-means:
- **Clustering Methodology**: The clustering algorithm grouped certifications based on variables such as location, building type, and certification rating. K-means was chosen for its ability to partition data into distinct clusters.
- **Features Considered**: Features like geographic location, building sector, and certification level were used to create clusters, revealing hidden groupings and relationships.
- **Key Findings**: The clustering revealed that certifications tend to cluster in specific geographic regions and building types. For example, there was a noticeable grouping of high-rated buildings in commercial sectors within urban centers like London.

This machine learning analysis provided a clearer picture of regional and sectoral trends in sustainable construction certifications.

## Challenges Encountered
- **Dynamic Web Elements**: The GreenBookLive database employed dynamic elements that initially blocked straightforward scraping attempts. I had to resolve this by simulating browser requests using tools such as Selenium to mimic user interaction.
- **Data Consistency**: The dataset contained irregularities, such as inconsistencies in location formatting and varying certification date formats, requiring thorough data cleaning.
- **Scalability**: The scraping process was throttled to avoid overloading the server with requests, necessitating a balance between speed and completeness.

## Key Insights
- **Trends in Certification**: Over the past five years, there has been a significant increase in the number of buildings receiving higher BREEAM ratings (Excellent or Outstanding). This reflects growing emphasis on high-performance sustainable building practices.
- **Regional Analysis**: London and the South East dominate in terms of the number of certified buildings, but there is also noticeable growth in regions like Scotland and the North West.
- **Sectoral Distribution**: Commercial and residential buildings make up the bulk of certifications, but there’s also increasing interest in certifying public infrastructure, such as schools and hospitals.

## Conclusions
This project highlights the importance of BREEAM certifications as a marker of sustainable development. The data suggests that the construction industry is progressively adopting higher standards of environmental performance, particularly in certain regions and sectors. Further analysis could investigate the factors driving these certifications, including regulatory changes and market demand for greener buildings.

## Technical Details for Scraping
- **Libraries Used**:
    - `requests` for sending HTTP requests to the BREEAM search page.
    - `BeautifulSoup` for parsing the HTML and extracting data.
    - `Selenium` for handling dynamically loaded content.
    - `Pandas` for cleaning and analyzing the data.
- **Scraping Process**:
    - Initial setup of web scraping logic focused on capturing the raw HTML of the page.
    - Identification of specific HTML tags containing the required data (e.g., building names, certification types).
    - Use of Selenium to handle dynamic page loads and extract the fully rendered data.
- **Handling Errors & Throttling**:
    - Implemented error handling to manage unexpected changes in page structure.
    - Added delays between requests to avoid IP blocking and to be considerate of the website’s server load.

## Further Directions
This scraping project serves as a foundation for future work, including deeper analysis of sustainability certifications across other global certification schemes or a longitudinal study to measure the rate of certification growth in response to new regulations.

