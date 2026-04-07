# Finetuning_LLM_on_AWS(Sagemaker)

Instruction finetuning of the LLM model name "TinyLlama/TinyLlama-1.1B-intermediate-step-1431k-3T" downloaded from Huggingface  with given instruction dataset on AWS sagemaker.

##  Project Overview

1.Upload the dataset to s3 bucket.

2.Download the pretrained model from hugging face through sagemaker IDE , read the dataset from s3 bucket through sagenaker IDE.

2.Format the dataset as per instruction finetuning of model and Tokenize the data.

3.Train the model(Supervised Finetuning) with tokenized data and save model in the s3 bucket.

4.Deploy the trained model saved in the s3 bucket as an API Endpoint.

5.configure the  API endpoint in AWS Lambda function and trigger the lambda function(send requests) through API Gateway.

6.Built RAG application with finetuned LLM calling through API gateway.


## Project Structure
```
 Finetuning-on-aws               
├─ finetuning_experiments       
│  └─ experiment.ipynb          
├─ inference                    
│  └─ inference.py              
├─ scripts                      
│  └─ train.py                  
├─ deployment_of_model.ipynb    
├─ estimator_launcher.ipynb     
├─ inference_app.py             
├─ lambda_function.py           
├─ pharma_instruction_data.csv  
├─ rag_app_backend.py           
├─ rag_app_ui.py                
├─ rag_app_ui_deprecated.py     
├─ README.md                    
├─ requirements.txt             
└─ requirements_inference.txt   
                          
```

## 🚀 AWS configuration

### 1. Create IAM Roles
```bash

A. Create SageMaker role

 Attachpolicies: AmazonS3FullAccess ,AmazonSageMakerFullAccess,CloudWatchFullAccess

B. Create Lambda role
 Attachpolicies: AmazonSageMakerFullAccess,AmazonDynamoDBFullAccess,AmazonS3FullAccess,CloudWatchLogsFullAccess

```

### 2.Create S3 Buckets for Dataset & Model Artifacts

```bash
A. Create first Bucket (for dataset)
B. Create Second Bucket (for model artifacts)
```
### 3.Verify and Note the paths

```bash
A. s3://llm-finetune-dataset-suman/datasets/
B. s3://llm-model-artifacts-suman/models/
```

### 4. Create SageMaker Notebook Instance

```bash
A. Keep the necessary requirements in the requirements.txt
B. Then install with the below command: Pip install -r requirements.txt

```
### 5. Create AWS Lambda Function

### 6. Create DynamoDB Table (for logs)

## 🚀 Quick Start

### 1. Environment Setup
```bash
# Clone the repository
git clone https://github.com/suman520-git/Finetuning-on-aws.git
cd Finetuning-on-aws

# Create virtual environment
conda create -p venv python==3.11 -y
conda activate venv/ 

# Install dependencies
pip install -r requirements_inference.txt
```
### 2. Configuring variables

```bash

GOOGLE_API_KEY ="xxxx"

GROQ_API_KEY ="xxxxx"

OPENAI_API_KEY="xxx"

API_URL = "xxxx"  # Replace with your actual API Gateway endpoint

API_KEY= "xxxxx"  # Replace with your actual API Gateway api key

```

### 3. Application  Usage

```bash
# For running the application through Sreamlit
step.1  streamlit run .\Finetuning-on-aws\rag_app_ui.py   

```
## Application UI

![image alt](https://github.com/suman520-git/Finetuning-on-aws/blob/main/Screenshot 2026-02-17 005239.png?raw=true)




