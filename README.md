# Pandas Data Cleaning and Exploratory Data Analysis (EDA) Projects

This repository showcases my projects utilizing **Pandas** for data cleaning and exploratory data analysis (EDA). These projects illustrate essential techniques for preparing datasets and deriving insights through visualizations.

## Project 1: Data Cleaning

### Overview
In this project, I demonstrate how to clean and preprocess a dataset of customer call lists. The goal is to ensure the data is structured, accurate, and ready for analysis.

### Key Steps in Data Cleaning:
1. **Importing Libraries**:
   ```python
   import pandas as pd
   ```
   We start by importing the Pandas library for data manipulation.

2. **Loading the Dataset**:
   ```python
   df = pd.read_excel(r"J:\PANDAS\Customer Call List.xlsx")
   ```
   The dataset is loaded from an Excel file.

3. **Removing Duplicates**:
   ```python
   df = df.drop_duplicates()
   ```
   Any duplicate entries are eliminated to ensure unique records.

4. **Dropping Unnecessary Columns**:
   ```python
   df = df.drop(columns="Not_Useful_Column")
   ```
   Columns that do not contribute to the analysis are removed.

5. **Stripping Whitespace from Last Names**:
   ```python
   df["Last_Name"] = df["Last_Name"].str.strip("123._/")
   ```
   Extraneous characters and whitespace are removed from the last names.

6. **Cleaning Phone Numbers**:
   ```python
   df["Phone_Number"] = df["Phone_Number"].str.replace('Na--','')
   ```
   Invalid characters are removed from phone numbers to ensure proper formatting.

7. **Splitting Address into Components**:
   ```python
   df[["Street_Address", "State", "Zip_Code"]] = df["Address"].str.split(',', 2, expand=True)
   ```
   The address is split into separate columns for better usability.

8. **Normalizing 'Do Not Contact' Values**:
   ```python
   df["Do_Not_Contact"] = df["Do_Not_Contact"].str.replace('Yes','Y')
   ```
   The entries in the 'Do Not Contact' column are standardized for consistency.

9. **Filling Missing Values**:
   ```python
   df = df.fillna('')
   ```
   Missing values are filled to maintain the integrity of the dataset.

10. **Dropping Unwanted Entries**:
    ```python
    df.drop(x, inplace=True)
    ```
    Rows with missing phone numbers or marked as 'Do Not Contact' are removed.

11. **Resetting the Index**:
    ```python
    df = df.reset_index(drop=True)
    ```
    The index is reset after cleaning to maintain a sequential order.

## Project 2: Exploratory Data Analysis (EDA)

### Overview
In this project, I analyze the world population dataset to derive insights and visualize trends using various techniques.

### Key Steps in EDA:
1. **Importing Libraries**:
   ```python
   import pandas as pd
   import seaborn as sns
   import matplotlib.pyplot as plt
   ```
   We import necessary libraries for data manipulation and visualization.

2. **Loading the Dataset**:
   ```python
   df = pd.read_csv(r"J:\PANDAS\world_population.csv")
   ```
   The dataset is loaded from a CSV file.

3. **Setting Display Options**:
   ```python
   pd.set_option('display.float_format', lambda x: '%.2f' % x)
   ```
   This improves the readability of float outputs.

4. **Data Exploration**:
   ```python
   df.info()
   df.describe()
   df.isnull().sum()
   df.nunique()
   ```
   Basic statistics and information about the dataset are generated to understand its structure and content.

5. **Visualizing Correlations**:
   ```python
   sns.heatmap(df.corr(), annot=True)
   plt.show()
   ```
   A heatmap is created to visualize the correlation between different features.

6. **Grouping and Analyzing by Continent**:
   ```python
   df.groupby('Continent').mean().sort_values(by="2022 Population", ascending=False)
   ```
   Population statistics are analyzed and grouped by continent.

7. **Population Trends Over Time**:
   ```python
   df2 = df.groupby('Continent')[['1970 Population', '1980 Population', '1990 Population', '2000 Population', '2010 Population', '2015 Population', '2020 Population', '2022 Population']].mean().sort_values(by="2022 Population", ascending=False)
   df3 = df2.transpose()
   df3.plot()
   ```
   Trends in population growth over the decades are visualized using line plots.

8. **Box Plot Visualization**:
   ```python
   df.boxplot(figsize=(20,10))
   ```
   A box plot is created to visualize the distribution of population figures.

## Conclusion
These projects illustrate fundamental skills in data cleaning and exploratory data analysis using Pandas. The techniques demonstrated are essential for any data-driven decision-making process.

### How to Run the Projects
1. Clone the repository to your local machine.
2. Ensure you have the necessary libraries installed (`pandas`, `seaborn`, `matplotlib`).
3. Adjust file paths as necessary for your environment.
4. Execute the scripts to view the results.


