# Boto3 Basics

In order to start using boto3 you need to install the sdk

```
pip3 install boto3
```

You also need to configure AWS credentials
This will depend on how you already have them configured.

The easiest way is to create the credentials file `~/.aws/credentials` and add your access key and secret access key.
For example:

```
[default]
aws_access_key_id = YOUR_ACCESS_KEY
aws_secret_access_key = YOUR_SECRET_KEY
```

After this has been configured, we can go ahead and start coding our python scripts.

##

As a first example we will describe all EC2 instances

```python
import boto3

ec2 = boto3.client('ec2')
response = ec2.describe_instances()
print(response)
```

You will get an output with a lot of text. This is the description of the EC2 instances.
To better understand the output, we will refer to the documentation provided by AWS.

[ec2 documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/ec2.html#instance)
