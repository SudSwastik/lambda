# AWS Lambda Setup 


> Login To Your IAM Account

```
$ aws configure
```
> Create a Role 
```
$ aws iam create-role --role-name lambda-hello-world-role --assume-role-policy-document file://trust-policy.json

```
> Add Lambda Basic Permission
```
$ aws iam attach-role-policy --role-name lambda-hello-world-role --policy-arn arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole
```
> Create lambda function and make a zip of it.

```
$ zip hello-world.zip hello-world.py
```

> Create a Lambda Function

```
$ aws lambda create-function --function-name hello-world --zip-file fileb://hello-world.zip \
  --handler hello-world.hello --runtime python3.9 --role arn:aws:iam::684897107346:role/lambda-hello-world-role 
```

> Invoke The Lambda Function
```
aws lambda invoke --function-name hello-world  response.json --region=ap-south-1
```

> See The Response
```
$ cat response.json
```