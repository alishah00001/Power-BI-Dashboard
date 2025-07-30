<img width="471" height="253" alt="image" src="https://github.com/user-attachments/assets/151d17ad-10cb-4f07-a4d5-12fb6f49d375" />
# Applied Statistics and Data Visualization Project: Global Population Dynamics

## Project Overview

This project focuses on a comprehensive analysis and visualization of global population dynamics. Using Power BI Desktop, the project explores population figures, projections, and related demographic indicators across various countries and time periods. The analysis leverages three primary datasets: "Population Figures & Projections.csv", "Population Figures & Projections Metadata.xlsx", and "Country Groupings.xlsx".

## Key Analyses and Visualizations Performed

### Data Understanding and Initial Exploration:
* **Population Figures & Projections.csv:** This file contains information related to population over a time period, including Country Name, Country Code, Time, Time Code, Population male & female, Population growth (annual %), Rural and Urban population, life expectancy, birth rate, and death rate.
* **Population Figures & Projections Metadata.xlsx:** This file includes descriptions, definitions, or units for the columns in the Population Figures & Projections dataset.
* **Country Groupings.xlsx:** This file provides a mapping of countries in terms of regions and income groups.
* **Notable Observations:**
    * The data includes detailed information on population figures like male population and female population for each country over multiple years, plus there is also a growth matrix with the name of Population growth (annual%) which can be used to identify trends like periods of growth and decline for specific countries and regions.
    * The dataset includes information on urban and rural population for each country which can be used to determine trends of shifting people from one place to another place globally or within a specific region over a period of time.
    * The dataset includes columns like life expectancy at birth, birth rate, and death rate. These indicators provide information on how the quality of life changes across different countries and regions over a certain period.
    * The “Country Grouping” file gives information for grouping countries across different regions, income levels, or other metrics, enabling comparative analysis across different groups of economies.

### Dashboard Objectives and Justification of Visualizations:

The dashboard aims to visualize population trends, urbanization patterns, and health indicators with interactive capabilities.

1.  **Population Trend (Line and Stacked Column Chart):**
    * **Purpose:** To visualize population trends (including urban population, rural population, and total population) over time using a line and stacked column chart to highlight the difference in population across the top 5 most populated countries and other countries (using filters).
    * **Justification:** Bar and column charts are very useful for comparing values across discrete categories and subcategories, allowing quick interpretation due to distinct height and color differences. Line charts are ideal for showing temporal trends because humans can easily track the direction and steepness of a line. By combining them, the chart provides a comprehensive view: the line focuses on the overall trend in population, and the stacked column focuses on the relative distribution of population.

2.  **Life Expectancy (Filled Map):**
    * **Purpose:** To visualize countries and analyze their life expectancy rate using color on a map interactively.
    * **Justification:** Humans have a strong ability to process and interpret maps due to their alignment with mental models of geography. Color intensity is a pre-attentive characteristic, allowing users to quickly understand differences in life expectancy rates across different countries. The map uses spatial positioning and color coding to convey data quickly compared to tabular or textual data. It provides clear geographical insights, and interactive tooltips allow users to see detailed information without cluttering the map.

3.  **Urban vs. Rural Population Growth (Stacked Area Chart):**
    * **Purpose:** To compare urban and rural population growth using a stacked area chart to identify urbanization patterns across time (year).
    * **Justification:** Stacked area charts allow viewing multiple components within one view while highlighting their individual trends over different categories or time. It uses different colors to split the area under the line by another categorical variable. From this chart, viewers can easily differentiate the trends in urban and rural populations.

4.  **Natural Increase Rate (Card):**
    * **Purpose:** To represent the average of the natural increase rate.
    * **Justification:** A card minimizes visual clutter and visualizes a value without much effort. It isolates that specific value from the rest of the dashboard so that it becomes a main focal point for the viewer. The natural increase rate is an important indicator, which is why it is represented on a card.

5.  **Birth Rate, Death Rate, and Population Growth (Line Chart):**
    * **Purpose:** To plot a line chart for birth rate, annual population growth, and death rate at different periods of time (years) to identify how the quality of life and healthcare changes across different countries with the passage of time.
    * **Justification:** Multiple line charts are used to compare data split out by another categorical variable and are highly effective for showing trends over time. Distinct colors for lines enable quick recognition and differentiation of trends. This chart helps to highlight critical patterns such as periods of high birth rates, death rates, or population growth, providing actionable insights for analyses.

### Dashboard Layout, Formatting, and Composition:
* **Layout:** The dashboard uses a top-bottom and left-to-right hierarchy. Graphs for the top 5 countries and life expectancy from the map are on the top, prioritizing key insights. The stacked area chart and line chart provide deeper analytics and are located on the bottom left and bottom right. Interactive filters for country name and year are added, aligning with best practices for dynamic and interactive experiences.
* **Formatting:** Color coding is used to differentiate between urban and rural populations in the area chart and to emphasize trends in the line chart for clear segmentation. Titles, legends, and axes are clearly labeled across all visuals, and consistent font and style are used throughout the dashboard.
* **Composition:** The dashboard effectively uses chart types suited to their purpose, such as a bar chart for comparing, a line chart for trend visualization, and a stacked area chart for population breakdown. The prominent display of the KPI "natural increase rate" focuses on critical metrics, and all graphs adhere to best practices and theory.

### Dashboard Construction Steps (Power BI):
1.  Open Power BI Desktop.
2.  In the Get data section of the home ribbon, select "Excel workbook."
3.  Navigate to where the Excel files are saved.
4.  Click "Transform data" to open Power Query Editor.
5.  In Power Query Editor, remove blank rows from the "Country Grouping" file.
6.  Replace null values in some columns with "unclassified."
7.  Replace header names if they were not appropriate.
8.  In the main file, change the 'Time' column's data type from decimal to date.
9.  Load the data into Power BI.
10. In the model section, create relationships between tables (e.g., between 'Time Code' in "Population Figures & Projections" and "Code (List of economies)").
11. Create a new measure named "total population" by summing 'Population, female' and 'Population, male'.
12. Create a new measure named "Natural Increase Rate" by calculating `SUM('Birth rate, crude (per 1,000 people)') - SUM('Death rate, crude (per 1,000 people)')`, applying `ALLEXCEPT` for 'Time'.
13. **Visualization 1 (Line and Stacked Column Chart):**
    * Drag the chart to the canvas.
    * Drag 'Country Name' to the X-axis.
    * Drag 'Sum of Urban population', 'Sum of Rural population', and 'Sum of Total population' to the Column Y-axis.
    * Drag 'Average of total population' to the Line Y-axis.
    * Apply a "Top N" filter to 'Country Name' to show the top 5 countries by 'Sum of total population'.
    * Sort the axis by 'Sum of total population'.
    * Rename column names and titles as needed.
14. **Visualization 2 (Filled Map):**
    * Drag the filled map to the canvas.
    * Add 'Country Name' to the 'Location' field.
    * Format fill colors using conditional formatting (Fx) with a gradient based on 'Average of Life expectancy at birth', setting minimum, middle, and maximum values and colors.
    * Add 'Average of Life expectancy at birth' to the 'Tooltips' field.
    * Name the visualization appropriately.
15. **Visualization 3 (Stacked Area Chart):**
    * Drag the stacked area chart to the canvas.
    * Add 'Time (Year)' to the X-axis.
    * Add 'Average of Urban population' and 'Average of Rural population' to the Y-axis.
    * Rename the title and column names.
16. **Visualization 4 (Card):**
    * Drag the card visual to the canvas.
    * Select 'Natural Increase Rate' from the data panel.
    * Rename the title.
17. **Visualization 5 (Multiple Line Chart):**
    * Drag the multiple line chart to the canvas.
    * Apply 'Time (Years)' to the X-axis.
    * Add 'Average of Death rate' and 'Average of Birth rate' to the Y-axis.
    * Add 'Average of Annual Population Growth' to the secondary Y-axis.
    * Rename the title and column names.

### Critical Evaluation of the Dashboard:
* **Strengths:**
    * Effectively represents the population of the top 5 countries through a line and stacked column chart.
    * Clearly shows different trends of birth rate, death rate, and annual population growth through a line chart.
    * Represents the distribution of urban and rural population through a stacked area chart.
    * Visualizes life expectancy with respect to each geographic location through a filled map chart.
    * Provides filters for country and year, enabling users to get more specific information.
    * Prominently displays the natural increase rate as a KPI in a card.
* **Limitations:**
    * The dashboard does not have drill-down options for more granular analysis.
    * The color patterns used in this dashboard may not be fully accessible to color-blind users.
