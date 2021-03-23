# Scenario:

Create following cloudformation templates to deploy following resources 


Template 1 - S3 Source Code Bucket

`Task:` Create a cloudformation template that creates a S3 Bucket that we can use to upload the packaged python lambda source code to.

`Definition of success:` Output the name of the s3 bucket in cloudformation.

---


#### Upload GetItemDynamoDbLambda.zip to created S3 bucket


Template 2 - Lambda and DynamoDb:

`Task:` create a cloudformation template to deploy lambda from S3 bucket and DynamoDb table resouce and allow the lambda to access the DynamoDb.

`Lambda Requirements:`
- Python handler: `get_item.lambda_handler`
- Python 3.7, timeout 10 seconds
- Environment variables: TABLE_NAME, TABLE_REGION, LOG_LEVEL.

After deployed stack populate the DynamoDb database with the following data:
```
{
  "City": "London",
  "Country": "United Kingdom",
  "FirstName": "John",
  "LastName": "Doe",
  "PhoneNumber": "+441234567890"
}
```
and run the lambda with the following test event:
```
{
  "Details": {
    "ContactData": {
      "CustomerEndpoint": {
        "Address": "+441234567890"
      }
    }
  }
}
```
`Definition of success:`
- Cloudformation outputs all resources created
- Lambda will return the data retrieved from the DynamoDb Table.