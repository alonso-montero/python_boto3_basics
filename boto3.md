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

In order to analyze the structure of the output, we will see the output of a single EC2 instance
To do this, we will modify the previous code a little.

```python
import boto3

ec2 = boto3.client('ec2')
response = ec2.describe_instances( InstanceIds=[
        'i-0705660b11abfdeb0',
    ])
print(response)
```

According to the documentation above, you will see that this response is a dictionary. But this dictionary has other lists and dictionaries inside of it.

Now, commonly you dont need all of the information from an instance, or you want a piece of information from multiple instances. To do this we have to manipulate the response.
In the following example, we will retrieve only the instance ID from all of the instances on the account.

```python
import boto3

ec2 = boto3.client('ec2')
response = ec2.describe_instances()
for r in response['Reservations']:
    for i in r['Instances']:
        print(i['InstanceId'])
```

You may also want to retrieve only instances with specific characteristics. To do this, Boto3 provides filters so you don't have to manually search for them.
In this example, we will only get the name of instances wich have a stopped state.

```python
import boto3

ec2 = boto3.client('ec2')
response = ec2.describe_instances(
   Filters=[
        {
            'Name': 'instance-state-name',
            'Values': [
                'stopped',
            ]
        },
    ], 
)
for r in response['Reservations']:
    for i in r['Instances']:
        print(i['InstanceId'])
```
A common need is to retrieve the instance name.

There is no specific method provided by boto3 to do this. We have to do it by hand and iterate through the EC2's tags and look for the name.

In the following example, we will print the instance id and the name for all running instances.

```python
import boto3

ec2 = boto3.client('ec2')
response = ec2.describe_instances()
for r in response['Reservations']:
    for i in r['Instances']:
        if 'Tags' in i:
            for k in i['Tags']:
                if k["Key"] == "Name":
                    print(i["InstanceId"],",",k["Value"])
        else:
            print(i["InstanceId"],",",'-')
```

Take notice that we need to verify that the 'Tags' keys exists on the reservation. If not the script will error out if there is an instance with no name

Error cases like this need to be taken into account when dealing with this sort of code. Before performing important operation, please run tests to verify everything runs as it should.


