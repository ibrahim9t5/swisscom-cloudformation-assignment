# swisscom-cloudformation-assignment

ASSIGNMENT:

 In this assignment we kindly ask you to add additional security features to an existing cloudformation stack.
 The current, basic cloudformation template doesn't contain any additional security featuress/configurations. Please have a look at the cfn-nag report. There are a couple of findings which have to be fixed. Please extend the cloudformation template accordingly.


Pre-Requisite

1) Python
2) Docker
3) Docker Compose
4) AWS CLI

##############################

To Run the Stack

####Step 1) Clone the repository using below URL

https://github.com/ibrahim9t5/swisscom-cloudformation-assignment.git

####Step 2) go to the repository using ssh terminal

####Step 3) In repo terminal run local stack using docker:

docker-compose up

####Step 4) Make sure AWS is authenticated in local stack using:

export AWS_ACCESS_KEY_ID=foobar
export AWS_SECRET_ACCESS_KEY=foobar
export AWS_REGION=eu-central-1

####Step 5) Run below aws command to create stack:  #### make sure you are in the repo #####

aws --endpoint-url http://localhost:4566 cloudformation create-stack --stack-name swisscom0001 --template-body file://stack.template --parameters ParameterKey=BucketName,ParameterValue=swisscom0001

####Step 6) Run below command to confirm stack ran and created resources successfully

aws --endpoint-url http://localhost:4566 s3api list-buckets

####Step 7) Run below command to check logs if there is any security report of cfn

docker logs cfn-nag


##########################

NOTE: to restart docker in case of any error during docker up run: docker-compose restart 

NOTE: to recreate report run: docker-compose restart cfn-nag

