# Configuring VPC Manually

- ***VPC***
	- Go to the AWS Services and select VPC
	- Click `Your VPCs` from the left pane
	- Click on `Create VPC` and provide the following details

	```
	Name 		: myCustVPC01
	CIDR Block 	: 192.168.0.0/16
	Tenancy	: Default
	```
	
	- Click `Yes Create`

- ***Subnets***
	- Click on `Subnets` in the left pane
	- Click on `Create Subnet`
	- Create 2 subnets with the following details
	- Subnet01
		
		```
		Name			: Subnet01
		VPC			: Select the VPC created earlier
		Availability Zone	: us-ease-1a (In my case)
		CIDR Block		: 192.168.1.0/24
		```

	- Subnet02
		
		```
		Name			: Subnet02
		VPC			: Select the VPC created earlier
		Availability Zone	: us-ease-1b (In my case)
		CIDR Block		: 192.168.2.0/24
		```

- ***Internet Gateway***
	- Click on `Internet Gateways` in the left pane
	- Click on `Create Internet Gateway`
	- Name it

	```
	Name tag : myIGW
	```
	
	- Select that Internet Gateway and click on `Attach to VPC`
	- Select the VPC
	
- ***Route Tables***
	- Now we need to add the Subnets and Internet gateway to the route tables
	- Click on `Route Tables` in the left pane
	- Select the Route Table
	- In the below section click on `Routes` and click on `Edit`
	- Add the Internet Gateway to 0.0.0.0/0 address to allow all the traffic

	```
	Destination 	: 0.0.0.0/0
	Target		: Select your IGW device
	```

	- Click on `Save`
