# DOWNLOAD AND MODIFY THE CLOUDFORMATION TEMPLATE:
--------------------------------------------------

Download the "Drupal_Multi_AZ.template" from "https://github.com/LinuxLibrary/cl-pub/blob/master/MOD01/templates/Drupal_Multi_AZ.template".

# wget https://github.com/LinuxLibrary/cl-pub/blob/master/MOD01/templates/Drupal_Multi_AZ.template

Now make a copy of this template to use for this exercise.

# cp -prv Drupal_Multi_AZ.template My_Cust_Multi_AZ.template

Let us make some changes to this new template.

Step 1:
	Replace the AvailabilityZone(AZ)s with your own.
	%s/{ "Fn::GetAZs" : "" }/[ "us-west-2a", "us-west-2b" ]/g

Step 2:
	Change the Min and Max number of instances under the "WebServerGroup"
	"MinSize" : "2"
        "MaxSize" : "6"
Step 3:
	Change the Target from HTTP to TCP under "HealthCheck"
	"Target" : "TCP:80" (Remove the / )
Step 4:
	Copy the contents of "1802_scaling_policies_and_alarms.txt" and paste those those under
	"WebServerGroup" (The autoscaling group)
Step 5:
	Change the default Web and DB instance types.
	Web:
	Set Default to "t2.micro" under "InstanceType"
      		"Default" : "t2.micro",
	DB:
      	Set Default to "db.t2.micro" under "DBClass"
		"Default" : "db.t2.micro",
Step 6:
	Disable MultiAZ for DB
	Set the Default to "false" in "MultiAZDatabase" section
Step 7:
	Change the AMI details
	Under "AWSRegionArch2AMI" section you need to provide the AMI id.
	- Go to the EC2 Dashboard
	- Click on AMIs in the Left pane
	- Search for the AMIs which are free and also supports HVM
	- Get the id of the AMI
	- Change the ID in the template
	  "us-west-2"      : { "32" : "ami-46da5576", "64" : "ami-7172b611", "64HVM" : "ami-7172b611" }
