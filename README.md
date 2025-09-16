# Serverless Web Application on AWS

- This project demonstrates how to deploy a serverless web application using AWS services including S3, API Gateway, Lambda, DynamoDB, and CloudFront. 
- The application hosts static content, provides secure API endpoints, interacts with a DynamoDB table, and delivers content globally through CloudFront.

# Architecture Overview

- Amazon S3 → Hosts static web assets (HTML, CSS, JavaScript).
- API Gateway → Provides REST API endpoints (GET, POST) for the web app.
- AWS Lambda (Python) → Backend logic to handle API requests.
- Amazon DynamoDB → NoSQL database for storing and retrieving application data.
- Amazon CloudFront → CDN to serve S3 content securely via HTTPS with improved performance.

# Features

- Static website hosting on Amazon S3
- API integration via AWS API Gateway
- Serverless backend using AWS Lambda (Python)
- Database storage with Amazon DynamoDB (CRUD operations)
- Secure delivery with CloudFront + HTTPS

# Prerequisites

## AWS Account

- IAM user with permissions for S3, API Gateway, Lambda, DynamoDB, and CloudFront
- AWS CLI configured locally
- Basic knowledge of Python and web development

#  Deployment Steps

### 1 Setup S3 for Static Hosting

- Create an S3 bucket (enable public access for testing or configure with CloudFront for production).
-  Upload your static files (index.html, script.js, styles.css).
- Enable Static Website Hosting.

### 2 Create DynamoDB Table

- Table Name: studentData
- Primary Key: studentId (String)

### 3 Build Lambda Functions (Python)

- GET Lambda → Fetch records from DynamoDB
- POST Lambda → Insert records into DynamoDB
- Attach an IAM Role with dynamodb:Scan, dynamodb:PutItem, dynamodb:GetItem, dynamodb:UpdateItem, and dynamodb:DeleteItem.

### 4 Configure API Gateway

- Create REST API
- Add GET → linked to getStudent Lambda
- Add POST → linked to insertStudent Lambda
- Enable CORS for frontend calls
- Deploy API and note the endpoint URL

### 5 Secure with CloudFront

- Create a CloudFront distribution
- Origin = your S3 bucket (static website hosting endpoint)
- Configure Default Behavior to redirect HTTP → HTTPS
- Attach SSL/TLS certificate (via AWS ACM if using custom domain)

# Testing

- Open your CloudFront URL (or S3 website endpoint).
- Submit data via the frontend form (POST request to API Gateway).
- Retrieve records (GET request).

# Screenshot

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/92824959-f52a-4488-b512-8daddd2bd9fd" />

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/ae1352c0-8ec5-4782-81ad-fd0560a0a466" />

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/0383f7ff-d1fc-4c88-b107-727786d0f901" />

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/12288994-1418-4ccf-aa56-397c62c17c10" />


# Future Improvements

- Add authentication (Amazon Cognito)

- Implement request validation in API Gateway

- Add CloudWatch dashboards for monitoring
