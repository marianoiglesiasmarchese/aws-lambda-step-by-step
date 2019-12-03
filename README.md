# aws-lambda-step-by-step
guide to work with aws lambdas and it best practices


# create a lambda - sam init 

```bash
sam init --runtime python3.7 --dependency-manager pip --app-template hello-world --name sample_lambda
```

https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-cli-command-reference-sam-init.html

# create an input event for your lambda - sam local generate event

```bash
# Generate the event that S3 sends to your Lambda function when a new object is uploaded
sam local generate-event s3 [put/delete]

# Generate the event that SQS sends to your Lambda function when something is sended to the queue
sam local generate-event sqs [put/delete]
```
https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-cli-command-reference-sam-local-generate-event.html

# create a file with environment variables - local.env.json

```bash
{
  "MyFunction1": {
    "TABLE_NAME": "localtable",
    "BUCKET_NAME": "testBucket"
  },
  "MyFunction2": {
    "TABLE_NAME": "localtable",
    "STAGE": "dev"
  },
}
```
https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-using-invoke.html#serverless-sam-cli-using-invoke-environment-file

# build the lambda - sam build

```bash
# To build on your workstation, run this command in folder containing SAM template. Built artifacts will be written to .aws-sam/build folder
sam build

# To build inside a AWS Lambda like Docker container
sam build --use-container
```
https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-cli-command-reference-sam-build.html

# run the lambda - sam local invoke

```bash
sam local invoke --event events/event.json --env-vars local.env.json 
```
https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-cli-command-reference-sam-local-invoke.html

# run the lambda with a gateway - sam local start-api

```bash
sam local start-api --env-vars local.env.json
```
https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-cli-command-reference-sam-local-start-api.html
