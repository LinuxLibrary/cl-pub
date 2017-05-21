# Auto Scaling

- Features
	- Elasticity
	- Bootstraping / Dynamic Configuration
	- CloudWatch or Manual schedule configuration
	- Notifications
	- It is a free feature from AWS

- Configuring Auto Scaling
	- From the Management console go to EC2
	- From the left pane select `Launch Configuration`
	- Click on `Create Auto Scaling Group`

	- Step 1: Select an AMI
	- Step 2: Choose Instance Type
	- Step 3: Configuration Details

	```
	Create Launch Configuration
	Name : webASG
	```

	- Step 4: Add Storage
	- Step 5: Configure Security Group
		- Select the previously created security group
	- Step 6: Review and launch the configuration

	Now you'll be directed to create an Auto Scaling Group
	
	- Step 1: Create Auto Scaling Group Details

	```
	Launch Configuration	: webASG
	Group name		: WebServersASG
	Group Size		: 2 (or as per your choice)
	Network			: Select your VPC
	Subnet			: Select the subnets created under the above VPC

	Advanced Details:
	Load Balancing		: webLB
	Health Check Type	: ELB/EC2 (Already we've configured Health Checks on EC2 instances while configuring the ELB. So this time select ELB)
	Health Check Period	: 300 Seconds
	```

	- Step 2: Configure Scaling Policies

	```
	Create Aut0 Scaling Group

	Select `Use scaling policies to adjust the capacity of this group`
	
	Scale between `min` and `max` instances. This is where we can set the mn and max number of instances scaled
	
	Increase Group Size:
	
	Name : IncreaseGroupSize
	Create Alarm:
	Whenever: `Average` of `CPU Utilization`
	Is: `>=` `70` percent
	For at least: `1` consecutive periods of `5 minutes`
	Name: IncreasedCPUAlarm

	Take the action:
	`Add` `1` `instances` when `70` <= CPUUtilization < `80`
	`Add` `2` `instances` when `80` <= CPUUtilization < `90`
	`Add` `3` `instances` when `90` <= CPUUtilization < +infinity

	Instances need `300` seconds to warm up after each step

	Decrease Group Size:

	Name : DecreaseGroupSize
	Create Alarm:
	Whenever: `Average` of `CPU Utilization`
	Is: `<=` `60` percent
	For at least: `1` consecutive periods of `5 minutes`
	Name: DecreasedCPUAlarm

	Take the action:
	`Remove` `1` `instances` when `60` <= CPUUtilization < `50`
	`Remove` `2` `instances` when `50` <= CPUUtilization < `40`
	`Remove` `3` `instances` when `40` <= CPUUtilization < +infinity

	Instances need `300` seconds to warm up after each step
	
	You can create this as well like above and depending on your choice
	```

	- Step 3: Configure Notifications
	- Step 4: Configure Tags
	- Step 5: Review and create ASG
