# Data Modeling with dbt and Amazon Redshift

This project demonstrates data modeling and transformation using dbt (Data Build Tool), with the final data stored in Amazon Redshift Serverless.
It follows data engineering best practices, including version control, modularization, testing, and documentation.


# Project Overview

Using simulated mobile sales data, this project showcases how to transform raw transactional data into clean, analytics-ready models.
The transformations are performed with dbt, ensuring data consistency, quality validation, and documentation automation.


# Tech Stack

• Amazon Redshift Serverless → Data warehouse for analytical storage

• dbt (Data Build Tool) → SQL transformations, testing, and documentation

• Python 3.12 → Runtime environment for dbt via Poetry

• Poetry → Dependency and environment management

• WSL2 (Ubuntu 24.04) → Linux development environment within Windows

• Git & GitHub → Version control and project hosting

• CLI (Command Line Interface) → dbt operations (dbt run, dbt test, etc.)


# Data Structure

| Layer           | Model                | Description                                            |
| --------------- | -------------------- | ------------------------------------------------------ |
| **Raw Layer**   | `raw_mobile_sales`   | Original unprocessed data                              |
| **Clean Layer** | `clean_mobile_sales` | Aggregated and standardized model by brand and product |


# Data Quality Tests

• Implemented and validated through dbt tests:

• not_null → Ensures mandatory columns contain no null values

• unique → Validates uniqueness of key identifiers (e.g., marca)

• accepted_values → Removed intentionally after a failed test to maintain integrity


# How to Run

1 - Install dependencies with Poetry

poetry install

2 - Configure dbt connection

• Update your profiles.yml with Redshift Serverless credentials.

3 - Clean project build

poetry run dbt clean

4 - Run dbt models

Run dbt models

5 - Execute dbt tests

poetry run dbt test


# Example Outputs

• Successful dbt model execution:

poetry run dbt run

• Passed dbt tests:

poetry run dbt test

• Query results on Redshift:

SELECT * FROM clean_mobile_sales;

### Example result:

| marca   | produto       | total_vendido | receita_total |
| ------- | ------------- | ------------- | ------------- |
| Samsung | Galaxy A52    | 100           | 1500          |
| Apple   | iPhone 13     | 50            | 5000          |
| Xiaomi  | Redmi Note 11 | 200           | 1000          |

# Key Learnings

• How to model and transform data using dbt + Redshift

• Implementing data quality tests and modular SQL design

• Managing dependencies and environments with Poetry

• Executing dbt pipelines in a Linux environment (WSL2)

