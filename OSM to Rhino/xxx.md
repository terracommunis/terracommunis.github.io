# $\color{red}{\textsf{[DRAFT]}}$

# OSM to Rhino

### Objectives
- Extract essential geospatial data from OpenStreetMap to support project pitches and feasibility studies, particularly in markets where early CAD/GIS data purchases may be cost-prohibitive.
- Integrate this data into Rhino/Grasshopper with organized, custom layers to facilitate analysis, data management, and alignment with project-specific needs.

### Tools and Libraries Used
- **OSM API** and **OSMnx**: Used OSM API via the OSMnx library to pull geospatial data for various elements such as buildings, roads, and amenities in target regions.
- **Rhino.Compute and Rhino3DM**: Employed Rhino.Compute for efficient data processing and conversion to Rhino-compatible formats, while Rhino3DM facilitated data handling within Rhino.
- **Grasshopper**: Enabled geospatial analysis and data manipulation directly within Rhino, leveraging Grasshopper’s parametric environment for data categorization and layer management.

### Step-by-Step Data Collection and Import Process
- **Data Extraction**: Used OSMnx to query and retrieve relevant geospatial data for specific project areas, including various urban elements such as roads, buildings, and land use.
- **Data Processing**: Converted the raw data into suitable formats (e.g., polylines, polygons) compatible with Rhino.
- **Layer Categorization in Rhino**: Organized imported data into custom layers within Rhino to separate elements like roads, buildings, and green spaces. This categorization facilitated easier data management and project-specific customization.
- **Geospatial Analysis in Grasshopper**: Enabled specific geospatial analyses directly within Grasshopper, such as proximity to transport networks or density calculations, to support project decision-making.

### Challenges Encountered
- **Data Complexity**: Managing diverse geospatial datasets with varying levels of detail required careful data filtering and processing.
- **Format Compatibility**: Converting data from OSM formats to Rhino-compatible structures (e.g., NURBS curves, meshes) required additional scripting and customization in Rhino.Compute.
- **Layer Management**: Ensuring efficient layer organization within Rhino for large datasets necessitated optimized workflows in Grasshopper to maintain performance.

### Insights and Benefits
- By automating the data extraction and import process, this approach saved time and reduced costs typically associated with purchasing early-stage CAD/GIS data.
- The use of custom layers in Rhino provided a flexible framework for detailed analysis, allowing for project-specific geospatial queries and enhanced data management.
- This workflow offers a scalable solution for feasibility studies in any region, enabling rapid data visualization and early-stage project insights aligned with specific client or project requirements.







![HubbleHQ Office Rental](links/website.jpg)
*Figure 1: Global map showing BREEAM-certified project locations, colour-coded by use class (e.g., Residential, Commercial).*

