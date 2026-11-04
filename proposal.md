# Project Proposal
## Project Title
Data Quality Inspection and Schema Integration for Advertised Udemy Online Courses

## Team and Roles
Team Member 1: Project coordinator & workflow design
Team Member 2: Dataset selection & exploratory data analysis
Team Member 3: Outlier detection and categorical value standardisation
Team Member 4: Documentation and GitHub maintenance

## Introduction brief
This project uses a public Udemy online course dataset. It records course price, content duration and subscriber enrolment numbers. We will investigate typical dirty-data issues including inconsistent category labels in the level field, extreme numeric outliers in subscriber count and non-standard timestamp format. We also simulate heterogeneous schema integration by combining this dataset with a second online course dataset, which introduces unit conflicts for duration.

## Problem Statement
The level field uses inconsistent text labels with redundant words for the same category.
Subscriber numbers contain extreme numeric outliers that distort statistical analysis.
Mismatched duration units will cause format conflicts once two separate course datasets are integrated.

## Links
GitHub Repository: [https://github.com/qianqianmiao/dirty](https://github.com/qianqianmiao/dirty-data-integration-project)
MS Teams Channel: (https://teams.microsoft.com/l/chat/19%3Ae39ae848f5f34bcba98ae2654a16f4bb%40thread.v2/conversations?context=%7B%22contextType%22%3A%22chat%22%7D)
