<img width="455" alt="image" src="https://github.com/user-attachments/assets/a0151c66-e457-402b-bb60-563161b32c7e" /># AWS_Telco_Customer_Churn_S3-Glue-Redshift-Athena-Airflow

![image](https://github.com/user-attachments/assets/1d06724a-359b-4dd9-8f94-cf4a503e9e77)

Telco Customer Churn Data Pipeline 
AWS Cloud Data Engineering Project |Data Pipeline using Apache Airflow, Glue, S3, Redshift, PowerBI

I want to share my latest Data Engineering project where I put my skills to the test by working with an AWS cloud using Databricks and load into BI tools.

🔬𝗣𝗿𝗼𝗷𝗲𝗰𝘁 𝗢𝘃𝗲𝗿𝘃𝗶𝗲𝘄: End-to-end data engineering on AWS. Where I ingested data from S3 to Redshift using Glue, transformed it with Glue, loaded it into Athena and Redshift, and reported with BI tools. Also used IAM and VPC for data governance. More information can be found in the GitHub repository.

💾 𝗗𝗮𝘁𝗮 𝗦𝗼𝘂𝗿𝗰𝗲: https://www.kaggle.com/datasets/blastchar/telco-customer-churn/code

🎯 𝗣𝗿𝗼𝗷𝗲𝗰𝘁 𝗚𝗼𝗮𝗹𝘀:

• Store data in S3.
• Run Airflow on EC2
• Transform and clean with Glue
• Load data into Redshift.
• Create interactive reports with BI tools
• Implement IAM and VPC for governance.

 🔧The tools that are covered in this project are:

1. Amazon S3
2. Amazon EC2
3. Amazon IAM
4. Amazon VPC
5. Amazon Glue
6. Amazon Redshift
7. Amazon Athena


## 1. Run EC2 to Install Airflow

### 1.1 Setting up EC2, Airlfow and VPC

On EC2 page launch instance
  
<img width="947" alt="image" src="https://github.com/user-attachments/assets/66a82317-ad2b-48bf-a322-b0b687c6b6ce" />
<img width="444" alt="image" src="https://github.com/user-attachments/assets/ba20f5a9-9c1c-4f04-8fa9-59e9bded9a2e" />
<img width="437" alt="image" src="https://github.com/user-attachments/assets/6aae095c-9d9e-4083-ad99-b49af6cdeb22" />
<img width="455" alt="image" src="https://github.com/user-attachments/assets/600185c8-5722-4cef-b0a8-2ea688c0ef86" />

### 1.2 Connect to Instances
<img width="404" alt="image" src="https://github.com/user-attachments/assets/cb04d595-8848-42b6-9675-27a867790068" />

Once connect:
- sudo apt update
- sudo app install python3-pip
- sudo apt install python3.10-venv
- press esc
- python3 -m venv customer_churn_venv
- source customer_churn_venv/bin/activate
- sudo pip install apache-airflow
- pip install apache-airflow-providers-amazon
- airflow standalone
- copy the password
- go back to the instances > click security goup > add inbound rule > custom TCP, 8080, anywhere

Open airflow
- copy the ip address from instances and add :8080 etc 18.235.101.34:8080
- username: admin, password from the terminal just now

### 1.3 Modify code from local VSCode

Open Visual Studio Code

<img width="505" alt="image" src="https://github.com/user-attachments/assets/51613fff-82b3-4ef0-8f4d-c52467b2a3e5" />

- connect SSH to the instance
- open the folder
- open airlfow.cfg > set the load_examples = FALSE
- open airflow > +dag folder > +customer_churn_dag.py
- restart airflow in instance
- control + C
- airlfow standalone

## 2. Create bucket to store file (source)

<img width="661" alt="image" src="https://github.com/user-attachments/assets/10b444a2-fcea-4c64-b9b7-479ed42c4b91" />
<img width="661" alt="image" src="https://github.com/user-attachments/assets/4b82279b-524f-4d7c-9ba4-18b732e27b8c" />

Upload the file inside the bucket

# 3. Setup Glue Crawler and ETL from S3

Create crawler
<img width="952" alt="image" src="https://github.com/user-attachments/assets/d356dac1-ef62-4a8f-8600-b70e4262db39" />
<img width="952" alt="image" src="https://github.com/user-attachments/assets/5d393668-378d-49ee-a0a5-82720632233c" />
<img width="955" alt="image" src="https://github.com/user-attachments/assets/de89c2ae-bfa8-4869-9f6e-5d7da273d3c9" />
<img width="956" alt="image" src="https://github.com/user-attachments/assets/2f4b0026-d7bb-4bcd-b079-cd08badfd257" />

After everything is setup, run the crawler

# 4. Setup AWS Athena for query

- create bucket for temporary data storage for query
<img width="668" alt="image" src="https://github.com/user-attachments/assets/4da3bb83-9469-452d-9fc1-d96ec3e1eaec" />

query the data
![image](https://github.com/user-attachments/assets/4632ea88-d5cc-4acc-a10d-64f6672ade7e)


# 5. Setup Redshift Cluster and create table


# 6. Create Glue crawler, connector to Redshift and run ETL job


# 7. Orchestrate the task using Airflow
