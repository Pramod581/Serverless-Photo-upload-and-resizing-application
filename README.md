# Serverless-Photo-upload-and-resizing-application
## Objective: 
To design and deploy a fully serverless web application where users can upload photos through a web interface, and the images are stored, processed, and served securely using AWS services.

## Features
•	Upload photos directly to an Amazon S3 bucket
•	Automatically trigger an AWS Lambda function when a photo is uploaded
•	Lambda can:
o	Process or resize images (e.g., create thumbnails)
o	Store metadata
o	Move or copy images to another bucket
o	Log upload events
•	100% serverless and scalable.
Architecture Overview
+-----------------+                 +----------------------+                +---------------------+
|   Frontend    |      --->     |   S3 Bucket         |    --->      | AWS Lambda    |
|  (Web/App)  |  Upload  | (photo-bucket) | Trigger  | (processImage) |
+------------------+                 +---------------------+               +----------------------+
        |                                                           |
        +--------------------------------------------+
                 View / Download
Step 1: Create two S3 Buckets
1.	Sign in to the AWS Management Console.
2.	Navigate to Amazon S3 → Buckets → Create bucket.
3.	Choose a unique name for both.
4.	Leave other settings default and click Create bucket.

![alt text](image.png)
Step 2: Create a Lambda Function
1.	Go to AWS Lambda → Create function.
2.	Choose Author from scratch.
3.	Enter:
o	Function name: processPhotoUpload
o	Runtime: Python 3.9 (or Node.js, etc.)
4.	Under Permissions, choose or create an execution role with:
o	AmazonS3FullAccess
o	SNS FullAccess
o	Lambda basic execusion rule
5.	Click Create function.
Created a role by using IAM as mentioned below
![alt text](image-1.png)
![alt text](image-2.png)
![alt text](image-3.png)
Created a function and added the source bucket to the created function
![alt text](image-4.png)
Created an SNS topic for the notification 
![alt text](image-5.png)
![alt text](image-6.png)
Subscribed with email address
![alt text](image-7.png)
Step 3: Add Lambda Code
Uploaded the python code by uploading zip file from local system(CreateThumbnail)
![alt text](image-8.png)
Added environment variables which allow for dynamic configuration of your Lambda function without altering the code.
![alt text](image-9.png)
Step 4: Test the Setup
Here we have to execute the created code in Lambda function, after execution need to check destination bucket which we have added to lambda fuction. That image is stored 
Conclusion
The Serverless Photo Upload Application effectively demonstrates how AWS services such as Lambda, S3, and S3 Events can be integrated to create a simple yet powerful serverless workflow. By using S3 for image storage and triggering AWS Lambda functions through S3 events, the system automates backend processing without the need for managing servers. This approach ensures scalability, cost efficiency, and ease of maintenance. Overall, the project showcases the potential of AWS serverless architecture to handle real-time file uploads and processing in a reliable and efficient manner.
