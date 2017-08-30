# Writing a CloudFormation template

- A CloudFormation template is a JSON-formatted text file that describes your AWS infrastructure.
- Template includes several major sections:
	- AWSTemplateFormatVersion
	- Description
	- Metadata
	- Parameters
	- Mapping
	- Conditions
	- Outputs
	- Resources (THE ONLY SECTION THAT IS REQUIRED)
	
- Let us take a look at a template which only contains a Resources section

```
{
  "Resources":{
    "Name-of-your-bucket":{
      "Type":"resource type"
	}
  }
}
```

- In the above example we need to replace 2 things
	- "Name-of-your-bucket" to "MyFirstBucket01"
	- "resource type" to "AWS::S3::Bucket"
- Now after the modifications the template will look like below

```
{
  "Resources":{
    "MyFirstBucket01":{
      "Type":"AWS::S3::Bucket"
	}
  }
}
```
