
# AWS Rekonigition

## Step 1.
Login to AWS. Get keys from CSV file.

## Step 2.
Create a folder for project and move into it.

```bash
mkdir aws-rekog
cd aws-rekog
```
Clone repository into the folder.
```bash
git clone 
```
Once inside, run:

```bash
python -m venv venv
```
Virtual environment is created.

## Step 3.
Activate the virtual environment. 
```bash
source venv/bin/activate
```
Now, install dependencies.
```bash
pip install requirements.txt
```

## Step 4.
Run:
```bash
aws configure
```
Enter credentials.

Create collection on AWS-Rekonigition:
```bash
aws rekognition create-collection --collection-id persons --region us-east-1
```
Create S3 Bucket:
```bash
aws s3 mb s3://persons1238 --region us-east-1
```

Create a table on DynamoDB:
```bash
aws dynamodb create-table --table-name facerecognition \
--attribute-definitions AttributeName=RekognitionId,AttributeType=S \
--key-schema AttributeName=RekognitionId,KeyType=HASH \
--provisioned-throughput ReadCapacityUnits=1,WriteCapacityUnits=1 \
--region us-east-1
```

## Step 5. 
Run the `lambda_function.py` on AWS Lambda.
Deploy it.

## Step 6.
Run the following command:
```bash
python ./putimages.py
```
This puts the sample images on S3 Bucket.

## Step 7. 
Move into test folder for testing:
```bash
cd test
python ./testing.py
```
