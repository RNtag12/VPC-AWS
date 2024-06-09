# VPC-AWS
This is a guide to how you can deploy a Highly available, secure and scalable web application on AWS. it features a VPC architecture in AWS with two public subnets and four private subnets.

<h2>General Information</h2>
Amazon Web Services (AWS) is a subsidiary of Amazon that provides on-demand cloud computing platforms and APIs to individuals, companies, and governments, on a metered, pay-as-you-go basis. 
AWS is the world’s most comprehensive and broadly adopted cloud, offering over 200 fully featured services from data centers globally. <br/>
AWS offers the widest variety of databases that are purpose-built for different types of applications so you can choose the right tool for the job to get the best cost and performance. AWS is architected to be the most flexible and secure cloud computing environment available today. 
With AWS, you can leverage the latest technologies to experiment and innovate more quickly. 
AWS provides a highly reliable, scalable, low-cost infrastructure platform in the cloud that powers hundreds of thousands of businesses in 190 countries around the world.

The official home of AWS is https://aws.amazon.com.

<h2> Project Description</h2>
This project aims to create an AWS infrastructure using CloudFormation templates. The setup includes a Virtual Private Cloud (VPC) with multiple public and private subnets, internet gateways, NAT gateways, security groups, EC2 instances, and an RDS database. The infrastructure supports two main applications: a Café web application and an API application, each with its own security configurations and resource allocations. This project is designed for deploying web and API applications with secure, scalable, and highly available infrastructure components. By incorporating load balancers, auto scaling groups, NAT gateways, carefully configured security groups, and a high-availability RDS instance, the project shows how to set applications using AWS that are both secure and capable of handling varying loads efficiently.
<br />

<h2>Features</h2>

- <b>VPC with 2 public subnets and 4 private subnets</b> 
- <b>Internet gateway for internet access</b>
- <b>NAT Gateway for outbound internet access for instances in Private Subnets </b> 
- <b>EC2 instances for the two applications and bastion host</b>
- <b>RDS instance (database)</b> 
- <b>2 load balancers to handle the traffic</b>
- <b>Auto scaling groups</b> 
- <b>Security groups (firewalls)</b>

<h2>Interactions in the VPC</h2>
The overall solution architecture is made of a VPC that is connected to the internet. The VPC serves as the foundation of the network from which AWS resources can be lunched. For the internet to reach the resources inside of the VPC, an Internet Gateway (IGW in the template) must be created. An IGW acts as a channel for communication between resources in the VPC and the internet. Note that the IGW is connected to the VPC via the VPCtoIGWConnection (VPCGatewayAttachment). In the VPC, there are public subnets and private subnets that will contain the resources that will be used for the project including EC2 instances. Public Private subnet 1 host to web application instances that manage user interactions and receives communication over the internet using port 80. These instances connect to the internet via an Internet Gateway (IGW), which allows both incoming and outgoing traffic. The Application Load Balancer (ALB) distributes incoming traffic evenly among the web instances, ensuring that no one instance is overloaded and therefore improving scalability and flexibility. In Private subnets 1 and 2 there are also API Endpoint instances. Those instances allow programmatic access to the application over port 5000, which is only accessible by web instances via configured security groups. The private subnets connect to the internet via NAT Gateways which prevents direct internet access of the private subnets from the internet. The database instance (RDS) is on private subnet 3 and 4 and cannot be accessed directly from the internet. It is only accessible from the web application instance with read and write access enabled using IAM roles. The RDS Database instance can also be accessible It enables high availability with multi-AZ deployment, ensuring uninterrupted operation during disruptions. Security groups and IAM roles maintain access controls, enabling only authorized instances to interface with the database and therefore assuring more security within the VPC..
<br />

<h2>Steps to execute the project</h2>

- <b>Launch the cloud formation template attached in the project</b> 
- <b>Create a bastion host to SSH to your instances in the private subnets</b>
- <b>Create a launch template and configure  auto scaling groups</b> 
- <b>Create target groups and attach them to application load balancers </b>
- <b>Update the auto scaling groups to match your specifications</b>



