This is a terraform project to create resources in AWS. You can use this code to create an autoscaling group consisting of 2 servers with the latest Amazon Linux2, 
that are behind an ALB. A VPC is created with 3 public subnets (where ALB resides) and 3 private subnets (where the ASG resides). The ASG connects to the internet through a NAT Gateway. A bastion/VPN server is also created using OpenVPN. This templates assume that you have already created a key that will be pulled from ~/.ssh/ directory and that you have set up the `AWS_ACCESS_KEY_ID` and `AWS_ACCESS_KEY_ID` environment variables.

You can also customize the following variables in the modules file:

```
- vpc_cidr 
- tenancy 
- private0_cidr 
- private1_cidr 
- private2_cidr
- public0_cidr 
- public1_cidr 
- public2_cidr

#VPN user to create
- ovpn_user 

#Instance type for VPN
- instance_type 

#Instance type for web
- instance_type_web 
```
This template uses a script to install OpenVPN made by dumrauf. You can connect to every server with ec2-user using the OVPN file created in your home folder with OpenVPN client.
