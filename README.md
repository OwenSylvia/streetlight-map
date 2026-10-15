# Municipal Infrastructure Asset Management Dashboard
### A Geospatial Infrastructure Study & Financial Backlog Analysis of Santa Barbara, CA

---

## Live Interactive Dashboard
The live interactive web map portal can be accessed directly at:
https://github.io

*Note: For optimal functionality, view this portal on a desktop or tablet web browser. Users can pan, zoom, and select individual assets to inspect the embedded attribute tracking data.*

---

## Project Overview
Many small-to-medium municipalities manage localized physical infrastructure networks using fragmented legacy systems, analog blueprints, or unorganized spreadsheets. This project replicates an enterprise-grade municipal asset inventory and utility mapping workflow tailored for local government public works operations. 

Using Santa Barbara, California, as a study area, I constructed a relational geographic database, executed financial asset depreciation equations, mapped interconnected linear electrical circuits, and deployed a fully responsive web map dashboard.

---

## Technical Process and Methodology

### 1. Tabular Data Integration & Geocoding Data Pipeline
The core phase of this project focused on transforming raw, non-spatial tabular data into a functional geographic database. I initiated this pipeline by structuring an unorganized spreadsheet containing text-based addresses and baseline engineering metrics. 

Because the source file completely lacked coordinate geometry (X/Y data), I engineered a geocoding data pipeline using QGIS and the open-source OpenStreetMap Nominatim web service. The technical process involved:
* Ingesting the tabular `.csv` schema into the spatial environment as a delimited text layer.
* Parsing the full text-string addresses through the web engine to fetch corresponding real-world geographic coordinates.
* Generating 30 discrete point geometry features embedded with spatial references, successfully projecting the tabular entries onto their precise real-world locations along the Santa Barbara street grid.

### 2. Relational Database Management & Schema Configuration
To ensure the inventory functioned as an operational management tool, I configured a rigorous relational database schema. This involved establishing strict data type constraints—specifically cleaning and converting currency fields into pure numeric data types (real/decimals) so the system could perform mathematical functions. I implemented attribute fields to track key variables, including unique identifiers (`Asset_ID`), material classifications, and compliance markers tracking accessibility status (`ADA_Compliant`) against modern structural legal standards.

### 3. Data Engineering & SQL Expressions
A critical bottleneck for public works directors is calculating immediate financial liabilities for budget allocation. To automate this process within the layer attributes, I executed an conditional "If/Then" mathematical query inside the QGIS Field Calculator. 

By identifying assets displaying critical wear (Condition Scores of 1 or 2), the database expression was engineered to query the clean numeric unit cost column to calculate localized financial risk, while setting stable, active assets to zero:

```sql
CASE 
    WHEN "Condition_Score" <= 2 THEN "Estimated_Cost"
    ELSE 0
END
```

This data transformation successfully isolated maintenance liabilities from active assets, enabling users to run queries to determine the total financial backlog required for Capital Improvement Programs.

### 4. Cartography & Linear Network Design
Map features were dynamically styled using categorized symbology based on operational status (Green representing healthy, active units; Red indicating an immediate need for repair). To simulate an authentic municipal power grid, assets were linked into separate, isolated localized electrical loop circuits using geometric snapping rules. This prevented the false connectivity of the entire network onto a single grid line, mirroring real-world circuit design. Clear font buffering was integrated around floating `Asset_ID` markers to maintain legibility against high-contrast background aerial satellite imagery.

### 5. Web GIS Deployment
The final step involved converting the localized QGIS workspace into an open-source web format. The vector geometries, attribute forms, and styling rules were compiled into a self-contained, lightweight HTML package using a web mapping extension. This allowed the full database to render natively across standard desktop and mobile browsers via GitHub Pages without requiring external database software.

---

## Data Pipeline Visualization

### Tabular Spreadsheet Source to Spatial GIS Point Geometry
Below is the visualization of the data transformation process, illustrating the migration from raw tabular rows to fully mapped point features integrated onto the Santa Barbara aerial satellite network.

![Tabular Spreadsheet to Spatial Map Comparison](PATH_TO_YOUR_SCREENSHOT.png)
*(To update this image: Upload your screenshot to your GitHub repository, copy its file path, and replace `PATH_TO_YOUR_SCREENSHOT.png` with your actual file name.)*

---

## Core Competencies and Academic Pathway
* **GIS Software Tools:** QGIS (Open-Source), ArcGIS Pro, Esri Virtual Desktop Infrastructure (VDI).
* **Data Integration:** Delimited text files, tabular geocoding, table joins, spatial joins, and SQL query filters.
* **Academic Context:** First-year student at Santa Barbara City College (SBCC) explicitly pursuing a dedicated Geographic Information Systems (GIS), Geomatics, and Geospatial Technology career pathway. This project was developed independently to gain hands-on technical experience with municipal spatial datasets and cloud-based data deployment.

