# Install and Configure AWS CLI Tools

> NOTE : I am doing this exercise as ROOT. If you are using as normal user try to use this with sudo privillages

* Step 1 : Install Python-PIP
```
- CentOS :

 # apt-get install python-pip

- UBUNTU :

 # yum install -y python-pip

```

* Step 2 : Install awscli using PIP
```
pip install awscli
```

* Step 3 : Verify
```
# aws --version
aws-cli/1.11.0 Python/2.7.6 Linux/4.2.0-c9 botocore/1.4.58
```

* Step 4 : Create AWS Access Keys
 - Go to AWS console
 - Services -> IAM -> Users
 - Select your user
 - Select "Security Credentials"
 - Click on "Create Access Key"
 - Download the Credentials

* Step 5 : Configure your Access keys to use awscli
```
# aws configure
AWS Access Key ID [****************KEKA]: < Paste your Access Key ID >
AWS Secret Access Key [****************/Tu5]: < Paste your Secret Access Key >
Default region name [us-east-2]: < Paste your zone name >
Default output format [json]: 
```

* Step 6 : Verify
```
# aws ec2 describe-regions --output text
REGIONS ec2.ap-south-1.amazonaws.com    ap-south-1
REGIONS ec2.eu-west-1.amazonaws.com     eu-west-1
REGIONS ec2.ap-southeast-1.amazonaws.com        ap-southeast-1
REGIONS ec2.ap-southeast-2.amazonaws.com        ap-southeast-2
REGIONS ec2.eu-central-1.amazonaws.com  eu-central-1
REGIONS ec2.ap-northeast-2.amazonaws.com        ap-northeast-2
REGIONS ec2.ap-northeast-1.amazonaws.com        ap-northeast-1
REGIONS ec2.us-east-1.amazonaws.com     us-east-1
REGIONS ec2.sa-east-1.amazonaws.com     sa-east-1
REGIONS ec2.us-west-1.amazonaws.com     us-west-1
REGIONS ec2.us-west-2.amazonaws.com     us-west-2
```
