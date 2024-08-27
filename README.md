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
1. Set up ec2 instance

Launch an EC2 instance
- EC2 > Launch Instance
- Give it a name
- Select the OS image – suggest ubuntu
- Select the instance type – this will depend on the use case, and in particular the size of the data
- Select / create a key pair – this will download a .pem file
- Allow HTTP & HTTPS traffic from the internet (check this)
- Click on Launch Instance

Update security key of EC2 instance (to allow Airflow)
- Select the instance
- Choose the security tab
- Select security groups
- Select ‘edit inbound rules’
- Add rule – custom TCP, assign port range 8080, source ‘Anywhere IPv4’, save rule (check this)

Install Python dependencies on EC2 instance
- Select instance and click on Connect
- EC2 instance connect > click connect
- Install dependencies

```
sudo apt update
sudo apt install python3-pip
sudo apt install python3.12-venv
```

Create a virtual environment in an EC2 instance

```
python3 -m venv test_pipeline_venv
source test_pipeline_venv/bin/activate
```	
Install libraries

```
sudo pip install pandas
sudo pip install s3fs
sudo pip install apache-airflow
```

2. Connect to ec2 instance remotely using vs code

Connect to EC2 via SSH
- Open VSCode
- Select instance and click on Connect
- Choose SSH client tab
- Copy the example at the bottom
- Navigate to the folder that has your .pem key in the terminal
- Paste the command and press enter
- This will bring you into the virtual machine

Create a folder and file in the VM

```
mkdir temp_folder
cd temp_folder
touch test_etl.py
```

- Can now use nano test_etl.py to open up a text editor and starting coding
- Exit and run python3 test_etl.py to run the script

Connect EC2 to VSCode
- Open VSCode
- Install Remote – SSH extension if needed
- Select remote window option in bottom left
- Select ‘connect to host’
- Then ‘configure SSH hosts’
- Select the correct .ssh folder, which will create a config file
- In the config file, add details of the host (the EC2 instance) and save
  - The hostname should be the public IPv4 address
  - User is just ubuntu or similar
  - IdentityFile is where you specify the .pem to use and its path
- Select remote window option in bottom left again
- Select ‘connect to host’
- Select the host you have just created
- Select Linux as the platform
- See the connection in the bottom left hand corner
- File > open folder > okay – to see and open the file system of your VM

Give EC2 instance access to an S3 bucket (assumes you have already created an S3 bucket - see section below)
- Select the instance
- Actions > security > modify IAM role
- Create new IAM role
- Create role > AWS service > EC2 > next
- Search for ‘ec2’ and tick the box for ‘AmazonEC2FullAccess’
- Search for ‘s3’ and tick the box for ‘AmazonS3FullAccess’
- Next > name the role > create role
- Go back to instance and select the IAM role > click on update IAM role

#### aws cli / credentials

Create an access key
- IAM > security credentials > access keys > create access key
- Copy key name and secret key into notepad / csv

Configure AWS
- In a terminal activate your virtual environment – source test_pipeline_venv/bin/activate
- Install AWS CLI
  
```
sudo apt install awscli
```

- Run aws configure

```
aws configure
```

- Enter the access key and secret key you generated
- You can ignore region and output format
- This will create a new folder called .aws which contains a config file and credentials file which holds the keys

Get AWS session token

```
aws sts get-session-token
```

### terraform
1. Set up cloud infrastructure using terraform

### lambda

### set up pipeline components
#### S3

Create an S3 bucket:
- Navigate to S3
- Create bucket
- Give it a name e.g. lginform-api
- Click on create bucket


#### PostgreSQL
1. X
#### Redshift
1. X
#### Airflow

Initialise airflow
- Within EC2 VM navigate to correct folder
- airflow standalone
- This will stand up an airflow server and create a new folder called ‘airflow’ in the current directory
- Select EC2 instance
- Copy the Public IPv4 DNS
- Paste into browser
- Add ‘:8080’ to the end
- Username and password are provided in the terminal


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

Create DAG
- Connect VS code to EC2 instance
- Open file explorer
- Create new folder called dags in the airflow folder
- Create a new file in that folder called ‘test_dag.py’ 


### github actions





