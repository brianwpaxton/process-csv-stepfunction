# process-csv-stepfunction
Example of processing a CSV file using a step function

## Deploy
aws cloudformation deploy \
  --template-file csv-processing.yaml \
  --stack-name csv-processing-demo \
  --capabilities CAPABILITY_IAM

Then get the bucket name:

aws cloudformation describe-stacks \
  --stack-name csv-processing-demo \
  --query "Stacks[0].Outputs"

You should see something like:

CsvBucketName
UploadPrefix
StateMachineArn
LambdaArn

## Upload a test CSV

Create:

id,name,value
1,John,100
2,Jane,200
3,Bob,300
4,Alice,400
5,Steve,500

Then upload it:

aws s3 cp test.csv s3://YOUR-BUCKET-NAME/input/test.csv
