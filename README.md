# Serverless-Architecture

Role Creation
To enable necessary AWS services and their interactions, the following roles and permissions were assigned:
AWSLambdaBasicExecutionRole – Grants basic execution permissions for AWS Lambda.
AmazonDynamoDBFullAccess – Provides full access to DynamoDB for data storage and retrieval.
AmazonS3FullAccess – Allows full access to Amazon S3 for hosting static files.
AmazonAPIGatewayAdministrator – Enables full administrative capabilities for API Gateway.

DynamoDB Configuration
Created a new DynamoDB table.
Defined a Table Name and set a Partition Key (Primary Key) for efficient data indexing and retrieval.

Lambda Function Deployment
Created a new Lambda function.
Selected the appropriate programming language (Python).
Assigned the IAM role created above for necessary permissions.
Added Python code to the Lambda function for processing API requests.
Conducted a test run by creating a test event and verifying that data was successfully stored in DynamoDB.

API Gateway Configuration
Created a REST API in API Gateway.
Defined necessary resources.
Integrated the API Gateway with the Lambda function.
Created HTTP methods (POST, GET, PUT, DELETE) and enabled Lambda proxy integration for dynamic request handling.
Deployed the API, selecting a new stage, which provided an Invoke URL.

Testing the API Gateway
Browser Test: Accessed the API using the Invoke URL and the /Students resource.
https://lxdgloit6a.execute-api.us-east-1.amazonaws.com/Test/Students
Postman Test: Sent POST requests with JSON data to insert records into DynamoDB.
Verification: Checked DynamoDB to ensure records were successfully stored and retrieved.

S3 Bucket Configuration

Created a new S3 bucket with a unique name.
Selected the AWS region (us-east-1).
Modified bucket permissions to allow public access for website hosting.
Uploaded static files (HTML, CSS, JavaScript) to the bucket.
Enabled Static Website Hosting:
Navigated to Properties → Static Website Hosting.
Selected Enable and set index.html as the default file.
Copied and stored the S3 Website Endpoint for future use.

CloudFront Integration
Created a CloudFront distribution for optimizing API Gateway responses and static file delivery.
Added API Gateway as an Origin:
Defined API Gateway URL as the CloudFront origin.
Configured HTTPS-only policy for security.
Defined Behavior Rules:
Set Path Pattern to /students*.
Mapped API Gateway as the origin for the pattern.
Allowed GET, POST, OPTIONS methods.

Enabled CORS with:
Origin: * (or specific CloudFront domain)
Headers: Content-Type, Authorization
Deployed the CloudFront distribution and updated API requests to use the CloudFront URL.

Final Testing & Validation
Accessed the CloudFront URL to verify static website hosting.
Sent API requests through CloudFront to ensure optimized API responses.
Confirmed data flow from API Gateway to Lambda and then to DynamoDB.
Ensured all functionalities (static file hosting, API interactions, and database operations) worked seamlessly.
