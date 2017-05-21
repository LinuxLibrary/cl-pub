# Elastic Load Balancer

- Characteristics
	- Region wide load balancer
	- Can be used internally or externally
	- SSL Termination and Processing
	- Cookie-based sticky session
	- Integrates with Auto-Scaling
	- ELB EC2 health checks / Amazon CloudWatch
	- Integrates with Route53

- ***Configuring ELB***
	- From the Management Console go to EC2
	- From the right pane select Load Balancers
	- Click on `Create Load Balancer`
	- Give the details

	- Step 1 : Define Load Balancer

	```
	Name : webELB
	Create LB Inside : Select your VPC
	Create an Internal LoadBalancer : Check this if you need an Internal one

	LoadBalancer Protocol	LoadBalancer Port	Instance Protocol	Instance Port
	HTTPS/HTTP		443/80			HTTPS/HTTP		443/80

	Select Subnets:
	Select all the subnets spread accross the AZs through which you want to balance your load on
	```

	- Step 2 : Assign Security Groups

	```
	Uncheck the default one and select the one which you've prepared for this
	```

	- Step 3  Configure Security Settings

	```
	Upload your SSL certificate if you have choosen your LB protocol as HTTPS
	```

	- Step 4 : Configure Health Check

	```
	Ping Protocol	: HTTPS/HTTP
	Ping Port	: 443/80
	Ping Path	: /index.html

	Advanced Details:
	Response Timeout	: 2 Secs
	Health Check Interval	: 10 Secs
	Unhealthy Threshold	: 2
	Healthy Threshold	: 10 
	```

	- Step 5 : Add EC2 Instances

	```
	Select your EC2 instances accross the AZs you have
	
	Check the below 2 options
	1. Enable Cross-zone load balancing
	2. Enable connection draining : 300 Secs 
	(This will make the new users not connected to the unhealthy instances and connections on the old instances drained slowly
	but not immediately, depending on what the app/user is doing)
	```

	- Step 6 : Add Tags

	```
	Key	: Name
	Value	: webELB
	```

	- Step 7 : Review
		- Review the changes and create the load balacner
