# $\color{red}{\textsf{[DRAFT]}}$

# Scraping HubbleHQ: A Data-Driven Exploration of London’s Office Rental Market

## Introduction
In the heart of London's vibrant Westminster, I embarked on an office development project that required a deep understanding of the local rental market. By collecting and analyzing real-time data on office spaces, I aimed to make informed decisions on rent prices, hot desk options, and meeting room availability. Web scraping emerged as the ideal solution for gathering fresh insights into market trends, prices, and spatial dynamics, particularly from platforms like HubbleHQ.

### Why Web Scraping?
Web scraping is a powerful method to obtain up-to-date information directly from websites. For this project, scraping HubbleHQ provided immediate data on office rentals in Westminster, filling gaps left by traditional datasets, which may be outdated or lack specific insights on flexible workspaces, rent per desk, and spatial characteristics.

### Understanding the Dataset
Before diving into code, defining essential data fields was key. Here are the columns that provided the most valuable insights:

- OfficeName: The name of the office space provider (e.g., WeWork).
- PostCodeArea: The postal code area indicating the location of each space.
- Rent/Month: Monthly rent for private offices, hot desks, etc.
- DeskNumber: The number of desks available in each listing.
- AreaSize: Total office space size (square feet or square meters).
- Price/Person: Cost per person, derived from the rent and desk number.
These fields are critical for evaluating trends, especially in understanding the price per desk and spatial comparisons.

### Tools and Libraries Used
For this project, I used Python, along with a few key libraries:

- BeautifulSoup and Requests: To send HTTP requests and parse HTML data from HubbleHQ's listings.
- Pandas: For efficient data manipulation and analysis.
- Matplotlib/Seaborn: To visualize trends in office rental prices and space sizes across London.
These libraries provide a robust, efficient toolkit for web scraping and data analysis, with BeautifulSoup handling HTML parsing and Pandas allowing for large dataset management.

## Step 3: The Web Scraping Process
To get started, I focused on HubbleHQ as a data source for current office rentals in London. Before scraping, I ensured compliance with their terms of service and respected their robots.txt file to avoid scraping restricted areas.





## Introduction
In today’s rapidly evolving real estate landscape, access to accurate and up-to-date information is crucial for businesses seeking office space. HubbleHQ, a leading office rental platform in London, provides a wealth of data on available office spaces, rental prices, and location specifics. This project focused on scraping and analyzing data from HubbleHQ to gain deeper insights into London’s office rental market and uncover key trends across different areas of the city.

![HubbleHQ Office Rental](links/website.jpg)
*Figure 1: Global map showing BREEAM-certified project locations, colour-coded by use class (e.g., Residential, Commercial).*

## Project Objective
The primary goal of this project was to utilize web scraping techniques to collect real-time data on office listings from HubbleHQ. By gathering detailed information on office spaces, prices, locations, and amenities, I aimed to:

- Conduct a comprehensive comparison of office rentals across different areas of London.
- Analyze the rental price trends and availability in popular business districts versus emerging areas.
- Use mapping techniques to visualize office listings geographically, allowing for intuitive comparisons of office space density and pricing.

## Why This Matters
With hybrid work models and fluctuating demand for office spaces, understanding the rental landscape is more important than ever. Businesses need to make informed decisions about where to locate, while real estate professionals benefit from data-driven insights into market trends. This project provides an in-depth view of the office rental market, offering valuable information for both renters and stakeholders in London’s commercial real estate sector.

## Methodology

### Data Scraping Setup:
- I developed a web scraping script using Python and libraries like `requests` and `BeautifulSoup` to extract data from HubbleHQ’s office listings.
- Data points collected included office location, price per desk, office size, and amenities offered.
- **Challenges:** The website presented dynamic content loading, which required simulating user behavior using `Selenium`.

### Data Cleaning & Processing:
- After collecting the data, I processed it using `Pandas` to clean up inconsistencies and handle missing values.
- Office listings were grouped by location and office size to enable comparison across different regions of London.

### Data Visualization:
- Geographic mapping tools such as `geopandas` and `Folium` were used to plot office listings on an interactive map of London, making it easier to identify price hotspots and regions with high office space availability.
- Further analysis was conducted to compare rental prices in established business districts like Canary Wharf and The City with newer areas such as Shoreditch and Whitechapel.

## Challenges Encountered
- **Dynamic Content:** HubbleHQ’s listings page uses dynamic loading, meaning that office listings are not fully loaded when the page first loads. I had to utilize `Selenium` to automate scrolling and simulate interactions to scrape all available data.
- **Data Cleaning:** Some listings contained incomplete information, such as missing prices or inconsistent office size descriptions, requiring careful data handling to ensure accurate analysis.
- **Geolocation Issues:** Some office listings did not include exact addresses, which made geolocation mapping tricky. I used the nearest available data points to ensure these listings were mapped accurately.

## Key Insights
- **Price Trends by Area:** Unsurprisingly, office spaces in The City and Canary Wharf command the highest rental prices, but newer areas like Shoreditch offer competitive pricing and flexible office spaces, appealing to startups and tech firms.
- **Geographical Distribution:** The map visualization clearly shows a higher density of office listings in central London, while areas further out offer larger office spaces at significantly lower prices.
- **Sectoral Demand:** The data also revealed that coworking spaces and serviced offices are becoming increasingly popular, particularly in creative hubs like Shoreditch and Hackney.

## Conclusions
This project has highlighted the diversity of London’s office rental market, with clear trends emerging across various districts. For businesses looking to establish a presence in London, the data provides valuable insights into pricing and office availability, helping to guide decision-making in an unpredictable market.

## Technical Details for Scraping

### Libraries Used:
- `requests` for sending HTTP requests to the HubbleHQ site.
- `BeautifulSoup` for parsing the HTML structure.
- `Selenium` to handle dynamic content and load all office listings.
- `Pandas` for cleaning and analyzing the data.
- `geopandas` and `Folium` for mapping and geographic visualization.

### Scraping Process:
- The scraping script navigated through multiple pages of office listings, simulating user interaction to ensure all data was captured.
- Extracted data was stored in a structured format (CSV) for easy analysis and visualization.

### Handling Errors:
- Implemented robust error handling to manage timeouts and incomplete page loads, ensuring data consistency throughout the scraping process.

## Next Steps
While this project focused on London, the approach can be scaled to other cities where office rental markets are rapidly changing. Future analysis could include longitudinal studies to track market changes or compare London’s office rental trends with those in other major business hubs.
