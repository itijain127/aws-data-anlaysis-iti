# Comprehensive Analysis of Vancouver Parks Dataset

## Descriptive Analysis

### Project Description
Descriptive Analysis of Vancouver Parks Data

### Project Title
Understanding Park Size Distribution Across Vancouver Neighborhoods

### Objective
The primary goal of this project is to conduct a descriptive analysis of Vancouver’s parks dataset. By summarizing park size characteristics, identifying trends, and generating insights, this analysis informs urban planning and resource allocation strategies.

### Dataset
The dataset includes information about parks in Vancouver, containing the following key features:
- **ParkID**: Unique identifier for each park.
- **Hectare**: Size of the park in hectares.
- **Neighbourhood Name**: The neighborhood where the park is located.
- **Facilities**: Available amenities in the park.
- **Washrooms**: Number of washrooms available.
- **GoogleMapDest**: Location details for navigation purposes.
![Dataset from Open Data portal](https://github.com/itijain127/aws-data-anlaysis-iti/blob/16963bd36727e909f173eb7a2ec39653fe40c081/Images%20Project%201/Figure%202%20(Analysis%20chart%20of%20average%20park%20size%20per%20neighbourhood).png)
#### Dataset Details
- **Records**: 216
- **Columns**: 15
- **Data Types**: 3 integers, 1 double, 11 strings
- **Quality**:
  - 99.99% valid entries
  - Less than 1% missing values
  - No duplicate rows

)
### Methodology
#### 1. Data Collection and Preparation
- Data was downloaded from the City of Vancouver Open Data Portal in CSV format.
- Stored in AWS S3 bucket with structured folder paths based on ingestion year, month, and week.
- **Tools**: AWS S3 and Draw.io for workflow visualization.

![Design in draw.io for data implementation](aws-data-anlaysis-iti/Images Project 1
/Figure 3 (Design in draw.io for data implementation).png)

#### 2. Descriptive Statistics
- Used AWS Glue DataBrew to generate summary statistics.
- **Key Metrics Calculated**:
  - Average Park Size per Neighborhood: Total park area divided by the number of parks in each neighborhood.
  - Park Size Distribution: Categorized into small, medium, and large parks.

![Analysis chart of average park size per neighbourhood](Images Project 1/Figure 2 (Analysis chart of average park size per neighbourhood).png)

#### 4. Customer Segmentation (Neighborhood Analysis)
- Segmented neighborhoods based on:
  - Average park size (e.g., large vs. small parks).
  - Number of parks per neighborhood.
- Analyzed patterns of parks distribution.

#### 5. Insights and Findings
- **Neighborhoods with the largest average park sizes**:
  - West End (52.03 hectares).
  - Killarney (19.74 hectares).
- **Neighborhoods with the smallest average park sizes**:
  - Grandview-Woodland (0.78 hectares).
  - Mount Pleasant (0.99 hectares).
- Densely populated areas (e.g., Downtown) prioritize smaller parks for accessibility.

#### 6. Recommendations
- Increase green space allocation in neighborhoods with smaller average park sizes.
- Focus on optimizing park accessibility in dense urban areas.
- Implement targeted development for parks in underserved areas.

### Tools and Technologies
- **Python**: Pandas, Matplotlib, Seaborn for data analysis and visualization.
- **AWS Services**:
  - S3 for data storage.
  - Glue DataBrew for profiling and cleaning.
  - Glue for ETL pipelines.
- **Visualization Platforms**: Tableau for creating dashboards (optional).

### Deliverables
- **Detailed Report**: Summarizes methods, findings, and recommendations.
- **Visualizations and Dashboards**: Highlights key insights clearly.
- **Presentation**: Communicates findings and actionable strategies to stakeholders.

---

## Exploratory Data Analysis

### Project Description
This project involves conducting an Exploratory Data Analysis (EDA) on the parks dataset of Vancouver. The aim is to uncover patterns, trends, and insights related to park sizes across different neighborhoods. The analysis highlights the distribution of park sizes, identifies neighborhoods with the largest and smallest parks, and investigates the relationship between the number of parks and their average size.

### Project Title
Analyzing Park Sizes in Vancouver: An Exploratory Data Analysis

### Objective
The primary goal of this project is to perform an exploratory data analysis (EDA) on the parks dataset from the City of Vancouver. This involves:
- Understanding the distribution of park sizes across neighborhoods.
- Identifying neighborhoods with the largest and smallest parks by average size.
- Exploring the relationship between the number of parks and their average size.

### Dataset
The dataset includes:
- **ParkID**: Unique identifier for each park.
- **Hectare**: Size of the park in hectares.
- **Neighbourhood Name**: The neighborhood where the park is located.
- **Facilities**: Availability of amenities in the park.
- **Washrooms**: Number of washrooms available.
- **GoogleMapDest**: Geolocation data for navigation purposes.

#### Dataset Details
- **Records**: 216
- **Columns**: 15
- **Data Types**: 3 integers, 1 double, 11 strings
- **Quality**:
  - 99.99% valid entries
  - Less than 1% missing values
  - No duplicate rows

### Methodology
#### 1. Data Collection and Preparation
- Data organized in AWS S3 with folders structured by year, month, and week for ingestion.

#### 2. Data Profiling
- Used AWS Glue DataBrew to assess data quality and generate descriptive statistics.

#### 3. Data Cleaning
- Applied cleaning transformations using AWS Glue DataBrew:
  - Handled missing values.
  - Standardized column formats.
  - Renamed columns for clarity.

#### 4. Data Pipeline Design
- Designed an ETL pipeline in AWS Glue to calculate metrics like average park size.

#### 5. Data Analysis and Visualization
- Visualizations created using Python libraries (Matplotlib, Seaborn):
  - **Bar Charts**: Displayed average park sizes by neighborhood.
  - **Scatter Plots**: Highlighted relationships between park count and size.

#### 6. Exploratory Analysis
- Explored the relationship between park size and park count.

---

## Data Wrangling

### Project Description
Data Wrangling for Park Analytics in Vancouver

### Project Title
Data Wrangling for Enhanced Park Analytics in Vancouver

### Objective
To clean, transform, and consolidate the Vancouver Parks dataset to prepare it for robust analysis and reporting.

### Methodology
#### 1. Data Collection
- Data gathered from the City of Vancouver Open Data Portal and stored in AWS S3 buckets.

#### 2. Data Assessment
- Profiling with AWS Glue DataBrew revealed 99.99% valid entries with minimal missing values.

#### 3. Data Cleaning
- Cleaned data using AWS Glue DataBrew:
  - Handled missing values.
  - Standardized formats and renamed columns.

#### 4. Data Transformation
- Derived new metrics like **average park size by neighborhood**.
- Grouped and aggregated data for statistical analysis.

#### 5. Data Consolidation
- Unified data for both user-friendly (CSV) and system-optimized (Parquet) formats.

### Deliverables
- Cleaned datasets in CSV and Parquet formats.
- Documentation and visualizations of data insights.

---
