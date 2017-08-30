# Internet Gateway (IGW)

IGW will be used to get connectivity between our instances to the internet. Without the IGW our instance will not have any internet connection also we can't be connected to it. Once after creating an Internet Gateway we need to attach it to a VPC we want.

- Go to VPC Service
- Select Internet Gateways
- Create Internet Gateway
- Provide a Tag
- Attach this to our VPC

> Only one Internet Gateway can be attached to a VPC at a time. An IGW cannot be dettached from a VPC while having active AWS resources within the VPC
