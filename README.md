
## Data Wrangling

### Project Description
Data Wrangling for Park Analytics in Vancouver

### Project Title
Data Wrangling for Enhanced Park Analytics in Vancouver

### Objective
To clean, transform, and consolidate the Vancouver Parks dataset to prepare it for robust analysis and reporting.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/6db0cacf00f4fc44f9663136706ad5111c7a15c8/Images%20Project%201/Figure%203%20(Design%20in%20draw.io%20for%20data%20implementation).png)

### Methodology
#### 1. Data Collection
- Data gathered from the City of Vancouver Open Data Portal and stored in AWS S3 buckets.
- 
#### 2. Data Profiling
- Profiling with AWS Glue DataBrew revealed 99.99% valid entries with minimal missing values.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project%201/Figure%205%20(Data%20profile%20overview%20from%20data%20profiling%20in%20data%20brew).png)

#### 3. Data Cleaning
- Cleaned data using AWS Glue DataBrew:
  - Handled missing values.
  - Standardized formats and renamed columns.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project%201/Figure%208%20(Data%20cleaning%20output%20stored%20in%20two%20S3%20locations).png)

#### 4. Data Transformation
- Removed any blank cells if any.
- Changed the column names wherever required.
- Following recipe is created for Data transformation

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project%201/Figure%207%20(Data%20cleaning%20and%20recipe%20created%20for%20the%20dataset).png)

### Tools and technologies

- Amazon S3 for storing the data.
- Amazon Glue Databrew to profile and clean the data.

### Deliverables
- Cleaned datasets in CSV and Parquet formats avaialable for user ans System.
- A comprehensive report documenting the data wrangling process, including challenges encountered, methods employed, and final dataset characteristics.

### Timeline
- This project was completed in 1 week including phases for assessment, cleaning, transformation, and documentation.

---

### Descriptive and Exploratory Data Analysis

#### Project Title: Data Analytical Platform (DAP) Design and Implementation for Vancouver Parks

#### Objective: 
To design and implement a data analytical platform for the city of Vancouver that enables descriptive and exploratory analysis of park data and calculates the cost of running this platform on AWS. The goal is to derive insights into park size distribution and its relationship to the number of parks across neighborhoods.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project%201/Figure%202%20(Analysis%20chart%20of%20average%20park%20size%20per%20neighbourhood).png)

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project%201/Figure%2012%20(Analysis%20of%20relation%20between%20avg.%20park%20size%20and%20number%20of%20parks%20per%20neighbourhood).png)

---

#### Dataset: 
The dataset used in this project, sourced from the Open Data Portal - City of Vancouver, contains 216 records with the following features:

- **ParkID**: Unique identifier for each park
- **Name**: Name of the park
- **Hectare**: Size of the park in hectares
- **Facilities**: Available facilities in the park
- **Washrooms**: Availability of washrooms
- **GoogleMapDest**: Location link
- **Other Columns**: Additional relevant fields

#### Data Source:
![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project%201/Figure%201%20(Parks%20Dataset).png)


---

### Methodology:

#### Step 1: Data Ingestion
1. Logged into the AWS Management Console.
2. Created a raw data bucket: `parks-raw-iti`.
3. Organized data into subfolders: `Parks/Ingestion_Year=2024/ingestion_month=11/ingestion_week=47/`.
4. Uploaded the dataset to S3 for further processing.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project%201/Figure%204%20(Data%20ingestion%20in%20raw%20bucket).png)

---

#### Step 2: Data Profiling
1. Used AWS Glue DataBrew to profile the dataset.
2. Key findings:
   - **Rows**: 216
   - **Columns**: 15
   - Data Types: 3 integers, 1 double, and 11 strings.
   - Clean Data: 99.99% valid entries, <1% missing values, no duplicates.
   - Generated visualizations such as box plots and correlation matrices.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project%201/Figure%205%20(Data%20profile%20overview%20from%20data%20profiling%20in%20data%20brew).png)
---

#### Step 3: Data Cleaning
1. Created a DataBrew project and recipe for cleaning operations.
2. Applied transformations: handled missing values, standardized formats, renamed columns.
3. Outputs stored in S3:
   - CSV: `s3://parks-trf-iti/Parks/Data_cleaning/user/`
   - Parquet: `s3://parks-trf-iti/Parks/Data_cleaning/system/`
4. Partitioned the data by `official` for better organization.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project%201/Figure%208%20(Data%20cleaning%20output%20stored%20in%20two%20S3%20locations).png)

---

### Descriptive Analysis

#### Analysis Question:
“What is the distribution of park sizes (in hectares) across different neighborhoods in Vancouver, and which neighborhoods have the largest and smallest average park sizes?”

#### Implementation:
1. Designed the ETL pipeline in AWS Glue to calculate average park size.
2. Steps:
   - Extracted raw data from S3.
   - Dropped irrelevant columns.
   - Grouped data by `neighbourhood_name`.
   - Calculated average park size using aggregation.
3. Stored results in S3:
   - System: `s3://parks-trf-iti/average-park-size/system/`
   - User: `s3://parks-trf-iti/average-park-size/user/`

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project%201/Figure%2010%20(ETL%20Pipeline%20design%20for%20Descriptive%20analysis%20matric).png)

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project%201/Figure%2011%20(Result%20of%20the%20Descriptive%20metric%20data%20stored%20in%20S3%20bucket%20for%20System%20and%20user).png)


#### Key Findings:
| Neighborhood              | Average Park Size (Hectares) |
|---------------------------|-----------------------------|
| West End                 | 52.03                       |
| Killarney                | 19.74                       |
| South Cambie             | 14.03                       |
| Grandview-Woodland       | 0.78                        |
| Mount Pleasant           | 0.99                        |

- **Largest Parks**: West End (52.03 hectares).
- **Smallest Parks**: Grandview-Woodland (0.78 hectares).

---

### Exploratory Analysis

#### Analysis Question:
“What is the relationship between the number of parks and their average size across neighborhoods in Vancouver?”

#### Implementation:
1. Designed a second ETL pipeline in AWS Glue:
   - Calculated metrics: Average Park Size and Park Count.
   - Cleaned and grouped data by `neighbourhood_name`.
2. Stored results in S3:
   - System: `s3://parks-trf-iti/park-size-count-relation/system/`
   - User: `s3://parks-trf-iti/park-size-count-relation/user/`
  
![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project%201/Figure%2013%20(ETL%20pipeline%20design%20for%20exploratory%20analysis%20explaining%20the%20relation%20between%20number%20of%20parks%20and%20avg%20size).png)

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project%201/Figure%2014%20(Output%20data%20stored%20in%20S3%20bucket).png)


#### Key Findings:
| Neighborhood              | Number of Parks | Average Park Size (Hectares) |
|---------------------------|-----------------|-----------------------------|
| Downtown                  | 22              | 1.45                        |
| Dunbar-Southlands         | 7               | 5.67                        |
| Hastings-Sunrise          | 16              | 7.12                        |

- **Downtown**: High park count (22) but small average size (1.45 hectares).
- **Dunbar-Southlands**: Fewer parks (7) but larger average size (5.67 hectares).
- **Hastings-Sunrise**: Balanced count (16) and size (7.12 hectares).

---

### Tools and Technologies:
- **AWS Services**: S3, Glue, DataBrew
- **Visualization Tools**: Draw.io, AWS Glue Console

---

### Deliverables:
1. ETL pipelines for descriptive and exploratory analysis.
2. Cleaned and transformed datasets in CSV and Parquet formats.
3. Insights into park size distribution and relationships with park count.
4. Visualizations and detailed documentation.

---

# Project Title: Data Enrichment and Analysis for Parks Dataset for city of Vancouver

## Objective:
The objective of this project was to enhance and prepare the City of Vancouver Parks dataset by converting it from a non-relational to a relational format, ensuring that the data is well-structured, accessible, and ready for analysis. The goal was to organize and enrich the data for advanced analytics, using AWS Glue for data transformation and Amazon Athena for querying.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project-2/Figure%201(Design%20in%20draw.io)%20-%20.png)

## Dataset:
- City of Vancouver Parks dataset (original dataset in raw formats like CSV, JSON, and Parquet, stored in Amazon S3 buckets).

## Methodology:
1. **Creation of a Data Catalog:**
   - A data catalog named **parks-datacatalog-iti** was created in AWS Glue to act as a centralized repository for the metadata of datasets stored in Amazon S3.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project-2/Figure-2(Data%20Catalog%20Created%20in%20AWS%20Glue).png)

2. **Configuration of Data Crawlers:**
   - Two crawlers (**parks-raw-crawler** and **parks-trf-crawler**) were configured in AWS Glue to scan the raw data in S3, detect the schema, and transform it into relational tables.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project-2/Figure%203%20-%20Crawler%20created%20for%20both%20raw%20and%20transformed%20bucket.png)

3. **Storing Tables in a Database:**
   - The tables generated by the crawlers were stored in the **parks-datacatalog-iti** database in AWS Glue for easy access and querying.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project-2/Figure%204%20-%20Generated%20tables%20as%20a%20result%20of%20crawler%20run.png)

4. **Execution of Crawlers:**
   - The crawlers successfully transformed the raw data into structured tables in various formats (CSV, JSON, Parquet) and populated them in the Glue Data Catalog for easy querying.

5. **Data Analysis with Amazon Athena:**
   - Using Amazon Athena, SQL queries were executed on the transformed data to perform descriptive analytics (e.g., calculating average park sizes and total parks in each neighborhood).
   - Results of these queries were stored in a curated S3 bucket (**parks-cur-iti**) for future reference.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project-2/Figure%205(Descriptive%20analysis%20using%20SQL%20query%20in%20Athena).png)
  
6. **Insights from Query Results:**
   - Actionable insights, such as variations in park distribution and average park size by neighborhood, were derived from the query results.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project-2/Figure%207%20-%20(Amazon%20Athena%20SQL%20Query%20results).png)


## Tools and Techniques:
- **AWS Glue**: For creating the data catalog, configuring crawlers, and transforming raw data into a relational format.
- **Amazon Athena**: For querying structured datasets and performing SQL-based analysis.
- **Amazon S3**: For storing raw, transformed, and curated data.
- **SQL**: For executing queries on the data stored in Athena.

## Deliverables:
1. The **parks-datacatalog-iti** created in AWS Glue for managing metadata.
2. Relational tables generated from raw data, stored in the AWS Glue Data Catalog.
3. Outputs from SQL queries executed in Athena, stored in the curated S3 bucket **parks-cur-iti**.
4. A report showcasing the insights derived from the analysis, including park sizes and distribution metrics.
5. A detailed explanation of the data enrichment process, methodology, tools used, and the insights generated.

---

# Project: Data Protection and Governance for Parks dataset for city of Vancouver

## Objective:
The objective of this project was to implement data protection and governance practices for the City of Vancouver Parks dataset to ensure data confidentiality, integrity, and availability. Additionally, it aimed to ensure compliance with governance policies by automating data quality checks and securing sensitive information using AWS services.

## Dataset:
- City of Vancouver Parks dataset (transformed dataset stored in Amazon S3 buckets and managed within AWS Glue Data Catalog).

## Methodology:
1. **Data Protection Measures:**
   - **Encryption**: A custom encryption key **Parks-key-iti** was created using AWS Key Management Service (KMS) to secure the dataset, ensuring confidentiality and control over the encryption/decryption process.
  
![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project-2/Figure%208%20-%20Custom%20key%20created%20in%20KMS.png)
     
   - **Replication for Data Redundancy**: Replication rules were set up for both raw and transformed data buckets to enhance data availability and ensure disaster recovery. Replication was configured from the raw data bucket (**parks-raw-iti**) to the backup bucket (**parks-raw-back-iti**) and from the transformed data bucket (**parks-trf-iti**) to the backup bucket (**parks-trf-back-iti**).

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project-2/Figure%209%20-(Replication%20rule%20created%20for%20raw%20bucket).png)

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project-2/Figure%2010(Replication%20rule%20created%20for%20Transform%20bucket).png)

2. **Data Governance Implementation:**
   - **Data Quality Pipeline**: A data quality pipeline named **parks-QPC-iti** was created in AWS Glue. This pipeline automated data quality checks, ensuring compliance with governance policies and helping to maintain data accuracy and consistency.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project-2/Figure%2011%20(Data%20Quality%20ETL%20pipeline%20created%20in%20AWS%20Glue).png)

   - **Sensitive Data Detection**: A Transform node to **Detect PII (Personally Identifiable Information)** was incorporated into the pipeline to identify and handle sensitive information such as Canada Passport Numbers and Government Identification Numbers.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project-2/Figure%2012%20(Step%20implemented%20in%20ETL%20Pipeline%20to%20detect%20sensitive%20data).png)
  
   - **Data Quality Evaluation**: Data was evaluated for completeness and freshness using an **Evaluate Data Quality** node. The pipeline ensured that the data was complete, up-to-date, and met quality standards.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project-2/Figure%2013%20(Data%20evaluated%20based%20on%20freshness%20and%20uniqueness).png)
    
   - **Failed and Passed Records Handling**: Data that passed the quality checks was routed to a **Passed** folder, while data that failed the checks was routed to a **Failed** folder for further processing.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project-2/Figure%2014%20(Data%20Quality%20folder%20created%20in%20transform%20bucket).png)

3. **Storing Quality-Checked Data**: 
   - The quality-checked data was stored in the **Passed** and **Failed** subfolders within the transformed S3 bucket (**parks-trf-iti**) for further analysis and troubleshooting.
  
![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project-2/Figure%2015%20(Result%20of%20passed%20quality%20data%20stored%20in%20S3).png)

## Tools and Techniques:
- **AWS KMS (Key Management Service)**: For creating and managing custom encryption keys to ensure data confidentiality.
- **Amazon S3**: For storing raw, transformed, and replicated data with redundancy.
- **AWS Glue**: For creating the data quality pipeline, configuring sensitive data detection, and performing data quality evaluation.
- **SQL**: For querying and validating the quality of the data.

## Deliverables:
1. A custom encryption key (**Parks-key-iti**) created in AWS KMS to secure the dataset.
2. Replication rules configured for both raw and transformed data buckets to ensure data availability and disaster recovery.
3. An automated data quality pipeline created in AWS Glue to ensure governance policies are met, with stages for detecting sensitive data and evaluating data quality.
4. Segregated data stored in the **Passed** and **Failed** folders within the transformed S3 bucket.
5. A detailed report documenting the implementation of data protection and governance measures, including encryption, data replication, data quality checks, and handling of sensitive data.
---
# Project: Data Observability for Parks Dataset for city of Vancouver

## Objective:
The objective of this project was to implement continuous monitoring and observability for the City of Vancouver Parks dataset. The goal was to track and visualize system performance, monitor data integrity, and proactively detect issues using AWS services such as CloudWatch and CloudTrail, ensuring that the data analytics platform operates smoothly and meets business requirements.

## Dataset:
- City of Vancouver Parks dataset (transformed dataset stored in Amazon S3 buckets and analyzed using AWS Athena).

## Methodology:
1. **Monitoring Dashboard Creation:**
   - A custom monitoring dashboard named **Parks-DAP-Mon-Dash-iti** was created in **Amazon CloudWatch** to provide real-time insights into system performance. This dashboard displayed key metrics such as bucket size, number of objects in each bucket, and estimated charges for data storage and processing.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project-2/Figure%2016%20(Dashboard%20created%20in%20AWS%20CloudWatch).png)

2. **Setting Up Alarms:**
   - Alarms were set up in Amazon CloudWatch to trigger when specific thresholds were crossed, such as when the bucket size exceeded 500,000 bytes in a single day. This ensures proactive management and quick action on potential issues such as data overflow or unexpected growth.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project-2/Figure%2017(Alarm%20set%20up%20for%20all%20three%20Storage%20Buckets).png)

3. **CloudTrail Logging Implementation:**
   - **CloudTrail** was configured to capture detailed logs of all user activities and API calls within the data platform. A trail named **parks-trail-iti** was created to track actions like starting queries, creating resources, and logging in users. These logs provide a complete audit trail for compliance and troubleshooting.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project-2/Figure%2018%20(Trail%20created%20in%20cloud%20trail).png)

4. **Event History Logging:**
   - The **Event History** feature of CloudTrail was used to track various user interactions and API activities. This included logging key events such as initiating queries, creating or deleting resources, and monitoring user logins, helping identify anomalies and ensuring the system operates as expected.
  
![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20Project-2/Figure%2019%20(Trail%20showing%20event%20history).png)  

## Tools and Techniques:
- **Amazon CloudWatch**: For monitoring system metrics, creating a custom dashboard, and setting up alarms for proactive issue management.
- **AWS CloudTrail**: For tracking and logging all user activities and API calls within the data platform, providing a detailed audit trail.
- **SQL**: For querying logs and metrics related to system performance and events.

## Deliverables:
1. A custom **Parks-DAP-Mon-Dash-iti** dashboard created in Amazon CloudWatch to visualize system performance metrics and track the health of the data analytics platform.
2. onfigured alarms to notify stakeholders when critical storage thresholds are exceeded, ensuring timely resolution of potential issues.
3. Detailed logs captured by CloudTrail, offering a complete history of user activities and API calls for audit and troubleshooting purposes.
4. Logs of key user events, including query executions and resource management activities, tracked using CloudTrail's event history feature.
5. A report documenting the setup of the monitoring dashboard, alarm configurations, and CloudTrail logs, explaining the tools and techniques used to ensure system visibility and detect issues early.

---

---

### **Project: Data Wrangling for Program Review Data for Academic Department of UCW**  

The Goal was to perform all these steps in AWS console as per the requirements of the projects which was designed in Draw.io.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20UCW/Draw.io.png)

Following projects were executed to acheive this:

#### **Project Title**  
Data Wrangling for Program Review Data  

#### **Objective**  
To prepare and clean the program review data for analysis by addressing inconsistencies, handling missing values, and structuring the data for downstream processes.  

#### **Dataset**  
- **Source**: Program review dataset provided in Excel format.  
- **Key Features**:  
  - Review ID  
  - Program Name  
  - Review Status  
  - Completion Date  
  - Reviewer Information  
  - Additional relevant fields  

#### **Methodology**  
1. **Data Ingestion**:  
   - Loaded the dataset into AWS S3 for processing.  
   - Organized files into structured folders for accessibility.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20UCW/Data%20ingestion%201.png)
     
2. **Data Cleaning**:  
   - Addressed missing values and standardized formats using AWS Glue DataBrew.  
   - Removed duplicates and ensured data integrity.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20UCW/Data%20cleaning%20recipe.png)
  
3. **Profiling**:  
   - Profiled the data using AWS Glue DataBrew to identify quality issues and understand dataset characteristics.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20UCW/Data%20Profiling.png)

#### **Tools and Techniques**  
- **AWS Services**:  
  - S3 for storage  
  - Glue DataBrew for cleaning and profiling  
- **Visualization Tools**: Draw.io for workflow design  

#### **Deliverables**  
1. Cleaned and structured dataset stored in S3.  
2. Data quality report with identified issues and resolutions.  
3. Workflow diagram for data wrangling processes.  

---

### **Project 2: Descriptive Analysis for Program Review Data for Academic Department of UCW**  

#### **Project Title**  
Descriptive Analysis for Program Review Data  

#### **Objective**  
To summarize and analyze program review data, focusing on metrics such as completion review rates and trends over time.  

#### **Dataset**  
- **Source**: Program review dataset provided in Excel format.  
- **Key Features**:  
  - Review ID  
  - Program Name  
  - Review Status  
  - Completion Date  

#### **Methodology**  
1. **Metric Calculation**:  
   - Built an ETL pipeline in AWS Glue to calculate the completion review rate using:  
     
     Completion Review Rate = Total Number of Completed Reviews\Total Number of Reviews
  

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20UCW/ETL%20pipeline.png)

#### **Tools and Techniques**  
- **AWS Services**:  
  - Glue for ETL  
- **Visualization Tools**: Excel and Draw.io  

#### **Deliverables**  
1. Completion review rate metric results.
3. Stored pipeline results in an S3 bucket.  

---

### **Project 3: Data Enrichment and Analysis for UCW Dataset**  

#### **Project Title**  
Data Enrichment and Analysis for UCW Dataset  

#### **Objective**  
To enhance the dataset by converting non-relational data into a relational format and performing advanced analytics for better policy and program review insights.  

#### **Dataset**  
- **Source**: Program review dataset in Excel format.  
- **Key Features**:  
  - Review ID  
  - Program Name  
  - Review Status  
  - Completion Date  

#### **Methodology**  
1. **Data Enrichment**:  
   - Created a data catalog and configured AWS Glue Crawlers to convert the non-relational dataset into a relational format.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20UCW/Crawlers.png)

   - Stored relational tables in a centralized database for querying.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20UCW/Relational%20Database.png)

1. **Analysis**:  
   - Used Amazon Athena to perform SQL queries for descriptive and exploratory analysis.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20UCW/Athena.png)

2. **Result Storage**:  
   - Stored enriched data and query results in partitioned folders in S3.  

#### **Tools and Techniques**  
- **AWS Services**:  
  - Glue for crawling and data catalog creation  
  - Athena for SQL analysis  
  - S3 for storage
  - DyanamoDB for storing relational database

#### **Deliverables**  
1. Relational tables accessible via the AWS Glue Data Catalog.  
2. Analytical insights into program reviews.  
3. Partitioned data stored in S3 for further analysis.  

---

### **Project 4: Data Protection and Governance for Program Review Dataset**  

#### **Project Title**  
Data Protection and Governance for UCW Dataset  

#### **Objective**  
To secure the UCW dataset by implementing encryption, redundancy, and data quality governance mechanisms.  

#### **Dataset**  
- **Source**: Program review dataset in Excel format.  

#### **Methodology**  
1. **Data Protection**:  
   - Created a custom encryption key in AWS KMS to secure sensitive data.  
   - Configured replication rules for raw and transformed buckets to ensure redundancy.

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20UCW/reprule%20raw.png)

![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20UCW/Reprule%20trf.png)
  
2. **Governance**:  
   - Designed a Data Quality Pipeline in AWS Glue to detect PII and evaluate data completeness and freshness.  
   - Organized data into "Passed" and "Failed" folders based on quality checks.
  
![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20UCW/Data%20QPC%20%20pipeline.png) 

#### **Tools and Techniques**  
- **AWS Services**:  
  - KMS for encryption  
  - Glue for data quality checks  
  - S3 for storage and replication  

#### **Deliverables**  
1. Custom encryption key for secure data handling.  
2. Redundant datasets stored in backup S3 buckets.  
3. Segregated quality-checked data for analysis.  

---

### **Project 5: Data Observability for Program review Dataset for Academic Department of UCW**  

#### **Project Title**  
Data Observability for UCW Dataset  

#### **Objective**  
To implement monitoring and observability measures for the UCW dataset to ensure reliability, integrity, and efficient resource utilization.  

#### **Dataset**  
- **Source**: Program review dataset in S3.  

#### **Methodology**  
1. **Monitoring Dashboard**:  
   - Created a custom CloudWatch dashboard to monitor bucket size, object count, and estimated costs.
  
![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20UCW/Dashboard.png) 
  
2. **Alarm Configuration**:  
   - Set up alarms to detect critical thresholds, such as excessive storage usage.
   -    
3. **Event Logging**:  
   - Enabled CloudTrail logging to track API activities and user actions for compliance.
  
![Alt text](https://github.com/itijain127/aws-data-anlaysis-iti/blob/main/Images%20UCW/Cloud%20trail.png) 

#### **Tools and Techniques**  
- **AWS Services**:  
  - CloudWatch for dashboards and alarms  
  - CloudTrail for event tracking  

#### **Deliverables**  
1. CloudWatch dashboard for real-time monitoring.  
2. Configured alarms for proactive issue detection.  
3. Detailed event logs for auditing and troubleshooting.  

---






