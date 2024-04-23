# data-engineering-guidance
This README describes our corporate standards and guidelines on how to build data pipelines in AWS. It uses an example of pulling data from a public API, storing this in AWS S3, moving it into PostgreSQL in RDS and modelling it with dbt, all scheduled using Airflow and powered by EC2 / lambda.

It is meant as a way of building consistency in how we do data engineering in RBK & LBS, and improving the efficiency of our data operations. Reading and digesting these guidelines is also an important step in onboarding for all new data engineers.

Please note: These are guidlines and not set in stone rules and we recognise that different use cases will require different solutions. It is permissible to deviate slightly from these guidelines, in terms of standards, style and tools, so long as you still follow basic practices of documenting your code and submitting PRs.

## set up access
1. Get a unified.gov account to access AWS
2. Get access to the data-AI dev account in AWS

## security
1. what do they need to know?

## set up environment
1. Download various software locally - python, git, docker desktop, an IDE (we suggest vs code), terraform, AWS CLI etc
   
## project structure
1. Create a github repository for each new data pipeline / project
2. This repo should have the following structure: [insert]
3. It should at a minimum include a gitignore, readme etc

## documentation
1. Standards around documentation

## development lifecycle, ci/cd, iac, containerisation
1. All pipelines should go through the steps of dev > test > prod. Provide example of basic data pipeline moving data from dev > test > prod databases in Postgres. Does prod database sit in a separate account?
2. Set up resources for each environment using terraform
3. Use docker to replicate the same environment across each step
4. CI / CD is handled via GitHub actions yaml file

## code standards and guidelines
1. modular code
2. clean code principles
3. functional programming

## pull request and code reviews

## guidelines for building data pipelines on AWS

### principles & patterns
1. requirements
2. architectural patterns
3. ETL vs ELT
4. idemoptency
5. data privacy and PII data
6. understanding cloud costs

### compute
#### lambda
1. when to use lambda
#### ec2
1. when to use ec2
2. set up ec2 instance
3. connect to ec2 instance remotely using vs code

### extraction & ingestion
#### from a database
#### from an api

### storage
#### s3 & boto
#### data lake principles & file formats

### transformation & data modelling
#### python (pandas / pyspark)
#### dbt

### serving
#### rds postgres
#### powerbi
#### google drive / sheets

### orchestration & scheduling
#### cron / eventrbridge / task scheduler
#### airflow
#### github actions

### testing & validation
#### unit testing
#### integration testing

### data governance
#### data quality testing
#### metadata and data catalog
#### lineage
#### logging and monitoring

