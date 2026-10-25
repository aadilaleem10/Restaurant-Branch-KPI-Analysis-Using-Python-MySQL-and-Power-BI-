# Global Restaurant KPI Analysis

## Project Overview

The **Global Restaurant KPI Analysis** project analyzes a global restaurant dataset using Python, Pandas, NumPy, Matplotlib, Seaborn, MySQL, and Power BI. The project follows an end-to-end data analytics workflow: the original dataset was provided, missing values and other data-quality issues were handled in Python, the cleaned dataset was exported as a CSV file, the data was loaded into MySQL, and Power BI was used to build a dashboard using the database as its data source.

The notebook describes a dataset containing **9,551 restaurants across 15 countries and 141 cities**, with information such as restaurant ratings, cuisines, cost/price range, votes, and online-delivery availability.

## Project Workflow

1. **Dataset provided**  
   Started with the supplied restaurant dataset in CSV format.

2. **Exploratory Data Analysis (EDA)**  
   Used Pandas to inspect the dataset, review column types and summary statistics, and identify missing values and duplicate rows.

3. **Data cleaning with Python**  
   - Standardized column names to lowercase `snake_case`.
   - Removed the `switch_to_order_menu` column because it had no analytical value in this dataset.
   - Replaced missing cuisine values with `Not Available`.
   - Removed duplicate rows.
   - Added an `is_rated` label to distinguish rated and not-rated restaurants based on vote counts.
   - Converted Yes/No fields for table booking, online delivery, and current delivery into Boolean values.
   - Trimmed whitespace from text values and reset the DataFrame index.

4. **Data visualization and exploration**  
   Created charts with Matplotlib and Seaborn to explore:
   - Cities with the highest number of restaurants.
   - Distribution of aggregate restaurant ratings.
   - Ratings across price ranges.
   - Share of restaurants offering online delivery.
   - Number of restaurants in each rating category.

5. **Export cleaned data**  
   Saved the cleaned DataFrame to `global_cleaned.csv` using Pandas. The notebook writes this file to its current working directory; update `OUTPUT_PATH` if you want to save it to a specific folder.

6. **Load data into MySQL**  
   Used `mysql-connector-python` to create the `global_kpi_db` database and load the cleaned data into the `cleaned_data` table.

7. **Build a Power BI dashboard**  
   Connected Power BI to the database/data source and created a dashboard to present restaurant KPIs and trends visually. The dashboard was created in Power BI; it is not included in this notebook file.

## Tools and Technologies

- **Python** — data processing and analysis
- **Pandas** — loading, cleaning, transforming, and exporting data
- **NumPy** — creating the rated/not-rated label
- **Matplotlib and Seaborn** — exploratory charts
- **MySQL** — storing the cleaned dataset in a database table
- **mysql-connector-python** — transferring data from Python to MySQL
- **Power BI** — dashboard development and KPI visualization
- **Jupyter Notebook** — documenting and running the analysis workflow

## Repository Contents

- `Global_KPI_Analysis.ipynb` — notebook containing data loading, EDA, cleaning, visualizations, CSV export, and MySQL loading code.
- `global_cleaned.csv` — cleaned dataset generated when the notebook is run.
- `charts/` — folder for charts saved by the notebook.
- Power BI dashboard file — add your `.pbix` file to the repository if you want to share the dashboard.

> The CSV, chart images, and Power BI file are generated or maintained separately; they are not embedded in the uploaded notebook.

## How to Run

### 1. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn mysql-connector-python
```

### 2. Prepare the source dataset

Place the original CSV file in an accessible location and update `RAW_PATH` in the notebook to point to that file.

### 3. Configure MySQL securely

Make sure your MySQL server is running. Update the connection settings in the notebook for your own environment.

**Security note:** Do not publish database passwords in a public notebook or repository. Use an environment variable or a local configuration file excluded from version control. Replace any password that has already been exposed in a public repository.

### 4. Run the notebook

Run the cells in order. The notebook will inspect and clean the dataset, generate exploratory charts, export `global_cleaned.csv`, and attempt to create/populate the MySQL database and table.

### 5. Connect Power BI

In Power BI, connect to the MySQL database using the appropriate MySQL connector/driver and credentials, select `global_kpi_db.cleaned_data`, and build the visuals and KPI cards required for your dashboard. The exact connection steps may vary depending on your Power BI and MySQL driver setup.

## Potential Business Questions

The cleaned dataset and dashboard can help explore questions such as:

- Which cities have the largest numbers of listed restaurants?
- How are restaurant ratings distributed?
- How do ratings vary by price range?
- What proportion of restaurants offer online delivery?
- How many restaurants fall into each rating category?
- How do restaurant characteristics vary across locations?

These are analysis questions supported by the available fields; conclusions should be drawn from the actual dashboard and data rather than assumed in advance.

## Important Notes

- The notebook's source path is configured for a local Windows machine. Update it before running on another computer.
- The notebook creates the database and drops/recreates the `cleaned_data` table each time the MySQL-loading cell is run. Back up any important table data before rerunning that cell.
- The uploaded notebook uses **MySQL**, not Microsoft SQL Server. If your Power BI connection was actually made through Microsoft SQL Server, document that additional step separately; otherwise, describe the data source as MySQL.
- Validate the data types and cleaning results after loading, especially if you modify the source dataset.

## Project Summary

This project demonstrates a complete beginner-friendly analytics pipeline: **raw CSV → Python EDA and cleaning → cleaned CSV → MySQL database → Power BI dashboard**. It combines data preparation, exploratory analysis, database integration, and dashboard reporting in one workflow.
