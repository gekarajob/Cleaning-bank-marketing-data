# Cleaning-bank-marketing-data
# Bank Marketing Campaign Data Cleaning Project

## Overview
In this project, I was tasked with cleaning and reformatting data collected during a bank's marketing campaign, aimed at encouraging customers to take out personal loans. The bank will use this cleaned data to set up a PostgreSQL database for easier data storage and management, particularly for future campaigns.

The initial data came in a single CSV file, `bank_marketing.csv`, which required specific transformations and cleaning. After processing, I split the data into three separate files: `client.csv`, `campaign.csv`, and `economics.csv`, each following a strict format that the bank specified.

## Dataset
The raw dataset, `bank_marketing.csv`, contains client information, campaign details, and economic indicators. I worked on transforming it into the required structure, ensuring it follows the specified data types and cleaning rules before splitting it into the three final CSV files:

1. **client.csv**
2. **campaign.csv**
3. **economics.csv**

## Data Cleaning and Formatting

Each output file follows a set of cleaning requirements and column specifications, which I applied during the data transformation process.

### 1. **client.csv**

| Column         | Data Type | Description                            | Cleaning Details                                                              |
|----------------|-----------|----------------------------------------|-------------------------------------------------------------------------------|
| client_id      | integer   | Client ID                              | No changes needed                                                             |
| age            | integer   | Client's age in years                  | No changes needed                                                             |
| job            | object    | Client's type of job                   | Replaced any `.` characters with `_`                                          |
| marital        | object    | Client's marital status                | No changes needed                                                             |
| education      | object    | Client's level of education            | Replaced `.` with `_`, and converted `unknown` to `np.NaN`                    |
| credit_default | bool      | Whether the client's credit is in default | Converted to boolean: 1 for "yes", 0 for "no"                              |
| mortgage       | bool      | Whether the client has a mortgage      | Converted to boolean: 1 for "yes", 0 for "no"                                 |

### 2. **campaign.csv**

| Column                    | Data Type  | Description                                  | Cleaning Details                                                                |
|----------------------------|------------|----------------------------------------------|--------------------------------------------------------------------------------|
| client_id                  | integer    | Client ID                                    | No changes needed                                                              |
| number_contacts            | integer    | Number of contact attempts in the current campaign | No changes needed                                                        |
| contact_duration           | integer    | Last contact duration in seconds             | No changes needed                                                              |
| previous_campaign_contacts | integer    | Number of contact attempts in the previous campaign | No changes needed                                                       |
| previous_outcome           | bool       | Outcome of the previous campaign             | Converted to boolean: 1 for "success", 0 for others                            |
| campaign_outcome           | bool       | Outcome of the current campaign              | Converted to boolean: 1 for "yes", 0 for "no"                                  |
| last_contact_date          | datetime   | Last date the client was contacted           | Created from day, month, and a fixed year (2022), formatted as `YYYY-MM-DD`    |

### 3. **economics.csv**

| Column               | Data Type | Description                              | Cleaning Details        |
|----------------------|-----------|------------------------------------------|-------------------------|
| client_id            | integer   | Client ID                                | No changes needed       |
| cons_price_idx       | float     | Consumer price index (monthly indicator) | No changes needed       |
| euribor_three_months | float     | Euribor three-month rate(daily indicator)| No changes needed     |

## Data Processing Steps

Here's how I handled the data cleaning and splitting process:

1. **Loaded the Data**: First, I imported the raw `bank_marketing.csv` using Pandas.
2. **Data Cleaning**: I applied all necessary transformations:
   - Replaced `.` with `_` in certain columns.
   - Converted certain string values to booleans (e.g., "yes"/"no" to 1/0).
   - Created new columns, such as the `last_contact_date`, from existing data.
3. **Splitting the Data**: After cleaning, I split the dataset into three CSV files—`client.csv`, `campaign.csv`, and `economics.csv`—with the correct formatting and data types.
4. **Exporting the Data**: Finally, I saved each cleaned DataFrame as a CSV file for future use in a PostgreSQL database.

## Output Files
After completing the cleaning process, I generated the following three CSV files:

- `client.csv`: Contains client-specific details like age, job, marital status, and mortgage information.
- `campaign.csv`: Contains campaign-related information such as the number of contacts, campaign outcomes, and previous campaign details.
- `economics.csv`: Contains economic indicators relevant to the client, such as the Consumer Price Index and Euribor rates.

## Conclusion
With the data cleaned and split, the bank can now import this structured data into a PostgreSQL database. This setup will not only store the current campaign's data but also make it easier to load data from future campaigns.
