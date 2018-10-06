# s3-create-elasticsearch-record
This Python 3.6 package for AWS Lambda creates a record in AWS Elasticsearch when sent an 'ObjectCreate' event from an s3 bucket. 
* Set up "ObjectCreated" event triggers to this Lambda function from as many s3 buckets as you like. Can handle multiple staging environments.
* Also creates a new index in Elasticsearch if you don't already have one.
* Captures object information such as title, content-type, content-length, and all custom metadata. This is customizable.
* Results can be searched by both full-text and keyword in Elasticsearch/Kibana.


## Thanks:
Credit to Amit Sharma (@amitksh44) for the [original scripts](https://aws.amazon.com/blogs/database/indexing-metadata-in-amazon-elasticsearch-service-using-aws-lambda-and-python/) in Python 2.7.  This update allows you to use Python 3.6 and the latest Elasticsearch build to keep a dynamic catalog of your Data Lake objects in AWS S3.  

See the accompanying repo to **remove records** as well.

## Requirements:
* AWS S3 bucket
* AWS Lambda 
* AWS Elasticsearch endpoint

## Configuration 
* First time packaging a Python script for Lambda?  [Read this guide.](https://aws.amazon.com/premiumsupport/knowledge-center/build-python-lambda-deployment-package/)
* Update your AWS Lambda endpoint under *user constants* in **lambda_function.py** (Note the AWS default port for Elasticsearch is 80.)
* All required modules are currently included in the AWS Lambda environment, except for Elasticsearch. 
* If you need, `pip install elasticsearch -t .` will update Elasticsearch locally (and install urllib as well.)
* Run `chmod -R 755` on all files
* Zip and upload file to your Lambda function.
