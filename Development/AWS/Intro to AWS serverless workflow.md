# Introduction to AWS serverless

__READ THE FOLLOWING DOCUMENTATION:__ 
	[AWS CloudFront](https://aws.amazon.com/es/cloudfront/)
	[AWS S3](https://aws.amazon.com/es/s3/)
	[AWS Lambda](https://aws.amazon.com/es/lambda/)
	[AWS API Gateway](https://aws.amazon.com/es/api-gateway/)


[[Amazon cloudfront]]

[Documented pattern](https://docs.aws.amazon.com/es_es/solutions/latest/constructs/aws-cloudfront-apigateway-lambda.html)

### Amazon CloudFront

-   Configure Access logging for CloudFront Distribution
-   Enable automatic injection of best practice HTTP security headers in all responses from CloudFront Distribution
    

### Amazon API Gateway

-   Deploy a regional API endpoint
-   Enable CloudWatch logging for API Gateway
-   Configure least privilege access IAM role for API Gateway
-   Set the default authorizationType for all API methods to NONE
-   Enable X-Ray Tracing
    

### AWS Lambda Function

-   Configure limited privilege access IAM role for Lambda function
-   Enable reusing connections with Keep-Alive for NodeJs Lambda function
-   Enable X-Ray Tracing
-   Set Environment Variables
    -   AWS_NODEJS_CONNECTION_REUSE_ENABLED (for Node 10.x and higher functions)