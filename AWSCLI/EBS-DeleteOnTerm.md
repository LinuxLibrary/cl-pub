- Get Public IP of the EC2 instance by instance tag
	aws ec2 describe-instances --filters "Name=tag:Name,Values=jmlpocec2" | jq .Reservations["0"].Instances["0"].NetworkInterfaces["0"].Association.PublicIp

- Change EBS volume DeleteOnTermination action
	aws ec2 modify-instance-attribute --instance-id <INSTANCE_ID> --block-device-mappings "[{\"DeviceName\": \"/dev/sda\",\"Ebs\":{\"DeleteOnTermination\":false}}]"

- Get instance IDS of the instances 1..3
	for i in {1..3}; do aws ec2 describe-instances | jq .Reservations["$i"].Instances["0"].InstanceId | tr -d '"' >> ids.txt; done

- Change EBS volume DeleteOnTermination action for the Instance IDS
	for _ID in `cat ids.txt`; do aws ec2 modify-instance-attribute --instance-id $_ID --block-device-mappings "[{\"DeviceName\": \"/dev/sda1\",\"Ebs\":{\"DeleteOnTermination\":false}}]" ; done

- Get the status of the EBS volume DeleteOnTermination for the instances 1..3
	for i in {1..3}; do aws ec2 describe-instances | jq .Reservations["$i"].Instances["0"].BlockDeviceMappings["0"].Ebs.DeleteOnTermination; done