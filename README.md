# data-engineering-guidance
This README describes our corporate standards and guidelines on how to build data pipelines in AWS. It uses an example of pulling data from a public API, storing this in AWS S3, moving it into PostgreSQL in RDS and modelling it with dbt, all scheduled using Airflow and powered by EC2 / lambda.

It is meant as a way of building consistency in how we do data engineering in RBK & LBS, and improving the efficiency of our data operations. Reading and digesting these guidelines is also an important step in onboarding for all new data engineers.

Please note: These are guidlines and not set in stone rules and we recognise that different use cases will require different solutions. It is permissible to deviate from aspects of these guidelines, for example tooling, so long as you still follow best practices such as version control, creating documentation, writing tests, submitting PRs etc.

## get access
1. Get a unified.gov account to access AWS
2. Get access to the data-AI dev account in AWS

## security
1. what do they need to know?

## overview of data engineering lifecycle
1. Project structure
2. Setting up basic infrastructure for data pipelines in AWS
3. Infrastructure automation (IaC) - set up resources using terraform
4. Setting up pipeline components e.g. S3, Redshift, PostgreSQL
5. Environment automation - using docker to replicate the same environment across each step of dev > test > prod
6. Writing code
7. Testing code
8. Version control, pull requests & code reviews
9. CI / CD - handled via GitHub actions yaml file
10. Documentation

### project structure
1. Create a github repository for each new data pipeline / project
2. This repo should have the following structure: [insert]
3. It should at a minimum include a gitignore, readme etc

### set up infrastructure
#### EC2
1. set up ec2 instance
2. connect to ec2 instance remotely using vs code

### terraform
1. Set up cloud infrastructure using terraform

### lambda

### set up pipeline components
#### S3
1. X
#### PostgreSQL
1. X
#### Redshift
1. X
#### Airflow
1. X

### docker
1. Containerize your pipeline using docker

### code standards and guidelines
1. modular code
2. clean code principles
3. functional programming

### testing code
#### unit testing
#### integration testing

### version control, pull request and code reviews

### deployment & ci/cd

### documentation
1. Standards around documentation

# data pipeline patterns and standards
## principles & patterns
1. requirements
2. architectural patterns
3. server vs serverless
4. ETL vs ELT
5. idempotency
6. data privacy and PII data
7. cost considerations

## extraction & ingestion
### from a database
### from an api

## storage
### s3 & boto
### data lake principles & file formats
### metadata and data catalog

## transformation & data modelling
### python (pandas / pyspark)
### dbt

## serving
### rds
### powerbi
### google drive / sheets

## monitoring, logging & testing
### data quality testing
### logging and monitoring
### lineage

## orchestration & scheduling
### cron / eventrbridge / task scheduler
### airflow
### github actions





