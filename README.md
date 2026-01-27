# PCOS Prediction Pipeline: Medallion Architecture on Databricks


## Project Overview

This project implements an end-to-end Data Engineering and Machine Learning pipeline to predict Polycystic Ovary Syndrome (PCOS) based on clinical markers.

    Note on Origins: This project is a streamlined, modernized reconstruction of a previous pipeline originally built on Snowflake. Following the "unfortunate loss" of the original Snowflake environment, this version was rebuilt from the ground up in Databricks, utilizing Unity Catalog and MLflow for improved tracking and scalability.

## Architecture: The Medallion structure

The data flows through three distinct layers:

    Bronze (Ingestion): * Source: CSV files landed in a Databricks Volume (/Volumes/main/pcos_raw/landing_zone/).

        Process: Raw data is captured "as-is" to preserve the original record. Columns are renamed to remove special characters, replaced with "_".

    Silver (Cleaned):

        Process: Schema enforcement, data type casting (e.g., converting integers to Booleans for symptoms), and column renaming for clarity.

    Gold (Feature Engineering):

        Process: Final refinement for analytics and ML. This layer handles null values and prepares the "flat table" used for training.


## important notes

    1. This project is a simplified version of my previous PCOS pipeline in SnowFlake. The SnowFlake project, due to a series of unfortunate circumstances, has been lost. I am reacreating it in Databricks, both to learn Databricks and to revise what i learned from the earlier project.

    2. The dataset used: https://www.kaggle.com/datasets/samikshadalvi/pcos-diagnosis-dataset is to perfect. The pipeline itself is very simple, due to not many changes needing to be made to the original data, will use more varied and "unclean" data in future projects. 