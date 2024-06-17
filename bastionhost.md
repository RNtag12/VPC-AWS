Creating a bastion host in the public subnet 1 for ssh connection
Specifications for the bastion host:
•	Name: Bastion Host
•	Amazon Machine Image (AMI): Amazon Linux 2023 AMI
•	Instance type: t2.micro and uses the vockey key pair
•	In the network settings, select Rod_VPC and select Public subnet 1
  o	Auto-assign Public IP: enabled
  
• Create a security group that only allows the following traffic:
  o	Type: SSH
  o	Port: 22
  o	Source type: anywhere
