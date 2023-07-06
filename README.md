<h1 style="text-align: center;">AWS</h1>

### Contents
* AWS Intro
* EC2
* App and Database Deployment
* Use User Data
* Create Image
* Set-up Monitoring
* S3
* Differences AWS/Azure

### AWS Intro

Amazon Web Services (AWS) is a cloud computing platform that provides a wide range of services and tools for building and managing applications and infrastructure in the cloud.
AWS offers various services such as computing power, storage, databases, networking, and more, enabling businesses to scale and deploy applications with ease.
AWS provides a flexible and cost-effective solution, allowing users to pay only for the resources they use.

### EC2

Amazon Elastic Compute Cloud (EC2) is Amazon's cloud-computing platform, Amazon Web Services, that allows users to rent virtual computers on which to run their own computer applications. 

#### Launching an EC2 Instance
1. Change Region to Ireland
2. In EC2 Dashboard click Launch Instance
3. Set name, Image as Ubuntu 18.04 (1e9 can be used to filter in Community Images), Use tech241 key rather than individual key pairs, Set up same security as Azure (These new settings can be saved and used again)

![](https://i.imgur.com/D4O1n0I.png)

#### How to SSH into an EC2 Instance
We will once again SSH into our virtual machine. Differences include that the username is ubuntu and instead of public IP will use the public DNS provided 

![](https://i.imgur.com/ZJkXIxE.png)

#### How to Terminate an EC2 Instance
To delete the virtual machine, you may terminate the instance by selecting the option in the state drop down menu, this can be one while it is still running. ![](https://i.imgur.com/G84SKdc.png)_

### App and Database Deployment
Once SSH'd into our VMs, again we will create our scripts, put in their contents, give them execute permissions and run them. Note: Blocker before was to use DNS again over IP in app enviromental variable.

![](https://i.imgur.com/lbRSHdA.png)

### Use User Data
In the case to automatically deploy database rather than use the script, when creating the VM we can navigate to Advanced settings, use user data at the bottom and put the contents of our script. This will cause it to run as the root user on deployment.

![](https://i.imgur.com/HBFsusY.png)

### Create Image
An Amazon Machine Image (AMI) is a template that contains a software configuration (for example, an operating system, an application server, and applications). From an AMI, you launch an instance, which is a copy of the AMI running as a virtual server in the cloud.

AMIs cost less to run then a virtual machine.
![](https://i.imgur.com/rhLnNVY.png)

### Set-up monitoring

1. Log in to the AWS Management Console.
2. Navigate to the CloudWatch service.
3. In the left-hand menu, click on "Alarms" and then click on "Create alarm."
4. On the "Create Alarm" page, select the EC2 instance you want to monitor from the drop-down list.
5. Under "Create Metric Filter and Alarm," click on "Select metric."
6. In the "Browse" tab, select "Per-Instance Metrics" and then choose the desired instance from the list.
7. Scroll down and expand the "CPUUtilization" metric.
8. Set the conditions for the alarm. For example, you can set the threshold to be triggered when the CPU utilization exceeds a certain percentage for a specific period of time.
9. Configure the actions for the alarm. Click on "Create new topic" to create a new SNS (Simple Notification Service) topic, which will send email notifications.
10. Enter the necessary details for the SNS topic, including the email addresses to which you want to send the notifications.
11. Configure the remaining alarm settings as per your requirements.
12. Click on "Create alarm" to save the alarm configuration.

### S3 

Amazon S3 or Amazon Simple Storage Service is a service offered by Amazon Web Services that provides object storage through a web service interface. We will use CLI instead to help with IaC . In S3 files are stored in buckets which are similar to Azures blobs.
#### Configure AWS
```
aws config

access key:

secret key:

region name: eu-west-1

default output format: json
```
#### Install packages
```
pip install awscli #Access AWS
pip install boto3 #Establish connection to S3
```
#### Create bucket
```
# Import boto3
import boto3

# Set up S3 connection
s3 = boto3.client("s3")

# Create a bucket in the eu-west-1 region
bucket_name = s3.create_bucket(Bucket= "tech241-henry-python-bucket", CreateBucketConfiguration={"LocationConstraint":"eu-west-1"})

# Print bucket name to confirm working script
print(bucket_name)
```
#### Upload to bucket
```
# Import boto3
import boto3

# Set up S3 connection
s3 = boto3.client("s3")

# Upload file to S3
upload_file = s3.upload_file("testfile.txt", "tech241-henry-python-bucket" , "testfile.txt")

# Print successfully uploaded to confirm working script
print("Successfully Uploaded File")
```
#### Download from bucket
```
# s3.download_file(bucket_name, object_name, file_path)
# Download File
# Import boto3
import boto3

# Set up S3 connection
s3 = boto3.client("s3")

# Download file from S3
s3.download_file("tech241-henry-python-bucket", "testfile.txt", "testdownload.txt")

# Print successfully uploaded to confirm working script
print("Successfully Downloaded File")
```
#### Delete bucket
```
[Yesterday 13:52] Luke Fairbrass

aws s3 rm s3://tech241-luke-bucket/testfile.txt
```


### Differences AWS/Azure
* Azure uses resource groups, AWS not necessary.
* Azure has static public IP, AWS has dynamic public Ip.
* Different terminology (launch instance vs create vm)

