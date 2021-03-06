# CREATING AN ELB ( ELASTIC LOAD BALANCER ):
--------------------------------------------

We need to perform the following steps to create a LoadBalancer.
- Create 2 instances running Apache Web Server
- Create a load balancer
- Configure the loadbalancer to send traffic to these instances
- Verify the load balance

Let us configure the instances first
- Go to EC2 Dashboard
- Launch Instance
- Select Amazon Linux AMI and Click Next
- Click on Advanced Details
- Click on User Data
- Give the following script
```
	#!/bin/bash -v 
	yum -y install httpd
	service httpd start
	echo "<h1>WEB-01 $HOSTNAME</h1>" > /var/www/html/index.html
```
- Click Next to Add Storage
- Click Next to Tag Instance
- Click Next to add SG
- Create a new SG for ELB exercise and Allow HTTP and SSH
- Click on Launch

Configure a second EC2 instance in the same way.
- Change the echo command to display WEB02 instead of WEB01


Let us create the Load Balancer and attach the instances into the LB
- Go to EC2 Dashboard
- In the left pane click on Load Balancers
- Create Load Balancer
- Classic Load Balancer
- Give it a name
- Leave it to check for port 80
- Select the ELB SG
- Configure the health checks
- Choose the instances to add to the load balancer
- Select the Load Balancer and click on the Instances tab below
- Wait till the instances status is InService
- Now go to the Description tab and copy the DNS name (A Record)
- Try to open it in a browser or else CURL it.
- You need to notice that is being redirected to both the hosts simultaneously
