# OIBSIP_domain_taskno.three
# Project Summary: Airbnb NYC Data Cleaning and Preprocessing
This project focuses on the essential data cleaning and preprocessing steps of a dataset containing Airbnb listings in New York City. The primary goal was to prepare the raw data for a reliable and robust analysis by addressing common data quality issues.

1. Data Loading and Initial Inspection
The analysis began by loading the Airbnb dataset from a zipped CSV file. A preliminary inspection of the data was performed to understand its structure, including:

Shape: The dataset contained 48,895 rows and 16 columns.

Data Types: The data types of each column were checked to identify potential issues, such as date columns stored as strings.

Summary Statistics: df.describe(include="all") was used to get a high-level overview of both numerical and categorical features, revealing the presence of missing values and potential outliers.

2. Handling Missing Values
Several columns had missing values, which can negatively impact an analysis. These were handled as follows:

reviews_per_month: This numerical column, which had over 10,000 missing values, was filled with the median value of the column. Using the median is a robust way to handle missing data as it is less sensitive to outliers than the mean.

host_name and name: These text-based columns had a small number of missing values (21 and 16, respectively). They were filled with the string "Unknown" to maintain the integrity of the data without removing a significant number of rows.

last_review: This column also contained many missing values, but since it's a date and its missingness often corresponds to listings with no reviews, it was not filled in the same way as other columns. This decision was made to preserve the meaning of a listing having no review.

3. Removing Duplicates and Standardization
To ensure data consistency and accuracy, several standardization and duplicate removal steps were performed:

Duplicate Rows: A check for fully duplicate rows in the dataset confirmed that there were no identical duplicates, so no rows were dropped based on this criterion.

Column Name Standardization: All column names were converted to lowercase for consistency, making them easier to work with in code.

Text Standardization: The neighbourhood_group column was cleaned of any leading or trailing whitespace to ensure that all unique values are correctly identified.

Handling Outliers: A box plot for the price column revealed a significant number of extreme outliers. To mitigate their impact on future analysis, listings with a price of \$1000 or more were removed, resulting in a cleaner dataset with a more representative price distribution.

# Tools Used
Pandas: Essential for all data manipulation tasks, including loading the data, handling missing values, creating new columns, and dropping unnecessary ones.

NumPy: Used for efficient numerical operations.

Matplotlib.pyplot and Seaborn: Utilized for data visualization, specifically to create box plots for outlier detection.

Zipfile: Used to extract the dataset from a compressed zip archive.
